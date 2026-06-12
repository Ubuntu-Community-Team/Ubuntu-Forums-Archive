---
title: "Sound file when Linux boots up: customization"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by kb5lnx on 2008-01-13
Hope you might help with this important customization, needed in quiet places?
:guitar:
I installed Pendrivelinux on a USB flashdrive, I really do not like the sound file it plays when Linux boots up.  Besides this, there are many circonstances where one might want a silent boot, while keeping the possibility of other sounds at will/when needed. Although I mentioned a distro other than Ubuntu, please answer, using Ubuntu as an example, if necessary.  I  use Gnome desktop.

I do need sound on my laptop to be on, otherwise, so it's only the boot up sound that is the problem. 
I need to :
1)-identify the file played during boot up (at to least, find out its directory, and the file extension; then I could test files until the solution is found)
2)- prevent it from being played when Linux boots up

:confused: Please tell me what that filename is, its location, and how to prevent it from being played?

---

### Post by dcstar on 2008-01-13
> **kb5lnx said:**
> Hope you might help with this important customization, needed in quiet places?
:guitar:
I installed Pendrivelinux on a USB flashdrive, I really do not like the sound file it plays when Linux boots up.  Besides this, there are many circonstances where one might want a silent boot, while keeping the possibility of other sounds at will/when needed. Although I mentioned a distro other than Ubuntu, please answer, using Ubuntu as an example, if necessary.  I  use Gnome desktop.
.......
:confused: Please tell me what that filename is, its location, and how to prevent it from being played?

System-Preferences-Sound, knock yourself out.......

---

### Post by kb5lnx on 2008-01-20
> **dcstar said:**
> System-Preferences-Sound, knock yourself out.......

:confused: Thanks but Been there done that prior, --  the menus did not offer a selection to stop the boot-up sound:  that's why I asked for info on the ACTUAL FILES involved, in the post starting this thread. 

It seems the quickest solution would be to delete the BOOT-UP SOUND FILE; alternatively if I could edit the CONFIG FILE that loads up the boot-up sound file,( that would  be great, as I need to delete the desktop background image file as well - aside).

To give you an idea of the menu problem in my distro, also,  I cannot save the changes;  for instance, I'm able to change the desktop image through the menus, as root, but the "finsih" and"close" buttons don't save, even though I loaded the distro as "persistent", not  running purely from RAM.  SO -- to repeat: I need to work with the files themselves (--specifically the sound files, for the subject of this post--), so I can get a saved, stable and reliable result.  I need an expert to help me find, and EDIT MANUALLY  (or delete) the actual files involved in the boot-up music..:guitar:

---

### Post by smurphy_it on 2008-01-20
I am an ubuntu user so I am unable to give you exact file names.  I can tell you that in the case of Ubuntu I have two startup sounds.  I have the sound file which plays when I get at the login window (change via System, administration, Login Window) and the 2nd sound happens when I login (System, Preferences, Sound).

Without viewing the setup in pendrivelinux I probably can't help much.

---

### Post by kb5lnx on 2008-01-20
while GUI and menus differ between distros, I expect the basic directory structure is based on the core Linux kernel and is shared by different distros? Thst's why I'm hoping an expert will come in and givce me those needed FILENAMES & PATHS (in Ubuntu, if not in Pendrivelinux: t hen I may be able to find the  CORRESPONDING ones in Pendrivelinux).

Btw, I installed that distro  because it is so easy to do on a USB flashdrive, and when it boots, it offers me the choice of running entirely from RAM, saving the USB flashdrive from rewrites -  in fact I can even simply pull  out the flashdrive and leave Linux apps running;  but I would like even better to be able to get that functionality from Ubuntu.  The version of Ubuntu I downloaded was so huge, that I can only see installing it on a desktop, not on a USB flashdrive, and certainly not running entirey from RAM... so that's an other thread for later, --for now I'm just trying to get rid of the problem music in Pendrivelinux, so I can boot my laptop with it "anywhere", --not just at home.

---

### Post by realillusions on 2008-01-20
/usr/share/sounds/log[in|out].wav

---

