---
title: "Multiple boot questions"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Spotta on 2007-05-06
Hi

While being quite advanced at Win, like most people posting here I'm a Linux n00b.
I've finally taken the plunge, downloaded both Ubuntu and Kubuntu live cd's, tested with my hardware and then decided to install to my hdd's to fully check them both out.
I have been dual booting XPx64 and Vista for the last few months, but Vista works fine with all my software so I decided to get rid of my x64 partiton and install them in the space.
I spent a while searching this forum for hints, Imaged all drives for back up and partitioned the space as 1GB swap, 20GB unpartitioned from within Win and then decided to install Ubuntu - this went fine.
Ubuntu and Vista db fine.
Then feeling more at home with the install, proceded to install Kubuntu, during the install shrinking the 20GB Ubuntu partition down to 10GB, creating another 10GB partition for Kubuntu. It automatically choose the existing swap partition (is this a problem?) and seemed install ok.

Now when I boot, Ubuntu Works, Vista works but Kubuntu doesn't.
I get a loading screen, the blue lines completes, then it hangs with the cursor flashing.

How do i go about fixing this- Do I uninstall and install again and does it need it's own swap partition?

Cheers

Spotta

---

### Post by benerivo on 2007-05-06
I'm not sure what the problem is, it may be that the window environment has failed to start and could have something to do with the graphics card driver. Try typing something at the flashing prompt such as startx to see what happens.
 Anyway I think this may become irrelevant as I think you should have a more straightfoward OS installation on the pc. By having both ubuntu, and kubuntu installed separately you are really doing pretty much the same thing twice, as they are both essentially the same distro, except they are using different desktop environments. What you should do is just install ubuntu, then from within ubuntu, you can add the kde desktop environment through the synaptic package manager (searching for kubuntu-desktop). When installed you can then boot in to Ubuntu and have the choice of either Gnome or KDE to use.
 Having linux distros use the same swap partition is correct.

---

### Post by Tux Aubrey on 2007-05-06
Hi, I saw your thread sitting unanswered (but so, obviously did benerivo) so, although I'm no expert on this, I'll give my two cents worth.

Triple (or more) booting is fine but for what I think you are after its probably not necessary.

You can have both the Gnome (Ubuntu) and KDE desktops running on the same installation.  This will save you space and the hassles of carrying duplicate files and /homes.  The different desktops and their native apps will then be available as different "sessions" from the Ubuntu log-in screen.  

The most direct way to install the KDE desktop is to open the terminal and copy this:

```
sudo aptitude install kubuntu-desktop
```

Otherwise you can search for it in Synaptic.

Then log out (don't shutdown) and use a KDE session (from the bottom left of the log-in screen)

If you like it, you can just delete the Kubuntu partition. (You might want to tidy up the file called root/grub/menu.lst later to remove all references to it.)

There's lots more you can do with sessions and a whole raft of different window managers.  Lots of fun.

Enjoy

---

### Post by Spotta on 2007-05-06
Thanks to the pair of you.
I cannot seem to be able to find the thread now - but when I was researching there was a reason why I installed both distro's instead of doing the other way.

I think you pegged it when you mentioned about graphics drivers. typing startx did nothing on the normal boot, but when typed in recovery mode something happened and I got the msg 'Fatel Server Found - no screens found' - although it works fine from the cd.

My machine is set up with 3 screens, a 20" & 19" on a PCI-E 7900GT and a second 19" on a PCI FX5500.
Both distro's work fine from the cd (but only on the 19" attached to the 7900GT) getting the triple screens sorted was going to be a future question when I had learnt the basics - but it looks like its causing problems already

Spotta

---

