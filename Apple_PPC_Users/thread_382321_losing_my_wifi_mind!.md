---
title: "losing my wifi mind!"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by indica on 2007-03-11
ok,i'll admit it  i'm not totally brilliant with ubuntu, i've been running it on my desktop system for a long time without any of the problems i'm currently experiencing, but it is the least used of the three comps i have

i'm about ready to tear my hair out.  i've reinstalled dapper like 4 times now and if i have to install again i'm gonna scream.  

i'm using an ibook g4, it's a airport extreme, bcm4306 and i've tried the wifidocs walkthrough, both it and the short posting at the end in troubleshooting.  i've also tried the nickm one. and the 4306 w ndiswrapper howto, i can't get this to work and i have no idea what i'm doing wrong here

i had high hopes for being able to use somethin easy like network manager......grrr

---

### Post by x64Jimbo on 2007-03-11
First of all, why are you using Dapper? The latest version is Edgy, and it works a lot better with WiFi than Dapper.

---

### Post by maggot_brain on 2007-03-11
I'd try the 6.10 release or wait until 7.04 comes out sometime in April.  Also NDiswrapper won't work on PowerPC machines as it's a method of using Windows drivers under Linux.  Windows drivers are only for X86 (Intel and AMD processors.

I've heard that under the latest development releases of 7.04 (also known as Feisty) Airport Extreme works fine.  The driver for the Broadcom chipsets were integrated into kernel 2.6.17 which comes with Ubuntu 6.10 but you'll want the latest version of the kernel 2.6.20 which will be included in 7.04.

My advice - be patient and wait until 7.04 is released!

---

### Post by indica on 2007-03-11
> **x64Jimbo said:**
> First of all, why are you using Dapper? The latest version is Edgy, and it works a lot better with WiFi than Dapper.

i know i suck :) but i was having problems getting edgy at the time and i had dapper handy on a disk......i was feelin lazy and i'm under some time pressure to get this ibook up and running so i can sell my windows laptop.   i don't relish the thought of having to hang out at my desktop instead of on my nice comfy couch

i'd read that ndiswrapper wouldn't work on a powerpc maching but i'm getting desperate ;)

---

### Post by trash on 2007-03-13
> **indica said:**
> i know i suck :) but i was having problems getting edgy at the time and i had dapper handy on a disk......i was feelin lazy and i'm under some time pressure to get this ibook up and running so i can sell my windows laptop.   i don't relish the thought of having to hang out at my desktop instead of on my nice comfy couch

i'd read that ndiswrapper wouldn't work on a powerpc maching but i'm getting desperate ;)

ya i'm going to try sativa and see if that helps:lolflag:

---

### Post by indica on 2007-03-13
hehehe thanks trash!

ok so i'm seriously losing my mind.  after many late nights, tons of coffee, and several more frustrating install/partitioning/angry software problems,  i'm now running edgy, and followed the robino howto again, and STILL my stupid wifi doesn't work

so can anyone tell me specifically what driver i should be extracting firmware from for an airport extreme?  it seems to list several and i think i'd rather poke my eyes out with hot pins than install AGAIN if this doesn't work this time.
also should i be using network-manager?  it says it shouldn't work for some macs yet it seems to be working on mine just fine, just not registering my wireless network

i have a straight-jacket, i'm not afraid to use it

---

### Post by patwrik on 2007-03-14
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)


Try this method...I have the same card and tried the methods that you have tried with no worky....

This method did work for me though...

---

### Post by ditsch on 2007-03-14
If you still have your OS X on a separate partition, you could also use your own firmware from OS X. The firmware is located in ```
/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2
``` 

I am using networkmanager in Feisty on an iBook G4 and it is great. No probs so far (except some trouble after returning from suspend).

---

### Post by indica on 2007-03-15
that howto didn't work for me, but i just re-installed this time from the alternate instead of the live cd so we'll see how that goes this time

no, i got rid of osx :(   but i will get the disc back soon so....i suppose i could put it on there, i may have to.....

did you still have to extract the firmware in feisty?
how's it running in general?

---

### Post by ditsch on 2007-03-15
No, I didn't have to extract manually. During the installation of bcm43xx-fwcutter, the firmware was downloaded and extracted by the package. So, all I had to do to get Airport Extreme to work was to install the fwcutter, no pre- or post-installation tasks.

In general, with Feisty there are the usual obstacles with PPC. The only thing that is a bit weird at the moment is suspend behaviour of the iBook, which forces me to reboot sometimes after returning from suspend.

---

### Post by indica on 2007-03-15
grrrrrr  i wish i didn't have to wait until april for feisty if it was that easy.   i don't want to wait that long if it's going to be that is.  this is ridiculously frustrating

---

### Post by indica on 2007-03-15
ok so it looks like the driver is working properly but under iwconfig i'm getting access point invalid, what does that mean?

---

### Post by ditsch on 2007-03-15
Network-Manager is way easier than configuring your net with iwconfig, at least when you don't know the command options. Are you using encryption in your network? Can you see the access point when you do ```
iwlist eth1 scan
```?

---

### Post by indica on 2007-03-15
ya, but network manager is more frustrating to me than just troubleshooting it through the terminal
i've been using ubuntu for ages on my desktop pc, just never tried it on an ibook before
 iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:0D:3A:25:C0:FF
                    ESSID:"yellowsubmarine"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-48 dBm  
                    Extra: Last beacon: 68ms ago

---

### Post by ditsch on 2007-03-15
Which kind of encryption do you use? Perhaps you need to configure that first, especially if you are using WPA/WPA2.

---

### Post by indica on 2007-03-15
wep and it seems to recognize that just fine

---

### Post by indica on 2007-03-16
ok so i switched routers and that didn't help any....though it resulted in an awesome signal boost in my windows lappy

does anyone know what this is?  p.s. i'm cute and willing to pay you in kisses

---

### Post by ditsch on 2007-03-16
Can you turn off encryption for testing? Just to ensure this is not an encryption-related thing.

---

### Post by x64Jimbo on 2007-03-16
> **indica said:**
> p.s. i'm cute and willing to pay you in kisses
Bribery, eh?
 :lolflag:

---

### Post by indica on 2007-03-16
if i have to resort to bribery...yes :D ;)

---

### Post by indica on 2007-03-16
i've tried the encryption thing, doesn't seem to help, but i'll try that again once i'm done dual-booting, i had to give up and put mac os back on.  i need to get rid of the windows lappy i'm using now.  funny enough the wireless worked flawlessy in mac os......almost enough to make a person sell out ;)

---

