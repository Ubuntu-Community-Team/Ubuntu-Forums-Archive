---
title: "No access rights to my NTFS partitions"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Nightmist on 2007-04-21
Hello,

I have some NTFS partitions that I have mounted using something called Storage Device Manager. When I try to access these (called sda5, sda6, sda7) I get this message:

"Unable to enter file:///media/sda6. You do not have access rights to this location."

I just need to access it for the movies and music I have stored there, but it's important enough since now my Kubuntu is silent.

Thanks for any help.

---

### Post by oilchangeguy on 2007-04-21
try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Drakkor on 2007-04-21
I know I'll probably get slammed for this, but Ubuntu can be ntfs read/write
Super quick way:

---

### Post by Nightmist on 2007-04-21
> **Drakkor said:**
> I know I'll probably get slammed for this, but Ubuntu can be ntfs read/write
Super quick way:

Why would you get slammed? I would rather do it without having to use a terminal, so I can use that to more easily convince friends to get Linux.

---

### Post by mysticrider92 on 2007-04-21
Some people don't like Automatix for various reasons. I find it to be a very useful tool for many things.

---

### Post by oilchangeguy on 2007-04-21
automatix is the way to go. to bad that auto mount program is not in automatix for version 6.06.

---

### Post by oilchangeguy on 2007-04-21
> **mysticrider92 said:**
> Some people don't like Automatix for various reasons. I find it to be a very useful tool for many things.
those that don't like it are command line junkies. and automatix makes things much easier for the average user, who just wants to install something, and not go thru the hassle of performing 50 commands to get it done.

---

### Post by sunexplodes on 2007-04-21
I think the bad rep Automatix2 gets is generally unfounded, but it's best to install things with it one or two at a time, so if something breaks your machine, you have some idea what did it.

---

### Post by Drakkor on 2007-04-21
Thanks for the support guys,lol  :) 
Yeah I just installed Fiesty yesterday, and now I'm pretty much all set up, thanks to Automatix, and Synaptic !
I have heard some people say you're not leaning anythiing, but everyone doesn't need to understand how an internal combustion engine functions just to drive a car !!

---

### Post by Nightmist on 2007-04-21
> **Drakkor said:**
> Thanks for the support guys,lol  :) 
Yeah I just installed Fiesty yesterday, and now I'm pretty much all set up, thanks to Automatix, and Synaptic !
I have heard some people say you're not leaning anythiing, but everyone doesn't need to understand how an internal combustion engine functions just to drive a car !!

I hear you. I used to run Gentoo. It was fun to see how you do everything, but I had to read a lot of HOWTOs to do stuff. And once everything was up and running, the commands to update the system were simple, and I only ran into problems when I needed to update the kernel. But.. hey, some things break when I update the kernel in Ubuntu as well.

After a while I forgot the commands, though, as I mainly used Gentoo to work in, not work on. And it's easier to recall where to click than it is to recall a command. So for me it will be easier to, a few months from now, to use Automatix to mount these drives, when I need to install it on another computer or whatever, instead of remembering all those commands.

Now... I forgot the command to delete directories. How do I delete my old (failed) mount directories easily? (hey, this is the beginner talk, right?)

:)

---

### Post by Drakkor on 2007-04-21
Nothing's perfect or forever......  if it's not the software, maybe your hard drive will turn up toast. The only precaution I take is to image my Ubuntu drive before making radical changes , so if I break it, in 10 minutes 
I have everything restored like it never happened ,lol  :)

---

### Post by Nightmist on 2007-04-21
Well, anyway... I found the command to delete directories, and the Automatix thing worked like a charm. But is there an easy way to change to "sudo" mode when using Konqueror (or whatever file browser is best)?

---

### Post by kwilliam on 2007-04-21
> **sunexplodes said:**
> I think the bad rep Automatix2 gets is generally unfounded, but it's best to install things with it one or two at a time, so if something breaks your machine, you have some idea what did it.
My understanding is that Automatix installs software without telling the package manager.  So when you go to upgrade your system (say, from Dapper to Edgy) stuff breaks.  I've never used it myself.  I used EasyUbuntu on Dapper, and haven't used anything except a few terminal commands for Edgy.  (The [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repository makes installing media playback codecs (like DVD's) really easy.)

---

### Post by Drakkor on 2007-04-21
> So when you go to upgrade your system (say, from Dapper to Edgy) stuff breaks.
That's why I never upgrade, IMHO a clean install is always best ! :)

---

