---
title: "[Android] HOWTO: Ad hoc Wi-Fi for Android"
date: 2013-03-06
forum: Any Other OS
---

### Post by prodigy_ on 2013-03-06
This is a quick and quite dirty guide to configuring custom Wi-Fi on Android including ad hoc. It's not really step-by-step and assumes a fair bit of knowledge but still (hopefully) can be useful.


**Preamble:**

Last summer I bought an Android 2.3.5 based device and I've treated it mostly as a regular mobile phone. But at some point curiosity always defeats laziness. Last week I finally decided to dig a little deeper. After installing terminal emulator I instantly realized that for anything serious I would need to learn adb (basically Java). Well, how about something really simple then? Like configuring wireless to suit my needs? 


**Option 1 – regular Wi-Fi:**

The easiest way to get a Wi-Fi connection going on Android is (obviously) to connect to a hotspot or router. For that you don't need this howto. If you have a laptop with a wireless chipset that supports AP mode you can simply [turn it into a hotspot](http://thenewbieblog.wordpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu/).

As for me I don't have a wireless router at home but I have two rather old laptops. Unfortunately both have Intel 3945ABG Wi-Fi which works perfectly fine under Linux but doesn't support AP mode.


**Option 2 – reverse tethering:**

Well, let's try the other way round then – enable Wi-Fi hotspot mode on the phone and connect to it from a laptop. This certainly works but I don't want regular tethering, I want reverse tethering and NAT that will allow me to use my wired Internet connection. Temporary NAT on a Linux machine is pretty straightforward:

```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo /sbin/iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
```

Should be good enough. Trying to ping 8.8.8.8 from the phone – damn, doesn't work. Annoying but expectable. **route -n**. No dice. **route del default**. No, on Android they doesn't support this option either, only **route add …**. Alright (on the phone from root shell):
```
route add default gw 192.168.43.252 dev ap0
setprop net.dns1 8.8.8.8 # resolv.conf is NIH so we need our own way
setprop net.dns2 8.8.4.4
```

Well, everything works now and I can ping both ways and open webpages in browser. Time to d/l some SSH server? Evidently not, because Google Store downloads are stuck at *Waiting for network...* WTF? With some googling I found out that the store relies on Google Talk for downloading and Google Talk won't even try to connect unless it finds a regular Wi-Fi or cellular data connection. In other words “No we won't just send a packet and wait for timeout like any sane program would do.”


**Option 3 – ad hoc wireless: **

Since I want to d/l some apps, tethering won't do. Time to try something else... Oh, it's quite easy to [create an ad hoc network](https://help.ubuntu.com/community/WifiDocs/Adhoc#Wireless_Extensions_CLI_tools_Method) with iwconfig. There's no guarantee that your Android device will see such networks but mine does.

Unfortunately I can't force my laptop card to use WPA in ad hoc mode, so I create an open network in this example and limit communication by using a /30 subnet (not a great solution in the long run but there's always OpenVPN):

```
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 4
sudo iwconfig wlan0 essid 'network-name'
sudo ip link set wlan0 up
sudo ip addr add 10.0.0.1/30 dev wlan0
```

Surprisingly for Android you need the same commands except that issue them from root shell without sudo and specify a different IP (in my example there's only one: 10.0.0.2). But first you need to turn on Wi-Fi in your device settings and try to "connect" to your ad hoc network (it will automatically "connect" when you change settings with iwconfig).

Note: Android likes to revert wireless to managed mode so it's a good idea to make a shell script with all necessary commands.

NAT/routing is the same as for reverse tethering (see above) except that you need to specify the correct device when you add the default route on the Android device. In my case it's ap0 for tethering and wlan0 for ad hoc.

---

### Post by Chogan on 2013-04-24
dows this method work with ubuntu 12.04 and android 4?
is there any command to find if my wifi supports AP mode?

---

### Post by prodigy_ on 2013-04-24
> **Chogan said:**
> dows this method work with ubuntu 12.04 and android 4?
Should work with 12.04 but I'm not sure about android 4. Try and find out.

> **Chogan said:**
> is there any command to find if my wifi supports AP mode?
Yeah: [https://help.ubuntu.com/community/WifiDocs/MasterMode#Test_an_adapter_for_.22master_mode.22](https://help.ubuntu.com/community/WifiDocs/MasterMode#Test_an_adapter_for_.22master_mode.22)

---

