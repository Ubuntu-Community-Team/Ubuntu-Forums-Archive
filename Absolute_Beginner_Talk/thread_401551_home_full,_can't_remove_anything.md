---
title: "/home full, can't remove anything"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-04-04
After rebooting last night I logged back in to find I couldn't get past the kdm or gdm screen.

After some googling I found the problem related to my /home directory being full. I have my /home on a seperate drive.

So, I figure delete some files and move on. I have no idea how I filled the 75gb drive to begin with since I save all my files to a 3rd drive on /home/download (which is 93% full). Only thing I can think of is while trying to transfer some DVDs from /home/download to a mounted samba file the files got copied to a temp somewhere.

I tried to remove several large files, including a ripped cd to free up space. They removed correctly (rm -rf) but it didn't free up any space. It still shows up being 100% even though I have deleted well over 1gb worth of files. I also tried deleting /home/taddy/tmp/* and rm -rf on both KDE and Gnome trash. The files appear removed but again the space doesn't show as cleared on the HDD.

What the heck is going on here?

---

### Post by taurus on 2007-04-04
Boot into recovery mode from GRUB menu and delete stuff in /home/**username** or /home/download that you don't need then.

```
cd /home/**username**
```

---

### Post by ComplexNumber on 2007-04-04
further to what taurus has said, you could temporarily transfer some of your files to /temp. well, thats if you have the space on the root partition. for example, if you have a large directory of audio or video files, you can temporarily move them over to /tmp. once you are able to boot into /home again, you can have a good sort out :mrgreen:.

you may need to delete /home/.Trash-root too if it has become too large.

i'm not too sure about the fact that its still showing 100%. i think that it may need refreshing, but hasn't.

---

### Post by taddy_porter on 2007-04-04
That's the problem. I do go in and delete stuff, but the space still remains 100% full. I don't understand that.

---

### Post by taurus on 2007-04-04
How did you remove it?  Look in the trash bin to make sure there is nothing in there, either.

```
ls -la ~/.Trash
```

---

### Post by taddy_porter on 2007-04-04
Got it. Don't know why it did this, but my HTPC on a windows box is mounted over samba as /home/taddy/HTPC.

When I logged in to recovery mode as root and did a rm -rf /htpc/* it cleared 40gb's of space. I checked in that directory prior to running the command and it only showed 100mb's of used space. Strange. It's gotta be something with my HTPC actually getting full during transfers.

Thanks for the help.

---

