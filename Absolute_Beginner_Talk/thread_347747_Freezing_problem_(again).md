---
title: "Freezing problem (again)"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Allen Clearwater on 2007-01-27
Well, for being advertised as being extremely user-friendly, and full of helpfulness, I find this forum severely lacking.  It's been almost three weeks since I asked for help, and the only response I got was on asking for more info.  I'm going to try this again, and I hope I get some help this time.  If not, I might be asking on instructions on how to uninstall Ubuntu. . .

I've got a newly installed v6.06 seemingly working distribution, but whenever something other than firefox tries to access the internet (updates, installer), the system locks up and won't respond to anything. Even firefox freezes periodically. I have a winXP system to fall back on for internet use if need be.  Also, any time I try to open any sort of Administrative program/Application, the system also freezes. I discovered this trying to edit GRUB to boot into windows automatically (tutorial)

My computer has the following specs:
1300 mhz processor
576 MB RAM
nVidea GeForce2 (64MB)
PPPoE internet (Thru Startech router) (MTS highspeed lite)
(if it matters) onboard C-Media sound card
LG DVD burner

---

### Post by JamieC on 2007-01-27
I have a few questions...
[list=1]
[*] What desktop environment are you using? Gnome, KDE?
[*] Are they hard lockups? Are you able to move the mouse? Have you tried restarting the X server (CTRL + ALT + BKSP)?
[*] How frequent are these freezes?
[/list]

---

### Post by Allen Clearwater on 2007-01-27
1: I have no idea.  I used the liveCD, and there was an installer on the desktop (is that the right term?)
2: Completely locked up.  Neither the mouse or keyboard responds.  Numlock won't even toggle.  Only way to fix the thing is to do a hard reset using a hardware reset button
3: They happen when I use firefox for more than ten minutes, and every time I launch a program that isn't a game

ps: Thanks for taking the time to help!  it's hard to find someone that'll actually talk to you if you have less than 50 forum posts :)

---

### Post by firstc624 on 2007-01-27
i just learned this today before a hard reset using th e power button us the following combination to see if the keyboard has actually died or not.

ctrl+sys rq+s,u,b  that will try to reboot w/o hard kill.   see if that works.  i have heard that it will run under most lockups that linux lets it run anyway.

Just a thought

---

### Post by davarino on 2007-01-27
I am sure this will show what a fool I can be sometimes, but are you sure that you are not running in Live CD mode?

In other words, you are not running Ubuntu with the Live CD in your drive, correct?

The next matter is often a trippingstone for newbies to Linux. Using the "sudo" program is not well documented in most Linux books, because many distributions don't use it. In Ubuntu, sudo is the lynchpin of logging in as a root user... without using sudo you can do doggone little. 

Open a terminal (try Applications > Accessories > Terminal) and type in "sudo synaptic". You will be prompted for a password, which is the same password that you use to log in after you enter your user id.

(If you have never used this method of "sudo log-in", you may have just found the solution to some of your problems. **sudo always requires the *user's individual password***. If you have two different user id's with different passwords, you will use one of two different passwords to sudo log-in, depending on which user you are logging in from.) **If sudo is new to you, this may be the only thing you will have to learn about at this juncture. You *may* be able to solve all your problems with what you have just learnt about sudo**.

Failing that...

First thing to check is what is your text editor... open another terminal and type in the word "gedit" (without quotes). You probably will get an editor to come up. If not, try "kedit". If you can **not** get an editor to come up, stop here and make some noise on the forum. (We don't want to be mucking around with a system settings without a dependable way of editing system files.)

If you get an editor, close it and continue.

Which nVidia driver are you using? (I have an nVidia card and I had a devil of a time getting it to run well once upon a time.) Probably you still have the Synaptic Package Manager open: look at the packages to see if either "nvidia-glx" or "nvidia-glx-legacy" is ticked (or "checked").

If neither is ticked, you are running the opensource "nv" driver... not such a good idea.

The fix? If you indeed are using a GeForce2 card, tick the "nvidia-glx-legacy" box. That is the older proprietary driver from nVidia. Newer cards such as nForce, FX series, 4 series and 6 series will use the non-legacy driver.

After that, go to the Apply box in the Synaptic menu and click it. Any dialogs that come up should be answered by you with "Yes". You will load a better driver this way. (You will also be removing the opensource "nv" driver.)

Next, you'll need to sudo open your text editor: "sudo gedit /etc/X11/xorg.conf". (Assuming that you are using the text editor "gedit".)

Look for a line that reads like:

Driver   "nv"

and change it to

Driver   "nvidia"

and then save the file and exit your text editor.

Now you shut down your X session by pressing Control-Alt-Backspace together.

The X windows system will reboot and you may well get to see an nVidia logo jump up for a few seconds.

This might be the whole problem. I hope so.

---

### Post by P235 on 2007-01-27
For future reference when faced with a hard freeze:

[http://ubuntuforums.org/showthread.php?t=315404]("http://ubuntuforums.org/showthread.php?t=315404")

Try not to hard boot - a.k.a. pulling the power - too often as this will likely mean some inodes will be misplaced and you will have to reboot your computer with the live cd to run fsck on your partitions to repair them.  It's not a serious process to check your hd for problems with fsck, but it is a hassle.  If you do end up rebooting your computer with alt-prt scr-r,s,e,i,u,b, I'd suggest you shutdown afterwards, then start it back up.  Computers remember all the traumatic things we users inflict upon them so it's best to let them have a shut eye and come back with a clean slate.

You can check out Ubuntu Linux Resources (a.k.a. Psychocats) to see a comparison of Gnome and KDE here:

[http://psychocats.net/ubuntu/kdegnome]("http://psychocats.net/ubuntu/kdegnome")

---

### Post by Allen Clearwater on 2007-01-28
Alright, I've established that I'm using GNOME, and launching "sudo synaptic" from the terminal seems to work, but being a Linux n00b, I have no idea what to do once I'm there.

Alright, I'm going to start at the beginning.  It all started after I installed Ubuntu to my tertiary hard drive. (primary master-> windows; primary slave-> NTFS storage; secondary master->Ubuntu; secondary slave-> DVD burner)  I'd booted it up for the first time, and it loaded flawlessly.  When I was sitting at the desktop, trying to decide where to begin, this thingy pops up and asks me to install updates.  I click where it tells me to, and a list comes up.  I go through it, and check the ones that I think should be installed, the click "Install".  Bam-shebam, and she's locked up tighter than Fort Knox.  None of the key combos that were listed here seemed to do anything.

And there was a question in there somewhere, but I lost it.:(   So instead, I pose this: WTF do I do with this "sudo synaptic" application?:confused:

---

### Post by davarino on 2007-01-30
Sorry to take so long getting back.

Sounds like you picked-and-chose like I have done at times: not exactly rightly. I have found through nasty experience that the best way to do updates is to accept ALL the updates suggested... one basic reason is that there can be one eentsy-weentsy one that you don't tick that might be the fulcrum to the entire package (a Windoze comparison: you delete a .dll because it doesn't seem like you need it). [As an aside, there are some "purists" who will advise you NOT to do automatic or unquestioningly-accepted updates... which is fine for anyone who truly eats, drinks, and breathes Linux. The rest of us, mere mortals that we are, should be willing to trust the updating programs to know a little more and to be more efficient than we.] 

Don't even worry about the Synaptic thing at this point... let's try to get your system updates settled. This will likely do it:

Boot up and go to your main menu (I'm assuming Ubuntu, not Kubuntu) and click on System > Update Manager. You will be prompted for a password; use your USER password that you logged in with. Click OK.

You'll get a growing-bar display and, if everything is working the way it ought to (big "if" sometimes) you'll get a very similar window to the one you had just before this all went to pot on you. There should be a tick-off list. This time, accept*** all*** of them (they *are* probably all pre-ticked) by clicking "Install Updates". If you did not get a list, click on "Check"... maybe you'll get it that way.

Let me know what happens. There is also a way to check the updating with Synaptic, but let's leave that alone for the present. And of course there's always the (unpleasant?) option of re-installing... which at least starts you off with a clean slate.

Good luck.

---

### Post by Allen Clearwater on 2007-01-30
Absolutely nothing new.  Same thing happened.  I left them all checked, and clicked install, then froze.

Maybe it's because I live in a freezing igloo in Canada </sarcasm>

---

### Post by davarino on 2007-01-31
Sorry to hear that.

One last try:

Open a terminal (Applications > Accessories > Terminal). Then run these two commands:

sudo apt-get upgrade
sudo apt-get dist-upgrade

Might do it. If not, I would (being who I am) start from square one and reinstall the whole durn thing. Good luck... I wish I knew more.

Well, at least you have an igloo to keep the cold out. We've been having an unusually cold winter here... about 20 nights so far below freezing and snow 10 days ago. Lasted until early afternoon. That's the way I like snow: once in 3 or 4 years until 2 p.m.

---

### Post by Allen Clearwater on 2007-01-31
<insert appropriate curse here> Well, this settles it.  The HD that housed Ubuntu just failed completely.  It started with a clicking, then a clunk, then nothing.  Comp refuses to acknowledge its existence.  Until I can raise funds for a replacement, my forays into the world of LINUX are over.

Does anyone know how to remove GRUB through windows xp?  My HD config is in a previous post.

---

### Post by jkeyes0 on 2007-01-31
To fix your MBR for XP, insert your windows XP cdrom, boot from it, and choose the repair using recovery console option. Once you're in the recovery console, run the command "fixmbr" (you have to confirm it). That should put it back to the Xp bootloader.

Also, aside from the fact that your hard drive was failing, part of the problem could have been due to running the drive off the same controller as your CD-Rom drive. the CD-rom drive causes the entire bus to run slower, and can cause problems with any hard drive (even in XP). I tried it at one point with my XP system, and I believe I ended up with a lot of hard reboots due to freezeups.

---

### Post by Allen Clearwater on 2007-01-31
Well, at least XP is working the way it should. . .
Thanks for all the help peoples!  I guess the not-answering fluke thingy was just that; a fluke!  I'll be looking for a new HD for awhile, so until it is found, so long!  Be excellent to eachother! :guitar:

---

