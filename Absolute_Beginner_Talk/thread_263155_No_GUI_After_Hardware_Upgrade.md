---
title: "No GUI After Hardware Upgrade"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by FOSman on 2006-09-22
Hello,

I installed Xubuntu a couple months ago on some old hardware (which I was really happy about since everything Just Worked, and it meant I didn't need to buy a new computer).  Ironically, the CPU and PSU both died recently (nice little smoke curls and all).  So I decided to get a new mobo, CPU, PSU, RAM, and GPU.  Nothing fancy.  I'd say it's all been out for at least a year, now.  Anyway, hooked everything up, POST fine, tweaked BIOS, reboot to OS, but then it gives me the error: "Failed to start X server".  xorg.conf shows the entry for the old graphics card, so that's obviously a problem, but I'm not sure what else I should be looking for.  So I have a few questions.

First, is that going to be the only device I need to worry about?  (It's a PCI-E Nvidia card while the old one was a AGP ATI card... if any of that makes a difference.)  The new CPU is an AMD 64 whereas the old one was an AMD Athlon.  I have 1G RAM now.  It was a measly 256M before.  I can't imagine the mobo causing any problems, but I'm still very new to Linux, so I'd like to make sure.

Second, what do I need to do to get the system to recognize the correct graphics card?  If any of the other hardware needs to be dealt with, what else do I need to do?

Third, would it be possible to reinstall over the existing installation such that it updates the existing installation with the correct config settings and (if necessary) installs the correct drivers?  If so, would it be easier or just make a mess of everything?  I don't want to lose any of the data on the HDD if I can help it.

Last, since I'm here, does anyone have advice on whether I should upgrade to the 64 bit kernel now (and what problems that might cause)?  I'm currently running the i386 kernel.  I like keeping system usage low, so I want to stick with Xubuntu over the others, but if I can take full advantage of the CPU, that would be nice.

If any of these questions are answered elsewhere, my apologies for not finding them myself, and I hope you'll be kind enough to point me in the right direction.

Thanks for your help!

---

### Post by FOSman on 2006-09-22
Solved it.  Just had to follow the [guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") for installing the latest nvidia drivers.  I'd tried a similar (though much shorter) suggestion from another thread that turned out not to work, so I didn't think the guide would, either.  Just goes to show what a little frustration will make you do.

However, one problem I had with the guide is that it calls for gedit or kate, neither of which is installed by default in Xubuntu (and kate is a GUI app, anyway; I think gedit is also), and since I didn't want to install a new editor just for one job, I went with vim instead, an editor I'm only barely familiar with, but more-so than emacs.  I would suggest that the guide be updated to take into account people who don't have access to the GUI, and walk us newbs through working with these editors so we don't have heart-attacks trying to use them (or maybe that should be a different guide; not like I'm the right person to be writing them).  Most GUI editors are pretty straight forward, so anyone who's used windows notepad should be right at home with them.  But for CLI editors, that's not the case, and we need help with that.

For the other vim newbs, here's a crash course.  Start vim like any other editor in the commandline (e.g. vim path/to/new/or/current/file).  When you're in the vim command interface (which is where you start), typing ":h" (without quotes) goes to the help menu.  ":w" saves any changes to the file.  ":q" quits (this also works to quit out of the help menu).  You have to hit the enter key after each command.  Typing "i" lets you make changes to the file, after which all the keys function like you'd expect.  While in edit mode, hit the Esc key when you're done making changes to go back to the command interface.

As for my questions on upgrading the kernel, I'll read through the "64-bit Processor Users" forum and decide from there.  To everyone who took the time to read, thanks.

---

