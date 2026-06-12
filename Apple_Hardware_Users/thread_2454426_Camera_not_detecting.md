---
title: "Camera not detecting"
date: 2020-11-29
forum: Apple Hardware Users
---

### Post by luuhuu on 2020-11-29
Hello, i'm new to the forums and I switched from Mac os to Ubuntu and the laptop's built-in camera is not detecting in the cheese application or any application that is using a camera.

---

### Post by yapidumoac on 2020-11-29
What's the exact make and model of the laptop and what version of Ubuntu? Type this at the console:

$xinxi -F

[How To Install "inxi" Package on Ubuntu]("https://zoomadmin.com/HowToInstall/UbuntuPackage/inxi")

---

### Post by luuhuu on 2020-11-29
Ubuntu 20.04 and 11-inch macbook air I belive.

---

### Post by wildmanne39 on 2020-11-29
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by yapidumoac on 2020-11-29
> Ubuntu 20.04 and 11-inch macbook air I belive. 

There are 11 (eleven) different versions of the Macbook Air. Without knowing the exact make and model, it is impossible to progress with this technical support request. Do you mind providing the results of xinxi -F ..
[URL="https://support.apple.com/en-gb/HT201862"]
Identify your MacBook Air model[/URL]

---

### Post by ActionParsnip on 2020-11-30
What is the output of:
```

sudo dmidecode -t 1; lsusb; lsb_release -a; uname -a

```
Thanks

---

### Post by luuhuu on 2020-11-30
So I used the command line on terminal. what information do you need?

---

### Post by luuhuu on 2020-11-30
Actually you said you want the make and model of the laptop. Where can I find that in the specs information while I used "[COLOR=#000000]xinxi -F[/COLOR]" on terminal?

---

### Post by ActionParsnip on 2020-11-30
All of it. Copy the text and paste as an update so we can see what the command output says...

---

### Post by luuhuu on 2020-11-30
System Information
	Manufacturer: Apple Inc.
	Product Name: MacBookAir6,1
	Version: 1.0
	Serial Number: C02KVC7VF5N7
	UUID: ad9e864e-7972-fa56-a5d3-902cb199eadb
	Wake-up Type: Power Switch
	SKU Number: System SKU#
	Family: MacBook Air
is this what you wanted?

---

### Post by luuhuu on 2020-11-30
xinxi -F didn't work for some reason so I used the one Action gave me.

---

### Post by ajgreeny on 2020-11-30
It's not ***xinxi -F***, it should be ***inxi -F***

Thta must have been a typo by yapidumoac.

---

### Post by luuhuu on 2020-12-01
ah

---

### Post by luuhuu on 2020-12-01
```
System:
  Host: "name"-MacBookAir Kernel: 5.4.0-54-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Apple product: MacBookAir6,1 v: 1.0 
  serial: <superuser/root required> 
  Mobo: Apple model: Mac-35C1E88140C3E6CF v: MacBookAir6,1 
  serial: <superuser/root required> UEFI: Apple v: 427.0.0.0.0 
  date: 10/21/2020 
Battery:
  ID-1: BAT0 charge: 28.9 Wh condition: 34.5/38.8 Wh (89%) 
CPU:
  Topology: Dual Core model: Intel Core i5-4250U bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 895 MHz min/max: 800/2600 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel Haswell-ULT Integrated Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 5000 (HSW GT3) 
  v: 4.5 Mesa 20.0.8 
Audio:
  Device-1: Intel Haswell-ULT HD Audio driver: snd_hda_intel 
  Device-2: Intel 8 Series HD Audio driver: snd_hda_intel 
  Device-3: Broadcom and subsidiaries 720p FaceTime HD Camera 
  driver: bdc-pci 
  Sound Server: ALSA v: k5.4.0-54-generic 
Network:
  Device-1: Broadcom and subsidiaries BCM4360 802.11ac Wireless Network 
  Adapter 
  driver: wl 
  IF: wlp3s0 state: up mac: 84:38:35:4d:a4:7c 
Drives:
  Local Storage: total: 113.00 GiB used: 14.10 GiB (12.5%) 
  ID-1: /dev/sda vendor: Apple model: SSD SD0128F size: 113.00 GiB 
Partition:
  ID-1: / size: 110.23 GiB used: 14.09 GiB (12.8%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 61.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 251 Uptime: 22m Memory: 3.79 GiB used: 2.59 GiB (68.4%) 
  Shell: bash inxi: 3.0.38 
```
okay I used inxi -F in terminal this time I think it gives more information.

---

