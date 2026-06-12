---
title: "Complete Linux Newb having resolution problems"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by EWatford on 2007-10-14
Hello all,

I am extremely, extremely new to Linux.

I actually work as a computer tech but all my knowlege is in relation to windows.

I loaded up ubuntu because I really want it to be a learning experience, and I'd like a chance at doing something a little different.

My current setup is a machine I built:

Socket 478 ASUS P-4s800 mb
2.8ghz P4
1.5gb RAM
Nvidia 6800 gt

19" Westinghouse LCD Widescreen (native 1440x900)

I got the drivers for linux off of nvidia's website and got them installed.

I even found out how to download the xserver-xorg client.

Here is where the breakdown occurs:


Im completely lost as to how I actually set my resolution.

I've tried searching forums, using information on these forums, and Im just completely lost.


If anyone wouldnt mind giving me a little help that would be very, very amazing.


Thanks

---

### Post by Pumalite on 2007-10-14
System>Preferences>Screen Resolution

---

### Post by EWatford on 2007-10-14
well sure I found that, but it doesnt have a 1440x900 resolution listed. 

In fact, it doesnt have any widescreen formats listed.

---

### Post by Pumalite on 2007-10-14
Check and see what driver you have installed. Make sure is 'used'.
Widescreen:

[http://www.codeodor.com/index.cfm/2007/3/16/Ubuntu-and-Widescreen-Resolution-Fixed/1035](http://www.codeodor.com/index.cfm/2007/3/16/Ubuntu-and-Widescreen-Resolution-Fixed/1035)

[http://ubuntuforums.org/showthread.php?t=280683&page=3](http://ubuntuforums.org/showthread.php?t=280683&page=3)

[https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/63551](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/63551)

---

### Post by EWatford on 2007-10-14
I checked those resources.

It really comes down to the fact that I do not understand how to code all of what I'm looking at.

I don't know if something is missing.

I tried copy/pasting the text from the generic template found here:

[http://ubuntuforums.org/showthread.php?t=280683&page=3](http://ubuntuforums.org/showthread.php?t=280683&page=3)


I couldn't get it to work.

Also, is there a reason that my graphics driver would become uninstalled?

---

### Post by skompier on 2007-10-14
I have the same monitor and the ONLY way I was able to get it to work was by installing 7.10RC. It was set up automatically. I added the info to xorg.conf manually and was able to select 1440x900, but the display was all weird looking.

---

### Post by EWatford on 2007-10-14
So the monitor could be incompatible?

Maybe I am oblivious but how could that happen?

---

### Post by Baka no Kami on 2007-10-14
> **skompier said:**
> I have the same monitor and the ONLY way I was able to get it to work was by installing 7.10RC. It was set up automatically. I added the info to xorg.conf manually and was able to select 1440x900, but the display was all weird looking.


Not being in front of Ubuntu right now I can only guess, but you may want to recheck some of the setting in the monitor section of you xorg.conf.  Specifically check HorizSync and VertRefresh (I think those are the options) and make sure they list the same ranges from the tech specs on the monitor. If X is trying to draw the desktop with a hori or vert setting that's outside the range the monitor can do then it would look distorted when the monitor tried to fit it on the screen.

---

### Post by skompier on 2007-10-14
> **EWatford said:**
> So the monitor could be incompatible?

Maybe I am oblivious but how could that happen?

No..that monitor is fine. I tried getting widescreen in 7.04 and tried ALL of the forum suggestions. No joy. I used 1280x1024 and it was fine. When I installed 7.10, I had 1440x900 in the Preferences>Screen Resolution drop down and I had to do nothing. It just worked.

---

### Post by alienexplorers on 2007-10-14
If you are running a nvidia card, you could run
> gksudo nvidia-settings
which is the nvidia setup tool.

---

### Post by EWatford on 2007-10-14
Ok, so I ran the setup utility, and I told it to Force Full GPU Scaling, and tried to set 1440x900.

It still says on frontend is 1152x864.

I'm really not wanting to install another OS after just doing this one.

I'm willing to do the work learning to code it if I have to, I'd just rather not reinstall the OS.


Thanks for the help so far guys

---

### Post by ryanryan on 2007-10-14
I had a very similar problem when I recently installed ubuntu for the first time.  You need to edit your xorg.conf file.  I followed the advice given to me at the following link and it solved my problem.  Read the following thread for directions.  [http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html](http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html)
When you get to the part where you add more resolutions, just make sure it's a resolution that your display is capable of.  

- Ryan

---

### Post by Faud on 2007-10-14
> **alienexplorers said:**
> If you are running a nvidia card, you could run

which is the nvidia setup tool.

Check this first, on my set up it didnt show all of the resoulitions at first but they were in the nvidia settings manager.
Then manually edit your xorg file, adding in the resoulition that you want. Make sure that the resoulition that you want is frist on the list like

1200x1024  1024x768  800x600
Where as I want 1200x1024 as my resoulition. Then save it (after making a backup first, ofcourse:)) and then log out and restart X.

Good luck

---

