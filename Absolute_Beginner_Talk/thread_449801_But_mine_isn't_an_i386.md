---
title: "But mine isn't an i386"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by hightails on 2007-05-20
I have considerable Windows experience, but no Linux. My PC is a 2.4GHz Athlon XP mulitiboot with 1Gb RAM. 

I have just installed my first Linux flavour (Feisty for Standard Personal Computer). All seems to have gone OK, though I haven't configured hardware etc yet. But when I look in Add/Remove Programs to see what range of apps were included, approx two thirds are listed as "cannot be installed on your computer type (i386)". 

I looked through the earlier posts on this forum and concluded I needed either the 686 or the K7 versions. Then I realised they don't exist in Feisty.

Can I really access only a third of these programs with Feisty and a 2.4GHz machine?

---

### Post by Bachstelze on 2007-05-20
Did you by any chance install the amd64 version of Ubuntu ?

---

### Post by rsambuca on 2007-05-20
If you go to System -> Administration -> System Monitor, the first tab will show what version of ubuntu you have installed.  It sounds to me like you might have installed the 64-bit version.

---

### Post by ugm6hr on 2007-05-20
I think you get this warning if your computer is not connected to the internet when you try to load Synaptic Package Manager or Add/Remove..

---

### Post by rsambuca on 2007-05-20
> **ugm6hr said:**
> I think you get this warning if your computer is not connected to the internet when you try to load Synaptic Package Manager or Add/Remove..

NO.  Not correct.

---

### Post by hightails on 2007-05-22
Thanks for the fast response everyone!

I am as certain as I can be that I did not download the 64-bit by mistake. I am not an IT pro, but am very aware that mine is a 32-bit. As this was my first Linux download, I was watching carefully what I was doing, and can't believe I would have made such a daft mistake. I have checked in System Monitor first tab, and it doesn't really tell me whether the software is 32 or 64-bit. All it says is that the version is "7.04 (Feisty)", and that the processor is "AMD Athlon(tm) XP".

I thought rsambuca was on to something, as I haven't yet configured my modem. But ugm6hr seems quite sure that won't be the problem. I will try to set the modem up and check, just to be sure.

Any other ideas still welcome.

---

### Post by Parmenion on 2007-05-22
Id agree with rsambuca's analysis .... Though, maybe your repos are pointing to the amd64 versions ...Just a thought there.

---

### Post by hightails on 2007-05-23
Sorry, Parmenion. I don't understand what you mean by "maybe your repos are pointing to the amd64 versions". How would I check and correct this?

By the way, I have found a file on the CD I burned and used to install Feisty. It's called readme.diskdefines and it's first line reads 
#define DISKNAME  Ubuntu 7.04 "Feisty Fawn" - Release i386
So it don't look like the 64-bit version.

---

### Post by Famicommie on 2007-05-23
Could you please open up a terminal (Applications -> Accessories -> Terminal), input the command ```
uname -a
``` and tell us what the output is?

---

### Post by hightails on 2007-05-23
Output as follows
Linux *ID* 2.6.20- 15- generic #2 SMP *Date/Time* UTC 2007 i686 GNU/Linux

---

### Post by rsambuca on 2007-05-23
This is kinda strange to me.  Can I ask what CD you used to install with?  ie. Did you use the Desktop (liveCD), or the alternate CD?  Did you do a standard installation, or server installation, or OEM installation?

I just have never really heard of that type of problem with a regular installation before.

---

### Post by hightails on 2007-05-24
I used Desktop (not alternate). I obviously should have used standard and not server or OEM, but to be honest I can't remember selecting between them during installation.

I'm busy for the next few days, but if I don't hear any more ideas I will try another fresh install early next week, paying careful attention to installation type, and let you know what happens.

---

### Post by igknighted on 2007-05-24
> **hightails said:**
> I have considerable Windows experience, but no Linux. My PC is a 2.4GHz Athlon XP mulitiboot with 1Gb RAM. 

I have just installed my first Linux flavour (Feisty for Standard Personal Computer). All seems to have gone OK, though I haven't configured hardware etc yet. But when I look in Add/Remove Programs to see what range of apps were included, approx two thirds are listed as "cannot be installed on your computer type (i386)". 

I looked through the earlier posts on this forum and concluded I needed either the 686 or the K7 versions. Then I realised they don't exist in Feisty.

Can I really access only a third of these programs with Feisty and a 2.4GHz machine?

What if you just try to install through Synaptic or easiest of all through the cli (via the 'sudo apt-get install <package>' command)?  I (note: opinion) think add/remove programs is a waste of HD space as it frequently errors and doesn't show you everything available.

Just as a test, try going to the CLI (applications -> accessories -> terminal) and typing "sudo apt-get update", no quotes though.  This should update the package list.  Then try "sudo apt-get upgrade".  This will update any packages installed that have newer versions available.  If you don't get any errors from these, try to install something (either with synaptic or through the CLI).  I would stick with these choices in the future, they tend to be more reliable.

If you get any errors post them.  Also, if you error out during the first command (the update one), can you post the result of the command "cat /etc/apt/sources.list" as well?

---

### Post by hightails on 2007-05-24
Hi again folks. I have still haven't managed to configure that modem yet, and can't really try igknoghted's suggestions until I have done so. It's a Speedtouch 330 USB, which according to other forums needs some kind of firmware update to work with Ubuntu.

I'm busy over the weekend, so will get back to you all early next week when I've found time to get that sorted.

Thanks again for all your help so far.

---

### Post by parts-man73 on 2007-05-24
I'm a new user myself but..... if he modem isn't configured/working, then it would seem that this is why he could not use the "add/remove programs", as an internet connection would be required to do any sort of downloading.

-Brian

---

### Post by franck3d on 2007-05-24
> **hightails said:**
> I have still haven't managed to configure that modem yet, and can't really try igknoghted's suggestions until I have done so. It's a Speedtouch 330 USB, which according to other forums needs some kind of firmware update to work with Ubuntu.


I had that modem for the longest time (the stingray, right?), and it can be made to work in linux.
check here for some hints.

[speedtouch for ubuntu]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

but honestly, I wasn't really able to get to the point where I was happy until I ditched it and bought a dsl ethernet modem.  Now the modem is always connected and when ever I boot into ubuntu, or from a LiveCD, I have instant internet access.

let us know if you have success with your modem

---

### Post by hightails on 2007-05-31
Thanks for your input guys. For me this has now become more about the modem than the original problem.

I have actually been comparing Ubuntu and Mandriva as my first ventures into Linux. The bottom line is that I have managed to make the USB modem work in Mandriva using the method on [http://www.linux-usb.org/SpeedTouch/mandrake/index.html](http://www.linux-usb.org/SpeedTouch/mandrake/index.html). Unfortunately, I have not yet managed to get the equivalent process for Ubuntu (on the same site) to work.

I have been through the Ubuntu process twice. As far as I can tell, the firmware is installed, but the modem still doesn't work. I have tried looking in the system log, but have been unable to understand what's happening in normal mode, never mind the verbose mode referred to in the trouble-shooting paragraph on the linux-usb site. I have also been unable to check the contents of the secrets and speedtch files, because these are inaccessible (red cross).

At present it looks as if I will end up taking Mandriva further and dropping Ubuntu for the time being, unless anyone else out there has any idea what else I can do.

Seems a shame to throw Ubuntu away over one piece of hardware, but I don't particularly want to buy a router at present and Mandriva looks OK so far.

---

### Post by franck3d on 2007-06-01
> **hightails said:**
>  I have also been unable to check the contents of the secrets and speedtch files, because these are inaccessible (red cross.


in the terminal-cd to the directory where those files are located and
sudo gedit secrets.pap

(or chap or whatever)
that should allow you to see what's there, if you are still interested...

the first distro I tried was mandrake about 5 years ago and I got the modem working there after following several tutorials.

good luck,

---

### Post by hightails on 2007-06-02
Thanks franck3d. I really am new to this and didn't know that command.

However, I had already accessed these files (since my last post) by finding out how to log on as root (and straight back off again afterwards, of course!). Confirmed both files are OK, so at least we know its not that. Will keep trying a bit longer. I have some ideas picked up from another thread.

---

### Post by hightails on 2007-06-02
Fixed and Fixed!!!!!!

SOLUTION TO PROBLEM 2 - Modem Connection

Someone on another thread pointed me to [http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701). This tells of 
an installable program for Speedtouch 330 modems written by StevenHarper. I used his version 0.4.8. It worked first time for me. 

I suggest anyone reading this passes this one on. I spent hours on this problem before Rui Pais pointed me at this simplest of solutions.

SOLUTION TO PROBLEM 2 - Why can't these apps be installed

Having fixed the modem problem I connected triumphantly, accepted the offer to update the list, and most if not all apps are now available. Don't know if it was the absence of the connection that was the problem (see earlier debate), or whether updating the list did the trick.

Thanks everyone for all your help.

---

### Post by ugm6hr on 2007-06-02
> **hightails said:**
> 
SOLUTION TO PROBLEM 2 - Why can't these apps be installed

Having fixed the modem problem I connected triumphantly, accepted the offer to update the list, and most if not all apps are now available. Don't know if it was the absence of the connection that was the problem (see earlier debate), or whether updating the list did the trick.


I was part of that earlier debate, and think it is updating the list that makes the difference.  Although it won't offer (or allow you) to update the list without an internet connection, so they amount to the same thing.

Pleased your on board.

---

