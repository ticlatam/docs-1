---
title: API Reference
weight: -1000
source: 'https://github.com/TheThingsNetwork/node-app-sdk/blob/master/DOCUMENTATION.md'
---

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## Application

Application is an application on the network.

Type: {appId: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), payloadFormat: PayloadFormat, decoder: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, converter: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, validator: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, encoder: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, registerOnJoinAccessKey: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?}

**Properties**

-   `appId` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `payloadFormat` **PayloadFormat** 
-   `decoder` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `converter` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `validator` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `encoder` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `registerOnJoinAccessKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 

## key

Generates a new key to be used for Lora

**Parameters**

-   `length` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)**  (optional, default `16`)

## is-token

Returns true if the passed in string
is a json web token, and false otherwise.
It does NOT validate the token signature.

**Parameters**

-   `str` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** 

## 

A token that can register ApplicationSettings

## setup

Setup function that prepares the environment with the required
application and devices for testing.

## PayloadFunctions

PayloadFunctions is an object that bundles the payload functions of an
application.

Type: {decoder: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, converter: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, validator: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, encoder: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?}

**Properties**

-   `decoder` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `converter` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `validator` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `encoder` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 

## open

`open` creates and opens a HandlerClient for the application with the specified ID.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The ID of the application you want to manage.
-   `accessKerOrToken` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `opts` **[DiscoveryOptions]({{< relref "../#discoveryoptions" >}})?** Optional options to pass to the Discovery client.
-   `tokenOrKey`  The Access Token or Access Key used to authenticate.

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[HandlerClient]({{< relref "../#handlerclient" >}})>** 

## AccountClient

`Account` is a client for The Things Network account server API.
It can be used to manage applications and their EUIs, as well as gateways.
Either a Bearer Token or an Application Access Key can be used for
authentication. The latter method allows to use the `getApplication()`
function only.

Example:

    const account = new Account("accesKeyOrToken", "https://customserveradress.org")

**Parameters**

-   `accessKeyOrToken` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `serverAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)**  (optional, default `"https://account.thethingsnetwork.org"`)

### getAllApplications

Gets metadata about all applications that are accessible with
the given accessToken

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[AccountApplication]({{< relref "../#accountapplication" >}})>>** 

### getApplication

Gets the information that is stored about a given application.
This includes the EUIs, name access keys, collaborators.
The properties that can be retrieved depend on the rights of
the used authorization mechanism.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[AccountApplication]({{< relref "../#accountapplication" >}})>** 

### createApplication

Creates a new application on the account server.

**Parameters**

-   `app` **[MinimalAccApplication]({{< relref "../#minimalaccapplication" >}})** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;any>** 

### deleteApplication

Removes an application from the account server.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;any>** 

### addCollaborator

Adds a collaborator with a set of access rights to the given application.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `collaborator` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `rights` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[AppAccessRights]({{< relref "../#appaccessrights" >}})>** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;any>** 

### deleteCollaborator

Removes a collaborator by her username from an application

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `collaborator` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;any>** 

### addEUI

Adds an EUI to the given application. Must be hexadecimal with a length of 16.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `eui` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;any>** 

### deleteEUI

Removes an EUI from the given application.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `eui` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;any>** 

## HandlerClient

`Handler` is a  client for The Things Network handler APIs.
It can be used to get data from an application or to manage devices.

Example:

    const handler = new Handler("my-app-id", "my-app-access-key")

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `appAccessKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `opts` **[DiscoveryOptions]({{< relref "../#discoveryoptions" >}})?** 

### open

`open` opens the client to the handler.

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[HandlerClient]({{< relref "../#handlerclient" >}})>** 

### data

Open a data client that can be used to receive live application data

Returns **[DataClient]({{< relref "../#dataclient" >}})** 

### application

Open a application manager that can be used to manage the settings and devices of the
application.

Returns **[ApplicationClient]({{< relref "../#applicationclient" >}})** 

## DiscoveryOptions

Type: {address: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, insecure: [boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?, certificate: ([Buffer](https://nodejs.org/api/buffer.html) \| [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String))?}

**Properties**

-   `address` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `insecure` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** 
-   `certificate` **([Buffer](https://nodejs.org/api/buffer.html) \| [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String))?** 

## ApplicationClient

A client that manages devices on the handler.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `tokenOrKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `netAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `certificate` **([Buffer](https://nodejs.org/api/buffer.html) \| [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String))?** 

### constructor

Create and open an application manager client that can be used for
retreiving and updating an application and its devices.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The ID of the application you want to manage
-   `tokenOrKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The Access Token or Access Key used to authenticate
-   `netAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The gRPC address of the handler where the application is registered
-   `certificate` **([Buffer](https://nodejs.org/api/buffer.html) \| [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String))?** An optional certificate used to connect to the handler securely

Returns **void** 

### get

Get the application

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Application]({{< relref "../#application" >}})>** 

### setPayloadFormat

Change the payload format of the application.

**Parameters**

-   `format` **PayloadFormat** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### setCustomPayloadFunctions

Set the custom payload functions of the application and set the format
to custom.

**Parameters**

-   `fns` **[PayloadFunctions]({{< relref "../#payloadfunctions" >}})**  (optional, default `{}`)

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### setRegisterOnJoinAccessKey

Set the registerOnJoinAccessKey or remove it.

**Parameters**

-   `to` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### unregister

Unregister the application from the handler.

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### devices

List the devices of the application

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;Device>>** 

### registerDevice

Register a device in the application.

**Parameters**

-   `devID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `device` **DeviceUpdates** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### device

Get the device specified by the devID

**Parameters**

-   `devID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;Device>** 

### updateDevice

Update the device specified by the devID with the specified updates

**Parameters**

-   `devID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `updates` **DeviceUpdates** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### deleteDevice

Delete the specified device.

**Parameters**

-   `devID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** 

### getEUIs

Returns the EUI(s) for this application from the account server.

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)>>** 

### getDeviceAddress

Return a device address for the given constraints.

**Parameters**

-   `usage` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;Usage>** The list for wich the address will be used.

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Buffer](https://nodejs.org/api/buffer.html)>** address - A buffer containing the address.

## ApplicationSettings

ApplicationSettings hold the settings of an application.

Type: {payloadFormat: PayloadFormat?, registerOnJoinAccessKey: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?}

**Properties**

-   `payloadFormat` **PayloadFormat?** 
-   `registerOnJoinAccessKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 

## DataClient

DataClient is a client for The Things Network data API.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `appAccessKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `mqttAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

### constructor

Creates a new DataClient and opens the MQTT connection.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `appAccessKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `mqttAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **void** 

### close

Close the mqtt connection

**Parameters**

-   `force` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** passing it to true will close the client right away, without waiting for the in-flight messages to be acked
-   `callback` **[Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)?** will be called when the client is closed

### end

Same as close (for backwards compatibility).

**Parameters**

-   `force` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** 
-   `callback` **[Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)?** 

### on

Starts listening to events.

Possible events (application messages):

-   `uplink` (or `message`): Messages sent by the devices to the appliction.
-   `activation`: An alias for the `activations` (see `event`)
-   `event` (or `device`): Events that happen to devices. You can filter on
    the events by adding more parameters. For instance:
    -   `downlink/scheduled`
    -   `downlink/sent`
    -   `activations`
    -   `create`
    -   `update`
    -   `delete`
    -   `down/acks`
    -   `up/errors`
    -   `down/errors`
    -   `activations/errors`

See [The MQTT API Reference](https://www.thethingsnetwork.org/docs/applications/mqtt/api.html)
for more information about these events and what their payloads look like.

MQTT connection events:

-   `error`: An error occured / the initial connection failed.
-   `connect`: A connection to the MQTT broker was established.
-   `disconnect`: The connection to the MQTT broker was lost.
-   `reconnect`: A reconnect to the MQTT broker is attempted.
-   `close`: A connection (attempt) failed.

**Parameters**

-   `event` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name of the event to listen to.
-   `args` **...[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;any>** 
-   `devID`  An optional devID. If not passed will subscribe to the event for all devices.
-   `callback`  The callback to call when the event occurs.

**Examples**

```javascript
// listens to all uplinks from all devices
client.on("uplink", function (devID, message) {})
```

```javascript
// listens to all uplinks from the device with id `foo`
client.on("uplink", "foo", function (devID, message) {})
```

```javascript
// listens to all device events for all devices
client.on("event", function (devID, message) {})
```

```javascript
// listens to all device events for device with id `foo`
client.on("event", "foo", function (devID, message) {})
```

```javascript
// listens to the `downlink/scheduled` events for device with id `foo`
client.on("event", "foo", "downlink/scheduled", function (devID, message) {})
```

```javascript
// listens to the `downlink/scheduled` events for all devices
client.on("event", "+", "downlink/scheduled", function (devID, message) {})
```

Returns **void** 

### off

Stop listening to events.
The argument structure is the same as for `on()`.

**Parameters**

-   `event` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `args` **...[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;any>** 

Returns **void** 

### send

Send a downlink message to the device with the specified device ID.

**Parameters**

-   `devID` **DeviceID** The device ID of the device to send the downlink to.
-   `payload` **(PayloadArray | PayloadRaw | [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) | PayloadFields)** The raw payload as a Buffer, an Array of numbers, a hex string  or an object of payload fields.
-   `port` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** The port to send the message on.
-   `confirmed` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Set to true for confirmed downlink.
-   `schedule` **Schedule** Set to the scheduling you want to use (first, last or replace).

## Service

Service is an enum of the possible services types to get from the discovery
server.

Type: (`"router"` \| `"broker"` \| `"handler"`)

## application

`application` creates and opens an ApplicationClient for the application with the specified ID.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The ID of the application you want to manage
-   `accessKeyOrToken` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The Access Token or Access Key used to authenticate
-   `opts` **[DiscoveryOptions]({{< relref "../#discoveryoptions" >}})?** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[ApplicationClient]({{< relref "../#applicationclient" >}})>** 

## app

The app used for testing

## 

Settings for the discovery server

## Announcement

Announcement is an announcement on the discovery server.

Type: {id: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), serviceName: [Service]({{< relref "../#service" >}}), serviceVersion: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), description: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), pb_public: [boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean), url: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), netAddress: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), mqttAddress: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), apiAddress: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), publicKey: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, certificate: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?, metadataList: [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;any>?}

**Properties**

-   `id` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `serviceName` **[Service]({{< relref "../#service" >}})** 
-   `serviceVersion` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `description` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `pb_public` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** 
-   `url` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `netAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `mqttAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `apiAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `publicKey` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `certificate` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 
-   `metadataList` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;any>?** 

## data

`data` creates and opens an DataClient for the application with the specified ID.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The ID of the application you want to manage
-   `accessKeyOrToken` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The Access Token or Access Key used to authenticate
-   `opts` **[DiscoveryOptions]({{< relref "../#discoveryoptions" >}})?** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[DataClient]({{< relref "../#dataclient" >}})>** 

## 

Settings for the handler

## account

`account` creates an AccountClient for the user associated to the specified key or token.

**Parameters**

-   `accessKeyOrToken` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The Access Token or Access Key used to authenticate
-   `serverAddress` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The URL to the account server to use. Defaults to "<https://account.thethingsnetwork.org>"

Returns **[AccountClient]({{< relref "../#accountclient" >}})** 

## Discovery

Discovery is a client for The Things Network discovery API

**Parameters**

-   `opts` **[DiscoveryOptions]({{< relref "../#discoveryoptions" >}})**  (optional, default `{}`)

### constructor

Create a new Discovery client.

**Parameters**

-   `opts` **[DiscoveryOptions]({{< relref "../#discoveryoptions" >}})**  (optional, default `{}`)

Returns **void** 

### getAll

`getAll` returns announcements for all services known to
the discovery server that match the service name.

**Parameters**

-   `serviceName` **[Service]({{< relref "../#service" >}})** The name of the services to look for, eg. `"handler"`

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Announcement]({{< relref "../#announcement" >}})>>** 

### get

`get` returns the announcement for the service with the
specified service name and id.

**Parameters**

-   `serviceName` **[Service]({{< relref "../#service" >}})** The name of the services to look for, eg. `"handler"`
-   `id` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The id of the service to look for, eg. `"ttn-handler-eu"`

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Announcement]({{< relref "../#announcement" >}})>** 

### getByAppID

`getByAppID` gets a handler announcement by application ID.
It looks up the handler the application is registered to.

**Parameters**

-   `appID` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Announcement]({{< relref "../#announcement" >}})>** 

## AppAccessRights

AppAccessRights

Type: (`"settings"` \| `"delete"` \| `"collaborators"` \| `"devices"` \| `"messages:up:r"` \| `"messages:up:w"` \| `"messages:down:w"`)

## services

services is a map with the known service names for the discovery server.

Type: {}

### Handler

Handler is a Handler service

### Router

Router is a Router service

### Broker

Broker is a Broker service

## MinimalAccApplication

The minimal payload for to the POST /applications route
of the account server

Type: {id: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), name: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)}

**Properties**

-   `id` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 

## AccountApplication

AccountApplication contains the metadata of an application
returned by the account server. Presence of optional fields
depends on the [access rights]({{< relref "../#appaccessrights" >}}) of the used accessKey / -token.

Type: any