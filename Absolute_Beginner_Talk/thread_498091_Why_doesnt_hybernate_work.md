---
title: "Why doesnt hybernate work?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-10
When ever I use it it crashes the splash load screen, then I have to restart the computer.

---

### Post by davidsrsb on 2007-07-10
Hibernate is always dodgy on Linux, because of acpi bugs and flaws in the whole Linux method at this time, but you must have enough swap - at least 2x ram size

---

### Post by macogw on 2007-07-10
Let me tell you a story....
Once upon a time, in a place called Redmond, Washington, there was an evil monopoly called Microsoft that was being challenged by these little groups of hackers making nice software for free.  Fearing that their position as a monopoly would be in trouble, Microsoft made a deal with a bunch of hardware manufacturers.  The deal was that the hardware manufacturers would each disobey the standards for ACPI (power management) and then tell Microsoft exactly what they had changed so that Microsoft could make sure its own software would be able to handle these bugs that were purposely introduced in the hardware.  The deal also included not telling those little groups of hackers what the secret special bugs were.  This would ensure that Microsoft's competition would stumble when trying to make power management work properly in software that didn't come from Microsoft.  If consumers can't use hibernate or suspend, they thought, they will think everything that's not from Microsoft is junk!  The little groups of hackers carried on, tweaking the code for each piece of hardware individually, trying to discover what each company had done to break ACPI standardization on each piece of hardware.  It was slow work, though, and sometimes when they got it working on one piece of hardware, it'd break for another piece of hardware, so they had to be very careful about what changes they made.  Those little groups of hackers aren't quite so little anymore, but they're still fighting the buggy hardware and trying very hard to make it work with no hints as to what to do.

by the way, if you want a source, [here](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf) is a pdf of a Microsoft memo from 1999 which was released as evidence in Comes v. Microsoft in January 2007.

---

### Post by ~~Tito~~ on 2007-07-11
Wow, Bill Gates can suck the Linux Penguin's balls. . . LOL, hahahahahahahahahaha. . . . . . Does that swap change work, if so how?

---

### Post by ~~Tito~~ on 2007-07-11
Does it work? Anyone? 
Hp Pavilion zv5000 Ati mobility Readeon version.

---

### Post by ~~Tito~~ on 2007-07-11
bump . . .

---

### Post by AmyRose on 2007-07-11
> **~~Tito~~ said:**
> Does it work? Anyone? 
Hp Pavilion zv5000 Ati mobility Readeon version.Are you using the proprietary ATI drivers? Proprietary video drivers sometimes keep that from working, but as an nvidia owner, I'd rather have OpenGL than hibernate.

Personally, I don't mind not being able to hibernate. What's wrong with (gasp!) shutting down normally? :P

---

### Post by ~~Tito~~ on 2007-07-11
No, I'm just use to using it. Na ill just set the settings to make it when i close the lid of my laptop to close it.

---

### Post by ~~Tito~~ on 2007-07-11
Wait, it wont. . .  . Any other program that will do it?

---

### Post by gohanssjn on 2007-08-28
Personally, I love hibernate.  I usually keep a few documents open on my laptop for class and being able to get them up quickly but not burn any power is a huge plus.

---

### Post by st33med on 2007-08-28
Try this:
```
sudo apt-get install uswsusp
```

Then:
```
s2disk
```

Does it work?

---

### Post by tact on 2007-08-28
I had a lot of problems with suspend and hibernate on my Dell Latitude D410 using the standard ubuntu kernels.   I just lived with it and did shutdowns each time.

A few weeks ago I found [this]("http://ubuntuforums.org/showthread.php?t=511974") thread that gives a guide how to get the latest "gutsy" kernel running on Edgy or Feisty.  Just for the sake of giving it a go (there is always the original kernels there in GRUB to fall back on)...  I followed the guide.  (I am currently running kernel 2.6.22-10)

I can report that now my laptop suspends, resumes, etc perfectly.  I love it.  

The wifi stack is also new and though this may have nothing to do with my experience now (cos I had no issues with networking before anyway and could never suspend/hibernate either) - I am happy to report that I can suspend/hibernate while connected to wifi (or wired) network at home, then resume and it does not matter if i am on a different wifi network, or changed to a wired network, wifi and wired adapters all resume perfectly!   I find it such a relief.  :)

---

### Post by tact on 2007-08-29
...oh ya forgot to mention...  DVD burning also works again with the newer kernel.  :)  No more burning coasters

---

