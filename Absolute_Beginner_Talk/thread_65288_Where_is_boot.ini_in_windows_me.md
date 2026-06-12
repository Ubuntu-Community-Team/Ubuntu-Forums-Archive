---
title: "Where is boot.ini in windows me??"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by olymoore on 2005-09-13
Im looking for boot.ini in Windows ME so i can edit it to run the install of kubuntu from the guide ive been using it says it is in C:\ but its not on my computer :? Does anybody know where it is??

---

### Post by Juergen on 2005-09-13
Can't your system boot from CD?

Anyway, AFAIR the file is hidden and might have the 'system' flag set.
So, in an explorer window open the menu 'extras'/'folder options' and enable all options like 'show hidden/system files'

And it is read-only (again AFAIR), so you have to reset that flag (in the file's 'properties') prior to editing (and reset afterwards if you want, I don't think it's necessary to do so)

---

### Post by aysiu on 2005-09-13
[QUOTE=olymoore]Im looking for boot.ini in Windows ME so i can edit it to run the install of kubuntu from the guide ive been using it says it is in C:\ but its not on my computer :? Does anybody know where it is??[/QUOTE] It's a hidden file. Honestly, though, it's much easier to put Kubuntu in charge of the dual boot. When it asks if you want to install Grub to the MBR, just answer yes.

[Here's](http://i22.photobucket.com/albums/b337/psychocats/hiddenfiles.jpg) how to see hidden files in Windows. I took the shot in XP, but it should work for ME, too.

---

### Post by olymoore on 2005-09-13
[QUOTE=aysiu]It's a hidden file. Honestly, though, it's much easier to put Kubuntu in charge of the dual boot. When it asks if you want to install Grub to the MBR, just answer yes.

[Here's](http://i22.photobucket.com/albums/b337/psychocats/hiddenfiles.jpg) how to see hidden files in Windows. I took the shot in XP, but it should work for ME, too.[/QUOTE]
Yea i have all the hidden files settings deselected and the protected windows files but boot.ini is not in the C:\.  This is the guide i am using [http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948) is theboot.ini bit not needed?

---

### Post by aysiu on 2005-09-13
[QUOTE=olymoore]Yea i have all the hidden files settings deselected and the protected windows files but boot.ini is not in the C:\.  This is the guide i am using [http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948) is theboot.ini bit not needed?[/QUOTE] You want to install Ubuntu without burning a CD? I think that's a really bad idea for a beginner. You should download the ISO and burn a CD and install Ubuntu yourself the normal way.

If you have dial-up or have no internet connection at all (i.e., you can't download the image of Ubuntu), honestly, Ubuntu is probably not the distribution for you, anyway--it's only one CD, so it's heavily dependent on the internet for installing software packages and updates.

If you have broadband, start the ISO download right before you go to sleep. It'll be ready for you when you wake up.

---

### Post by olymoore on 2005-09-13
Ive got the iso im just trying to install it without using a burner because mine is down at the moment

---

### Post by aysiu on 2005-09-13
[QUOTE=olymoore]Ive got the iso im just trying to install it without using a burner because mine is down at the moment[/QUOTE] I'm not sure if you consider [this forum](http://66.102.7.104/search?q=cache:MNW52QKVYmgJ:forums.afterdawn.com/thread_view.cfm/80087+windows+me+boot.ini&hl=en&start=1&lr=lang_en) a credible source, but someone there seems quite sure Windows ME doesn't have a boot.ini file.

Don't you have a friend with a CD burner? Someone you know?

---

### Post by olymoore on 2005-09-13
Yea, ill do that thanks for your help anyway mate

---

