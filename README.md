# Corona_ePaper_8266

![](https://i.imgur.com/vy0qx5z.jpg) 

### Sorry if this doesn't work immediately or properly, this is my first time sharing a Node-RED/Home Assistant project :)

## Parts:

Wemos D1 Mini (or any ESP8266-based board)

Connected D0 (GPIO16 to Reset)

![](https://i.imgur.com/AT4EOcy.jpg) 

Waveshare 4.2-in e-Paper screen

![](https://i.imgur.com/5Ylv8Ce.jpg) 

TP4056 charge/protect board

In the hot glue blob is a MCP1700 3.3V Voltage Regulator (with low q. current) SOT-23 package

![](https://i.imgur.com/jfcO4Ig.jpg) 

## Software:

#### Without delta:

Home Assistant and ESPHome

ESPHome:

I used Google's Roboto Font.

[https://fonts.google.com/specimen/Roboto](https://fonts.google.com/specimen/Roboto)

Home Assistant: 

- Need Coronavirus integration (included in newest updates)

- For temp. reading, need this in configuration.yaml

```
sensor:
  - platform: template
    sensors:
      temperature:
        unit_of_measurement: '°F'
        value_template: "{{ state_attr('weather.home', 'temperature') }}"
```

#### With delta:

Same as above, but including some Home Assistant addons, Node-RED and influxDB

In order to keep using ESPHome (and because it was easy-ish), I made Node-RED output to a sensor in Home Assistant.

Home Assistant:

- [https://github.com/zachowj/hass-node-red](https://github.com/zachowj/hass-node-red)  (can be installed via HACS or manually)

Node: 

- [https://github.com/zachowj/node-red-contrib-home-assistant-websocket](https://github.com/zachowj/node-red-contrib-home-assistant-websocket) 

Influx: uses database named `corona`