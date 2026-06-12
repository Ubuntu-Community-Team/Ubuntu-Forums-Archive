---
title: "Several questions"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by imaginos on 2006-10-02
My system:
- Ubuntu 6.06 (installed from standard CD)
- Dual boot with Win XP
- installed only build-essentials

Questions:

1.
I am in the phase of learning and understanding startup scripts, so I often want to copy/backup them, enter my additional comments and so on...
I would like to have a root user that will not be obligated to use sudo or enter password so frequently. It is very annoying and time consuming, at least in this early phase when I have constant need to make backup copies of startup scripts in their own directories.
- How do I do that?


2.
Until yesterday, everything was ok with mu "set" command. It had displayed a large list of environemnt variables, as it should. But now, when I execute "set" command, the screen is filled with something that looks like a souce code written in C. It could also be a part of a script, I am not sure.
- What went wrong and how can I fix this problem?
I have chaned one of .bashrc scripts (i changed PS1 prompt, nothing fancy) but I am not sure if that is a source of a problem, because restoring that file to previous state didn't solve the problem.


3.
I often need to paste text from, let's say, web page to a terminal. For example, a very large command is given in a tutorial and i want to paste it in bash to try it. Is there a way to do that?
I would also like to be able to select text from terminal (for example, som output given by a command) and paste it in a text file...
Is there a way to do this?


4.
My welcome splash screen with picure of ubuntu logo and startup echoes scrolling below that picureis in a lower resolution than my monitor is capable of displaying. I think that it runs i 800X600, while my TFT can display 1024X768. Could something be done to make startup splash screen appear in higher resolution?


5. How can I uninstall build-essentials? Does install procedure saves package in some folder (and filling up my hard disk space), and if so, I would like to know where so I could delete it (i have that package on Ubuntu CD).

6. 
I know this question has been asked million times, but i did not find a definite answer:
How to make NTFS partition writeable, but WITHOUT any apt-get actions? Is it possible to do it by changing fstab and other system settings files, without installing extra drivers and software?



Thank you in advance!

---

### Post by Iowan on 2006-10-02
1. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

3. What kind of terminal - the terminal emulators in Gnome have a copy and paste option under one of the pull-down menus.  They seem to work, whereas Ctrl-C, Ctrl-V do not.

---

### Post by skymt on 2006-10-02
2. The bash "set" command outputs shell variables and shell functions. I don't know how you had it work otherwise, you must not have had any functions defined. As a workaround, if you only want environment variables, use the env command.

3. Ctrl-Shift-C and Ctrl-Shift-V work for copy and paste in Gnome terminal.

4. It's a technical limitation. The latest beta of Ubuntu (Edgy Eft) fixes this.

5. Open Synaptic (System > Administration > Synaptic) and search for build-essential. It may not be installed. It isn't installed by default. If it is, remove it along with gcc, g++, libc6-dev, make, and dpkg-dev.

6. Ubuntu doesn't come with write-capable NTFS drivers. You need to follow one of the howtos, like [this one](http://ubuntuforums.org/showthread.php?t=217009).

---

### Post by Cruz on 2006-10-02
1.
In Applications -> Accessoirs -> Alacarte you can enable a "Root Terminal" in the System Tools group. You can then start this root terminal from Applications -> System Tools. You will be asked for your password only once for the first time and then you will have a root session. 

Actually you get the same if you open a normal terminal and then type sudo -i. 



3.

The easiest way:

Select the text in the browser. Klick on the terminal. Klick the middle button. The selected text will be pasted. 


4.

For me it helped to tweak my xorg.conf so that only 1024X768 and only the appropriate vsync and hsync rates are available. Since then everything looks just like I want it, but can't switch to anyhting else.

---

### Post by skymt on 2006-10-02
> **Cruz said:**
> 
4.

For me it helped to tweak my xorg.conf so that only 1024X768 and only the appropriate vsync and hsync rates are available. Since then everything looks just like I want it, but can't switch to anyhting else.

The OP is referring to usplash, which was limited to a low resolution in Dapper.

---

### Post by imaginos on 2006-10-02
Thank you very much for your answers, you're great. :)


6. 
Since I do not want to install additional drivers for NTFS, I decided to convert that partition to FAT32.
I don't think I have enough knowloedge to setup fstab myself, so, is there a way to "autodetect" and mount disks and remember that settings in fstab. 
In my opinion, if I replace the old line with this one it should do, but I am not sure:
```
/dev/hda3 /mnt/hda3 vfat user,rw,auto,noexec,sync,umask=111 0 0
```
Will this tag give read/write access when I combine it with umask=111 which is used to disable executing since the fat32 partition will contain only "data files" such as music, video, picures, documents, etc..


4.
I remember booting Ubutu from live CD, it had the same splash start screen, but there was an option (F4 as far as I can remember) that was used to change resolution, and it affected the splash screen immediatley.
Can something be done in that direction?

Thanx!

---

### Post by n0dl on 2006-10-02
In refrence to your copy and paste question simply highlight the text and middle click, click your mouse wheel, or press both of your mouse buttons at the same time in the desired terminal and thus pasting. (only works in X unless you have GPM up and running allowing you to have a mouse in tty/Console.

If you want to backup your files sudo cp filename filename.backup. If you messed things up either bootup a live cd and mount /dev/hda1 then do the opposite sudo cp filename.backup filename

---

### Post by Josey on 2006-10-02
3.
I've found that I can simply highlight text and it copies automatically and then click the scroll wheel down for paste.
Give it a try... this is default!

---

### Post by imaginos on 2006-10-03
1. 
After sudo -i, or entering root terminal, i still open certain files in read only mode when i click on them in file browser, and must go to terminal and execute: "sudo gedit filename" in order to edit it.
At least, is there a way to open terminal in current directory od file browser?

2.
env command works perfectly, 10x!

3.
Cut/paste with 3rd mouse button (wheel) and Ctrl-Shift-C/V also works fine. :]

5.
10x for the uninstall tip.

6.
I converted one partition to FAT32, and still can not write to it because I don't have permissions (I have root priviledges, ofcourse).
fstab line is:
```
/dev/hda6 /media/hda6 vfat defaults,rw,umask=000 0 0
```
How can I enable write priviledges? :(

---

### Post by skymt on 2006-10-03
1. In the root terminal, type "cd " (with the space), drag the folder to the the terminal window, and hit enter. If you want a file browser with root privileges, use "gksudo nautilus".

6. I'm afraid I can't help you with this one. I have no experience with FAT32 and very little with fstab hacking. Someone else?

---

### Post by imaginos on 2006-10-03
10x skymt, that's it!
kgsudo nautilus is what I was looking for. Great! :]


6.
It works with fstab settings I have shown, I just needed to reboot. :)

---

### Post by imaginos on 2006-10-03
4.
SOLVED!
I digged up this (fantastic) solution. Really great post!
[http://www.ubuntuforums.org/showthread.php?t=258484&highlight=tutorial+resolution+splash+vga%3D791+menu.lst](http://www.ubuntuforums.org/showthread.php?t=258484&highlight=tutorial+resolution+splash+vga%3D791+menu.lst)

Splash screen resolution can be changed to 1024x768 by changing file 
/boot/grub/menu.lst

find this line
```
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
```

and add at it's end:
```
vga=791
```

Also, find (commented!) line:
```
# defoptions=quiet splash 
```

and add the same:
```
vga=791
```

---

### Post by Charles Hand on 2006-10-05
> **imaginos said:**
> 
```
/dev/hda3 /mnt/hda3 vfat user,rw,auto,noexec,sync,umask=111 0 0
```

You can also add to the option list
```
,gid=nnnn,uid=nnnn
```
in order to set the ownership and group of the entire mounted fat32 partition.

---

