---
title: "Broadcom....Again"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by tentel on 2008-02-04
Surprise, surprise.

My bcm43xx card is having lots o' problems.

Who'd of thunk it?



Tomorrow I'm going to invest a few hours trying to get everything working.

The problem is, last time I tried to install Ubuntu on this laptop, I couldn't even get a wired connection to work, which seriously crippled my efforts.
I have little hope of it miraculously working this time, so I'll be having to focus most of my research on ways to install the drivers using offline methods.



So it boils down to three question:

Should I be focusing my efforts more towards fwcutter, or ndiswrapper?  which one is more simple to use with no internet connection?

When I booted from the live cd, the only way I could get it to boot was to hit f6 and type "noapic nolapic".  I have no idea what I did though, or what that means.  is it possible that that could be the reason why my wired connection doesn't work?


I could always just buy a new card.
Any recommendations on a good card that isn't too expensive? (ie, as cheap as possible.)  I'm dual-booting with vista, so i'd like to make sure it stays compatible in that regards as well. 


Thanks
-Tim

---

### Post by anewguy on 2008-02-04
The 2 options you flagged are for power management type things and would not have affected your wireless.  Simply put, you need a driver.  Some have started using the restricted driver and the firmware cutter method with mixed results.  I have had to set up a bcm43xx series wireless card many times and have for me found that ndiswrapper is the most dependable and reliable.  The trick will be if you cannot get a wired connection to work.

You have 3 prerequisites:

(1) you must have ndiswrapper and its utilities installed (available via the normal Synaptic package manager - but check -> if you installed 7.10 you will need to enable the repositories via the software sources option of system/administration),

(2) you will need the windows (non-vista) drivers for your card, preferably copied onto your desktop.  These files will include .inf and .sys files.

(3) you must "blacklist" the existing "dummy" driver in Ubuntu.  To do this:

cd /etc/modprobe.d

sudo gedit blacklist

add the following to the end of that file:

# blacklist dummy bcm43xx driver
blacklist bcm43xx

then save the file and exit the editor.

Now:

cd ~/Desktop
sudo ndiswrapper -l  <- lower case "L" - be sure this returns nothing

sudo ndiswrapper -i  xxxxx.inf  <-lower case "I", where "xxxxx" is the name of your driver .inf   file 

sudo ndiswrapper -m

sudo depmod -a

sudo modprobe ndiswrapper

Now reboot your PC.  When it comes back up single left click on the network icon on the top tray and see if any networks are listed.


Please post back with any questions/problems.

Good luck!:)

---

### Post by tentel on 2008-02-05
Thank you very much for the prompt reply, and clear instructions.

Non-Vista drivers you say?


thats good to know.


that'll definatly be easier.


I'm not going to attempt the actual installation tonight, but i know i've seen xp drivers many times and left the page with a sigh because i thought i couldn't use them.


this motivates me much more.



I'll post my results tommorrow.


thanks again.

-Tim

---

### Post by tentel on 2008-02-06
Thanks!

it worked great.

well, it would have if i hadn't screwed up.
i forgot to have the .sys file on my desktop, so it didn't work properly, but then i finally figured out how to get ndisgtk to install, so i just uninstalled and reinstalled drivers properly from there.


can i move the .inf files and .sys files off my desktop now?
or will the file path be messed up?

---

### Post by anewguy on 2008-02-06
I believe once you've installed them with ndiswrapper (or it's front end gui like you used), you can delete the files.  I don't know where it stores them - just never looked - but I have always deleted mine after installation.  Glad things worked out for you!

If you could, please also mark this thread as "Solved" so that others have another resource to look at.

Dave:)

---

