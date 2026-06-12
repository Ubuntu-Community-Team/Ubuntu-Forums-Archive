---
title: "ndiswrapper issues"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-08
hello all, i have posted a bunch of questions on wireless networking, which were prommplty answered, thx to everybody that helped, but i am still having a few issues.

i have ubuntu 6.10 edgy installed on an external harddrive which i boot off of onto my laptop.

my laptop's wireless card is a dell 1350 wireless card that i know uses a brodcom chipset. i have installed ndiswrapper succesfully but still cannot connect to my network because i have wpa encryption settings on my router that i won't remove (pesky nieghbors:lolflag:). 

but when i still cannot connect i ran 

```

 sudo pccardctl ident
```

and it returned something to the effect of

socket 0 
no vendor information.

i have no idea how to fix that, even after reading the how-to, i am a super noob and have no idea how to follow the next step.

i was wondering if that could be the problem or if there is something else i should try

thx a lot

---

### Post by Bachstelze on 2007-03-08
That *pccardctl* command is for PCMCIA cards, which is not what you want. Is your wireless adapter correctly detected (i.e. does it appear in *iwconfig*) ?

---

### Post by gameman12 on 2007-03-08
oooo thanks a lot. how dumb of me.

it does, but i still can't connect to my wpa network

---

### Post by Bachstelze on 2007-03-08
I can't help you then, as I rarely use WiFi and never WPA. This [Wiki page](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) seems quite helpful, though.

---

### Post by gameman12 on 2007-03-08
ooo,, thx for the link, i've tried that but my problem is i cannot acces the interent to download a wpa supplicant or network manager.

any suggestions?

---

### Post by Bachstelze on 2007-03-08
I'm 99% sure those packages are on your Ubuntu CD. Try to apt-get them and see if you're prompted for it.

---

### Post by gameman12 on 2007-03-08
i am using the live cd. i will try that. i have never been prompted but i have gotten many error messaages that iu have never bothered reading.

hahaha. r they on the live cd as well???

---

### Post by DNightFall on 2007-03-08
Yes, both of those are on the CD.

Have you checked to see if your **/etc/modprobe.d/ndiswrapper** file correctly alias's your hardware?

```
sudo gedit /etc/modprobe.d/ndiswrapper
```
should give you
```
alias eth1 ndiswrapper
```
where in this case eth1 is the logical identifier for my wireless hardware.

This was wrong as eth1 is where the system put my wireless and after configuring ndiswrapper, the alias line referred to wlan0.  After changing wlan0 to eth1, I was able to connect to my wireless router which I had temporarily set to unsecured while getting my card up and running. 

Then after installing the wpasupplicant:
```
sudo gedit /etc/network/interfaces
```
and configured:
```
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <ssid>
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <generated key>

auto eth1
```
for my wpa to work.

The WPA config is explained:
[http://www.ubuntuforums.org/showthread.php?t=318539]("http://www.ubuntuforums.org/showthread.php?t=318539")

Hope this helps!

---

### Post by gameman12 on 2007-03-08
thx sooo much guys. that was extremely helpful. i will try those steps for wpa as well, i just don't want to turn off the wpa settings. like i said, pesky neighbors. hahaha

so if i just put the live cd in my drive and enter the codes it will automaticlly install them?

i am a SUPER NOOB

---

### Post by DNightFall on 2007-03-08
Oops, forgot to mention that I only showed the lines of my **interfaces** file that concerned my wireless adapter.  I didn't remove all other lines and just left the lines shown.

Didn't want to leave any confusion!

---

### Post by gameman12 on 2007-03-08
ty, that would have thrown me off. haha.

i'm gonna try it now. i'll be back on the forum tonight to post if it worked or not.

so i just put the cd in the drive and use the install commands?

---

### Post by gameman12 on 2007-03-08
.

---

### Post by DNightFall on 2007-03-08
That or use Synaptic Package Manager.

---

### Post by gameman12 on 2007-03-08
ok, i did that i and it said it couldn't find the installer...

how can i fix that?

---

