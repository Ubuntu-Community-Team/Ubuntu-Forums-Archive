---
title: "xorg update messes beryl"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by 5ER on 2007-04-04
I just updated my system with latest kubuntu updates. After restarting x, beryl won't run. Running "beryl-manager" or just "beryl" does the same - restart x. That's probably because updates included an xorg update.

---

### Post by freebird54 on 2007-04-04
I hope you have a backup copy of xorg.conf sitting there!  Most likely cause of changes.  I fyou do have it, just page through current and backup together and see what the changes are....  

Or - make a NEW backup  (xorg.conf.backup.new) and try starting with the old backup.

Wobbly windows withdrawal? - horrific!  :D

---

### Post by ziaziu on 2007-04-04
Hello!! I get a similar problem.
With me it's that not only X restarts, the whole system reboots - very annoying!  I pinpointed it to Beryl as expected.  When I run metacitiy as the window manager all is fine, but the second Beryl is selected the POOF!  Reboot!,

I'll give the xorg file swap a try and let you know!

---

### Post by 5ER on 2007-04-04
I tried backups, one had same problem, two were driverless but beryl-manager loaded, so I used one of driverless and installed drivers on.
EDIT: Now it works fine

---

### Post by freebird54 on 2007-04-04
I Love a happy ending!   Glad you it going again.  Burn those windows, spin that cube...

---

### Post by ziaziu on 2007-04-04
Pretty much the same solution for me :)
I just followed the instructions in the Unofficial ATI driver howto  ([here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")) and it all snapped into reality :D

---

### Post by KubuntuKilledMe on 2007-04-04
Hi, i too updated my installation and lost beryl. When beryl-manager starts, X restarts. I read some suggestions up about going back to old xorg.conf files but that totallty baffles me as my xorg.conf file was NOT changed and all the backups (which are more like different stages of configuration) give the exact same problem with X restart.

I looked in these forums and couldn't find more threads about this. Beryl forums have search disabled, and nothing says Linux-user-friendly like having your forum search disabled.

Anyway, i find myself with absolutelly no idea of what to do. I've tried create new xorg.conf with the nvidia util, but OF COURSE it gives the same problem as that was how i had generated my old xorg.conf anyway, with just a couple changed lines for beryl. 

If anyone can post any info regarding this problem, it would be greatly appreciated. Ubuntu is doing so much for linux, please, PLEASE dont **** it up. Recent updates have been a nightmare of sloppyness, with broken python-uno and blender.

---

### Post by freebird54 on 2007-04-04
If there are no changes in your xorg.conf, I'm afraid I don't what you should try next.  But I *DO* have an answer for the disabled search in the Beryl Forums.  If you google, you cn usua;;y find those same threads by the 'back door'

What video/driver are you using?  Are you XGL or AIGLX?

Happy to help if possible!

---

### Post by KubuntuKilledMe on 2007-04-04
Thank you for your help.

The rendering method was "nvidia direct" or something similar. It was an option not available to ATI users, if i remember well. I followed an howto in these ubuntuforums.

My setup is basically the nvidia-generated xorg.conf, with one added line:

    Option "AddARGBGLXVisuals" "True"

Then i just installed beryl from custom repos and it just worked.


The xorg update is too recent for google to have indexed the relevant discussions in the beryl forums, but thank you for the reminder.

---

### Post by freebird54 on 2007-04-04
None of mt ATI tricks are going to work then - but hopefully someone with similar hardware to yours will dive in here soon.  Beryl is something awfully easy to get used to!

---

### Post by astoltz on 2007-04-04
Had the same problem here. Running Edgy with the Nvidia drivers (9745) installed from Nvidia - not from the repos.  

A re-install of the drivers fixed the problem and I am back to normal.  But during the re-install, the script complained that /usr/lib/xorg/modules/extensions/libglx.so "was not a symbolic link".  Everything went OK after that so I check the file now and it is in fact a sym-link to the Nvidia version of that file: libglx.so.1.0.9755 in my case.

Bottom line is that I'm 95% sure that a re-install is not necessary, just fixing that sym-link would have solved it.

---

### Post by KubuntuKilledMe on 2007-04-04
Thank you for your input, i will try driver reinstalation after i try the symlink trick.

---

### Post by KubuntuKilledMe on 2007-04-04
astoltz' solution works for me! In my system, libglx.so was indeed a regular file, and not even the same size as libglx.so.1.0.9746.

I fixed my system with the following commands, without having to reinstall the nvidia drivers:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1.0.9746 libglx.so

Thanks to all that helped.

---

### Post by 5ER on 2007-04-04
> **freebird54 said:**
> Beryl is something awfully easy to get used to!
Heh, heh, true :D
And it's not as hard and problemantic as the sticky says. Just backup xorg.conf

---

### Post by freebird54 on 2007-04-05
The sticky has been there a long time - and I don't KNOW how many updates it has seen since then - but I must have installed a dozen or more (hooked up to svn repos)

Glad you found the problem.  It didn't seem to make a difference to things on ATI (for once ATI came out better!  YEAY!)

---

