---
title: "[SOLVED] Restore Nautilus to former glory"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-19
Following a tip at LifeHackers, I modified two files used by Nautilus. That allowed a very nice PCMan File Manager to operate in the place of Nautilus. [http://lifehacker.com/software/linux-tip/change-gnome-menus-to-use-pcman-file-manager-288616.php](http://lifehacker.com/software/linux-tip/change-gnome-menus-to-use-pcman-file-manager-288616.php)

Unfortuneately, PCMan doesn't have a way to mount / unmount the optical drives.

I modified these 2 files:

/usr/share/applications/nautilus-computer.desktop

/usr/share/applications/nautilus-home.desktop

with these two lines respectively:

For Computer: Exec=pcmanfm / or Exec=gksudo pcmanfm / (for superuser browsing)

For Home: Exec=pcmanfm

Somebody using Feisty Fawn, ver. 7.04 and running Gnome and Nautilus, please copy those two lines from your file system in response to my post here, so that I might repair my File Manager. 

Yes, I know I should have backed up those files, or copied the original lines and commented them *in situ*. Yet, nowhere in the PCMan article does it mention a word about doing something as drastic as removing the device icons.

---

### Post by dinostabOMG on 2007-08-19
I'm a noob, but if you give me the step-by-step I'll help you out.

---

### Post by markusf21 on 2007-08-19
computer Exec=nautilus --no-desktop computer:
home Exec=nautilus --no-desktop
I hope that helps

also u can use snaptic to reinstall nautilus

---

