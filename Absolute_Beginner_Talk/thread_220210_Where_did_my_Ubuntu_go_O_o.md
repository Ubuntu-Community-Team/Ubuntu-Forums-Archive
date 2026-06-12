---
title: "Where did my Ubuntu go? O_o"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Anticamper on 2006-07-21
I recently instaled ubuntu and am a complete newbie. the first try, i wiped my windows drive from not understanding the partition manager(no big deal as i obviously back up). Then, the next morning, I instaled windows after wiping the drive and making 2 partitions. i had hoped i could dual boot with windows xp. got windows up and running so i instaled ubuntu. this somehow screwed with some random windows file causing it not to work so i reinstaled windows again. but now it has taken over my boot. meaning, i can't choose to boot from the ubuntu(though i am pretty sure its still there). as for my computer hardware,

[http://www.xfire.com/profile/anticamper86](http://www.xfire.com/profile/anticamper86)

i am having some trouble instaling a few things for ubuntu. i read somewhere that for alot of stuff i would have to "compile" stuff to make it work.i have no clue what any of this means so yea, i realy want to find someone who knows alot about ubuntu to sorta walk me through it. its alot to ask but yea, i'd realy apreciate the help. thats how i would learn best. if you know where any drivers for my hardware are can you link me? any help would be greatly apreciated

thank you for your time

PS:(i kinda posted this in the 64 bit section...sorries)

---

### Post by nalmeth on 2006-07-21
How to Restore Grub so you can boot:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
Get everything Ubuntu doesn't come with:
_[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)_
How to install anything in Ubuntu:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

EDIT:
I would go with the regular i386 kernel, it will make things easier for you, then you can reinstall later. For what it's worth, I'm STILL running i386 on my 64-bit, but kind of out of laziness more than anything :oops: It just means building workarounds for a lot of 32-bit apps you end up needing.

---

### Post by risbac on 2006-07-21
To reinstall Windows AFTER Ubuntu is a bad idea, as Windows always kindly ignore the other operating systems and propose only one choice at boot: itself...

In this situation, the wiki is always your best friend. Try to look for "grub reinstall", there is a page for this, as you are not the first one (it happened to me also ;-) ), nor the last one with this problem. 

For your hardware drivers, depends what is not working. Give us some more information. And usually you have a wiki page to install the most current hardwares which are not automagically recognized.

---

### Post by risbac on 2006-07-21
> i read somewhere that for alot of stuff i would have to "compile" stuff to make it work

Well, yes and no... Sometimes, for some specific needs, you don't have a package for a software (it's like the installation file for a Windows software). But you can still compile yourself from the code written by the author.

However, it's very rare. It's difficult to say if you will need to do so, depends what you wanna do with Ubuntu. If you have a specific problem, don't hesitate first to look at the wiki, maybe there is a solution, then search into the forums, and finally create a post if you don't have the solution.

---

### Post by Anticamper on 2006-07-21
> **nalmeth said:**
> How to Restore Grub so you can boot:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
Get everything Ubuntu doesn't come with:
_[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)_
How to install anything in Ubuntu:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

EDIT:
I would go with the regular i386 kernel, it will make things easier for you, then you can reinstall later. For what it's worth, I'm STILL running i386 on my 64-bit, but kind of out of laziness more than anything :oops: It just means building workarounds for a lot of 32-bit apps you end up needing.

thank you for your links


> **risbac said:**
> To reinstall Windows AFTER Ubuntu is a bad idea, as Windows always kindly ignore the other operating systems and propose only one choice at boot: itself...

In this situation, the wiki is always your best friend. Try to look for "grub reinstall", there is a page for this, as you are not the first one (it happened to me also ;-) ), nor the last one with this problem. 

For your hardware drivers, depends what is not working. Give us some more information. And usually you have a wiki page to install the most current hardwares which are not automagically recognized.

as for instaling windows after, i didn't want to do it that way as i know the windows partition stuff alot more. i am a pro at reinstaling windows :). when i instaled windows first though, windows got upset i think, maybe jelous. 

as for drivers, my soundcard sounds like its usin some sort of default driver. i can't use equalizers or else it makes the sound like gabage. also i noticed my volume is nowhere near as loud as it should be. its bareable, but i wouldn't mind improving it. as for video, i dunno, i would realy love to play starcraft on it. if i got starcraft working, i wouldn't need windows XD. but yea, i am using an msi mobo with the ati express 200 chipset. the onboard video is amazing but i am pretty sure it would need some drivers.

> **risbac said:**
> Well, yes and no... Sometimes, for some specific needs, you don't have a package for a software (it's like the installation file for a Windows software). But you can still compile yourself from the code written by the author.

However, it's very rare. It's difficult to say if you will need to do so, depends what you wanna do with Ubuntu. If you have a specific problem, don't hesitate first to look at the wiki, maybe there is a solution, then search into the forums, and finally create a post if you don't have the solution.

basicly there are a few programs i would like to instal, one of them being skype, but it isn't in the packet manager(the manager is a very useful lil piece of software mind you). anyways i was more or less askin about compiling to see if eather someone could point me to a site that will show me how, or even better, show me how to do it. thank you guys for your time/help. i am gonna try to fix the grub deal. be back soon i hope <3's

---

### Post by Third Thoughts on 2006-07-21
> **Anticamper said:**
> t
basicly there are a few programs i would like to instal, one of them being skype, but it isn't in the packet manager(the manager is a very useful lil piece of software mind you). anyways i was more or less askin about compiling to see if eather someone could point me to a site that will show me how, or even better, show me how to do it. thank you guys for your time/help. i am gonna try to fix the grub deal. be back soon i hope <3's

To get skype use the automatix auto-install script
[http://www.ubuntuforums.org/showthread.php?t=190025&highlight=skype](http://www.ubuntuforums.org/showthread.php?t=190025&highlight=skype)
This allows you to install a bunch of stuff including WINE, a sort of windows emulator that you might be able to get Starcraft up and running under.

~Andrew S.

---

