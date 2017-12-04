# Embedding the RuuviTag measurements to your site
## Required materials
* RuuviTags
* Raspberry Pi or similar gateway with network connectivity
* Server on the cloud

## Setting up InfluxDB and Grafana
* Provision a server. We prefer to use Digital Ocean for our VPSes, if you want to support us please use this (referral link)[https://m.do.co/c/97709646a3b5] to get some free credits for your server as well as to give use some referral credits.
* Install (InfluxDB)[https://docs.influxdata.com/influxdb/v1.3/introduction/installation/] and (Grafana)[http://docs.grafana.org/installation/debian/].

## Setting up Raspberry Pi
* Install (RuuviCollector)[https://github.com/Scrin/RuuviCollector] as per instructions at the repository.
* Configure the hostname or IP address and InfluxDB user and password in ruuvi-collector.properties
* Whitelist MACs of your tags if necessary (usually you do not have to whitelist tags).

## Setting up this site
* Folder grafana-files has a custom font as well as css for grafana. Install these to your Grafana's public folder, typically at 
/usr/share/grafana/public/
* Setup Grafana dashboard, either by importing dashboard.json or by configuring the dashboard with GUI. 
Remember to adjust the MACs of your graphs. You can select "light" theme which has vanilla Grafana CSS by appending `&theme=light` to the URL you're browsing.
* Setup the paths to your panels, typically you need to adjust only panelids. 
* This version of site loads the Grafana in iframes, which gives you access to real-time data. On the other hand, it results in a lot of connections
and downloads. On high-traffic sites or when you want to reduce size of your site download please consider using prerendered images instead of iframes. 