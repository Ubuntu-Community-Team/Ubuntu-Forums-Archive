---
title: "Step by step guide to get 8800gts running on ubuntu"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by notphilip on 2007-07-16
After reading several threads on this forum on how to make the 8800gts work with ubuntu without facing the black screen upon reboot, I am still left perplexed as to how I can make this work. I'm excited to be start using ubuntu and learning all the stuff about linux, but I am just clueless after several reformats and attempts to make this damn video card work. 

Can anyone please direct me in the direction to get it working (32 bit version of ubuntu)? This forum seems like it has a good, helpful community so I hope you all can help me out.

---

### Post by SubZeroGTS on 2007-07-16
Damn, I have a 8800GTS in my system and was about to mess around with Ubuntu, guess I should hold off on that?

---

### Post by NewJack on 2007-07-16
The search tab is a great tool.  :)

Try looking at this thread:  [http://ubuntuforums.org/showthread.php?t=496103&highlight=nvidia+8800gts](http://ubuntuforums.org/showthread.php?t=496103&highlight=nvidia+8800gts)

---

### Post by SubZeroGTS on 2007-07-16
I found this: 

[http://ubuntuforums.org/showthread.php?t=497264&highlight=8800GTS](http://ubuntuforums.org/showthread.php?t=497264&highlight=8800GTS)

Check the last post. Post in here if you get it to work. I guess I"ll have to figure out what all of that means before I attempt an install.

---

### Post by Ansible on 2007-07-16
I did ok with the 'envy' gadget.  I have a 8800gts card.  Here's a link:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

My story with this:  I installed ubuntu and then tried using the restricted nvidia driver installer that came with it - no dice.  X windows was toast after that.  Tried doing a manual install, didn't work for me.  Got irritated having to type in 80 character commands that didn't work for me, let the ubuntu install sit for a few weeks.  Finally got back around to playing with it, tried more terminal commands, gave up and reinstalled ubuntu completely.  First thing I ran was envy, it did fine.  I don't remember step-by-step how to install it, but I'm sure you can find out without much trouble. 

So the moral of the story is, after you install ubuntu, try getting your video card working first thing, don't bother with installing other stuff because you might want to dispose of it all to try again with a fresh install.  Envy and other methods probably work better with a fresh install I'm guessing.  

Once envy runs successfully, then there's this little issue: there is a ubuntu gadget under Preferences to set the screen resolution.  After the NVIDIA driver is installed, you might expect a new, complete list of resolutions to show up there - not so much.  Instead, look in the other menu where all the programs are (can't remember it, I'm on windows right now), and under Utilites I believe there is an nvidia control panel.  Change your resolution there.  It should work.  However, when you reboot it will revert to how it was before.

This is because you won't be able to save your changes (directly) that you make in the nvidia control panel.  It wants to save your changes to the xorg.conf file and make a backup, but that is write protected if you aren't sudo-ing.  I couldn't figure out how to run the nvidia thing as root, so instead I made a copy of xorg.conf and put it in my home directory.  Then I used the nvidia control panel to save on top of that file (it requires a file to be there), and then I did 'sudo nautilus' from the command line to enable me to copy the new xorg.conf file back to etc\x11 or whatever that directory is.  Be sure to back up the original file, of course.

So that's my experience - piece of cake, eh?  I'm very glad its working now though.

---

### Post by AlexenderReez on 2007-07-16
hm...give a try-->

> [http://forums.opencompositing.org/viewtopic.php?f=40&t=522](http://forums.opencompositing.org/viewtopic.php?f=40&t=522)

---

### Post by C.S.Cameron on 2007-07-16
This is how I got my 8800gts working:
Back up xorg.conf
Go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Read the instructions.
install envy and run
If you get a black screen try
sudo envy -t
Cork

---

### Post by notphilip on 2007-07-17
I've tried envy so many times as cameron suggested. Everytime is failure. 

I want to try that guide newjack posted, but its for 64 bit ubuntu and im using 32 bit. 

does anyone else remember how they did it?

---

### Post by NewJack on 2007-07-18
If you scroll down in that thread, I believe someone posted how they made changes for 32 bit.  Good Luck!

---

### Post by C.S.Cameron on 2007-07-18
Envy did not work for me at first either, got the black screen.
So I typed
sudo envy -t
This gave me several options.
I chose option 2, to remove Nvidia drivers.
The computer started churning away.
I went for a smoke.
When I returned, the Ubuntu login was waiting for me.
Mocha color had never looked so good.
Nvidia settings in apps, system tools made setting up duel monitors and resolution a snap.
Cork

---

