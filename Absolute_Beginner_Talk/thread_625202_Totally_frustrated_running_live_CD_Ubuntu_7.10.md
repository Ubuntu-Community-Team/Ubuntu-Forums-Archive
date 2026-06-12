---
title: "Totally frustrated running live CD Ubuntu 7.10"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Dan4221 on 2007-11-27
OK..downloaded 7.10..did the checksum..burned the CD and did the CD integrity check. The CD boots to the menu. I've tried the Start or Install Option, the Start Ubuntu in Safe Graphics Mode, the F6 mode. The systems boots through the expanding bar and then dies. I've tried this on two separate PC's and had the same result. I actually have Open SuSe  10.2 installed on one of the PC's. I can run the live Ubuntu 6.10 CD on either PC. I can run PCLinuxOS, Damn Small Linux, Freespire 1.0, Mandriva 2007 and Knoppix live CD's on either PC. So what is the problem with Ubuntu 7.10?  I thought that it's popularity was because of ease of use.

It seems like this is a common problem for 7.10 from what I've read in the forums. I've tried to read the various posts about this problem. As far as I can tell, there is no single place to read all the different replies to this issue. But I am still clueless about how to solve the problem.

I have an MSI K8MM3 motherboard with on board video with an AMD Anthon processor and 512K RAM.

---

### Post by kelbizzle on 2007-11-27
When you say it "Dies" What does this mean...does it freeze....does the computer shutoff? Is it reporting an Error? Try Switching to a virtual console ( CTRL+ALT+F1) to see if it gives you an error at that point. 

Have your tried an older BETTER support version of ubuntu. Alot of users are switching to Gutsy which seems to be the latest and greatest. Unfortunately with that come BUGS and PROBLEMS that people have not fixed or even worked around. Two suggestions. You said you already looked around found people with the same problem...Did you happen to find a bug report about the issue? If not try reporting one...I've seen people get PRO troubleshooting steps straight from the developers. Only by posting a report about an issue that just required some expert troubleshooting. The Second suggestion is to Try Feisty or even Edgy. They are stable. Gusty isn't stable just because it the newest. It's out because they have a schedule to stick too. Not because every bug has been found and they're ready to blow MS off the map.

---

### Post by dhobbs on 2007-11-27
If everything runs fine until the end you may have a problem with your X server.  This can either be a bad resolution that your monitor/graphics card does not like or a bad driver setup.  You should boot up with the splash screen disabled and verbose on.  That should print out what is happening step by step.  I'm pretty sure the Linux kernel itself is loading fine, so you should have access to a command line to see what the problem is.

---

### Post by Joeb454 on 2007-11-27
> **Dan4221 said:**
> I have an MSI K8MM3 motherboard with on board video with an AMD Anthon processor and **512K RAM**.

Wow! I thought we had gone waaaaaaaaay past the days of 512k RAM, I have a whopping 2048Mb RAM, and this poor guy only has 512k...if I could donate RAM, I would:lolflag:

No seriously, try burning the CD again, all mien have worked so far which is good, but I have printed ones now :)

---

### Post by Dan4221 on 2007-11-28
> **kelbizzle said:**
> When you say it "Dies" What does this mean...does it freeze....does the computer shutoff? Is it reporting an Error? Try Switching to a virtual console ( CTRL+ALT+F1) to see if it gives you an error at that point. 

.

I thank each of you for your responses. I have switched to the virtual counsel. I've tried reconfiguring the video without success. I've reviewed the logs and still can't find the problem. I know that I could use an earlier version. But I'm trying to learn more about Linux. I can't understand why a live CD doesn't boot right up. I know that it is a problem with starting X. I just haven't been able to find the solution to the problem.

---

### Post by Threbus5 on 2007-11-29
If left to execute on its own does the system display a desktop that has an icon "install" or hang before that?

I downloaded and attempted to install from the Gutsy CD during its boot process and that failed. 

However, allowing the CD to boot through to the GUI screen that displayed the icon for "install" then selecting "install" worked.

---

### Post by Dan4221 on 2007-11-29
> **Threbus5 said:**
> If left to execute on its own does the system display a 
However, allowing the CD to boot through to the GUI screen that displayed the icon for "install" then selecting "install" worked.

I'm not quite sure what you are saying about booting to the GUI screen. It will boot until the system tries to start a window. But it cannot do so. I can use CTRL+ALT+ F1 or  F3 to boot into a terminal. I've gone through several different logs. There seems to be a problem lading corentils. There are error messages indicating that part of it is missing.

There is also a message showing a failure to start Gnome. I get a message that it is already running when I attempt to Startx from the terminal. I am using PCLinux live right now to enter this post. It boots right up and works great. 

I really would like to get the Ubuntu 7.10 going. But I seem to be at a dead end.

---

### Post by ramjet_1953 on 2007-11-29
Sometimes there are problems using the LiveCD because of video card driver issues.

Another way is to download the alternate CD. This uses a more traditional text installer, which gets the system up and running, allowing you to then load your video driver.

The alternate CD is still very intuitive, and you should have no problems understanding it, as it has prompts and clear selections.

When burning the iso it is a good idea to use a slow burning speed of around 4 X to ensure a good, error-free burn.

Regards,
Roger :cool:

---

### Post by Dan4221 on 2007-12-05
Well I'm still feeling frustrated. I just got the live CD in the mail. I was hoping that it would work. No such luck. It stops at the same point as the CD's I burned. I don't know why there would be a problem with the video drivers since 6.10 boots up fine off the CD. There is supposed to be a complete list of start up options on the live CD. But I haven't been able to find the either.

---

### Post by anakrich on 2007-12-05
The fix is simple. Burn your CD with VERY LOW WRITE SPEED. It should not die. This is step 1. I strongly suggest this step first.
If still it dies, try the noapic and nolapic option as posted in other threads. Optionally, if the kernel loads and you have no display with lights on the keyboard blinking, you have problems with graphics in which case you may have to pass vga=791 or 771 (am not sure about the number, look it up on the help from live cd special boot parameters).

---

