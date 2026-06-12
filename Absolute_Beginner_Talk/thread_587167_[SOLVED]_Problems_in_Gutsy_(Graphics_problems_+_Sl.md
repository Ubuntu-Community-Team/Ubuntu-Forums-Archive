---
title: "[SOLVED] Problems in Gutsy (Graphics problems + Slow interne + No help)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by DaraJava on 2007-10-22
Hello all, 

I am having problems with my Gutsy. They are as follows:

[LIST]
[*]1 Slow internet
Ever since I got Gutsy this was slow. Haven't a clue whats going on here. EDIT: Internet is wireless and I am using a Dell wireless card.


[*]2 Graphics Problems
Before I upgraded to Gutsy I had problems similar to this: 
My graphics card is ati. I had problems with drivers from day one. I wanted desktop effects to work but they wouldn't. glxgears was running at about 500 fps. I eventually found a driver that worked fine (glx at about 2000) but when I went on to desktop effects it said "composite extensions not available" It also says this when I go to System>Preferences>Appearence>Visual effects . 


[*]3 No help
Help was up in the tool bar When I first upgraded. Gone now. Don't know why, how, or when.
[/LIST]

If I could get help on any of these problems I would be grateful, 

Thanks a mil,

Dara

---

### Post by molly_001 on 2007-10-23
You would need to tackle each problem one at a time, but it sounds to me like you did an upgrade and not a full-on installation of Gutsy onto a freshly formatted partition.  Is this correct?

Thanks and I'll await your reply.

---

### Post by DaraJava on 2007-10-23
> **molly_001 said:**
> You would need to tackle each problem one at a time, but it sounds to me like you did an upgrade and not a full-on installation of Gutsy onto a freshly formatted partition.  Is this correct?

Thanks and I'll await your reply.

Yeah you're right. Just an upgrade.

---

### Post by mhiggins on 2007-10-23
Check to see if your eth0 is in "roaming" mode. If it is it will likely have the wrong DNS servers. It will try to use your router as opposed to your ISP. I had the exact same problem. When I took the eth0 controller to Static IP and added in the DNS servers it started flying again !!

---

### Post by molly_001 on 2007-10-23
Are you in a position to be able to install Gutsy as a fresh install (not an upgrade) onto a freshly formatted position?  There have been a lot of issues I am reading about with folks who did the upgrade process.  If you were to grab an .iso of the Alternate Install CD, you would be able to install onto the partition upon which Ubuntu resides now, and I will bet that at least two of three of the problems in the OP will go away because of network and graphics configuration from the install start.

---

### Post by DaraJava on 2007-10-24
mhiggins, Yeah eth0 is in roaming mode but I don't see how that effects my internet speed because I am using a wireless connection. P.S. I am from Ireland too (kildare)

Molly, I would like to completely get rid of Ubuntu and install the whole thing on a freshly formatted drive, not partition. But I don't want to get rid of any of the programs or files that I have on my PC at the moment. Is there a possible way to do this? 


Thanks, 

Dara.

---

### Post by mhiggins on 2007-10-24
The roaming configuration will not allow you to change you DNS servers. It's the DNS servers that are the key to network performance (at least they were for me).

---

### Post by molly_001 on 2007-10-24
> **DaraJava said:**
> DaraJava wrote . . .

 I would like to completely get rid of Ubuntu and install the whole thing on a freshly formatted drive, not partition. But I don't want to get rid of any of the programs or files that I have on my PC at the moment. 



Dara,
We would have to make sure we are talking about the same meaning of the word "drive" and "partition".  To make that easier, answer this question:  Does your computer have one hard drive (physical metal object)?  Or does it have more than one hard drive?

---

### Post by P4man on 2007-10-24
Had the same with internet speed. Turned out it was caused by IPv6. Many people suffer from this, its easily solved though.

First, in firefox address bar, type "about:config". Locate "network.dns.disableIPv6" and set it to true.
restart firefox.

For some people that solves is already, not for me. Second thing to do then:

sudo gedit /etc/modprobe.d/aliases

Locate the line that has "alias net-pf-10" (and then something, don't recall what). Change it to "alias net-pf-10 off"

reboot, enjoy full speed internet again.

---

### Post by Jerry N on 2007-10-24
> **DaraJava said:**
> 

.. glxgears was running at about 500 fps. I eventually found a driver that worked fine (glx at about 2000) but when I went on to desktop effects it said "composite extensions not available" 



I don't have any help for your problem but where did you find the drivers that improved your glxgears response?  

Jerry

---

### Post by DaraJava on 2007-10-24
[QUOTE=mhiggins]
The roaming configuration will not allow you to change you DNS servers. It's the DNS servers that are the key to network performance (at least they were for me).[/QUOTE]
You were right. I changed it and it helped along with P4man's suggestion. Thank you.

[QUOTE=molly_001]
Dara,
We would have to make sure we are talking about the same meaning of the word "drive" and "partition". To make that easier, answer this question: Does your computer have one hard drive (physical metal object)? Or does it have more than one hard drive?[/QUOTE]
Yeah, I realise now that what I said was a bit ambiguous. I mean that my computer has one hard drive and I want to format the whole thing to get a brand spanking new Ubuntu on it. I don't see the point of having two Ubuntus (Ubunti?) on the same drive

[QUOTE=P4man]
Had the same with internet speed. Turned out it was caused by IPv6. Many people suffer from this, its easily solved though.

First, in firefox address bar, type "about:config". Locate "network.dns.disableIPv6" and set it to true.
restart firefox.

For some people that solves is already, not for me. Second thing to do then:

sudo gedit /etc/modprobe.d/aliases

Locate the line that has "alias net-pf-10" (and then something, don't recall what). Change it to "alias net-pf-10 off"

reboot, enjoy full speed internet again.[/QUOTE]
Thank you so much this made everything much faster!


[QUOTE=Jerry]
I don't have any help for your problem but where did you find the drivers that improved your glxgears response?

Jerry[/QUOTE]
fglrx I think. Not too sure though.





[QUOTE=DaraJava]
I am having problems with my Gutsy. They are as follows:

[SOLVED]    * 1 Slow internet
      Ever since I got Gutsy this was slow. Haven't a clue whats going on here. EDIT: Internet is wireless and I am using a Dell wireless card.[/SOLVED]
    * 2 Graphics Problems
      Before I upgraded to Gutsy I had problems similar to this:
      My graphics card is ati. I had problems with drivers from day one. I wanted desktop effects to work but they wouldn't. glxgears was running at about 500 fps. I eventually found a driver that worked fine (glx at about 2000) but when I went on to desktop effects it said "composite extensions not available" It also says this when I go to System>Preferences>Appearence>Visual effects .

    * 3 No help
      Help was up in the tool bar When I first upgraded. Gone now. Don't know why, how, or when.
[/QUOTE]
One down, two to go! That was the one that was the most important so the other two don't really matter as much. Although I would like some wobbly windows!

Thank you all for responding,

Dara

---

### Post by molly_001 on 2007-10-24
[quote=darajava]Darajava wrote ...
 
my computer has one hard drive and I want to format the whole thing to get a brand spanking new Ubuntu on it. I don't see the point of having two Ubuntus (Ubunti?) on the same drive
 
[/quote]
 
You mentioned wanting to save data from the hard drive.  There are a number of ways to do that, and end up with a 100% Ubuntu drive, in the end.
 
Do you have an external drive (USB external)?  Is the data you are wanting to keep on an NTFS volume (Windows volume) right now?  
 
Either way, you'll want to burn a copy of the LiveCD for GParted.  You can find it here:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
 
The latest version is 0.3.4-9 and it's a good one.  Burn that .iso to CD, and get back to me on your volumes.
 
Thanks.

---

### Post by frank002 on 2007-10-24
The line reads "alias net-pf-10 IPv6". Your suggestion is right on the money. I had the same problem with Gutsy (not in Feisty) and that solved it.

---

### Post by Aaron Guzman on 2007-10-25
> **P4man said:**
> Had the same with internet speed. Turned out it was caused by IPv6. Many people suffer from this, its easily solved though.

First, in firefox address bar, type "about:config". Locate "network.dns.disableIPv6" and set it to true.
restart firefox.

For some people that solves is already, not for me. Second thing to do then:

sudo gedit /etc/modprobe.d/aliases

Locate the line that has "alias net-pf-10" (and then something, don't recall what). Change it to "alias net-pf-10 off"

reboot, enjoy full speed internet again.

Thanks for that great post! This solved my slow internet problem. Thanks a lot! This website is GREAT!!!:)

---

### Post by DaraJava on 2007-10-26
Thanks anyway Molly but I fixed my "Composite extension not available" problem. So I'm not too bothered on getting a new Ubuntu.  :KS THANKS ANYWAY :KS

I'll explain what I did here for anyone that needs it:

First of all I edited my xorg.conf file. It is located in /etc/x11 . I changed

```

Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

to

```

Section "Extensions"
	Option		"Composite"	"1"
EndSection

```

Then I went to try to change System>Preferences>Appearance Preferences>Visual Effects from "none" to "extra" and it gave me an error message: "Cannot enable desktop effects". 

This meant that my composite extension problem was fixed but I figured that there was something wrong with my graphics card driver(graphics card is ati so there will usually be problems with drivers). I was using fglrx and glxgears was at about 2000 fps. I got some advice from some other thread to switch drivers to xserver-xgl.

Typed this into a terminal:
```

sudo apt-get install xserver-xgl

```

Restarted X by pressing *<ctrl>* + *<alt>* + *<backspace> *

Then it was fixed.

Wobbly windows all the way!!


So all I need is the help feature that went missing and I'll be running 100% perfect Gutsy! :guitar: Oh yeaaaah!

---

### Post by nick_h on 2007-10-26
I'm glad I found this thread.  I have also been having the slow internet problem.

---

### Post by DaraJava on 2007-12-07
All solved! Bar the help.

---

