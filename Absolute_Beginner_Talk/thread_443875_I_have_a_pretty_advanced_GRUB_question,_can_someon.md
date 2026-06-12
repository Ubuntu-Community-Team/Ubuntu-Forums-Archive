---
title: "I have a pretty advanced GRUB question, can someone help?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-14
Ok, here we go again.

**I want:  **
Ubuntu, Vista + program partition, and Dell MediaDirect.

**Obstacles:  **
Vista MUST have the 'BOOT' flag
I can NOT change the (hd0) MBR, or Mediadirect will cease to function

**My only real partition setup option is as follows:**
Primary: Vista 
Primary: Programs 
Extended: Ubuntu, Swap, MediaDirect

Here is the question.  Can I install GRUB to (hd0,1), which is the Vista partition, but not the primary MBR (hd0)?

---

### Post by crispy_420 on 2007-05-14
I don't think so. I may be wrong but grub wants to be the first thing seen as it tells the system where to go from there.

---

### Post by wormser on 2007-05-14
I found this on the following link.  You do not want to write Grub to the MBR.  Read the link for instructions.

> now that you have the linux.bin file, re boot  into windows xp and edit the c:\ boot .ini appending thsi line to the end:

C:\linux.bin="Linux"

now you can re boot into windows xp, but you'll get a choice between winxp and linux. when you choose linux, you'll get a grub menu to boot linux. 


[http://www.notebookforums.com/thread164182.html](http://www.notebookforums.com/thread164182.html)

---

### Post by gohanssjn on 2007-05-14
Vista does not use a boot.ini though.  It uses a BCD application.

---

### Post by jimrz on 2007-05-14
> **gohanssjn said:**
> Vista does not use a boot.ini though.  It uses a BCD application.

is adding a 2nd hdd an option?

---

### Post by confused57 on 2007-05-14
Maybe this would be an option:
[http://ubuntuforums.org/showpost.php?p=2644308&postcount=7](http://ubuntuforums.org/showpost.php?p=2644308&postcount=7)

---

### Post by gohanssjn on 2007-05-14
Well, here's the thing >.>

I am very much a perfectionist.  Why do I want MediaDirect?  Becuase without it, I have a button on my laptop that boots nothing.

However, I just found a guide that *may* let me install Ubuntu to my MD partition, and Vista to my main partition, and boot either based on what button I push.  Here's hoping!

---

### Post by gohanssjn on 2007-05-14
Ok, new question!

Can I make GRUB boot right into Vista and not load it's bootloader each time?

---

### Post by calraith on 2007-05-14
It sounds like you're not going to get around having Vista manage the bootable partitions, rather than grub.  So install grub to (hd0,linux) and try sumn like [EasyBCD]("http://neosmart.net/dl.php?id=1") or [VistaBootPRO]("http://www.vistabootpro.org/") to teach Vista's boot loader to find grub.  For what it's worth, I don't remember having much luck with EasyBCD last time I tried it (which was in January I think), and I've never seen VistaBootPRO till I found it on Google just now, so it could be a spyware-riddled piece of garbage for all I know.  Your mileage may vary.

In answer to your question, yes, you can make grub boot Vista automatically, but it still hits both the grub boot loader, then Vista's boot loader (hence the chainloader +1 directive in menu.lst).  No clue what a boot loader would have to do with MediaDirect, though.

---

### Post by gohanssjn on 2007-05-14
EasyBCD 1.52 wasfrustrating at some points, but 1.6 seems to do great now.

Problem is now, seems if I use hibernate and BCD, it goes straight to Vista.  UGH.

---

### Post by Computer Guru on 2007-05-15
I wouldn't say EasyBCD 1.52 was *terrible*, it just had some compatibility problems :P

EasyBCD 1.6 though - if I do say so myself, it works great :D

With regards to VistaBootPRO - the company distributing it has admitted to reverse-engineering EasyBCD's code (not difficult to do since it's .NET) and using it in their program with a different GUI. But they refuse to stop and we don't have the money and the lawyers to pursue this any further.

---

### Post by calraith on 2007-05-15
> **Computer Guru said:**
> But they refuse to stop and we don't have the money and the lawyers to pursue this any further.

We?  As in EasyBCD is yours?  Neat.

---

### Post by Computer Guru on 2007-05-15
The director of [NeoSmart Technologies](http://neosmart.net/) and author of [EasyBCD](http://neosmart.net/dl.php?id=1) at your service :)

---

### Post by gohanssjn on 2007-05-15
Oh, thanks!

Yeah, to be honest, I still used 1.52, and it wasn't terrible, I was just fustrated at one point :D

1.6 though, a God-send.  Sends me straight to GRUB when I want to too, Vista when I don't.  Awesome.

---

### Post by calraith on 2007-05-15
Go Computer Guru go!

---

### Post by n8bounds on 2007-05-15
Computer Guru, Anyone who makes it easier for people stuck with Vista to try linux is a friend.  Way to go!

---

### Post by Computer Guru on 2007-05-16
Thanks guys! :D

(you're making me blush!)

---

