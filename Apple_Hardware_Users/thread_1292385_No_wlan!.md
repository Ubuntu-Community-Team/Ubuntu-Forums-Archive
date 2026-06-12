---
title: "No wlan?!"
date: 2009-10-15
forum: Apple Hardware Users
---

### Post by Ali Kante on 2009-10-15
Hi folks,

this is my first post here. Hope, that many will follow... :P
I'm an IT consultant 8-), but my Linux skills are a little bit rusted :-\" and actually I'm having some problems installing ubuntu on a MacBookPro 5,5.

Here's the actual task:

yesterday I installed ubuntu 9.04 onto the MacBook and nearly everything worked fine. Even the wireless card worked, after a kick with /etc/init.d/network start.

Being happy that everything worked, I did an apt-get update+upgrade and after a reboot the wlan was gone.

the card will still be recognized:

```
lspci
Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller

```typing
```

ifconfig wlan0

```gets me an unsatisfying

```
wlan0: ERROR while getting interface flags: No such device

```thus remaining me in a state of confusion.

---

### Post by alexmurray on 2009-10-16
Try reinstalling bcmwl-kernel-source:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```

Sometimes the dkms build systems seems to fail even though it looks like it succeeds and the module isn't built properly, and so a rebuild usually fixes it. In this case it probably failed when you updated to a newer kernel, which would have forced a rebuild of the module.

---

### Post by Ali Kante on 2009-10-16
Hmm... I get this error:
```
E: Couldn't find package bcmwl-kernel-source
```

Hmm, trying to find it:
```
apt-cache search bcmwl
```

returned nothing. :confused:

---

### Post by charger01 on 2009-10-16
Ubuntu is simply NOT compatible with macbook pro 5,5:

- wlan not working out of the box
- lcd backlight control not working at all
- keyboard backlight control not working, and these is no way to turn it on
- sound not working out of the box, you have to recompile driver at every kernel changes

---

### Post by Ali Kante on 2009-10-16
> **charger01 said:**
> Ubuntu is simply NOT compatible with macbook pro 5,5:

- wlan not working out of the box
- lcd backlight control not working at all
- keyboard backlight control not working, and these is no way to turn it on
- sound not working out of the box, you have to recompile driver at every kernel changes

This URL tells me something else:
[it works]("https://help.ubuntu.com/community/MacBookPro5-5/Jaunty")

---

### Post by charger01 on 2009-10-16
> **Ali Kante said:**
> This URL tells me something else:
[it works]("https://help.ubuntu.com/community/MacBookPro5-5/Jaunty")

That link _**do not**_ tell the truth.
Try by yourself.

Is keyboard backlight working?
Is sound working?
Is led brightness controls working?

---

### Post by Ali Kante on 2009-10-16
> **charger01 said:**
> That link _**do not**_ tell the truth.
Try by yourself.

Is keyboard backlight working?
Is sound working?
Is led brightness controls working?

No
No 
No

:(

---

### Post by charger01 on 2009-10-16
> **ali kante said:**
> no
no 
no

:(


bam!

Ubuntu _**IS NOT**_ (yet) compatible with latest macbook pro.

The question is: there are any notebook that are perfectly 100% compatible with Ubuntu out of the box or after an easy drivers (free or not) installation? 

There are someone out there that asking why linux is not yet widely diffuse? :|

I gave you a clue.

.........

Ok, someone could argue that this is the price for a freedom. 
But for how long time we will can afford to pay this price?

I can't any more. I had to work with a perfect machine, or at least I can't be crazy serching over internet to find how to get sound working with ***[main_distro][version_name][version_status][desktop_environment][de_version][kernel_version][daily_built_timing]***....because even a variation of a last digit of kernel version can make the difference between can boot my pc or not...

I live this life for 10 (ten) years...this is not about passion for a compurt science, this is a about sadomasochism..
Ten years is passed by, but seems that nothing has changed. Now linux is more beauty to see and to use, but the "entry wall" is high like ten years ago. A simple update is enough to cause my computer stop working.

---

### Post by Ali Kante on 2009-10-17
You're right. It's very frustrating and time consuming. I have to work with that machine. Don't want to configure and troublesearch the whole day. Actually it's 3 days already.

---

### Post by guybrush.d on 2009-10-22
Hi Alicante,
I was full of doubts like you, but when i googled a lot and a lot and a lot i discovered linux can everything,
i have bought in february an apple ibook clamshell 'cause i've always desidered it, anyway i don't like mac os
for this laptop, i thought that linux can gave me more satisfactions so i removed mac os and began the trial.

First of all i removed netowrk manager an installed wicd, i think is smarter then iI started with various version of ubuntu,
 but i didn't get a lot of things working, so i tried slackintosh and even opensuse and then the things went better...

But you know we are here because we LOVE Ubuntu so i began a new trial, i removed everything and installed jaunty
then with apt  xubuntu-desktop and now i have a wonderful xubuntu 9.04 working on my clamshell. 
In 8 months of working i haven't been able to make the wifi working but last week a light got bright in my mind :guitar:, and i found this:
[http://www.linux-wireless.org/Drivers/](http://www.linux-wireless.org/Drivers/)

i haven't all on my hands but i posted a reply to another user, you can use the module airport and orinoco, (i loaded it into /etc/modules file) and troughout bcm43xx firmware (you have to put it into /lib/firmware)  after a reboot everything will work! Just browse the forum for wireless posts you will 
find my complete "how to" into a reply, you can find some good help into the opensuse forums, the firmware must be downloaded trought git. The only thing that doesn't work, and i have asked help for it, is the light of the wireless card, with opensuse it worked but not with ubuntu. 

HTHC!
(hope this helped, Ciao):P

PS.: JUST FOUND! Here is the copy of my early post:

Hi,
I just solved it!:razz: It was since February (when i got the clamshell) that i was looking for the solution! Well the problem is the airport and orinoco modules need a firmware to manage the airport card, if you look into the boot logs you should find some lines that say "Lucent/Agere firmware not found in /lib/firmware" or something. You just need to copy 
a file called "agere_sta_fw.bin" to /lib/firmware reboot and the wifi will work, you can get all the needed info on [COLOR=Red]_[http://linuxwireless.org/en/users/Drivers/orinoco](http://linuxwireless.org/en/users/Drivers/orinoco)_[/COLOR] 
2 more things:

1) you will need git-core to download the git repository.
2) the reported problem on firmare broken didn't happen to me so i didn't used recode_utf8, see the webpage for details.

The only thing that i don't like is that the light of wireless doesn't work i asked help and i'm waiting, i know it can because i tried opensuse before xubuntu and the light was flashing on it, but i love xubuntu for the laptop! so i'm waiting...CIAO!

---

