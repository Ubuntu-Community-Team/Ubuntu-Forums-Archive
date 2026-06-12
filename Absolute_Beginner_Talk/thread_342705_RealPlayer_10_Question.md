---
title: "RealPlayer 10 Question"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Vanish00 on 2007-01-20
I'm using 6.10 Edgy.  I attempted to install realplayer 10 manually following a guide on here which I can't find now.  My situation is I have 4 files which I installed into my /lib/user.  I also have RealPlayer 10 icon in my Sound & Video group under Applications.  My problem is that when I click on that icon i get "Failed to execute child process "realplay" (No such file or directory)".  Now if I go to /lib/user I can execute realplayer.bin but no sound.  any help is appreciated, just learning like the rest :wink:

---

### Post by taurus on 2007-01-20
That, /lib/user, directory is the weirdest that I have never seen on a Linux system!  The reason you can't run it because /lib/user is not in your path.

Why not use this guide to install it.  Should work for Edgy, too.

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

---

### Post by Vanish00 on 2007-01-20
I installed the RealPlayer now in .../Desktop/RealPlayer but still get same error:

"Failed to execute child process "realplay" (No such file or directory)"  

RealPlayer will not launch from Applications -> Sound & Video.  I try to open it up from the folder but will not prompt the set-up assistance.  I try to play a vido but closes the whole program.  How do i fix my error?  Also how do I delete the old files I had in /user/lib, I keep getting I dont have permission even though I am the only user.  How can I trash them?

---

### Post by nu2this on 2007-01-20
Vanish00,
1st when i tried to get Realplayer 10 it did as yours is doing so I just scrapped it in favor of
Songbird , VLC, Totem, & mplayer do a better job anyhow.
If however you are insistent that you must have Realplayer (as I was when I started)you might want to try Automatix
its here:[http://www.getautomatix.com/](http://www.getautomatix.com/)
2nd to remove Realplayer completely try```
sudo aptitude remove purge realplayer
```
Then if you've installed Automatix & you're using the Gnome UI check Nautilus Scripts for install. What that will do is put a line in the context menu called Scripts. When you click that you'll have 3 choices choose root nautilus here. you'll be prompted for the Password do that anther window will overlay the window of the folder you opened, that one has root permissions **BE VERY CAREFUL!** If you didn't install Automatix & Nautilus Scripts you can also do gksudo nautilus
Now if all has gone well Realplayer is totally gone & then you can a clean install of  Reaplayer using Automatix. Plus anytime you want to remove root only folders you'll be able to do that too.

---

### Post by Vanish00 on 2007-01-20
Thanks for the info I just installed Automatix, but I want a clean install for Realplayer now.  I've tried installing realplayer 2 times in different locations.  I tried to drag them to trash or just press delete but I always get that i dont have permission.  What do i have to do?  I did try the purge code but nothing got removed.

---

### Post by nu2this on 2007-01-20
Well Alright y  then,now that you have Automatix installed open it up look under Miscellaneous
for Nautilus Scripts check it for install hit the start at the top of the Automatix box let that install.
Once Automatix is done close out of it, then Places>Home Folder.
1)click edit choose Preferences check Show hidden and backup files, close
2)double click File System, then go thru  to files you listed at the top of your post once there
3)right click the file you want to trash in the context menu you should see an item there Scripts click that then choose "root-nautilus-here" you will be prompted for the password enter it click OK then
4)another window will overlay this one has root permissions **be very careful!** you should now be able to trash those files.
Write back with the results okay:)

---

### Post by Vanish00 on 2007-01-20
Ah! that help a lot, thanks!  I got Realplayer working now only to find video is great and audio lacking.  My audio sounds as if I'm streaming with static in the background.  I might look into another video program that you mentioned before.  The main reason I sticking with realplayer because it has Real Video 4.0 codec and Real Audio G2(Cook), not sure if anything has that.

Dumped Realplayer, and everything happily works in Totem Player!

---

