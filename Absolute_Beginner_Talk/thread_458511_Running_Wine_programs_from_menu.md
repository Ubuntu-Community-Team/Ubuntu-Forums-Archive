---
title: "Running Wine programs from menu"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by wxman on 2007-05-29
Hello

This is my first post here, and I hope I'm in the correct forum. 

I have a few educational games that ran in XP that I'm trying to get running in Ubuntu. I installed Wine correctly, I guess, because the games work fine from the terminal. I thought I followed the instructions correctly, and pasted the same command into the menu editor, but nothing happens. For example, I have one that runs from the CD drive only (no installation needed) and this works great from the terminal:
```
wine D:Muzzy.exe
```

Then I tried another one that did install onto the hard drive:
```
wine C:/SIERRA/TIMWIN/timwin.exe
```

I tried surrounding the address with quotes, and without, with no luck either way. I'm still learning the whole system so I was hoping I was just missing something simple.

---

### Post by annda on 2007-05-29
check your /media directory to see where the win drive is mounted. then use something like:

wine /media/my_windows_drive/SIERRA/TIMWIN/timwin.exe

---

### Post by mevets on 2007-05-29
Your cdrom drive probably isnt going to mount to the D drive. Look in /media to see where the cdrom was mounted

---

### Post by wxman on 2007-05-29
> **annda said:**
> check your /media directory to see where the win drive is mounted. then use something like:

wine /media/my_windows_drive/SIERRA/TIMWIN/timwin.exe

I installed the one on the hard drive using wine, and now I can only see the installed directory if I use the 'winefile' utility. If I look for it using the normal file browser, I can see the .wine directory. Under that I have a windows, and the SIERRA one, but no files in it. I realize the Wine is making a virtual C drive, but I don't get where to point to it.

---

### Post by wxman on 2007-05-29
It looks like I might have solve the one running in the CD drive. It seems to mount it as 'Muzzy' not as cdrom1 like I expected. I have no idea why it chose to do it like that, and it's going to be hard to make a menu if it changes the name with different CD's in the course.

I'm still working on the other one that's on the hard drive somewhere.

---

### Post by RomeReactor on 2007-05-29
Hi. wxman, try this:
```
wine /media/cdrom/Muzzy.exe
```
As for the one installed in the HD, the wine folder is hidden on your home directory; pressing CTRL+H while browsing with Nautilus will show all the hidden files and folders, and pressing it again will hide them. For this one, try:
```
wine /home/YOUR_USER_NAME/.wine/drive_c/SIERRA/TIMWIN/timwin.exe
```
I'm not sure that **drive_c** is correct, though (I don't have wine installed at the moment).

---

### Post by Ek0nomik on 2007-05-29
> **RomeReactor said:**
> Hi. wxman, try this:
```
wine /media/cdrom/Muzzy.exe
```
As for the one installed in the HD, the wine folder is hidden on your home directory; pressing CTRL+H while browsing with Nautilus will show all the hidden files and folders, and pressing it again will hide them. For this one, try:
```
wine /home/YOUR_USER_NAME/.wine/drive_c/SIERRA/TIMWIN/timwin.exe
```
I'm not sure that **drive_c** is correct, though (I don't have wine installed at the moment).

It is.

---

### Post by wxman on 2007-05-29
It looks like you were mostly correct. I did a file search for the 'timwin.exe' file and I found it at :
```
/root/.wine/drive_c/SIERRA/TIMWIN/timwin.exe
```

I might have told it wrong when I installed it - it was my first time.
Now it actually is working!

I can't seem to get the one in the CD drive to work unless I call the drive 'Muzzy'. I tried using the different drives listed in the media folder as cdrom, cdrom0, and cdrom1, but none worked. I'm going to try a few different Muzzy disks and see if they all mount the same way.

---

