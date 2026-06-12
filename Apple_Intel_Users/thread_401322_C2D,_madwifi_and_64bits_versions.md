---
title: "C2D, madwifi and 64bits versions?"
date: 2007-04-04
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-04-04
Now we have a version of madwifi for latest atheros airport extreme chipset and then, we don't have to use ndiswrapper 32 bits drivers for wireless.
Is anything more doesn't work with 64 bits version? I am testing Feisty beta in a new macbook, but i will try soon 64 bits feisty.

Can anyone tell me if it seems to be ok?

---

### Post by wigglydiggly on 2007-04-04
I've been using ndiswrapper with feisty on my C2D macbook for a while.  You're saying that I don't need to continue using it.  May I ask how do I remove it and start using madwifi?  Any input advice would be appreciated.

Thanks in advance.

---

### Post by gmc on 2007-04-06
> **Azathoth_ said:**
> Now we have a version of madwifi for latest atheros airport extreme chipset and then, we don't have to use ndiswrapper 32 bits drivers for wireless.
Is anything more doesn't work with 64 bits version? I am testing Feisty beta in a new macbook, but i will try soon 64 bits feisty.

Can anyone tell me if it seems to be ok?

Well I've done some testing of the [new atheros]("http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n") driver on my White Macbook and Ubuntu (feisty) 64bit. There's good news and bad.

The driver works quite well with my Linksys wrt54g router (using dd-wrt) if the network uses no wireless encryption, but as soon as I introduce either wep/wpa/wpa2 encryption, the driver can't connect to the router. This is definitely a step in the right direction.

My recommendation is not to  rely  on this driver just yet, but I would certainly recommend tracking it.

Gord

---

### Post by Azathoth_ on 2007-04-07
> **gmc said:**
> Well I've done some testing of the [new atheros]("http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n") driver on my White Macbook and Ubuntu (feisty) 64bit. There's good news and bad.

The driver works quite well with my Linksys wrt54g router (using dd-wrt) if the network uses no wireless encryption, but as soon as I introduce either wep/wpa/wpa2 encryption, the driver can't connect to the router. This is definitely a step in the right direction.

My recommendation is not to  rely  on this driver just yet, but I would certainly recommend tracking it.

Gord

Ahhh, this is the reason because i cannot connect to my wep using madwifi... :( Ok, a right step in the final way

---

### Post by H264 on 2007-04-12
How would I go about installing this driver? I have an iMac C2D, and wireless is the only way I can get internet to the room I am in.

---

### Post by gmc on 2007-04-13
> **H264 said:**
> How would I go about installing this driver? I have an iMac C2D, and wireless is the only way I can get internet to the room I am in.

Hi,

Well if you'd like to try the driver, you'll need the following packages:
```
sudo apt-get install gcc g++ libc6-dev linux-headers-`uname -r` build-essential debhelper 
``` then simply download the [driver]("http://snapshots.madwifi.org/madwifi-hal-0.9.30.10-current.tar.gz").
 Then ```
tar xvfz madwifi-hal-0.9.30.10-current.tar.gz
``` switch to the driver directory and  ```
sudo make; sudo make install
```Gord

---

### Post by Azathoth_ on 2007-04-13
gmc: you forgot to put aftersudo make install 
```
sudo modprobe ath_pci
```

---

### Post by gmc on 2007-04-13
> **Azathoth_ said:**
> gmc: you forgot to put aftersudo make install 
```
sudo modprobe ath_pci
```

Hi Azathoth,

:-) Your right, I did! Thanks for correcting me.

Gord

---

### Post by Azathoth_ on 2007-04-15
:) You're welcome

---

### Post by jajajavi on 2007-06-08
Then… I must to reinstall Ubuntu in my macbook c2d. What do you recommend to install now? 64 or 32? Gracias!

---

### Post by ronocdh on 2007-06-08
> **jajajavi said:**
> Then… I must to reinstall Ubuntu in my macbook c2d. What do you recommend to install now? 64 or 32? Gracias!
I don't quite understand. For 64-bit processors, I personally will always recommend a 64-bit operating system. Why do you say "then..."?

---

### Post by kzm. on 2007-06-09
i am a newbee. i am using ubuntu now for a year or so on my old pc laptop. 
i bought a macbook, because (believe it or not), for its specs and look it was cheaper than the pc's i would have wanted.

i have feisty 64bit running, but my wireless shows up and dissapears when ever it feels like. it never hooked me up to anything neither (no wpa or anything needed), though shows correctly wireless signals around me. i use mad wifi as discribed above, as i understood the wrapper are for 32bit and wont work under 64bit (i thought i read this a couple of times somewhere). the heat problem is ok. i installed smcfancontrol on osx and that allows you to set the fan speed. i actually set it to the minimum.. i like silence around me. and osx gets pretty hot as well. osx boots in no time and if i run eclipse on osx it also opens up much faster. i couldnt get the brightness control working, even though it should just work and the right mouse button problem (i think using f12 and f11 is an unpractical solution) i couldnt get working neither (mouseemu and gsynaptics are conflicting). also the mousepadscroll doesnt work and tapping makes me crazy, so i turned it simply off. for booting i used refit, i guess thats nicer than bootcamp. battery is less under ubuntu, but cpu goes nicely down to 4% or even 1% (i read people saying its up to 100% or 54% at least all the time)

i hope this helps you.

---

### Post by excrabot on 2007-06-15
> **gmc said:**
> Hi,

Well if you'd like to try the driver, you'll need the following packages:
```
sudo apt-get install gcc g++ libc6-dev linux-headers-`uname -r` build-essential debhelper 
``` then simply download the [driver]("http://snapshots.madwifi.org/madwifi-hal-0.9.30.10-current.tar.gz").
 Then ```
tar xvfz madwifi-hal-0.9.30.10-current.tar.gz
``` switch to the driver directory and  ```
sudo make; sudo make install
```Gord

Hi, forgive me but when you say switch to the driver directory, where is that more specificaly.. i'm lost at that point.

yes, i am somewhat newb like when it comes to linux and trying to get everything ironed out on my macbook C2D.

thnks

---

### Post by kzm. on 2007-06-17
you unpacked it.. so it should be right in front of you. do 

$ cd madwifi-hal-[press the tab and it will complete for you. if not press twice the tap and it will show you whats possible]

if you lost track of your installation you can locate it by

$ locate madwifi-hal

it probably should be in your home folder

$ cd ~/

if the locate doesnt find it update your locate through

$ slocate -u

might take some time (no response)

---

