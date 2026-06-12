---
title: "need help: unmounting volume scripts"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by bungnati on 2007-10-21
Hi
I need some help here. I have 2 volumes I would like to have automatically unmount upon login. I need root permissions to unmount them so I just cant simply unmount them i have to go thru terminal. Can anyone tell me how to write a script or simple app to do this upon startup or even just double click an icon and have them unmount.
Any help would be greatly appreciated.

John

---

### Post by Mister.Vash on 2007-10-21
Do you use these volumes for anything under ubuntu? Are these volumes used for anything at all? Why would you like to unmount them?

The file /etc/fstab generally controls what gets mounted, it you do not need the volumes mounted at all, it might just be easier to edit that file so that they don't load at all. If that is what you choose to do, be very careful editing the /etc/fstab file as it can cause problems if done wrong. Plenty of threads and docs on modifying it are around, but feel free to ask if you have questions.

---

### Post by rahimveron on 2007-10-21
Hey Vash to unmount them can i comment(#) out the windows partition(sda1) line in  /etc/fstab?
And to mount it again i have to remove the comment, isnit it? Or i am really being naive.

---

### Post by Shazaam on 2007-10-21
You can use gconf-editor to remove them from your desktop too.

---

### Post by Mister.Vash on 2007-10-21
Yes, you can comment them out.  Before modifying the file, the first thing to do is make a backup copy of the working file.

Since this is a system file, you need to run sudo when working on it.  Open up a terminal and type in:
```
sudo cp /etc/fstab /etc/fstab.backup
```

after you have done that, you can edit it by running:
```
sudo gedit /etc/fstab
```
then comment out the lines that you don't want loaded and save the file. Restart your system to make sure that everything loads correctly

---

### Post by bungnati on 2007-11-17
Thanks guys. the gconf editor method worked fine. Again Thanks for you rhelp.

---

### Post by Sproid on 2007-12-28
**Hi.**
 First Thanks for the solution you guys give already. Second, I understand half the way, I appreciate if you give a little more explanation on how to use gconf or with the other method fstab. I reach both with sudo in the terminal but don't know what to change. 

In my pc-desktop  I have ubuntu in the second hd and I can mount the other hd(windows xp) manually in the Computer folder. But In my laptop I have dual boot in one hd and the other 3 windows volumes are automatically mounted. My goal is that the 'Recovery' and 'OSS tools' partitions or volumes are not mounted at startup, or all with the option to mount the manually as I can do in my pc-desktop. Again tnx. Mery Xmas and Happy New Year 2008! :)

---

### Post by Shazaam on 2008-01-01
Sproid...
Do you want to remove the unwanted desktop icons for the auto-mounted volumes? If you do go to Applications>Accessories>Terminal and type this in:
```
gconf-editor
```
This code will open the "gnome configuration editor" Be carefull with what you change; (at least write down WHAT you changed) research what each setting does before making any changes. Got to "apps>nautilus>desktop" Uncheck "volumes_visible" This will remove the drive icons from your desktop but they will STILL auto-mount. To access them go to "Places" on your panel.

---

