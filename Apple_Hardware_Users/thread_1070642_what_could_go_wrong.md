---
title: "what could go wrong?"
date: 2009-02-15
forum: Apple Hardware Users
---

### Post by cosmicappuccino on 2009-02-15
I'm a Linux newbie and I'm contemplating installing Ubuntu on a partition on my Macbook (which already has Leopard and XP running successfully with Boot Camp).

I've already attempted an installation of Ubuntu on a 5-year-old PC I have, which doesn't seem to have worked because I can't log in (I've [[COLOR="Teal"]posted[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1069218")  about this in the beginner forum). I was happy to experiment with this older computer.

However, I value my Macbook rather more! I do really want Ubuntu on it, but am a little scared, and so would appreciate other Mac users' warnings and suggestions about how to avoid problems...

---

### Post by cyberdork33 on 2009-02-15
First read here for general install instructions:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Then check here to find information specific to your Mac model version:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by cosmicappuccino on 2009-02-15
Thanks! Really helpful.

---

### Post by spencercarran on 2009-02-15
I did the same thing and it worked out pretty well. If you go to [http://blog.gnist.org/article.php?story=Triple-Boot-OSX-Ubuntu-Vista]("http://blog.gnist.org/article.php?story=Triple-Boot-OSX-Ubuntu-Vista") there are instructions, the fact that it is XP rather than Vista should make no difference. You already have Windows in Bootcamp, so you're most of the way there already.

NB: When I followed the instructions on that site for where to put Grub, it broke my MBR anyways. Don't panic, OS X can still boot fine (it seems nearly impervious; I've destroyed my bootloaders so many times and OS X always survives) and rEFIt will fix your Ubuntu bootloader for you. For Windows, you will need to insert your recovery disk (this can also be the CD you used to install it) and ask it to fix your MBR. Now you will have a nice rEFIt menu to choose between the three operating systems and they will all boot just fine. This will still leave a delay with a menu for different kernels when you boot Ubuntu. Install the program Start-up Manager from Add/Remove to adjust the settings for Ubuntu's boot-up to your preferences- I personally got rid of the delay entirely and just have it go straight into Ubuntu. Others would recommend against that for recovery purposes, such as if you ever need to select a different kernel at start-up because you broke something badly.

---

### Post by cyberdork33 on 2009-02-15
> **spencercarran said:**
> Install the program Start-up Manager from Add/Remove to adjust the settings for Ubuntu's boot-up to your preferences- I personally got rid of the delay entirely and just have it go straight into Ubuntu. Others would recommend against that for recovery purposes, such as if you ever need to select a different kernel at start-up because you broke something badly.
yes, set the delay to like 3 seconds and turn on the hidden menu item and you will never see grub, but you can hit escape in those three seconds to get the menu up if you needed.

---

### Post by cosmicappuccino on 2009-02-16
Thanks!

Does anyone have any suggestions about partition sizes?

(Currently I have a 12GB partition for Windows - I kept it small as I hardly ever use it. I'd expect to use Ubuntu a bit more than Windows, although I'd keep using Mac OSX as the primary OS...)

---

### Post by cyberdork33 on 2009-02-16
10GB as a minimum (which includes space for swap).

Be prepared to reinstall windows as it does not like to have the partitions messed with after it has been installed. not that you will have to, but I would back things up in case.

---

