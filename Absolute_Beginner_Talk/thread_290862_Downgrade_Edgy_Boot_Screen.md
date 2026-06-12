---
title: "Downgrade Edgy Boot Screen"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Leed on 2006-11-01
Hello, 

Althought I have 20 Years of PC experience, I'm totally new to Linux. I'm still a bit lost, but do wish to set up my Ubuntu in a power user style. 

Unfortunatly I found that Edgy Eft is more directed to the simple user, for instance System Folders get hidden by default.

My question here is, can I get the boot screen to display what the system is doing, as I it did in Dapper Drake, followed by an "[ ok ]" when done. I don't like the idea of hiding this feature as other systems like Windows do. 

I am also interested in tips how to change the boot screen appearance, as well as key-combinations that can be used during boot (for full console view, alternate login, etc)

many thanks in advance

---

### Post by Drezliok on 2006-11-01
I would also like this as well.

I tried tapping a few keys that worked for other distros to allow me o see the stuff being loaded.

---

### Post by rfruth on 2006-11-01
Take the word "quiet" out of your current kernel in (/boot/grub/menu.lst)

```

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=2CA6-0780 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault

```

---

### Post by lambros on 2006-11-01
> Althought I have 20 Years of PC experience, I'm totally new to Linux.

Blimey, that's a lot :) 

> ... for instance System Folders get hidden by default.

I'm not sure what you mean here.  If I go to "Places" > "Computer" and click on "File System" on the left, I can see my system folders just fine.  What I'd call "System Folders" are things like: bin, boot, dev, etc, lib, mnt, proc, usr and those are visible in the root of your file-system.  The hidden folders are those whose names begin with a dot, and these typically live in your home folder: /home/myusername/.xyz/  These are for storing settings for various applications, and I wouldn't really call these "system" folders, because they are per-user (if you had more than one user account, each user would have their own different .xyz folder)  These folders **are** hidden by default.  You can see them in your file-browser by going to the "View" menu and choosing "Show Hidden Files".

> ... can I get the boot screen to display what the system is doing, as I it did in Dapper Drake, followed by an "[ ok ]" when done ...

You certainly can.  Just press Ctrl-Alt-F1 whilst the splash screen is shown during bootup.  You might possibly need to press Ctrl-Alt-F7 to get back to your graphical desktop.  In general, pressing Ctrl-Alt-(F1..F6) will switch between your "virtual consoles".

If you want to make this more permanent, you can disable the graphical splash screen by editing your menu.lst file as suggested by rfruth:

```
sudo gedit /boot/grub/menu.lst
```

Find the line that says:

```
# defoptions=quiet splash
```

and remove the "splash" so it looks like:

```
# defoptions=quiet
```

Strange as it may seem, you do need to keep the '#' at the beginning of the line here.  As rfruth suggested, you could try removing the "quiet" as well, but I haven't tried this myself.

To make your change take effect, after saving your edits, you will need to run the command:

```
sudo update-grub
```

Then reboot to enjoy a whole new splash-less experience :)  Prepare to be slightly disappointed though, because the traditional SysV-style "init" system has been replaced by Ubuntu's new "upstart" system.  This seems to drastically cut down the amount of information displayed in the boot sequence (I don't exactly understand why, but I believe that's the reason).

Hope that helps.  As for changing the boot screen appearance, this should be possible with more work.  This link has some info:

[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

Lambros

---

### Post by Leed on 2006-11-02
Thanks a lot for the help, especially rfruth, got my Boot screen working nicely the way it was in Dapper, really missed those kind System entries during startup.

@Lambros
I totally agree with you, that System folders are /etc, /usr, /boot ... 
and these are unlike the hidden files that those that start with a ".". 
While using Dapper Drake my System was Displayed in the File Manager as you explained. But since the upgrade to Edgy Eft Linux treats my System Folders as hidden files. In the Root of my File System per Default I only see the folders "home" and "media", all the others (etc, usr, boot...) only get displayed when I activate hidden files (Ctrl+H). I don't understand this and find it somewhat disturbing. 
Thanks a lot for the shortcuts upon start, I'll enjoy testing them.

Cheers
Leed

---

### Post by lambros on 2006-11-02
Hi Leed,

I think I've worked out what's probably causing your system folders to be hidden from your file browser.  In your root directory, you might have a file called ".hidden".  It is simply a text file that lists all the folder names that your file browser should hide.  Try running this command:
```
ls -a / 
```
Do you see a file called .hidden in the output?  If yes, that is what is causing your system folders to be hidden from you.

If you want to see your system folders in the root directory, simply delete this file, or move it out of the way with a command such as:
```
sudo mv /.hidden /.hidden-moved 
```

There is more information on this feature in the Ubuntu documentation.  Go to System -> Help -> System Documentation and do a search for ".hidden" (without the quotes).

Hope that helps,
Lambros

---

### Post by Leed on 2006-11-02
Cool, that did it. Thanks a million, just learnt a lot about gnome trough this :D

---

