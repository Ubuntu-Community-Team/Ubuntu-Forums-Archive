---
title: "making resolution changes stick, also booting OS 9 with yaboot"
date: 2004-11-17
forum: Apple PPC Users
---

### Post by Jim Z on 2004-11-17
Just got Ubuntu installed on my powermac (dual 800 QS) and it seems to work very well.  I have two issues that I can't quite figure out yet:

-  Resolution always comes up as 1280x1024.  I use the gnome menu to change it to 1280x960, but if X is restarted it's back to 1280x1024.  When I change the resolution I have the "Make this default" checked.
- when I installed, yaboot didn't pick up the OS 9 partition- I have OS X and OS 9 on the primary hard disk with separate partitions, and ubuntu takes the entire secondary disk.  I believe that OS X is /dev/hda10 and OS 9 is /dev/hda9.  I tried adding an entry to yaboot.conf (I'm not on the Mac now, I think it was "macos=/dev/hda9") but it didn't seem to take.

---

### Post by trash on 2004-11-17
After making your changes

hit control+alt+F2 (opens a new terminal)
login as root and enter ybin
then hit control+alt+F7 (brings you back to Ubuntu)

should do ya fine:)

---

### Post by sumanjay on 2004-11-17
About fixing the resolution - you could edit your XF86Config-4 file to make it permanent. The steps, if you need them, are-
1) Open a terminal by going Applications->System Tools->Terminal and type in the following command
```
sudo nano /etc/X11/XF86Config-4
```  Enter your user passowrd, of course.
2) Then move to the line which has the default depth value (by pressing **Ctrl+W** and entering **defaultdepth** in the search box.
3) This is the crucial step. Note which is your default depth and just move a few lines below, where a lot of the **SubSection "Display"** begin. Move to the SubSection which has the Depth setting at your DefaultDepth setting. Usually it is at 24, but it might be 8 for you. You need to change this as this is the setting that is being used everytime Ubuntu starts. The thing you need to change here is the **Mode** option -  add **"1280x960"** just after the Mode keyword so it will be used first. Note that it should be in quotes.
4) Press **Ctrl+X** to quit the editor program(nano), saving the file as you go.
5) Now restart X windows by logging out of Ubuntu and logging back on again or by pressing **Ctrl+Alt+Del**.

You should have the resolution set at 1280x960. HTH.

---

### Post by sumanjay on 2004-11-17
Trash's post will fix yaboot for you and mine should fix the resolution. When running ybin, you might wanna run it with the -v flag so you get some info on what's happening. 

```
ybin -v
```

---

### Post by trash on 2004-11-17
re: ybin -v


HAHAHAHAHA...

# ybin -v
ybin: Finding OpenFirmware device path to `/dev/hda9'...
ybin: Finding OpenFirmware device path to `/dev/hda10'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/hda9...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/hda9...
ybin: Installing /etc/yaboot.conf onto /dev/hda9...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...

ybin: Blessing /dev/hda9 with Holy Penguin Pee...

... gotta love that
 :twisted:

---

