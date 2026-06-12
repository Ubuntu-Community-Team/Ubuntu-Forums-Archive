---
title: "Ubuntu 13.04 blank screen w/cursor after live install"
date: 2013-06-08
forum: Apple Hardware Users
---

### Post by Strat1290 on 2013-06-08
Hello all,  I recently (with your help!) was able to successfully install Lubuntu on my G4 eMac PPC.  I want to see how Ubuntu 13.04 runs on my machine.  I can boot from the cd with the following parameters

live snd-powermac.blacklist=yes video=radeonfb:1024x768-32@60

After booting from the CD, the screen remains black with only the cursor.  I keep getting an error message stating: "...13.04 has experienced an internal error"  show details yields: "/usr/bin/nautilus"  I can click continue and the screen remains black.  (initially, that was saying compiz... not nautilus)

With ctrl-alt-delete I can log out, and I go to the Ubuntu login screen with the orange+pink background.  I can Login with "ubuntu" username, blank pw, and then I get right back to the black screen with the cursor and the error message.  

Any suggestions?  Thanksin advance!

Dan

---

### Post by este.el.paz on 2013-06-08
> **Strat1290 said:**
> Hello all,  I recently (with your help!) was able to successfully install Lubuntu on my G4 eMac PPC.  I want to see how Ubuntu 13.04 runs on my machine.  I can Login with "ubuntu" username, blank pw, and then I get right back to the black screen with the cursor and the error message.  

Any suggestions?  Thanksin advance!

Dan

Dan:

Welcome to Lubuntu . . . if it works, don't try to fix it by trying something else.  In PPC-land we need to see the letters "PPC" on the .iso before we can move forward . . . .  PPC is more and more "ancient" and therefore it isn't even mentioned by most distros.  I just checked the Ubuntu 13.04 download page . . . it only mentions 32 bit and 64 bit . . . none of the options has "PPC" in the name . . . .  Fall back, retreat to Lubuntu . . . I think Lubun might have a 13.04 version for PPC??  I didn't check that, just that Ubun doesn't have PPC option.

e.e.p.

---

### Post by Strat1290 on 2013-06-08
> **este.el.paz said:**
> Dan:

Welcome to Lubuntu . . . if it works, don't try to fix it by trying something else. In PPC-land we need to see the letters "PPC" on the .iso before we can move forward . . . . PPC is more and more "ancient" and therefore it isn't even mentioned by most distros. I just checked the Ubuntu 13.04 download page . . . it only mentions 32 bit and 64 bit . . . none of the options has "PPC" in the name . . . . Fall back, retreat to Lubuntu . . . I think Lubun might have a 13.04 version for PPC?? I didn't check that, just that Ubun doesn't have PPC option.

e.e.p.




Hi este, thanks for the reply.  The ISO does have ppc in it... is this not right?  I got the file here [http://cdimage.ubuntu.com/releases/raring/release/](http://cdimage.ubuntu.com/releases/raring/release/), looks like it is for PPC.  Lubuntu is working, however I was curious about Ubuntu.  

The name of the ISO is ubuntu-13.04-desktop-powerpc.iso

---

### Post by este.el.paz on 2013-06-08
> **Strat1290 said:**
> Hi este, thanks for the reply.  The ISO does have ppc in it... is this not right?  I got the file here [http://cdimage.ubuntu.com/releases/raring/release/](http://cdimage.ubuntu.com/releases/raring/release/), looks like it is for PPC.  Lubuntu is working, however I was curious about Ubuntu.  

The name of the ISO is ubuntu-13.04-desktop-powerpc.iso

Strat:

It looks like you found your way to a PPC page, so yes, that should be fine.  That page didn't show up when I went through the forum links to the Ubuntu community downloads . . . I think I've made this mistake before on what versions of 'buntu work for PPC . . . but Ubuntu doesn't seem to make that PPC option easy to find--since I didn't find it this AM.  It just seems like the Lubuntu version is more worked through for PPC as far as what others and my own experience has shown--ease of booting up w/o needing a lot of fiddling.

So, back to your experience with black screen and cursor . . . I probably can't offer any more help.  Usually if there is a video card driver problem you don't get passed a black screen or a divided screen . . . the fact that you can see where to log in and the cursor shows up is "better" . . . .  Perhaps try to play with the boot parameters at bit more . . . if you get to the first log in or Yaboot log in, you can hit "tab" or "shift" . . . and it gives you a list of other boot options?  It should give you that direction in the log in list where it shows "video=ofonly" . . . .  I have found that adding some of those to the boot parameters may make a difference.

e.e.p.

---

### Post by michiganmac on 2013-06-08
I've tried many times to get the Ubuntu 13.04 PPC live cd  to work on several of my Powermac G4's to no avail. Several weeks ago, I asked here on this forum if anyone had managed to get it to work on a Powermac G4 or G5, but no one responded. 

However, the live cd for Ubuntu 12.04 LTS (PPC) works really well on my MDD. No boot parameters are required. You might try out that one to see how you like Ubuntu compared to Lubuntu.

---

### Post by Strat1290 on 2013-06-08
Thanks, Mich.  Were you having the same problem as me?

I will try the ubuntu 12.04.  I like Lubuntu, however there are a lot of flash videos I cant play which is frustrating and I'd like the newer interface of Ubuntu.  I'll give this a shot.

---

### Post by este.el.paz on 2013-06-08
> **michiganmac said:**
> I've tried many times to get the Ubuntu 13.04 PPC live cd  to work on several of my Powermac G4's to no avail. Several weeks ago, I asked here on this forum if anyone had managed to get it to work on a Powermac G4 or G5, but no one responded. 

However, the live cd for Ubuntu 12.04 LTS (PPC) works really well on my MDD. No boot parameters are required. You might try out that one to see how you like Ubuntu compared to Lubuntu.

@mm:

Thanks for jumping in with your insights . . . which seems to parallel my own efforts to get something to run on my G4 iMac and G4 iBook; I may have tried the Ubun 12 version but didn't seem to give me much more than what I'm running now, which is the rsavage iso of Xubun 12.04, but using LXDE.  I think I was able to boot a Lu 13.04 beta awhile back on my iBook, when philw was looking for testers on it, but it isn't LTS so I hesitated to spend the time on it.  One of the issues for PPC is the hardware, and the other seems to be needing to retro compile the "nv" driver . . . which I did with some instructional help awhile back.  Now, with the LTS I'll be OK until 2017 apparently and if the iBook lasts that long I can think about what to update to . . . then.  In the meanwhile if something runs PPC OK without a lot of fiddling . . . I don't try to "fix it."  On my MBPro OTH, which is more current hardware there are more options, and it's like trying on the latest fashions . . . PPC is becoming more rare so giving support to the flavors that are more friendly to it, like Lubuntu, is a form of self-preservation . . . .

e.e.p.

---

### Post by michiganmac on 2013-06-08
> **Strat1290 said:**
> Thanks, Mich.  Were you having the same problem as me?

Yep, I use the same boot parameters and get the same error dialog box. When I click the continue button in the error dialog box, it disappears and the display shows a movable pointer on a black screen. That's as far as the procedure gets.

Hitting "control-alt-F1" will get me to a console. At that point, I don't know enough about Linux to do anything that helps. I can restart the computer back into OS X on my hard drive by typing "sudo reboot", then hitting return when prompted, but that's about all.

---

### Post by michiganmac on 2013-06-08
> **este.el.paz said:**
> @mm:

Thanks for jumping in with your insights . . . which seems to parallel my own efforts to get something to run on my G4 iMac and G4 iBook; I may have tried the Ubun 12 version but didn't seem to give me much more than what I'm running now, which is the rsavage iso of Xubun 12.04, but using LXDE.  I think I was able to boot a Lu 13.04 beta awhile back on my iBook, when philw was looking for testers on it, but it isn't LTS so I hesitated to spend the time on it.  One of the issues for PPC is the hardware, and the other seems to be needing to retro compile the "nv" driver . . . which I did with some instructional help awhile back.  Now, with the LTS I'll be OK until 2017 apparently and if the iBook lasts that long I can think about what to update to . . . then.  In the meanwhile if something runs PPC OK without a lot of fiddling . . . I don't try to "fix it."  On my MBPro OTH, which is more current hardware there are more options, and it's like trying on the latest fashions . . . PPC is becoming more rare so giving support to the flavors that are more friendly to it, like Lubuntu, is a form of self-preservation . . . .

e.e.p.

I agree with you about supporting Lubuntu. I tested Lubuntu 13.04 and I am currently actively testing Lubuntu 13.10. I've had 13.04 on my Ibook G4 (1.33 GHz mid-2005 model) for about 2 months and it has been rock solid stable. 

I find it's not as fast as OS X 10.5.8, but I feel it's more secure for using online, since OS X 10.5.8 hasn't had a security update in several years. This is the main reason I have decided to use Linux on my Powermac.

---

### Post by abtabt on 2013-06-09
can this help ?

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

---

### Post by abtabt on 2013-06-09
Bump

---

### Post by michiganmac on 2013-06-09
> **abtabt said:**
> can this help ?

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)


I just tried this with Ubuntu 13.04 on my Dual 1.25 MDD (with Radeon 9800 Pro video card) and it didn't help. I am able to get to a display with what appears to be the correct resolution for my monitor, but at an extremely low color depth. 

I have no problems using the Live CD for Lubuntu 13.04 or Lubuntu 13.10. I use the following boot parameters for Lubuntu:

```
live video=radeonfb:1920x1080-32@60 snd-powermac.blacklist=yes
```

The first part takes care of the resolution and color depth, and the second part fixes the "recursive fix..." error.

Thanks for trying, though. :p

---

