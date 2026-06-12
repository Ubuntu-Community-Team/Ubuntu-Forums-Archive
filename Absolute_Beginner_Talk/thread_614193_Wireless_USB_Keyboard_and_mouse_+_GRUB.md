---
title: "Wireless USB Keyboard and mouse + GRUB"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by eldara5 on 2007-11-15
I have a wireless keyboard and mouse, and they work fine with ubntu but it doesnt get power until after the OS boots same as windows, but because there is no power i cannt switch between Windows and Ubuntu at the start it keeps couting down and going to ubuntu. I need windows for gaming and i like ubuntu so id hate to delete it. Anyway to change the order So it boots into windows first and change it back so can boot into ubuntu (so i choose before restarting what OS to have) or a way to have my computer power everything from the second its switched on?

Thanks in advance,
Eldara

---

### Post by spiderbatdad on 2007-11-15
You can edit the grub list so that windows boots first. I once had a thread answered that explained how to edit the appropriate file, and it was rather easy to do. As far as selecting which os to boot before a restart...seems would require a small program to run before restart to edit the file each time.
If your mouse and keyboard are listed in System->Preferences->Sessions->Current Session, you might be able to edit the order to start sooner, but I doubt it would start before the os boots.

---

### Post by eldara5 on 2007-11-15
But could i edit the Grub list from both OS

---

### Post by spiderbatdad on 2007-11-15
no. Grub boot loader is a linux program

---

### Post by spiderbatdad on 2007-11-15
ok think I found the file. It's boot/grub/menu.lst  After all the commented lines you'll get into the boot order. You should see windows in the order. If you move it to the top it will boot by default.

 title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1

It should look something like that. In gedit you can just cut and paste then save the section you need. It will be after commented lines ## ## End Default Options ## ##
Hope this helps. Sorry for the newbie support.

---

### Post by meierfra on 2007-11-15
> But could i edit the Grub list from both OS

Yes . [fs-driver ]("http://www.fs-driver.org/") lets you edit Linux files from Windows.

---

### Post by meierfra on 2007-11-15
You can also just change the line

"default 0" 

in menu.lst.

Count the number of titles in menu.lst before  "windows". Put that number in place of "0".  
So for example if windows is the fourth title, change 

"default 0" to "default 3"

---

### Post by spiderbatdad on 2007-11-15
so you could write two little bash scripts to edit the file for you and even make launchers to click on to pre-select the os to boot after restart. That's too cool. I almost wish I still had a windows partition just to try it out on......well. not really, but it seems like a fun project.

---

### Post by eldara5 on 2007-11-16
Ye but when im in windows how to switch back to ubuntu?

---

### Post by meierfra on 2007-11-16
> Ye but when im in windows how to switch back to ubuntu?

As I said in post #6: get fs-driver . That lets  you edit /boot/grub/menu.lst from Windows. Change "default x" back to "default 0"

Did you search the forum  for other solutions of your "keyboard problem"?  I have seen various posts on the keyboard problems. But I didn't pay much attention to them, so I don't know whether there is a better solution.

---

