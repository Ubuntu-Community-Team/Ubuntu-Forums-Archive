---
title: "ASUS Eee PC 900 - 1015P - slow wireless and solution on Ubuntu 11.04 Natty Narwhal"
date: 2011-06-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ducuit on 2011-06-17
I am posting this in case anyone's had the same problem I have with two different generations of Eee PCs and two different Ubuntu versions (10.10 and 11.04).

Wireless connected quickly and did not freeze the laptop. However, the loading of pages took a long while as if trying to find domain name servers (DNS).

The problem, apparently, was the power management policy of the wireless card. This should be disabled.

To do this, follow these steps:
1. run in a terminal this command:
iwconfig
This is how you find out the interface of your wireless card. For me, it was wlan0 but it could be eth0, eth1 or other.

2. open a root nautilus:
sudo nautilus /etc/pm/power.d/

3. create an empty file with the name **wireless** in that directory.

3. enter the following in the newly created file, wireless (replace wlan0 with your interface if necessary):
#!/bin/sh
/sbin/iwconfig wlan0 power off

4. make sure your file is executable:
sudo chmod +x /etc/pm/power.d/wireless

5. restart or relogin in and see if problem persists.

---

### Post by The Ratman on 2012-11-02
I'm using Ubuntu 12.10 on an Eee PC 1001PQ and I confirm that this seems to solve the problem. Thanks, ducuit!

---

### Post by mike acker on 2012-11-04
I'm using an ASUS PCE-N10 

it is giving max. 10Mb/sec on 12.04:(

both my Win7 boxes getting 40 Mb/sec:)

i'll give your fix a try

---

### Post by mike acker on 2012-11-04
here's what comes of iwconfig:
```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AckerNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:AA:4B:11:85:F3   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

eth0      no wireless extensions.

```looks like power management is already off ....

but it still runs slowly

---

### Post by The Ratman on 2012-11-14
Here are some things I also tried (as well as turning off power management as described above). I'm using 12.10 (and loving it!)

TURN OFF HARDWARE ENCRYPTION

sudo -s
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

INSTALL BACKPORTED WIRELESS MODULES

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic

COMPILE COMPAT-WIRELESS

I think this actually does pretty much the same thing as installing backported wireless modules as above. There are some very good instructions for this [here]("http://askubuntu.com/questions/121932/ath9k-driver-reinstallation") (see 2nd answer). When I tried this something went a bit wrong and it messed up by system - but it's worked for others!

OTHER SOLUTIONS

I found some other solutions which I didn't actually try but apparently they helped others.

- disable rfkill polling (not sure what this means or how to do it)
- change System Settings > Network > Wireless > Options > IPv6 Settings > Method to Link-Local Only

---

### Post by The Ratman on 2012-11-22
I just want to confirm that changing the IPv6 Settings (as described above) really did seem to help - particularly with web applications that continually communicate with the server e.g. Google Docs.

---

