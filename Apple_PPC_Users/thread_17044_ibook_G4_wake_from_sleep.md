---
title: "ibook G4 wake from sleep"
date: 2005-02-25
forum: Apple PPC Users
---

### Post by gwilkes on 2005-02-25
I realize there is other threads about this I have read all of them but it still doesn't answer my following question:

First some background:
When I had warty installed my screen would shut off when the screen was closed but it wouldn't go to sleep.  This is normal for warty with an ibook G4.  When I upgraded to hoary, closing the lid did actually bring the ibook G4 to sleep, the sleep light even came on.  However, opening the lid seem to wake up the machine, a hard drive noise happens and the caps lock key lights up if I press it, but the screen doesn't come back on.

I saw all kinds of fixes in other threads for this issue with G3 ibooks, I tried them but none worked.  There is also a kernel patch but it's for 2.6.8 and I'm running 2.6.10 now, and that seems like a lot to go through for this issue.  It seems this kernel patch is the only way for now unless I'm wrong.  Has anyone else heard of any developments in this area.  Some said it may make it for the 2.6.11 kernel but others say it's too late.  Is the reality that I will have to wait for the 2.6.12 kernel or later for this to be fixed?  Does anyone know or know of any other possible workarounds?  Thanks for any replys.

---

### Post by Pineault on 2005-02-25
Same problem here,  anyone have a quick anwer, I do remeber something about hal, and setting up a mouse ping, but that was seen on the debian PPC users list this fall. Before I go and dig that out any other ideas or solutions ?

---

### Post by Richard on 2005-02-26
Same issue with an ibook g4 on hoary.
I will try kernel 2.6.11.

---

### Post by Richard on 2005-02-26
I just find this thread :
[http://forums.gentoo.org/viewtopic-t-239895-highlight-wake.html](http://forums.gentoo.org/viewtopic-t-239895-highlight-wake.html)
The script stop hald when ibook go to sleep.

---

### Post by Pineault on 2005-03-06
Did you or anybody try the script, just stopping or killing HALD doesn't change anything so I'm hesitating, don't know if it's the right solution. On Ibook G4, running Hoary with latest kernel. Before update this wasn't an issue, since suspend was not activited, but now it is.
BTW this is a major problem, I'm not using my ubuntu partition because of it... Is there another more official list linked to hoary development where this should be signalled.

---

### Post by Richard on 2005-03-06
I found a temporary solution (disable DRI) :

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6977](https://bugzilla.ubuntu.com/show_bug.cgi?id=6977)

---

### Post by Pineault on 2005-03-06
More questions...
What are the consequences of this temporary solution on the overall functionning of Xorg, and how exactly do I do this in a clean way...

thanks

BTW is this issue going to be resolved in Hoarty final ?

---

### Post by spoetnik on 2005-03-14
This bug is spoiling my ubuntu pleasure on my iBook. The quick sleep and wake-up is one of the strongest things an iBook has opposite to a x86 laptop.
I really hope this anoying bug will be solved in the final hoary.

Dissableing dri in /etc/X11/xorg.conf soles the problem, but is not a verry clean sollution.

---

### Post by Pineault on 2005-03-14
On my g4 Ibook, disabling DRI does'nt solve anything, at least the way I did it, ie commenting out the 2 entries concerning dri in X11/xorg.conf. The Ibook resumes but the screen stays black....

---

### Post by callipeo on 2005-03-14
[QUOTE=Pineault]On my g4 Ibook, disabling DRI does'nt solve anything, at least the way I did it, ie commenting out the 2 entries concerning dri in X11/xorg.conf. The Ibook resumes but the screen stays black....[/QUOTE]

Since I had a lot difficulties testing the sleep functionality, I would suggest to do the following test:

- follow the instruction at [https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39)
- reboot in single user mode (or sudo telinit 1)
- /etc/init.d/powernowd start
- /etc/init.d/pbbuttonsd start
- put the laptop on suspend to ram, and check if it wakes up

If that doesn't work, then your system has a problem :-)
If that works, you can try to dpkg-reconfigure xserver-xorg and disable the loading of the dri module, then reboot and let the system start at the default runlevel: sleep should work, but even if something goes wrong, you have localized the problem. BTW on my laptop, with dri disabled, sleep works just fine with hald running.

Hope this helps.

---

### Post by spoetnik on 2005-03-15
It seems the sleep bug is a different bug between G3 and G4. 
On my G3 Ibook stopping halt using a script solves the sleep problem.
Follow this link for the sollution: [http://ubuntuforums.org/showthread.php?t=2368](http://ubuntuforums.org/showthread.php?t=2368)

On my G4 Ibook, the problem is solved by just dissabeling dri. Edit /etc/X11/xorg.conf, and comment out the 'DRI' section. 

To bad that this bug show up on the latest kernel. Ik hope it will be solved in the final hoary version.

---

### Post by Pineault on 2005-03-15
Found a solution and a new bug...

Well configured adequately Xorg-server (without DRI) with the appropriate command, thanks.

But at first problem was not eradicated, actually my ibook wasn't sleeping anymore since I had modified the Powerpref settings, from suspend to ram to blank screen, that's the new problem I was having, when closing lid, screen went blan and wouldn't come up anymore...

Changed powerpref settings to suspend to RAM and sleep works fine, except that USB mouse does'nt work on wake up, forget to unplug USB devices.

Hope all this is cleared up in the new release...

no next problem/challenge is getting my USB wireless working adequately (Dlink dwl-122)

---

### Post by callipeo on 2005-03-16
[QUOTE=Pineault]Changed powerpref settings to suspend to RAM and sleep works fine, except that USB mouse does'nt work on wake up, forget to unplug USB devices.

Hope all this is cleared up in the new release...
[/QUOTE]

Unfortunately, this is a well-known problem; it seems there isn't a clean soultion. Maybe you can get some hints at [https://bugzilla.ubuntu.com/show_bug.cgi?id=7619](https://bugzilla.ubuntu.com/show_bug.cgi?id=7619)

---

### Post by Pineault on 2005-03-16
Put my Ibook to sleep after unplugging USB devices, wlan and wireless mouse, 
upon wake up screen black or so dark can't see anyhting, have to reboot....
Powerpref configured with blank screen options off...
When this doesn't happen usb crashes on wake  so no mouse our wifi (I have a Dlink122 usb wifi)

I'm realizing that the Ibook isn't at all usable with Ubuntu as a laptop, ie with suspend/sleep and with wifi...

It works only at my desk, plugged in the wired ethernet and plugged in the wall, but then that makes it a desktop not a laptop, so with ubuntu hoary my laptop becomes a desktop
 ](*,) 

I think I'll fall back on a kde installed on X OS until things get better, too many bugs

---

