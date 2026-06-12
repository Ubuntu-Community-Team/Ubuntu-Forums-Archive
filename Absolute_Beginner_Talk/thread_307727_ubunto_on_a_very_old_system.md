---
title: "ubunto on a very old system"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by crazy8 on 2006-11-27
Ok I have an old satellite pro 435CDS laptop that I would like to put ubuntu on. Well I have overcome the obstical of my BIOS not doing boot to cd/rom option. But now my next obsticle is that when I get the cd to boot I get the menue and select "start or install" then after it unpacks the kernle it says "Unable to locate RSDP" what does this mean and am I able to get past it?

Now before I get to much help here I should aslo probably let you all know this laptop is a pentium 100 or 133MHz system with 16MB of ram. If it is not feisable for me to put ubuntu on this system is it ok for me to ask if there is a *nix (preferably with a GUI) that I can put on this?

Thank you all for the help.

---

### Post by Grond84 on 2006-11-27
> **crazy8 said:**
> 
Now before I get to much help here I should aslo probably let you all know this laptop is a pentium 100 or 133MHz system with 16MB of ram. If it is not feisable for me to put ubuntu on this system is it ok for me to ask if there is a *nix (preferably with a GUI) that I can put on this?

Thank you all for the help.

Well, I'm new to all this, but if I'm not mistaken Xubuntu is geared for older hardware.  Sorry I can't help you with the first part though...

P

---

### Post by ngch on 2006-11-27
Ubuntu can only work at the very least with 32 MB, and that's without GUI. You can see the memory [requirements]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/memory-disk-requirements.html") here.

Sorry, but I'm afraid you have to look elsewhere. There are linux distributions that probably can work on ur laptop though.
[http://www.linuxlinks.com/Distributions/Mini_Distributions/]("http://www.linuxlinks.com/Distributions/Mini_Distributions/")

---

### Post by kerry_s on 2006-11-27
Try DSL-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by junglepeanut on 2006-11-27
I recommend Damn Small Linux (DSL) and puppyos, if you read this thread you will see if you are willing to work you can even get it for a big system like suse using icewm.
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=319077](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=319077)


I have 512mb, not much still, but more than yours, I am using icewm and typically I range around 70mb used (as long as firefox is not on), but I know this can be shrunk drastically just by switching some of the applications I use. Just going from gnome terminal to xterm is a 5-7mb change on my system. So applying changes like this through out your system should get you were you want to be.

Google turned up a lot, of posts about this as well. mulinux and delilinux were big hits.

---

### Post by K.Mandla on 2006-11-27
Yup. Go with DSL and see how that works for you. I've tried to squeak past the installer with less than 32Mb of memory and it just goes berzerk.

The only way I've ever heard of getting around that was to install the system on another machine, then transplant the hard drive ... or, zip up and installation and copy it into place on the new drive. Both of those methods sound like far too much work.

By the way, it is possible to get Ubuntu on a machine that old, but whether or not it's usable is for you to decide. If I may be so bold, check out ...

[http://www.ubuntuforums.org/showthread.php?t=294292](http://www.ubuntuforums.org/showthread.php?t=294292)

and

[http://www.ubuntuforums.org/showthread.php?t=259901](http://www.ubuntuforums.org/showthread.php?t=259901)

It can be done, but for my money there are better distros for machines that old. Have fun! :mrgreen:

---

### Post by Sef on 2006-11-27
> Try DSL-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

DSL needs 24 mb ram.  What you need is [Deli GNU/Linux]("http://delili.lens.hl-users.com/") or [Vector Linux]("http://vectorlinux.com/").

I have used Vector Linux and really like it.

---

### Post by kerry_s on 2006-11-27
> **Sef said:**
> DSL needs 24 mb ram.  What you need is [Deli GNU/Linux]("http://delili.lens.hl-users.com/") or [Vector Linux]("http://vectorlinux.com/").

I have used Vector Linux and really like it.

What gives you that idea?

Damn Small is small enough and smart enough to do the following things:

    * Boot from a business card CD as a live linux distribution (LiveCD)
    * Boot from a USB pen drive
    * Boot from within a host operating system (that's right, it can run *inside* Windows)
    * Run very nicely from an IDE Compact Flash drive via a method we call "frugal install"
    * Transform into a Debian OS with a traditional hard drive install
    * Run light enough to power a 486DX with 16MB of Ram  <-[COLOR="Red"]Dosen't say 24mb[/COLOR]
    * Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)
    * Modularly grow -- DSL is highly extendable without the need to customize

---

