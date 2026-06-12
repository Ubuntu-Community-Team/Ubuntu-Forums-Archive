---
title: "Ubuntu Christian Edition"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by MikRose on 2008-01-05
Since I'm not really sure what to ask, please bear with me:

I have been using Ubuntu (6.06, then 7.04) for many months.  When I heard about Christian Edition I ordered the CD and installed it on a clean install, then kept it updated.  When the Update to 7.10 appeared on my Update Manager, I upgraded to 7.10 over several days via a dial-up at night.  It told me I was upgraded and up-to-date.  Then I had trouble with internal/external modem (which I have since fixed-and have the linmodems for each version), so I did a clean reinstall of CE 7.04, then updated again.  To keep up with all the new features, I ordered 7.10 on CD from Linux (knowing it wasn't CE) and installed it on the largest free space on hdb (XP is on hda).  I have the Grub on hd0 and have the choice of OSs when I boot, and now have:

 2.6.20-16-generic, 2.6.20-15-generic, and 2.6.20-14-generic (7.10) versions. 

I notice a slow-down of my system when using any Linux now, and would simply like to have all removed except Christian Edition on hdb with XP on hda.  When I do that, how do I just keep my CE up-to-date?  Do I just download the recommended updates for my CE and that is all it takes?  Or if a new kernel comes out for CE (7.10), do I need to get that CD, or will my regular updates take care of that for me over time?  I just want CE from now on.

---

### Post by reckless2k2 on 2008-01-05
you can remove older kernels as long as your current kernel is working for you if that's what you're asking. sometimes people report bad kernel experiences and revert back to older kernel so that's why you keep at least 1 extra around.

---

### Post by MikRose on 2008-01-06
OK, thanks for the reply.  I guess that was what I was asking, but wanted to make sure I put in all the details "just in case".  I will go to Synaptic and refine my setup, thanks again.

---

### Post by Paulmd on 2008-01-06
> **MikRose said:**
> Since I'm not really sure what to ask, please bear with me:

I have been using Ubuntu (6.06, then 7.04) for many months.  When I heard about Christian Edition I ordered the CD and installed it on a clean install, then kept it updated.  When the Update to 7.10 appeared on my Update Manager, I upgraded to 7.10 over several days via a dial-up at night.  It told me I was upgraded and up-to-date.  Then I had trouble with internal/external modem (which I have since fixed-and have the linmodems for each version), so I did a clean reinstall of CE 7.04, then updated again.  To keep up with all the new features, I ordered 7.10 on CD from Linux (knowing it wasn't CE) and installed it on the largest free space on hdb (XP is on hda).  I have the Grub on hd0 and have the choice of OSs when I boot, and now have:

 2.6.20-16-generic, 2.6.20-15-generic, and 2.6.20-14-generic (7.10) versions. 

I notice a slow-down of my system when using any Linux now, and would simply like to have all removed except Christian Edition on hdb with XP on hda.  When I do that, how do I just keep my CE up-to-date?  Do I just download the recommended updates for my CE and that is all it takes?  Or if a new kernel comes out for CE (7.10), do I need to get that CD, or will my regular updates take care of that for me over time?  I just want CE from now on.


Christian edition seems to differ from Vanilla Ubuntu only by some applications. 
You'd update it to Gutsy by going in the terminal and typing:


```
sudo update-manager -c
```
Also, I'm betting it has slightly different repositories for software and updates. You can check them out by typing:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by twin_57103 on 2008-01-06
As far as updating: as long as you've got a high-speed internet connection, you should be able to do it through the update manager GUI automatically.  If you have dial-up, you may want to consider borrowing someone's high-speed connection for this, as it is a long process.  I haven't used CE (but hope to at some point), but it should be similar to any other *buntu in this regard.

God bless!
twin_57103

---

### Post by MikRose on 2008-01-10
One more time!  I was able to remove the 7.10 kernel from my system using the Synaptic Package Manager, but I left out the _Ubuntu 7.10, memtest 86+_ line.  Now it is the top line on my Grub during the initial boot!  Also, now XP has moved up as the second choice, ahead of my 7.04 CE kernel (which I'd like as my default).  I have read about editing the Grub, and my menu.lst file, but not sure of myself.  Would you like a copy of my mail.lst?  Since I can't boot into 7.10, I have made a copy of mail.lst using the terminal command in 7.04 CE, but I suppose the Grub is the Grub no matter what?  Thanks...

---

