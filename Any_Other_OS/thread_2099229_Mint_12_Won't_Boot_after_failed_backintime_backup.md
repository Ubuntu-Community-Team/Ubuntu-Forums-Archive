---
title: "Mint 12 Won't Boot after failed backintime backup"
date: 2012-12-29
forum: Any Other OS
---

### Post by Andy45 on 2012-12-29
Hello everyone,

This evening I was doing a backup with backintime  on a computer with limited HDD space when a dialog popped up saying I  had less than 1 GB of space left. I checked this in GParted, and sure  enough, the backup was taking up all the remaining space. I tried to cut  the backup short by deleting the directory where the backups would be  saved. This seemed to work - until I rebooted. It gave me a black screen  with text on it that complained about a broken pipe among other things,  and boot would hang. Does anyone know what happened and/or how to fix  it?

Thanks!

---

### Post by xenopeek on 2012-12-29
I'd start by seeing if you can still boot into recovery mode. Hold shift during boot to get the GRUB boot menu to show (if not shown by default), select the second option in the menu, "recovery mode". You should be taken to a another text menu, where near the bottom of the list you can choose to "drop to root console" or similar. Try that. You will be asked for root's password, which will be the same as the password you gave for the user created during installation of Linux Mint (unless you changed it since). 

Now, can you recall where you told backintime to save its snapshots? If that was in your home directory for example, then go there:
```
cd /home/yourusername
```
Then run the following command to see if you can find any pipes from backintime you might want to delete:
```
find . -type p
```
There will probably be a few pipes from other programs or browser plugins. Perhaps deleting any backintime pipes here will help.

---

### Post by Andy45 on 2012-12-29
Unfortunately when I boot into recovery mode, when I am trying to move down to the bottom option for root console, my keyboard won't respond. Pressing the down arrow key, mouse button, or any button for that matter doesn't do anything. My only guess as to why this would happen is that maybe when the destination for the rsync backup disappeared (when I deleted the folder that I told backintime to save the backups in the middle of the backup) it began deleting files rather than attempting backup or just quitting backup.

---

