---
title: "Blank Screen between Grub and Login"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Mikeoak on 2007-10-19
When I start my computer, after selecting Ubuntu OS, my screen goes blank until the login screen comes up, also blank at shutdown.  This is not a big problem as Gutsy is fine except for that.  I know that when I was using Mepis, I had to go into Boot>Grub and change the setting to 785.  Is there a similar fix for Ubuntu Gutsy?:KS

My system: Dell 2400 with Dell 17" LCD monitor

---

### Post by bdk6m2007 on 2007-10-19
I have the same hardware and have the same issue.  It's not an issue any more because other than the black screen everything seems to be working, however, when I first installed edgy I had problems and the machine would just hand with the black screen until I removed *splash* from the boot parameters.  I would LOVE to see a solution to this as it always makes me nervous when the screen is just black but the computer is obviously doing something.......

---

### Post by daskalos on 2007-10-19
I had exactly the same problem. 
I was able to solve it by installing startup-manager 
From startup-manager choose the correct resolution for you screen.

Then you must go to system menu -> system administration -> screen and grafics 
and reselect your monitor and your card. From what I saw this added some
options in xorg.conf. Save and reboot.
First time I rebooted I had to reselect my monitor since it is an lcd monitor and it gave
me only 640x400.

---

### Post by Mikeoak on 2007-10-19
Thanks.  From what I can find out, this is a common problem and a bug that needs to be fixed,hopefully in the next few days.  I tried changing the vga no to different settings: 791, 785, 792, 795, 788, but none of them made any difference.  Booting in a safe mode shows scrolling text, but you end up as root and also need to run startx.:lolflag:

---

### Post by bdk6m2007 on 2007-10-19
Thanks, I'll definitely give this a try when I get home tonight!

---

### Post by Mikeoak on 2007-10-19
Thanks for the info on the Startup Manager.:guitar:
That fixed it, but I have to leave it at 480x640 (doesn't work at higher resolution. resolution which apparently only sets resolution for boot up because when I login, my screen then shows at 1280x1024 which is what I prefer.

Also on my Gutsy install there is no systems administrator but I can go to Sysem>Preferences>Screen Resolution and change resolution there if I want>



[COLOR="SeaGreen"]Now I have a lesser problem.  When I boot into Ubuntu, I first get a message saying: "You passed and undefined mode number....  which I can get past by hitting the enter bar which scans then brings up the Ubuntu progress bar and splash.  Any ideas?[/COLOR]

---

### Post by bdk6m2007 on 2007-10-19
Sadly this didn't help.  :(  Looks like it's back to removing *quiet splash* from my boot lines and just not having the splash screen work.

I've had Ubuntu on this PC since edgy so it could definitely be a legacy issue.  Perhaps I'll setup a new partition and try installing from scratch again.......

---

### Post by Mikeoak on 2007-10-19
I had to fiddle with it several times before it worked.  First I set the Start-up Manager at my regular resolution and it did not work.  After rebooting, I set it at 640x480 + 16bits and then it worked just fine.  Good luck.

---

### Post by bdk6m2007 on 2007-10-19
OK well it turns out I'm not a good quitter.  I did what you suggested and just kept fiddling.  It's working for me with 640x480 at 8 bits/pixel.  The key here is vga=769 in my grub config file (menu.lst).

Despite my best googling I've never found anything that explains the mapping of the vga kernel option to resolutions/color depths/etc.  Maybe I'll download the source to startup manager and have a look there.

Thanks for all the comments folks.  This is a problem that's plagued me for a very long time and I'm glad to see it gone!

---

### Post by bdk6m2007 on 2007-10-19
Guess I should have tried a little harder with the search.  An explanation of the vga kernel option is at [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by Mikeoak on 2007-10-20
Glad to hear it.  It pays to hang in there and keep trying.  I know those small issues can drive you crazy.  I was hoping that the VGA nos would help me eliminate my warning that I get on boot up ("You have passed an undefined mode no...." , but so far all the ones I tried don't work.  It is minor compared to other probs. so for now I will just ignore it.:)

---

### Post by Tokke on 2007-10-26
I had the same problem on my HP Pavilion DV5157eu portable. 
I installed startup manager and changed the resolution to 800x600 (1024x768 also works)
Problem solved and my pc boots much faster now.

Thx all for the replies in this topic.

---

### Post by bdk6m2007 on 2007-10-29
Hey Folks-

Just as an FYI, and I'll preface this with "I'm not sure why this works", but I blew away my entire Linux partition over the weekend and re-installed from scratch.  The solution of only setting the [FONT=Courier New]vga[/FONT] kernel parameter was **not** sufficient to get the splash screen working.  I thought I would try this to see if I really understood the problem or not.  So I'm not 100% sure that I do.

So what I did was install [FONT=Tahoma]startup-manager[/FONT].  I  opened it up and it correctly indicated 640x480 since I set [FONT=Courier New]vga=769[/FONT] as my kernel parameters.  When I exited from startup-manager I got the "updating" dialog screen.  When I rebooted it works as expected showing the splash screen (albeit at the hideously low resolution of 640x480 but hey, at this point I'll take what I can get :) ).

So the bottom line is that just setting the [FONT=Courier New]vga[/FONT] kernel parameter is not sufficient to solve this problem, installing startup-manager is definitely required.  I'm not sure what it's doing, but it must set some configuration file other than just grub's menu.lst.

Hope this is helpful to other folks!

---

### Post by floke on 2007-10-29
See the fix from Sirwitti in this thread....

[http://ubuntuforums.org/showthread.php?t=573906](http://ubuntuforums.org/showthread.php?t=573906)

---

### Post by Mikeoak on 2007-10-29
Thanks Floke,

Following the suggestions, I was able to increase my splash resolution from 640x480 to 1024x786.  However, I lost my shut down splash... just goes blank.  My preference is to use 640 x480 in  /ect/splash.conf  so I can have splash on boot up and shut down.

Michael:)

---

### Post by tashmooclam on 2007-11-03
I selected 1042x768 in the Startup Manager, because this is my actual screen resolution.
Now it all works fine, looks good and starts up in 30seconds. Shut down also shows the ubuntu screen. 
I was not aware that 786 was a real screen resolution. 
For what it's worth.

---

