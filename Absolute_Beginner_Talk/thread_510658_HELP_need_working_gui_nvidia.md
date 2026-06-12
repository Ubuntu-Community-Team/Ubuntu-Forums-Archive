---
title: "HELP need working gui nvidia"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by paradoxchild on 2007-07-26
Pretty much no drivers are working correctly for me after I disabled restricted driver in restricted driver manager, I can no longer access gui no matter what I try. normal nv drivers (use dpkg-reconfigure -phigh xserver-xorg to change) gets the closest, but I can't actually see any of the gui. What happens is it ends up being a screen displaying one color, but the login screen comes up (known through noise it makes) I can login (blindly) and then I hear the noise that means I've logged in, but still can't see anything, if it try to go to another runlevel, the screen is all white and black crap everywhere, and I can't see what I'm typing at all. 

No one gave me a fix for it in previous post
[http://ubuntuforums.org/showthread.php?t=509607](http://ubuntuforums.org/showthread.php?t=509607)

---

### Post by scott_g on 2007-07-26
Can you try editing the xorg.conf file (pull up the recovery mode/text line interface, and type nano /etc/X11/xorg.conf), and try inserting nvidia as the driver in the device section.

Just an idea, not sure if it will work or not.

Do you still have the actual drivers installed?

Also, can you post the make of your video card?

Thanks/ Good Luck,
Scott

---

### Post by paradoxchild on 2007-07-26
I have an nvidia geforce 7600gt,
I have nvidia-glx-new installed right now, but as you can see from the other post I've tried the other drivers. I have tried using the 'nvidia' driver but it just gives me the no screens usable thing. (seen in other post). Using nv driver is closest to getting a working gui.

If there is someway of doing the gui equivalent of enabling restricted drivers after disabling them through gui. using fiesty, with 2.6-20-16 kernel
tried using the previous kernel; 2.6-20-15 but results were still the same.
I've tried nvidia-xconfig and nvidia-glx-config enable

I really don't know why it's not working, becuase I've installed updated drivers after kernel update, and stuff like that many times, and fixed xorg a lot. This is by far the most puzzling thing since no other posts give me anything that fixes it, even temporary.

---

### Post by scott_g on 2007-07-26
Hmm, tis quite the pickle.

Could you try booting the live CD, and comparing its xorg.conf file to the one you currently have?

Scott

---

### Post by paradoxchild on 2007-07-26
I've tried loading previous xorg.conf files that worked but it didn't help

---

### Post by paradoxchild on 2007-07-27
alright I've got it to where it boots up, but no gui is displayed at all, no input is sent to my monitor, but I hear the 'drums' and I can login and here the startup sound. I've tried using envy, didn't work, I've tired other option added to xorg which are supposed to fix that but nothing has worked.

So if you know how to fix it from displaying no gui at all but with nvidia-glx-new installed, please help

---

### Post by nitro_n2o on 2007-07-27
two things: 
1- did you play with your kernel lately (upgrade it, downgrade it, compiled yours ?? 
2- is the monitor connected right? the cable might be loose or something

---

### Post by spur on 2007-07-27
I know its a bit of a cop out, but I would save anything you want to keep and reinstall from scratch. It may save you a heap of time. These kind of things can be learnig experiences but for me at this point all I learn is better ways to pull my hair out so I cut my losses and run.

---

### Post by nitro_n2o on 2007-07-27
hmm...  try 
```
sudo restricted-manager -e nvidia-glx
```
I'm not sure about "nvidia-glx" but it should be the module name you are trying to enable

---

### Post by paradoxchild on 2007-07-27
i've reinstalled, and installed the kernel, used envy to uninstall stuff, etc. I will try the restricted-manager thing, and I just burned a feisty iso on a disc because I was about to save stuff I wanted and reinstall.

---

### Post by paradoxchild on 2007-07-27
tried it, you have to put nvidia not nvidia-glx or nvidia-glx-new, said module was already enabled, still no display comes up but it boots up.

Going to reinstall ubuntu, really weird that nobody, and no other post had a solution for this.

---

### Post by yorkie on 2007-07-27
sudo dpkg-reconfigure gdm

sudo  dpkg-reconfigure xserver-xorg
you could try these first

---

### Post by tomcheng76 on 2007-07-27
may be u can try vesa driver first instead of nv or nvidia

---

### Post by paradoxchild on 2007-07-28
so I ended up reinstalling ubuntu, fresh install of feisty, I installed some stuff I had in my old system, set up my panels, but in some settings. (beryl, compiz-fusion, dvd burning software, songbird, etc). I was using this just today and yesterday, it's been restarted mulitple times, and ctrl alt backspace even more to make sure everything is fine. So just now I go to boot in, no gui, drums are heard, try to use nv driver, restart gdm, a blank color and drums. I'll try out the dpkg-reconfigure gdm, and vesa drivers, the drivers I used where the ones right from restricted manager too, didn't install them manually. It's gotta be a recent update for feisty or something, the only thing I've added to xorg is the argb thing to get window decorations in beryl and compiz

---

### Post by paradoxchild on 2007-07-28
vesa drivers got my gui back up, but I much rather have nvidia-glx, so I'm gonna mess around with some stuff, thanks, I'll try reconfiguring gdm if any problems happen, I'll let you know how it turns out.

---

### Post by mgmiller on 2007-07-28
The 7600 gt should not use the nvidia-glx-new driver.  It should use the standard nvidia-glx one.  In order to use the new driver, you also have to install a kernel patch nvidia-new-kernel-source, and then reboot, or x won't start.  But as I said, your card doesn't use that driver, so don't even mess around with it.

---

### Post by paradoxchild on 2007-07-28
I've found the solution, which others have been unable to find, or just haven't got any help at all, I'll make a new post about it so everyone can use restricted drivers. 

I found the answer on feisty bug reports, all that has to be done is add this line to the Screen section in xorg

Option   "UseDisplayDevice"  "DFP"
restartx or gdm, and it works

---

### Post by michaelfitzi on 2007-07-28
Hello, I just installed 7.04 yesterday and I had similar problem. It seemed like the computer recognized that I had a monitor while it was booting, but as soon as it when to start Ubuntu it would go blank and my monitor light would flash. I searched around for awhile on the web and found a forum post that said it was the xorg file. I am VERY new to Linux so I tried it. The post had to do with dual video cards and it would switch over to the other when my screen went blank.  In order to see anything, I had to switch my cable to the 2nd card... If I wait to long, it says there is a problem with the graphics card and it will be disabled.  Anyway there was a value in the xorg file that was 4 or 5 and it represented the card. All I had to do was edit it to 5, I think... Sorry for being so useless, but this is my 1st Linux experience...

---

