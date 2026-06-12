---
title: "3D screen savers worked for me in Dapper, but don't work in Feisty. IBM ThinkPad T23"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2007-05-27
Hi all,

Anyone have any idea why all of the 3D screen savers (like molecule and GL Matrix) would work fine on my ThinkPad while running Dapper, but won't work in Feisty? The curious thing is that I'm dual-booting Dapper and Feisty and they *_still_* work in Dapper, but in Feisty they hang the system and make everything jerky, etc. No crashes yet, but not much love from the 3D stuff.

Any suggestions appreciated.

KC

---

### Post by spartan777 on 2007-05-27
did you install 3d drivers, or are you using intel graphics?

---

### Post by Carbonfish on 2007-05-27
Hi Spartan777,

Sorry it took me a while to get back here, but I had to get some sleep. 

I am using whatever is the out of the box, default graphics settings after a fresh Feisty install. I will look at the wikis and these forums for 3D drivers. Where would I look in my hardware settings to find out what I am running now? Or maybe a better question would be, how do I get there via command line? Also, I don't recall downloading 3D drivers for Dapper, but the 3D graphics work fine. Must be a Feisty thing eh?

Thanks, and also to anyone else who takes the time to respond.

KC

---

### Post by spartan777 on 2007-05-27
well, you can go to to System -> Preferences -> Hardware Information. 

[IMG]http://farm1.static.flickr.com/226/516582630_fb3341597e_o.png[/IMG]

that's my video card, an NVIDIA card, 6800 GT.

If you have Intel integrated graphics, I don't think you need to install anything, but I'm not really sure. I wish I had more experience with laptops. :(

---

### Post by Carbonfish on 2007-05-27
Bump.  I don't know if it will help resolve my issue, but  my video card shows up in lspci as 

VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05).

Thanks for helping...

KC

---

### Post by Carbonfish on 2007-05-27
Thanks spartan777,

I made my bump before I saw your reply. I think I found the video card, but am not able to find any information about whether of not I need to download any card-specific drivers to allow 3D to work in Feisty.

KC

---

### Post by Carbonfish on 2007-05-27
I guess that I'll bump this one last time before I figure that nobody has any suggestions regarding where I might start solving this screen saver problem.

Thanks to spartan777 for trying anyway... Anybody else with any ideas, I would appreciate the input.

KC

---

### Post by spartan777 on 2007-05-28
well, all I know is that the S3 savage is integrated graphics, so I don't really know why it won't work. sorry!

---

### Post by trippinnik on 2007-05-28
do you have acceleration enabled in you xorg.conf? I'd recommend taking a look at that and posting it here.  To get anything accelerated to work on my laptop (IBMx22) I had to edit /etc/X11/xorg.conf.

---

### Post by Carbonfish on 2007-05-28
Hi boys and / or girls,

Okay, here's a really bad photo (I still can't make a screenshot as I don't have a network connection for the Ubuntu box where I am right now) of the section of my /etc/X11/xorg.conf file that has to do with my video card. I don't see anything there that would lead me to believe that acceleration is off. 

If you can make out the text, what do you think? Oh yeah, sorry about the moire.

---

### Post by Talon2 on 2007-05-28
See this bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905)

You might want to add your own comments.  This bug is shown as a LOW priority.  I can't say that I agree.

---

### Post by Carbonfish on 2007-05-28
Hi Talon,

Man, you just saved me a ton of frustration. Thanks for pointing me to that bug. At least now I can either try to patch it, or I can wait until the devs get their ***priorities*** straight (get it?) Ha, hahahahahahahah!

Thanks again,

KC

---

### Post by Carbonfish on 2007-05-30
Just a follow-up to let anyone who cares know, that this issue is resolved. Thanks to Talon2 pointing me to the bug report over at Launchpad, I was able to apply a patch and get direct rendering working. I am indebted to Talon2 for pointing me in the right direction, and to the great folks over at Launchpad for making a script that got me over the rough spots that I didn't know how to deal with.

KC

---

### Post by tyrewt on 2007-05-30
Which "patch" did you use?    I've tried every fix suggested there and still have no direct rendering. Same laptop, same Ubuntu version.

---

### Post by Carbonfish on 2007-05-30
I used Tormod's easy installer. One caveat though, when you run the script the installer will ask you if you want to download the latest "git" packages/modules, the first time I ran the script I said yes and it failed to rebuild the modules. I suggest that you use the git package that Tormod supplied. Otherwise, the process was very straightforward.

KC

---

### Post by trippinnik on 2007-06-02
Sorry, I really can't read that.  but here's a link to the howto I used: [http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746) it's for a different type of card, but you may find it useful.

---

### Post by Carbonfish on 2007-06-03
*trippinnik said:  	"Sorry, I really can't read that. but here's a link to the howto I used: [http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746) it's for a different type of card, but you may find it useful."*


???     Okay, I'll bite... Can't read what?

---

### Post by Carbonfish on 2007-06-03
Oh wait! I just got it trippinnik. You were still back on the other page talking about my crappy screen shot. Thanks for trying again, but never mind dude. I got it handled over at LaunchPad. I really appreciate your willingness to help though.

KC

---

### Post by ageilers on 2007-06-04
I found this fix in another [[COLOR="DarkOrange"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2777327#post2777327").
 It worked great for me! IBM T-23 Supersavage running Kubuntu Feisty.

>  Re: HOWTO: Enable DRI (3D support) on SAVAGE cards
Keith.Burgoyne,

I followed these instructions:

Download this attachment: [http://librarian.launchpad.net/7385659/drm.tar.bz2](http://librarian.launchpad.net/7385659/drm.tar.bz2)

tar xjvf drm.tar.bz2
cd drm/linux-core/
make DRM_MODULES="savage"
sudo mv /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/savage.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/savage.ko.old
sudo mv /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/drm.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/drm.ko.old
sudo cp savage.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/savage.ko
sudo cp drm.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/drm.ko
sudo depmod -a

After rebooting, "glxinfo | grep direct" reports "direct rendering: Yes".


from here:
[https://bugs.launchpad.net/ubuntu/+s....20/+bug/88905](https://bugs.launchpad.net/ubuntu/+s....20/+bug/88905)

and they really helped me...I hope it helps you too

Thanks to compartist for this fix. I changed the kernel from 2.6.20-15 to 16 so you may want to adjust as necesssary for your kernel version.

[COLOR="Red"]Update:[/COLOR] I see Talon2 had a link to the bug report with the fix as well.

---

