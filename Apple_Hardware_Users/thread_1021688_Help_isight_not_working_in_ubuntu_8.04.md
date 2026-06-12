---
title: "Help: isight not working in ubuntu 8.04"
date: 2008-12-25
forum: Apple Hardware Users
---

### Post by etlizzie on 2008-12-25
I switched to linux about a month or two ago and haven't had too many problems. But try as I may, I cannot get isight to work. I've been reading the threads that talk about it, but I have had no luck.

Help? Can someone please tell me how to get isight to work. I'm running on a macbook 1,2.

---

### Post by hajk on 2008-12-26
> **etlizzie said:**
> I switched to linux about a month or two ago and haven't had too many problems. But try as I may, I cannot get isight to work. I've been reading the threads that talk about it, but I have had no luck.

Help? Can someone please tell me how to get isight to work. I'm running on a macbook 1,2.The FAQ at the the top of this Apple forum section has a Howto on getting iSight to work under Ubuntu 8.04 (Hardy). Can you tell us how that Howto failed you? Then we'll take it from there.

---

### Post by etlizzie on 2008-12-27
I added the mactel ppa. from there entered the codes that followed.

this is what i got:

lizzie@lizzie-laptop:~$ $ sudo apt-get update
bash: $: command not found
lizzie@lizzie-laptop:~$ $ sudo apt-get install isight-firmware-tools
bash: $: command not found
lizzie@lizzie-laptop:~$

---

### Post by pxwpxw on 2008-12-27
> **etlizzie said:**
> I added the mactel ppa. from there entered the codes that followed.

this is what i got:

lizzie@lizzie-laptop:~$ $ sudo apt-get update
bash: $: command not found
lizzie@lizzie-laptop:~$ $ sudo apt-get install isight-firmware-tools
bash: $: command not found
lizzie@lizzie-laptop:~$
You seem to have an extra $ there?
```

sudo apt-get update

```

---

### Post by etlizzie on 2008-12-28
Ok. that step worked.

how do i do the next step:
Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware

---

### Post by pxwpxw on 2008-12-28
> **etlizzie said:**
> Ok. that step worked.

how do i do the next step:
Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware
Have you done this
```

sudo apt-get install isight-firmware-tools

```

---

### Post by etlizzie on 2008-12-28
Yes, did that.

lizzie@lizzie-laptop:~$ sudo apt-get install isight-firmware-tools
[sudo] password for lizzie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
isight-firmware-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

how do i do the next step?

thank you for going through this step by step with me, i really appreciate it.

---

### Post by pxwpxw on 2008-12-28
> **etlizzie said:**
> Yes, did that.

lizzie@lizzie-laptop:~$ sudo apt-get install isight-firmware-tools
[sudo] password for lizzie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
isight-firmware-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

how do i do the next step?

thank you for going through this step by step with me, i really appreciate it.

You have to get the original AppleUSBVideoSupport file
 from your MacOSX system and copy it to /lib/firmware/ before the next step.

This is also explained in this other howto which might be a bit clearer
[https://help.ubuntu.com/community/AppleiSight](https://help.ubuntu.com/community/AppleiSight)

I just installed on my MacBook2,1 and it is working for cheese,
after I did a complete shutdown and restart when the install wass finished.

Is that ok, I am off to sleep now.

---

### Post by etlizzie on 2008-12-28
Ok, so I couldn't figure out how to do that.

I have the original Mac OS X system load discs, how do I extract the AppleUSBVideoSupport file from that?

---

### Post by pxwpxw on 2008-12-29
> **etlizzie said:**
> Ok, so I couldn't figure out how to do that.

I have the original Mac OS X system load discs, how do I extract the AppleUSBVideoSupport file from that?

Ah, you dont have Mac OSX installed. I looked at the MacOSX dvd but could not find the AppleUSBVideoSupport.

But google AppleUSBVideoSupport got this one - (some other refs too)

[http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt)

you can download it, I tried it , it worked, it checks out same size as my MacOSX version and gives the same size isight.fw.
 
But watch out for the popups from that site.

I just downloaded it to my test directory and extracted the isight.fw from there.
Like this -

pxw@wdc:~/test$ sudo ift-extract -a AppleUSBVideoSupport.txt 
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully
Then shut down completely and restart.

---

