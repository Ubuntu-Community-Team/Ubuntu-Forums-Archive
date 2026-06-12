---
title: "move firefox setup to another ubuntu-installation"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-08-31
I'm playing with Ubuntu v7.04 on both my PC and my laptop. I have a wery fresh install on my PC and i would like to copy as many features i have made on my laptop to my PC. 

First of all, I'm thinking about Firefox-setup. Is it possible to copy everything of firefox to my PC - setup, bookmarks, etc. ?

---

### Post by southernman on 2007-08-31
I think all you should need to do is copy/move the .mozilla folder from your home directory.

The . (dot) in front means it's a hidden folder, just in case you were not sure.

edited - the machine your moving to, rename the .mozilla folder to .backup.mozilla - so if it doesn't work you can replace it.

---

### Post by Thorun on 2007-08-31
That's what i thought too...

Now, i have copy'd the .mozilla folder to my PC, but all i get is an error message:
> Firefox is already runining, but is not responding. To open a ndw window, you must first close the existing Firefox process, or restart your system.
I have restarted, and looked into the running-processes-folder but there is no firefox-process running :(

fortunately i made a backup before starting to play with this stuff....

in the .mozilla folder there is two folders. One is called firefox. another is called cxhzm(whatever).default. 
On my to different computers, the cxhzm(whatever).default name is not the same. 
My logical sense tells me, that it should work by copying the .mozilla..... but.... but but....?!:confused:

---

### Post by aysiu on 2007-08-31
Those are two separate issues.

Copying /home/*firstuser*/.mozilla to /home/*seconduser*/.mozilla and then making sure the second user has ownership of the newly copied folder should do it: ```
sudo chown -R seconduser:seconduser /home/seconduser
``` Firefox already running is something else entirely. Press Alt-F2 and type ```
killall firefox-bin
``` Then try to launch Firefox again.

---

### Post by s26c.sayan on 2007-08-31
IIRC, there is a nice back-up extension for firefox called FEBE.

EDIT: [https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

### Post by Thorun on 2007-08-31
Yaaaayyy :D

Now it works like a charm. 
I just forgot the ```
chown -R seconduser:seconduser
``` All the folders was root:root because I used sudo all the way. 
Which i find odd. Every time i use sudo cp to copy stuff, the owner becomes root:root and allways has to be changed afterwords...

I'll try out the FEBE in a sec. 


Thank you wery much for the quick replys. That's the reason I'm progressing very fast with my new Ubuntu OS. :)

---

### Post by aysiu on 2007-08-31
*sudo* temporarily invokes root privileges, so if you copy with ```
sudo cp
``` the resulting files or folders will be owned by root.

---

### Post by Thorun on 2007-08-31
If you're stlil reading this thread - is it someway possible to export your home-dir/GUI-setup from computer 1 to computer 2 too? just like the firefox-settings.??

---

### Post by s26c.sayan on 2007-08-31
> **Thorun said:**
> If you're stlil reading this thread - is it someway possible to export your home-dir/GUI-setup from computer 1 to computer 2 too? just like the firefox-settings.??

Maybe this will interest you......
[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)

---

### Post by Thorun on 2007-08-31
Well. I'm wery impressed with the backup-posibilities in Ubuntu / Linux.

I've used Norton Ghost 2003 for a long period with my win98 -> Xp installations. But that program is not yet suited for ext3-fs. And it's not free!

Now, when I'm dualbooting - I can backup both my WinXP and my Linux with the perfect tool: 
partimage - one at the time. I don't like re-installs from scratch so I uses systembackups wery much. 

And now this tool - which backups my homedir AND my settings. And even with possibility to export it to another computer with different hardware. (try to use a Norton Ghost image from computer1 with computer2 with different hardware....... *sigh* - not good). 
Well - havent tried it out yet, but most likely i will soon.

Thank you for the link. :D

---

