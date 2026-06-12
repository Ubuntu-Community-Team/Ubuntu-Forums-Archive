---
title: "i can rename files when they're in use?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by kyalee on 2007-08-15
I am NOT complaining, but I am curious. In Windows when I tried to re-name a file that was currently open, it would give me an error message. But I was re-naming some video files and I didn't realize that one of them was currently playing when I went to re-name it. The changes took. No error message. Why? Is there something different about the way Linux handles files that lets you rename files when they're being used? Is it a bad idea to do it for some reason?

Like I said, this isn't a complaint or a problem at all. In fact, it's kinda nice. But I am curious about why there's a difference.

---

### Post by Bushfire on 2007-08-15
I'm going to make a horribly uninformed guess. I think that the filename is held as data on the inode, and the actual data is seperate from that. It doesn't try to stop you because it doesn't change anything except a string relating to that data, so no corruption is possible (it doesn't change the inode data etc)

As to why Windows won't let you...I know even less about Windows file internals than I do Unix file internals. So I have no idea.

---

### Post by Chaotic Thought on 2007-08-15
Yeah, it's a small but nice feature, isn't it ( : ...  For more fun, try *moving* a file while it's being played by your music player--I think you'll find that it will work without a problem and the file will continue playing. In fact, the application that is using the file will have no idea that the file has been moved, unless it's smart enough to actually check.

The difference is: Windows uses what are called _mandatory locks_ on files. It means that if a file is open in a certain way, no one else can open it (not even Administrator). That's exactly why Windows always says "You must restart Windows before the changes will take effect." -- that's because Windows itself can't change it's own files, so it has to add a little startup script to the system that will make the changes during bootup.

But Linux can change any file anywhere on the system. This is useful for updates. Here's an example: suppose you're using a calculator application, we'll call it "Version 1", and you notice that "Version 2" is available and want to upgrade. If you upgrade from Version 1 to Version 2 *while* the Calculator is actually running, then Linux saves a copy of the old version in memory and does not use the new version until you close down that program and restart it. Hopefully that made a little sense.

---

### Post by nhandler on 2007-08-15
Well, there is always a chance of problems occurring if you modify the file while it is in use. For example, You open the file in some program. The program stores the path to the file in a variable. You then rename the file. This causes the path stored in the variable not to exist, which results in an error.

In my opinion, there is a small chance of that happening. I just would be careful if it was an extremely valuable file.

---

### Post by Hobo Joe on 2007-08-15
Yet another win for Ubuntu. :D

---

### Post by Bushfire on 2007-08-15
> 
But Linux can change any file anywhere on the system. This is useful for updates. Here's an example: suppose you're using a calculator application, we'll call it "Version 1", and you notice that "Version 2" is available and want to upgrade. If you upgrade from Version 1 to Version 2 while the Calculator is actually running, then Linux saves a copy of the old version in memory and does not use the new version until you close down that program and restart it. Hopefully that made a little sense.


Well, to be picky, the program is already in the memory - once a process has been loaded and fork()'d, it doesn't care about the state of the executable on the harddrive. And the same goes for windows (or any multi-tasking OS for that matter).

---

### Post by Chaotic Thought on 2007-08-16
> **Bushfire said:**
> Well, to be picky, the program is already in the memory - once a process has been loaded and fork()'d, it doesn't care about the state of the executable on the harddrive. And the same goes for windows (or any multi-tasking OS for that matter).

But in Windows, running program does introduce a mandatory lock on the file. For example, try running **calc.exe** and while it's running try to overwrite or otherwise modify the program file **c:\WINDOWS\system32\calc.exe** and you'll probably find it will fail. In fact some weird stuff happens--I tried moving my **calc.exe** while it was running and windows seemed to create a *new* calc.exe in the original place, and it left a mandatory lock on the first one.

In any case, Linux makes a lot more sense in this regard. Permissions are used to lock out users from files, and root can always override them.

---

### Post by tgalati4 on 2007-08-16
For some fun:

When you are ready to wipe  your machine for a new distro, back up your /home and any other important data.

Then while the machine is running, start deleting system files and see how long the system stays up.

---

### Post by daveshields on 2007-08-16
Files are represented as inodes. To rename, or move,  a file is to change its parent directory. Doing that doesn't change the inode; it just associates the inode with a different directory.

---

