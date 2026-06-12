---
title: "Auto have a terminal command run each boot before X starts.. how?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-02
I found out how to get my correct resolution to display on my laptop, but it involves running the command **sudo 915 resolution 50 1280 800** everytime my system boots up, and I also have to restart X after doing so with **ctrl alt backspace**. I was wondering how I could automate this process, so the terminal command could execute on it's own before X even starts, so I don't have to do either task.

Any ideas? :D

---

### Post by Marsolin on 2006-10-02
I haven't tried doing anything similar myself, but you could try adding a script to the /etc/init.d directory.

---

### Post by UnknownVariable on 2006-10-02
I've gotta be honest, I don't recognize that programming language. Do you know if it's some form of C?

---

### Post by bluenova on 2006-10-02
Why not just add the right resolution to /etc/X11/xorg.conf?

---

### Post by Marsolin on 2006-10-02
> **UnknownVariable said:**
> I've gotta be honest, I don't recognize that programming language. Do you know if it's some form of C?

The language in those files are just shell scripts. You would just create a text file and add these lines to it.

#! /bin/sh
915 resolution 50 1280 800

It would already execute as root so the sudo would be unnecessary.

---

### Post by UnknownVariable on 2006-10-02
> **bluenova said:**
> Why not just add the right resolution to /etc/X11/xorg.conf?
The correct resolutions are set in the xorg.conf, but since my video card seems to be only partially supported, or something like that, I have to use the 915resolution tool on every boot.


> **Marsolin said:**
> The language in those files are just shell scripts. You would just create a text file and add these lines to it.

#! /bin/sh
915 resolution 50 1280 800

It would already execute as root so the sudo would be unnecessary.
Do I need to add some kind of file extension to that..? It didn't quite work. I created a new document on the desktop, named it 915resolution_changes, and added the two lines to it. The icon changed from a new document icon to an icon with the little grey-ish tilted square. I couldn't copy directly to the init.d directly because I didn't have permission, so I used a sudo cp command in the Terminal to get it there, where the icon of the file changed to a document with a green GNOME print and a red box with an X in the top right hand corner. I rebooted my system then, yet I still had to execute the command manually.

---

### Post by Marsolin on 2006-10-02
I forgot to add that you need to change the permission of the file to make it executable.

---

### Post by christhemonkey on 2006-10-02
You also need to add it to the boot scripts.

/etc/init.d/ is just where the actual scripts are kept.
This does not make them run on boot.

To do that you need to update the sym links.
```
sudo update-rc.d script_name defaults 
```
Allthough that wont specifically execute it before X starts.
To do that, you need to know what number in the boot up process X is.
Then you just need to rename your newly created symlink to a lower number than the X startup. (will be called gdm i believe)

---

### Post by UnknownVariable on 2006-10-02
Argh, I hate when my cookie session expires on me in the middle of typing a post. Whole thing got lost. Anywho~

I came up with the bright idea that the runlevel has something to do with the boot sequence, so I used the command **runlevel** in the terminal, to find out I'm now in runlevel 2. I have my 915reso file in the init.d directly, chmod'd to 755, all ready to go. The sudo command you posted up there should be pretty self explanitory to go through (though I read the man pages just in case). I have two small problems left: a) how do I find the correct number in the boot process that X, or gdm, is? And b) how do I rename the symlink after finding out the answer to a?

Small hint please? :lol: Even though this stuff is fun to mess around with~

---

### Post by UnknownVariable on 2006-10-02
Small bump~

---

### Post by firebirdworks on 2006-10-02
Humm...Well it probably won't work but...
Heres an idea, push the interrup keys (Ctrl + Alt + Backspace)  And then Open the terminal by the keys.  Either Alt + 1 or something, I have forgoten recently.

If it works, let me know.  If it doesn't, then at lease we learned what didn't work.  ](*,)

---

### Post by MonsterDog on 2006-10-02
Hopefully it'll be big enough:

man update-rc.d

I can't check that for sure cuz i'm in Puppy right now.
Good Luck

---

### Post by UnknownVariable on 2006-10-02
firebirdworks: And what should I do with the terminal if it does come up?

MonsterDog: I did give that manual a read, a lot was confusing however.. I'll give it another read, and see if it can tell me anything about boot sequences :D

---

### Post by n0dl on 2006-10-02
You just have to edit the /etc/default/915resolution file under root access. (It says it in the README)

---

### Post by UnknownVariable on 2006-10-02
> **n0dl said:**
> You just have to edit the /etc/default/915resolution file under root access. (It says it in the README)
I downloaded the program from um... Lemme get the link...

[http://packages.ubuntu.com/dapper/x11/915resolution](http://packages.ubuntu.com/dapper/x11/915resolution)

There. More specifically, I downloaded from this URL:

[http://archive.ubuntu.com/ubuntu/pool/universe/9/915resolution/915resolution_0.5.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/universe/9/915resolution/915resolution_0.5.orig.tar.gz)

All it came with was the executable file, so far as I know. I took a quick double-check in /etc/default/, and I don't have any 915resolution file.

Do you suggest I download 915resolution from synaptic and retry getting my video stuff worked out through that package instead? :eek:

---

### Post by bodhi.zazen on 2006-10-02
I posted a how-to on this issue here:

[bodhi's How-to](http://ubuntuforums.org/showthread.php?t=269052)

I cover how to start this at boot. Give it a try and give feed back if you would so as to help me help others. 8-)

---

### Post by MonsterDog on 2006-10-02
Unknown, NOdl is probably right.  I just stole the file from another distro.  This is what I did the first time, though.

sudo update-rc.d *scriptname* start 50 S . stop 50 0 6 .

Your script has to be in init.d (I think).  defaults didn't run it soon enough.  The 50's are the order that the script is executed.  I chose 50 just as a guess, that starts and stops the service half way through the init scripts.  FYI- the stop part should be unnecessary, but I can't say that works because I didn't do it that way.

Let me know if apt gets you a better package and readme.

Good Luck

---

### Post by rccharles on 2006-10-02
> **UnknownVariable said:**
> Argh, I hate when my cookie session expires on me in the middle of typing a post. Whole thing got lost. Anywho~

I came up with the bright idea that the runlevel has something to do with the boot sequence, so I used the command **runlevel** in the terminal, to find out I'm now in runlevel 2. I have my 915reso file in the init.d directly, chmod'd to 755, all ready to go. The sudo command you posted up there should be pretty self explanitory to go through (though I read the man pages just in case). I have two small problems left: a) how do I find the correct number in the boot process that X, or gdm, is? And b) how do I rename the symlink after finding out the answer to a?

Small hint please? :lol: Even though this stuff is fun to mess around with~

You could try run level 1.

press:
 control-alt-f1 
gets you into a terminal session.

logon...



try:
sudo bash
init 1         # brings down X11
950resolution  # run your script
init 2         # brings up X11 etc...

This will do the change manually.  You would then added the script to run level 1.  Assuming things worked.  Sorry, I do not now how to add the script to run level 1.  Perhaps you could add it to the beginning of run level 2.  Maybe you need to add it to the end of runn level 1.

Robert

---

### Post by UnknownVariable on 2006-10-02
MonsterDog: I tried the terminal command you supplied (replacing scriptname with my actual file's name) and it didn't boot up in the right resolution, unfortunately, so I reverted the changes (I love the man pages). I'll try a few other things before I download a different version of 915resolution, as this one is working so far and I'd hate to mess it up. :lol:

n0dl: Same note here, if worse comes to worse I'll give the other version of 915resolution a go.

bodhi.zazen: I tried your method, and I'm leaving feedback in your thread now. :o (It didn't work for me, however.)

---

### Post by UnknownVariable on 2006-10-02
rccharles: I think I misunderstood... if I used that method, wouldn't I have to do it manually on every boot?

---

### Post by bodhi.zazen on 2006-10-02
> **UnknownVariable said:**
> bodhi.zazen: I tried your method, and I'm leaving feedback in your thread now. :o (It didn't work for me, however.)

Thank you. I will watch this thread for now. If you get a solution please post.

May I assume my method worked other then having to run 915resolution manually after a re-boot?

If so, it seems this command can be added to ~/.xinitrc.

Note: I have never installed this driver and watch with interest.

---

### Post by MonsterDog on 2006-10-02
Unknown,

I hope this isn't too obvious.  You did go check to see that the right resolution wasn't available under Preferences?  I don't think it will automatically boot in the right res until you actually change it.

---

### Post by UnknownVariable on 2006-10-02
bodhi.zazen: Your method did work (as in, the Terminal commands, such as symlinking the files), however after a reboot I still had to manually set my resolution, so nothing was accomplished in the end result. For reference, my graphics card is a Mobil 915GM/GMS/910GML Express Graphics Controller, from Intel.

MonsterDog: Without manually using **sudo 915resolution 50 1280 800**, the only resolution selections are 1024x768, 800x600, and 640x480. Once I run the command however, 640x480 disappears and on the top of the list 1280x800 is added. So in otherwords, I believe the correct response to your post would be that yes, the correct resolution is *not* available under preferences until I run the 915resolution command.

---

### Post by bodhi.zazen on 2006-10-02
Try running earlier, S20resolution ?

---

### Post by UnknownVariable on 2006-10-02
Using S20resolution instead of S90resolution had the same result -- I booted into my low res system. (In your thread you linked I also pointed out a few typos in the code part, or at least I think I did, lol)

---

### Post by bodhi.zazen on 2006-10-03
Thank you for your post, :) I will fix my how-to if I can edit the original post, otherwise ??

Thank you for re-booting. Is the desired resolution available as an option?

Also, if you get a final solution I intend to update my post. Of course, if you would like to, I will give you the opportunity, lord knows you have done most of the work. :lol:

---

### Post by UnknownVariable on 2006-10-03
Sorry, I was away for a while (and after this post, I need to head to bed... It's nearly 1am and I have to get up in the morning, lol :D ).

Upon rebooting, the only resolution available is 1024x768, which is what the monitor immediately displays in. From there, I run the command **sudo 915resolution 50 1280 800** and restart X using **ctrl alt backspace**, and I then have the choices of 1280x800 (desired) and 1024x768 (not desired). The monitor also immediately displays in 1280x800 after X is restarted. :)

Believe me when I say I don't intend to stop until I get a solution though :lol: I've got to head to bed for now, but I'll be back in the morning to check up on this thread (and a few others) and reply with any new findings. :D Thanks for the continued support.

---

### Post by MonsterDog on 2006-10-03
Unknown,

I figured it was borderline offensive to ask that.  I was wrong, anyway, because X does set it all by itslef.  If you still have to run 915resolution, then the script didn't run at all.  If it were just a timing issue you should only have to ctrl-alt-BK.

This is all I had to do to get my Inspiron 1300 with the 915 intel chipset to display 1280x800.  I guess I was kind of lucky.

I copied the 915resolution file to /usr/bin.

I created a script file called RightRes:

[INDENT]#! /bin/sh
/usr/bin/915resolution 38 1280 800
#  script to be put in /etc/init.d[/INDENT]

I ran the following command:

[INDENT]root@J:/# update-rc.d RightRes start 50 S .
 Adding system startup for /etc/init.d/RightRes ...
   /etc/rcS.d/S50RightRes -> ../init.d/RightRes[/INDENT]

After re-booting X started in the proper resolution by itself.

I didn't need to make or install.  I just extracted the file from the tarball.  I haven't even looked at the xorg files this time around.

I was re-installing everything today after a HD upgrade when I found this thread.  All I can say is this is what worked for me, but it really was so easy.  Maybe it's because this is a totally clean install.  I got the wireless working first but hadn't done anything else.

I hope you get it working.  It looks so much better when it's right.

---

### Post by MonsterDog on 2006-10-03
I know I probably should have just edited my last post, but it's been hours.

Unknown,  I know this probably won't make any difference, but why did you choose mode 50 to change?  I chose to change the 1280x1024 resolution because that one is beyond my screens capabilities.  640x480 isn't right but it is at least usable.  It's also neater because the resolutions are still listed in the proper order (can you say anal-retentive, I thought you could!).

An addition to my last post:

Everything seems to be working just fine after setting up ndiswrapper and 915resolution except for hibernation.  For some reason the script doesn't get run when we come back from hibernation, but that's ok because hibernation doesn't seem to work in linux on this thing and I'm plugged in all the time, anyway.  Suspend works fine.

I chose Ubuntu because it was the first distro I tried that didn't need any boot parameters like acpi=off.  The sound and synaptics touchpad worked OOTB.  Even the touchpad gestures worked.  The only problematic issues were the widescreen resolution and wireless.  The bcm43xx native driver + firmware cutter didn't work for me, but ndiswrapper did as long as I used the bcmwl5a.inf file.  The standard bcmwl5.inf + ndiswrapper worked for other distros but ubu needed the other one.  Considering how well everything else worked, I would have even settled for having to run 915resolution manually and restart X every time.

BTW: If you find yourself having to reboot often just to edit a file or two AND your box can boot from USB, consider using Puppy.  Getting the wireless to work there can be kind of fun, but it boots in less than 40 seconds from a 128M thumb drive on my Inspiron.  And since you're always root in puppy it makes for some quick and dirty admin.

Have fun.

---

### Post by UnknownVariable on 2006-10-04
MonsterDog: The first mode I edited was not mode 50. I forget the mode number, but it was for 1024x768 32bit. That was the resolution that it was defaulting to booting up in, I figured if I switched it over then my computer could automatically boot in 1280x800 32bit. Apparently that wasn't the case as it just shoved me into 800x600 32bit without any other options in my resolution selection. I then tried editing using the mode which contained 640x480 32bit as there's no way I was ever going to use that resolution on a 15.4" widescreen laptop, lol. After I had restarted X after changing that mode, it worked perfect, and my options in the resolution are 1024x768 and 1280x800.


Note to all: I have found a solution to this problem! Of course, this method only applies to the screen resolution, but it worked for me. The 915resolution tool I was using was **not** gained from Synaptic. Using this tool, I had to run the command on every boot and restart X as well. Last night, I ran the command as usual, but before turning off the laptop I simply installed the 915resolution tool from Synaptic. I did nothing else but install it. Upon a reboot, my resolution was displayed correctly automatically. I assume the new 915resolution tool seen the command I had run earlier on the other 915resolution tool and decided to make the autocommand, automatically! :mrgreen: I'm pleased, to say the least~

---

