---
title: "Accesing Windows Partition."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Sonlc on 2006-04-28
I have a file in my Windows partition that I would like to copy to the desktop, but I cant seem to drag and drop.  Does anyone know how I can do this?  I really need help.


Thanks in advance

---

### Post by Sonlc on 2006-04-28
Anyone at all?

---

### Post by yager on 2006-04-28
[QUOTE=Sonlc]I have a file in my Windows partition that I would like to copy to the desktop, but I cant seem to drag and drop.  Does anyone know how I can do this?  I really need help.


Thanks in advance[/QUOTE]
I opened Applications->Accessories->File Browser and successfully dragged a picture file from my NTFS partition onto the desktop.  At what step does this break down on your setup?
1.  The file browser does not open.
2.  The windows drive is not visible.
3.  The windows drive is visible but you can not open it.
4.  The target file is visible but you can not select it.
5.  You select the file but it does not show up on the desktop.

The 2 and 3 can be corrected by mounting commands and some permissions on the directory that you mount the drives to.  4 and 5 are over my pay grade,  (oh wait I'm not paid here....).  4 and 5 are past my experience level. (Thats better.)

---

### Post by Jimmey on 2006-04-29
You need to figure out which partition Windows is using. This can be done, while in a terminal, by typing 
> sudo fdisk -l

The Windows one is the one marked "NTFS", and should read something like /dev/hda2 ( the number might change ).

Now you need to mount the partition ( bearing in mind that once it is mounted, you can't write to it - That means no saving files there, no deleting files, no moving files - all you can do is copy the files over ).

You need to decide where you'd like the partition to be mounted. If the place where you want it mounted already exists, you can skip this step.

If you'd like to set up a new folder for the mount, like /home/windows, you'll need to execute this command:

> sudo mkdir /home/windows

Once that's done, you're ready to actually mount the partition. Here's the command.

> sudo mount -t ntfs /dev/hdaX /place/to/mount

Replacing the 'X' with the number of the partition you want to mount, and the '/place/to/mount' with the place you want to mount it to :P

Edit: I actually just read your post. You'll probably need to act as root to do that...So, try 

> cd /place/you/mounted/and/where/file/is
sudo cp filename.extension /home/yourname/Desktop/filename.extension

---

### Post by Sonlc on 2006-04-29
Great Jimmey, thanks for the help!  Now the only problem is, that I need to move the file from my desktop onto a usb drive.  The USB drive is labled "RABSDA" and the file, which is on the desktop is called "3ComV2.0.zip".  When I try to drag it across, I get this message  ""/home/soni...mV2.0.zip" cannot be copied because you do not have permissions to read it."   Can anyone help me out with this?

---

