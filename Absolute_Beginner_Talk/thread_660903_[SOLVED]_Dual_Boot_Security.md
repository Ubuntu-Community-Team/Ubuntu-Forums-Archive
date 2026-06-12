---
title: "[SOLVED] Dual Boot Security"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by lil0tik on 2008-01-07
Hi all -

Sorry if this has been answered before / is a total noob question.  I'm currently running Gutsy on a Dell laptop, and am considering rebuilding it to dual-boot with XP (I hate it, but I make electronic music and can't do without some Windows apps).  I'd rather keep the windows install as minimal as possible - without cumbersome security-ware - and don't plan on using if for anything but making music with local tools.

So, my question is: If I ONLY connect to the internet while running Ubuntu, to what degree do I have to worry about windows security?  Will the XP install compromise Ubuntu's security?

---

### Post by jba6511 on 2008-01-07
you should be fine. Just use common sense, such as anti-virus when using xp, be careful what you download, etc.

---

### Post by stump138 on 2008-01-07
If you aren't using the internet, you could run XP jus fine and not worry.  It will have no effect on your ubuntu install other than the loss of hard drive space :)  I have a similar setup, that has no protections of any kind as I only boot windows to run one application.

Have you considered virtualization?  VMWare or virtualbox may be all you need.

GL on the setup:)

---

### Post by p_quarles on 2008-01-07
No, XP won't compromise Ubuntu in any way -- security or otherwise. They're completely independent of one another. 

If you leave the net connection off in XP, you really don't need to worry much about security ware.

---

### Post by PeterJS on 2008-01-07
As long as XP never sees the internet, and you don't pass (untrusted/unscanned) exes on to it you should be fine. It's kinda hard to compromise something that never sees the light of day.

---

### Post by mdpalow on 2008-01-07
> **lil0tik said:**
> Hi all -

Sorry if this has been answered before / is a total noob question.  I'm currently running Gutsy on a Dell laptop, and am considering rebuilding it to dual-boot with XP (I hate it, but I make electronic music and can't do without some Windows apps).  I'd rather keep the windows install as minimal as possible - without cumbersome security-ware - and don't plan on using if for anything but making music with local tools.

So, my question is: If I ONLY connect to the internet while running Ubuntu, to what degree do I have to worry about windows security?  Will the XP install compromise Ubuntu's security?

You'll be fine. However, you do sound like a perfect candidate for VMware. I have Windows XP installed in my Ubuntu as a 'virtual' system and run it when I have a need to use two special applications. If you're not sure what we're (me and stump138) are talking about - it's simply installing your Windows XP disk to a Virtual Server within Ubuntu. Then, when you need to run that special program, you just go to your menu and click on VMware and run Windows XP. Then Windows XP boots up right on your Ubuntu desktop. You can even go full screen mode, but be careful - you might forget your still running Ubuntu in the background. lol :) Sometimes when I've been working on something in Windows for a while AND in full screen, I forget I'm still in Ubuntu!

Anyway, here's a good link to install VMware:

[VMware Link]("http://ubuntuforums.org/showthread.php?t=183209")

It's actually pretty simple..

good luck...

---

### Post by lil0tik on 2008-01-07
Awesome!  Thanks very much to everybody for your input.  I'm certainly going to look into the VMWare option.

-pat.

---

