---
title: "Can Vmware Boot Original Xp?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by polpol on 2006-12-13
I am very new to ubuntu and I hope will get a good friendship with Ubuntu. Till now everything Ok. I am tired of holes and exploits of windows , w&#305;sh to continue with linux. Now sometimes I have to switch back into Xp , you know some softw. dont work on Ubuntu. But I wish do this even without living Ubuntu. I have seen on a web page that user can boot original xp, the very xp of dual boot not you create on Ubuntu, via vmware if you back-up hardware profile of  xp and use that backed up profile with Vmware.As far as I remember the man who prepared this method , also used sysrep.exe and given the /dev/hda to vmware. Is it possible and secure way? Technically it is good because you will completely have your settings of xp but ...

---

### Post by gn2 on 2006-12-13
Perhaps you could use the "Files and Settings Transfer Wizard" ?

---

### Post by loyaleagle on 2006-12-13
You can use WINE (Install it by using synaptic Package Manager). WINE mimics windows within Ubuntu linux WITHOUT having to install Windows in VmWare. Then you can go to WINEHQ ([http://www.winehq.com/site/??issue=304](http://www.winehq.com/site/??issue=304)) and check out what you need.

I'm new to Ubuntu and have made it work on my platform without to much trouble. Make sure you follow all instructions, step by step

Thanks, Loyaleagle

---

### Post by tudawggz on 2006-12-13
Vmware server is free software avalible from vmware that will let you create a virtual machine.  You should have a copy of windows Xp in order to install that.  Virtual machines allow you to try out operating systems in an environment that allows you to install them and run them on your existing operating system.  I reciently added it to my machine and was happy, but it did not give me access to all of my hardware (ie tvcard)  I would recomend checking it out to try and run some windows applications in windows, without having to boot windows.  I do not know if it will run games that require many resources, but it will run software like iTunes in your virtual Xp environment.

---

### Post by Velotix on 2006-12-13
I've just recently acquired Wine myself and it's awesome stuff, though depending on the program you may need to do a bit of tweaking to get them to work properly. You will definitely get much better performance out of Wine than VMWare running XP. A word of warning, though: the version in the Ubuntu repositories is out of date and is in dire need of an update.

[Follow the instructions on this page to get it installed. It works a treat. ^^](http://www.winehq.com/site/download-deb)

---

### Post by Kieranties on 2006-12-13
> **Velotix said:**
> ... You will definitely get much better performance out of Wine than VMWare running XP... 

Could you expand on that?  I don't understand how that works seeing as in the virtual machine you are actually running XP not an attempt at the workings of the windows API.  Once you have installed the additional elements with vmware server (it tells you how), the guest OS runs as smoothly as it would do normally.  

I have a 1.8 sempron running at 2ghz with 1.5gig of ram and 2gig swap.  I run Virtual Studio 2005 in xp and it doesn't falter, neither does ubuntu when I am ripping dvds in xp and watching a film or browsing the net in ubuntu.

---

