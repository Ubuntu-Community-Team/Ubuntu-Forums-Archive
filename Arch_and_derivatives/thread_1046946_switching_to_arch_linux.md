---
title: "switching to arch linux"
date: 2009-01-21
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-01-21
i have been using ubuntu for about 6 months,and now i want to have a bash at arch linux.i have come to know that it is incredibly faster.i was told that it would be way too faster on my machine.can someone please tell me a one-stop site to guide me into installing it in triple boot with ubuntu and windows xp?also,will it be possible to use ext4 in arch linux?

---

### Post by hrod beraht on 2009-01-21
Arch has an awesome wiki. Check out the [[COLOR="Blue"]Beginner's Guide[/COLOR]]("http://wiki.archlinux.org/index.php?title=Beginners_Guide&oldid=58738").

Bob

---

### Post by kerry_s on 2009-01-21
> i was told that it would be way too faster on my machine

someone might have exaggerated.

> also,will it be possible to use ext4 in arch linux?

not that i saw.

---

### Post by cardinals_fan on 2009-01-21
[http://ubuntuforums.org/showthread.php?t=1045349](http://ubuntuforums.org/showthread.php?t=1045349)

---

### Post by stonecoldjha on 2009-01-21
so arch linux is not faster than ubuntu?if it is,how faster will it be,i have heard that it is optimised for i686 architectures,and hence does much better.

---

### Post by SomeGuyDude on 2009-01-22
> **kerry_s said:**
> not that i saw.

Check the thread about the new kernel. Yes, you can use ext4 now. :)

Yes, Arch is definitely faster, but that's only one of the multiple benefits. Big ones are the rolling release idea, pacman as a fantastic package manager, the fact that you build it instead of installing it and then deleting the stuff you don't want, and that it's light on the resources.

---

### Post by kerry_s on 2009-01-22
> **stonecoldjha said:**
> so arch linux is not faster than ubuntu?if it is,how faster will it be,i have heard that it is optimised for i686 architectures,and hence does much better.

everything is faster than ubuntu.

how much faster depends on you and your hardware, the more you load it up the slower things might get, depends on the program.

---

### Post by jrusso2 on 2009-01-22
Ext 4 is still experimental so be prepared for mishaps if you chose to use it.

---

### Post by kerry_s on 2009-01-22
> **SomeGuyDude said:**
> Check the thread about the new kernel. Yes, you can use ext4 now. :)

Yes, Arch is definitely faster, but that's only one of the multiple benefits. Big ones are the rolling release idea, pacman as a fantastic package manager, the fact that you build it instead of installing it and then deleting the stuff you don't want, and that it's light on the resources.

gotcha, sounds a little if'y though. 
anyone talking about putting it on the installer yet or is it still to experimental?

---

### Post by kerry_s on 2009-01-22
> **jrusso2 said:**
> Ext 4 is still experimental so be prepared for mishaps if you chose to use it.

exactly what i was thinking.

---

### Post by fwojciec on 2009-01-22
> **jrusso2 said:**
> Ext 4 is still experimental so be prepared for mishaps if you chose to use it.
It is now considered "stable".

This is the exact phrasing from [kernel wiki](http://ext4.wiki.kernel.org/index.php/Ext4_Howto):
> Ext4 was released as a functionally complete and stable filesystem in Linux 2.6.28, hence it's safe to use it in production environments, but as any piece of software, it has bugs (which are more likely to be hit in the first stable versions). Any know critical bug will be quickly fixed.

EDIT: To answer the question from the original post -- yes, it is possible to use ext4 with Arch now (I do on two different computers), but it's not possible to install Arch directly on an ext4 partition just yet...  That will be possible once the new ISO with 2.6.28 kernel is released -- it is being finalized at the moment so it should be released soon.

---

### Post by kerry_s on 2009-01-22
> That will be possible once the new ISO with 2.6.28 kernel is released -- it is being finalized at the moment so it should be released soon.

thank you, that is what i was looking for.

---

### Post by jrusso2 on 2009-01-22
> **fwojciec said:**
> It is now considered "stable".

This is the exact phrasing from [kernel wiki](http://ext4.wiki.kernel.org/index.php/Ext4_Howto):


EDIT: To answer the question from the original post -- yes, it is possible to use ext4 with Arch now (I do on two different computers), but it's not possible to install Arch directly on an ext4 partition just yet...  That will be possible once the new ISO with 2.6.28 kernel is released -- it is being finalized at the moment so it should be released soon.

but as any piece of software, it has bugs (which are more likely to be hit in the first stable versions). Any know critical bug will be quickly fixed.

[http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199) Ext 4 Data Loss in Jaunty.  Have you read this yet?


Seems to be a lot of bugs for a released version.  The last jaunty thread I saw had at least  users in it that experienced data loss with ext 4.  You do what you want I will stick with what I want.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

---

### Post by smartboyathome on 2009-01-22
> **jrusso2 said:**
> but as any piece of software, it has bugs (which are more likely to be hit in the first stable versions). Any know critical bug will be quickly fixed.

[http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199) Ext 4 Data Loss in Jaunty.  Have you read this yet?


Seems to be a lot of bugs for a released version.  The last jaunty thread I saw had at least  users in it that experienced data loss with ext 4.  You do what you want I will stick with what I want.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

The Jaunty kernel, unlike Arch Linux's, has many, many patches applied to it. This could be part of the reason that EXT4 is less stable (conflicting patches are always a problem :(). I have been running EXT4, and haven't had any issues for the past couple days. I will keep my eyes out though. ;)

---

### Post by gjoellee on 2009-01-22
> **jrusso2 said:**
> Ext 4 is still experimental so be prepared for mishaps if you chose to use it.

I can't agree with you there. Ext4 was marked as stable with the kernel 2.6.28. If you have that kernel Ext4 will be a stable version, but Ext4 is a very young and untested filesystem, so there might be some glitches around.

It is a the same with software. When you reach the ie; 1.0 version there will almost always come a 1.0.1 later fixing a lot of issues found in the 1.0 release. It is the same with Ext4

---

### Post by stonecoldjha on 2009-01-24
i went through the wiki.its very simple to follow.but,i have ubuntu8.04, qnd windows xp already on my machine.i want to install arch linux in triple boot with them.while configuring GRUB,what should i do to make the GRUB automatically recognize all the three OSs and display the list at login,like it does when one installs ubuntu over windows?

---

### Post by mips on 2009-01-24
You need to edit the /boot/grub/menu.lst file

---

