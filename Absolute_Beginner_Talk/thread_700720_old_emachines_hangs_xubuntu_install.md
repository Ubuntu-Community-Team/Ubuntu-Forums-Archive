---
title: "old emachines hangs xubuntu install"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Lgevo on 2008-02-18
strange problem...tired ubuntu an xubuntu both alternatives also...but after i select install text or oem it will go to the black screen with the curser flashing an nothin will happen any advice its a celron intel with 633mhz made for windows me and 2000

---

### Post by erginemr on 2008-02-18
On the screen with the Ubuntu logo, there should be a list of function keys that you can use to set the screen resolution. I think the one through which you can select a lower resolution is F6. Try this to see if it helps.

Otherwise, you may download and install from the Ubuntu Alternate CD, which uses a text-based installer.

---

### Post by nickpaton on 2008-02-18
Hi and welcome to Ubuntu (Xubuntu!) and the forums!

Couple of things you need to check.

First that your PC has the following minimum system requirements:

> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to have at least 128 MB RAM.

The above is from [http://www.xubuntu.org/get]("http://www.xubuntu.org/get")

As Erginemr suggests, download and install using the 'Alternative' text version 

Secondly make sure your install CD has burnt correctly.

At the first install screen, run the option "check CD integrity" (or similar wording).  This makes sure that you have downloaded and burnt the install CD correctly.

If it says that there are errors, check the md5sum of the orginal download.
If it's OK try burning the CD again but at around x4 speed.  Don't use CDRW's which tend not to work very well.

If you don't know how to check md5sums search the forums and / or post back here for help.

Finally when you're at the first install screen, press F6 key and at the end of the command line which appears add:

```
noapic
```

and hit the enter key to run the install.

I've been using this program a lot recently and found it to work very well on older PC's and laptops.

Good luck and let us know how you get on.

Nick

---

### Post by Lgevo on 2008-02-18
Hey actually i have been using the alternitive sense i couldnt get the regular one to work.....still no luck sits on the black screen curser flashing in the top corner an nothin happens cant type anything either i hit install text based an then it just gose to that screen an sits
please any advice would help

---

### Post by Lgevo on 2008-02-18
nickpaton i will try what u have said i posted my last message a lil after u an before i seen u posted thx

---

### Post by Lgevo on 2008-02-19
ok the problem was in the bios it was set for only windows 98-2000 not used to old machines shoulda looked here 1st...but new problem INTEL(0): AGPGART...cant startx or anything stuck in command line any ideas??

---

