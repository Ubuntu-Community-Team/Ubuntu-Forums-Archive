---
title: "Ubuntu will not install"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by crkhobbit on 2007-03-19
Hi and thanks for reading this!  I have always been a Windows user (MCSA) but Linux and Ubuntu look like the answer to alot of my prayers.

I would love to never need to boot up Windows again, but Ubuntu will not install for me.  The CD boots up fine and it starts going through the load process but I eventually get to an error message saying that Xserver cannot be started and I may need to reconfigure it.  If I view the logs I can see that they end with a "no screens found" message.

I've managed to find the command to start the reconfigure process:
```
sudo dpkg-reconfigure xserver-xorg
```

And the command to restart Gnome:
```
sudo /etc/init.d/gdm restart
```

Gnome stops ok, but fails on the restart with no explanation.  I'm still running from the CD, I kinda feel that if I can install to my hdd then I could atleast fiddle with settings or install necessary drivers as well as being able to reboot without losing any settings.

If it matters, I have an Nvidia GeForce 7600 GS.  My best guess as to what is failing is either something associated with my video card, or maybe my mouse.

This is my first journey out of Windows territory, and I'm a little scared and a lot frustrated.  Any and all help is greatly appreciated!  Thanks in advance.

---

### Post by Kateikyoushi on 2007-03-19
Read this thread and follow the instructions. [LINK]("http://ubuntuforums.org/showthread.php?t=379807")

---

### Post by lamalex on 2007-03-19
what is your motherboard? I had this exact problem with an nforce4 asus k8n4-e deluxe. try putting these boot flag on (hit f6 before you hit enter to boot to live cd and add these: noapic acpi=off pci=nommconfig that worked for me.

---

### Post by crkhobbit on 2007-03-20
Thanks for the link to the other thread, that looks like it has the potential to fix my issue.

I have a VIA chipset motherboard, I can't remember the specifics.  Will post back this afternoon to let you know how these fixes work.  It's nice to have a couple different methods to try.  I'm not used to needing support, I'm usually the one that gives it and I usually can figure most things out on my own - Linux so far has been humbling which I seem to be reading in lots of posts.

Thanks sooo very much!

---

