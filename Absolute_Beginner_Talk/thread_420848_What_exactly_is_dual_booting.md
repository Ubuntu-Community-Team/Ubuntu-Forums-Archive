---
title: "What exactly is dual booting?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-04-24
So what is dual booting, If I want to boot vista and Ubunutu, already having ubuntu, how much room should I make for vista, do I need to make room for all my windows programs, or just for the os, I'm kind of confused:confused:

---

### Post by freebird54 on 2007-04-24
Dual boot, in this context, mean being given a choice on bootup as to which system to start.  If you are Ubuntu already, then you see choices when yolu start up now - Vista would just be another choice on that menu.

You need to leave room for the OS, and some of its programs.  Then you need to leave room for the rest of it on a filesystem that it knows how to read.  This COULD be a shared partition if you wish.  I don't know how well Vista plays with this scenario, but apparently it usually ships with 2 partitions - so it must at least be useable that way.

Hope that helps!

---

### Post by Emerzen on 2007-04-24
Hi, dual booting is having 2 (or more) operating systems available on 1 PC.  In other words, when you turn on your computer and the menu first appears, you'll have an option to select, say, Microsoft XP.  

Ubuntu and Windows do not interoperate when both installed, that means you'll need room for both OSs and all the programs you'll need for each.  How you'll divide your space depends on how big your harddrive is, and how many programs you'll want to run under each OS.

It's much easier to install Windows, then Ubuntu because when Ubuntu installs it will recognize Windows and automatically configure GRUB to boot Windows if selected.  When you install Windows after Ubuntu, Windows overwrites GRUB and ignores Ubuntu so you have to reinstall GRUB and configure it for both OSs.  In any case, if reinstalling Ubuntu is no big deal I would install Vista then Ubuntu.  

Now, finally, I've heard Vista has a new bootloader that may require some additional steps to have GRUB load for you.  I don't know as I don't have a copy of Vista.  I would search the forums and find out what others have experienced w/ Vista and dual boot.

---

### Post by LostArt on 2007-04-24
So will I experience a very large decrease in performance if I'm running relatively large programs like MAYA and Reason and playing far cry on win4lin

---

### Post by Emerzen on 2007-04-24
I'm not sure how this question relates to your first question?

---

### Post by LostArt on 2007-04-24
I wouldn't have to dual boot if I was just using windows emulation. Know what I mean

---

### Post by kevmartin on 2007-04-24
> **LostArt said:**
> I wouldn't have to dual boot if I was just using windows emulation. Know what I mean
I haven't read up on win4lin, but other virtualization programs do cause a performance hit. Win4Lin I see is $69.99 on their web site.  Others are available free - virtualbox and vmware are the popular ones.  There's also wine, which allows you to run (some) windows apps directly inside linux.

If Win4Lin is as good as they make out, I might consider paying for it, and they do have a money back guarantee ... hmmmm ... think I'll search the forums for others' experiences with it :)

---

### Post by Emerzen on 2007-04-24
I see what you mean, sorry.  I'ld imagine you would take a performance hit w/ emulation but I'm not sure as I don't emulate anything.  It seems to me, from what I've read though, that setting up emulation will be a much larger PITA than dual-boot which is pretty straightforward.

---

### Post by LostArt on 2007-04-24
I'M not sure though because I don't have much space for a dual boot, and I don't understand the whole partition thing. I wouldn't know how large to make it

---

### Post by Emerzen on 2007-04-25
How much space do you have on your drive?  Setting up partitions is pretty painless if you already have Ubuntu installed.

---

