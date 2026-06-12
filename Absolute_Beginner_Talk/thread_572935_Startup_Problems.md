---
title: "Startup Problems"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Starjun23 on 2007-10-11
Hey...im pretty new to Linux and Ubuntu so go easy on me.

Trying to modify my touchpad sensitivity I went against the warnings and edited xorg.conf. The system worked fine until I restarted. Then it refused to start the ubuntu shell. The blue screen came up and the diagnosis was a faulty xorg.conf file. So I followed typed in the command to reset xorg.conf (sudo dpkg-reconfigure....). After that the Ubuntu loads to the point where I enter my user name and password. Then there is a blank screen with the orange background, and I can move my mouse around. However it doesn't complete loading.

If anyone knows whats going on, please help me out.

THanks

---

### Post by Sef on 2007-10-11
Did you make a back up before you made the changes?

---

### Post by Starjun23 on 2007-10-11
A back-up of xorg.conf?  I didn't really change anything that existed, I added an 'inputdevice,' WHich didnt work.  WHen I used VI on the file, there were ! and other unpleasant signs after the lines I added.  WHen I sudo dpkg-ed it, these lines disappeared.  

The system now loads up to where I enter the user and password.  THen it makes the Ubuntu sound and proceeds as if everything is going as normal.  However, while I can move the cursor around on the background, no icons or start-bar show up.

---

### Post by Starjun23 on 2007-10-11
Yeah I know I should make backups...I'll be doing that from now on. Is there any way to do a complete sytem restore, like windows has? I have the CD, should I try loading from that. If it loads that way, how can I restore the hard-disk installation to its original settings. I have only been using ubuntu for 2 days, so not that many settings were changed, and only a few apps were installed.

---

### Post by brightscreamer on 2007-10-11
Wow...what a coincidence. I am having the same exact problem as you, Starjun! Except I think I made a backup copy while following instructions on a website. Any help would be very much appreciated!

---

### Post by mosiac on 2007-10-11
Yeah you can pop the cd in again and just have the install format the whole partition and reinstall, its just like you are installing all over again.

There should be a way to fix your xorg.conf file, but I myself have never really messed with it.

---

### Post by brightscreamer on 2007-10-11
I would really hate having to do that as it wouldn't teach me anything and it'd undo a lot of the work I've already done. How can I check to see if I made a backup and try to load it?

---

### Post by mosiac on 2007-10-11
Well if you think you made a backup do you know what you named it, hopefully something like xorgbk.conf or something relative, you can do a search for it by typing "locate whateverthenameofthebackupfileis" in a terminal and it should find it.

---

### Post by Starjun23 on 2007-10-11
I dunno....I think I fixed the xorg.conf file by dpkg-reconfiguring it, because before that the GUI wouldnt even load at all.  I think it must be some other problem.  These are the things I did after installing.

Installed various synaptics touchpad packages to try to get it to work(failed)
installed gvideo codecs,as some files werent playing
tried to compile a diff eq. plotting program written in c(failed)

Installed an Ubuntu sopported IDE

Can't think of anything else right now

---

### Post by Starjun23 on 2007-10-11
Does anyone know if its possible to access the linux file system through windows..?

---

### Post by brightscreamer on 2007-10-11
O.k., I located the backup! How do I run it/fix my issue now?

*Nevermind* I found a site that helped me load the backup! All set!

---

