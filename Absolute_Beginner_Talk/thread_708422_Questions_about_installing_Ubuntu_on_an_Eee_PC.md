---
title: "Questions about installing Ubuntu on an Eee PC"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by 1_maniac on 2008-02-26
These questions probably have been asked, but I've not found the answers

1)  I have an Asus EEE PC using Xandros - Not particularly user friendly to 
      me.

2) I would like to install Ubuntu, as I understand it is user friendly & more
     like using windows to add/remove programs & doing personalization.
     The other choice is to install XP - an nLite version

3) To install Ubuntu:
     - Use the F9 button upon start up - which resets the eee pc to factory
       settings.
     - Which version of Ubuntu do I download?  7.01?
     - can I install it from a USB thumb drive?
     - Just follow the prompts and Ubuntu will install over Xandros, becoming
        the new OS.
     - After Ubuntu is installed
        - use the DVD that came with the eee pc to install the drivers
        - all should work just like it came out of the box
           -including the wifi, internet, email etc
        - OR is it necessary to download programs such as FireFox / 
           Thunderbird and the other programs that came installed with
           Xandros?

This is all that I can think of, and please excuse my questions - I am new
to Linux and the learning curve for me is quite high.  I am trying to do 
my best learning Linux - Would the book " Linux for Dummys" of 
"Ubuntu for Dummys" be a viable option?  There are Barnes & Nobles
quite close.

If there is a really, and I mean really, simple step-by-step instructions
for the installation, would someone show me where to find it?

Lastly, I would like to thank anyone who would be taking time out of
their busy day to help out an olde man trying to keep mentally healthly
as I have the beginning of alzheimer's and will not bow down and become
a veg - sorry

---

### Post by Joeb454 on 2008-02-26
The eeePC also comes with a full fledged KDE Desktop Environment you know, though I'm not sure how to boot into it.

---

### Post by bapoumba on 2008-02-26
[https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC")
and the links at the bottom of the wiki page. Have fun :)

---

### Post by dstew on 2008-02-26
Xandros is Debian based, isn't it? You could just try ```
sudo apt-get install ubuntu-desktop
```That might not work, but the worst outcome would be that you just have to make a USB image and install Ubuntu the regular way. Back up important documents first, of course.

---

### Post by Joeb454 on 2008-02-26
**dstew** - I don't think eeePC's have a CD/DVD drive built in (if I remember correctly)

---

### Post by matey3 on 2008-02-26
> **1_maniac said:**
> These questions probably have been asked, but I've not found the answers

1)  I have an Asus EEE PC using Xandros - Not particularly user friendly to 
      me.

2) I would like to install Ubuntu, as I understand it is user friendly & more
     like using windows to add/remove programs & doing personalization.
     The other choice is to install XP - an nLite version

3) To install Ubuntu:
     - Use the F9 button upon start up - which resets the eee pc to factory
       settings.
     - Which version of Ubuntu do I download?  7.01?
     - can I install it from a USB thumb drive?
     - Just follow the prompts and Ubuntu will install over Xandros, becoming
        the new OS.
     - After Ubuntu is installed
        - use the DVD that came with the eee pc to install the drivers
        - all should work just like it came out of the box
           -including the wifi, internet, email etc
        - OR is it necessary to download programs such as FireFox / 
           Thunderbird and the other programs that came installed with
           Xandros?




Hi
 Sorry for replying because I am also new to Ubuntu but I have installed the server (feisty 7.04)   at work and I know a few things about installing Ubuntu.
- They have different versions of it so pick the one you think its the best for you (I took the server because they told me to).
I like Asus, so I think you have a very good computer. The first computer they gave me to install Ubuntu server, did Not work out at all? It must have had serious hardware issues? bcs the 2nd PC they gave me, installed Ubuntu easy and with no problerms.

- I think you can use its Grub boot manager to handle your partitions. (We have to wait for some pro to tell us I guess?).
As far as booting with a USB device, I guess it depends on your PC. I have a PC at home that does that (looks for a USB device at boot up) I am sure yours does too, if not then you have to go into your BIOS or CMOS to set it up.(I dont know which BIOS manufacturer ASUS uses but usually hitting Del key takes u to cmos at bootup) or may be one of the F keys?

-As far as the programs are concerned, as long as you have the CD in your PC (it usually auto mounts it) Ubuntu goes and gets what it needs or whatever you need from it or it goes out to the Net and gets it automatically.
sometimes you have to issue commands to get certain piece of software (like apt-get install) But Ubuntu already comes with email and web browsing programs (built in)....

OK...I like to see/hear what others have to say as well. thanks for the post..
 Good Luck!

---

### Post by IanW on 2008-02-26
The Eee has no CD/DVD drive, so unless you have access to a USB one, you'll need to create an Ubuntu pendrive using the instructions at [PendriveLinux]("http://www.pendrivelinux.com"). Then you should use the Ubuntu script pack from [here]("http://code.google.com/p/ubuntu-eee/downloads/list").

For Wireless, you'll need the MadWifi drivers (Deb file [here]("http://preview.tinyurl.com/2zvkaz")), and I'd recommend using Wicd instead of Network Manager.

For more detailed help, try the forums at [http://www.eeeuser.com]("http://www.eeeuser.com"), they even have one just for us Ubunteros.

---

### Post by 1_maniac on 2008-02-27
I have ordered a Ubuntu 7.01 CD along with the book of "Ubuntu for Dummys"

I hope that the install goes like it would if I were to install XP.  After installing XP you install the
drivers from the CD that came with the eee pc and all should work?  The other advise I read was
to install Ubuntu & the open a command window & use : sudo apt-get   ubuntu is suppose to
download the programs it needs to run properly.  At least, that's the plan right now.    

If, anyone know a better way or see holes in the way I think I am going to proceed. PLEASE 
don't hesitate to let me know!!

Thanks to you great people

---

### Post by 1_maniac on 2008-03-04
Got Ubuntu installed like butter!  Only one hitch, I can not get the wifi
to work ... Have read the wiki and tried to understand the postings here
on the forums, but I find them confusing, contradicting & I am downright
lost.   Would anyone be able to either send or post a very basic step by
step with what to type into the command window, I'd be greatly happy

Oh, I know this has been asked & answered many times, but if someone
would just find a few minutes to impart this wisdom to me - 

OH, I should tell you the PC I'm having the issue with is the Asus EEE PC
4GB with an 8GB SanDisc

Thanks again to you all

---

