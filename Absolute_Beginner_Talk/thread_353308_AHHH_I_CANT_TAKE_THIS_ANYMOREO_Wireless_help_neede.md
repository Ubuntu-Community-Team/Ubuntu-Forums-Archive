---
title: "AHHH I CANT TAKE THIS ANYMORE:O Wireless help needed"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by hotstuff on 2007-02-04
alright i finally got Ubuntu 6.10 installed on my computer a few days ago. Now i cant get my wireless USB dongle to work. it is a Linksys WUSB54G v4 and i think i need to get a driver for it. I have searched this on Google and even on these forums and i still dont get it:( Can some one help me? I cant live without Internet. and i hate CONSTANTLY switching back and fourth between windows and Ubuntu to use it.

---

### Post by hotstuff on 2007-02-04
Anyone? At this point im desperate:(

---

### Post by shareMenaPeace on 2007-02-04
Maybe this?
[http://ubuntuforums.org/showthread.php?t=225206&highlight=Linksys+usb](http://ubuntuforums.org/showthread.php?t=225206&highlight=Linksys+usb)

Or search the forum for linksys usb and such.

---

### Post by Bachstelze on 2007-02-04
You'll probably need [Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for this.

---

### Post by hotstuff on 2007-02-04
ahh this is so hard:(

---

### Post by deadgobby on 2007-02-04
Ahhh it can be a bugger. If you are getting flustered. Just away for a bit and hit agian.

---

### Post by Bachstelze on 2007-02-04
It's really not hard... Where are you stuck ?

---

### Post by hotstuff on 2007-02-04
> **HymnToLife said:**
> It's really not hard... Where are you stuck ?

im stuck at the Ndiswrapper installation. Im using this guide [http://www.ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G](http://www.ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G)
whenever i try to extract it. it dosent work.

---

### Post by phossal on 2007-02-04
This is one way of getting ndiswrapper off the cd:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```
Then you'll confirm it's installed using:
```
ndiswrapper -v
```

---

### Post by hotstuff on 2007-02-04
> **phossal said:**
> This is one way of getting ndiswrapper off the cd:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```
Then you'll confirm it's installed using:
```
ndiswrapper -v
```

its not on a cd:S

---

### Post by hotstuff on 2007-02-04
okay well i just extracted the ndiswrapper folder by right clicking it and pressing extract. now i have a ndiswrapper folder, but the command line prompts sudo make uninstall, etc. isnt working

---

### Post by phossal on 2007-02-04
You didn't install Ubuntu using a CD? How did you do it? If you're trying to *compile* your own ndiswrapper, as I suggest in my signature, you're going to need build-essential. It's a catch-22. You need either a CD or the internet for *that* too. You get build-essential to *build* ndiswrapper from the same places you *get* ndiswrapper.

---

### Post by hotstuff on 2007-02-04
i already have Ubuntu installed and yes i used a cd. So are you saying if i enter those command prompts while the cd is inside, i can install ndiswrapper?

---

### Post by hotstuff on 2007-02-04
ok i pop the cd in and i entered it in, apparently to update the files i need internet, thats the problem IM using Ndiswrapper to get my Wireless card to work so i can connect to the internet....what do i do now?

---

### Post by mdsmedia on 2007-02-04
> **hotstuff said:**
> ok i pop the cd in and i entered it in, apparently to update the files i need internet, thats the problem IM using Ndiswrapper to get my Wireless card to work so i can connect to the internet....what do i do now?The commands given should provide access to the CD to get the packages, rather than the internet.

---

### Post by phossal on 2007-02-04
> **hotstuff said:**
> ok i pop the cd in and i entered it in, **apparently to update the files i need internet, thats the problem** IM using Ndiswrapper to get my Wireless card to work so i can connect to the internet....what do i do now?

You're can use the install CD to get ndiswrapper even *after* you've installed Ubuntu. Then you can use ndiswrapper to install your wireless driver. 

[Edit] I think, once you put the cd in, it will open the package manager. Then you can search for ndiswrapper and install it. Otherwise, you have to use the commands I listed previously.

---

### Post by hotstuff on 2007-02-04
> **phossal said:**
> You're can use the install CD to get ndiswrapper even *after* you've installed Ubuntu. Then you can use ndiswrapper to install your wireless driver. 

[Edit] I think, once you put the cd in, it will open the package manager. Then you can search for ndiswrapper and install it. Otherwise, you have to use the commands I listed previously.

thanks man, the sudo apt-get update was going to the internet for some weird reason. But i left the command out and went to the sudo apt-get install ndiswrapper and it started to install thanks alot :D

---

### Post by phossal on 2007-02-04
Welcome. :D

---

### Post by hotstuff on 2007-02-04
NVM i figured it out:P

---

### Post by shareMenaPeace on 2007-02-04
> **hotstuff said:**
> haha i already have another question. One of the steps in this faq [http://www.ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G](http://www.ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G) is too take the installation cd for the network card and copy the WUSB54Gv4 folder to my home folder. and launch it using /home/username/WUSB54Gv4 but everytime i enter this it dosent launch i just get a: No such file or directory error. What is wrong?

Use your USERNAME not "username" it is just a placeholder.

For example
/home/hotstuff/   and linux is case sensitive just in case your username is Hotstuff.

---

### Post by hotstuff on 2007-02-05
I followed everystep in the Guide and it didnt work:S The driver is installed but it dosent show up in networking:S

---

### Post by shareMenaPeace on 2007-02-05
> **hotstuff said:**
> I followed everystep in the Guide and it didnt work:S The driver is installed but it dosent show up in networking:S
Open 
System -> Administration .-> Synaptic Package Manager

search for ndiswrapper - is it installed? If not install it. (checkbox and apply)

---

### Post by hotstuff on 2007-02-05
Yes i installed it already. i dont know whats wrong. I followed that Guide Carefullly and asked questions whenever i needed help:S

---

### Post by shareMenaPeace on 2007-02-05
The bottom part of the guide, did you done all the ndiswrapper instructions?
Was there old driver?

Do you get an error message?

What is the output of

```
sudo ndiswrapper -l
```
This should show the new driver i guess (Dont have ndiswrapper installed).

---

### Post by hotstuff on 2007-02-05
it says rt2500 installed

---

### Post by shareMenaPeace on 2007-02-05
Did you boot?

Is the usb device under System -> Administration -> Networking?

---

### Post by hotstuff on 2007-02-05
> **shareMenaPeace said:**
> Did you boot?

Is the usb device under System -> Administration -> Networking?

No thats the problem, its not showing up there.

---

### Post by shareMenaPeace on 2007-02-05
You donw all the ndiswrapper steps from the guide?

Basicly what you had todo was:

Install ndiswrapper
Get the driver 
Install driver

So ndiswrapper seems to work you also have the driver so maybe you didnt installed the driver?

Go back to the guide and check if you done all steps maybe uninstall the rt driver and than proceed as the guide states.

If this still not help create a new topic with a relevant headline. Something like: usb linksys wireless device not working.

---

### Post by shareMenaPeace on 2007-02-06
Ok i found a list with supported cards for ndiswrapper and yours is on it. I  even foudn a link to your driver

```
Card: Linksys WUSB54GPv1

    * Chipset: Prism54
    * USBID: Vendor=5041 ProdID=2235 (5041:2235)
    * Driver: I got this working (with WPA-PSK CCMP/TKIP) effortlessly using the ndiswrapper/wpa_supplicant packages bundled on the Ubuntu 6.06 CD. I used the Linksys WUSB54GPv4 1.02.00 driver release here which also includes the WUSB54GPv1 drivers in their own folder. I have not checked if this driver is the same as the one in the seperate WUSB54GPv1 driver release; I just know it works. Also, i had to blacklist the islsm modules (www.prism54.org) that ship with Ubuntu. 
```
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
As in your guide - if you not done this allready --  "blacklist the islsm modules (www.prism54.org)".

Download link to the driver
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1115416827517](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1115416827517)

The above driver should work if not try the below.
[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416827622&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416827622&pagename=Linksys%2FCommon%2FVisitorWrapper)

---

### Post by hotstuff on 2007-02-06
> **shareMenaPeace said:**
> Ok i found a list with supported cards for ndiswrapper and yours is on it. I  even foudn a link to your driver

```
Card: Linksys WUSB54GPv1

    * Chipset: Prism54
    * USBID: Vendor=5041 ProdID=2235 (5041:2235)
    * Driver: I got this working (with WPA-PSK CCMP/TKIP) effortlessly using the ndiswrapper/wpa_supplicant packages bundled on the Ubuntu 6.06 CD. I used the Linksys WUSB54GPv4 1.02.00 driver release here which also includes the WUSB54GPv1 drivers in their own folder. I have not checked if this driver is the same as the one in the seperate WUSB54GPv1 driver release; I just know it works. Also, i had to blacklist the islsm modules (www.prism54.org) that ship with Ubuntu. 
```
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
As in your guide - if you not done this allready --  "blacklist the islsm modules (www.prism54.org)".

Download link to the driver
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1115416827517](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1115416827517)

The above driver should work if not try the below.
[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416827622&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416827622&pagename=Linksys%2FCommon%2FVisitorWrapper)
Thanks, ill try it again after i get home from school tommorow. Thanks Again

---

### Post by hotstuff on 2007-02-06
Nvm

---

