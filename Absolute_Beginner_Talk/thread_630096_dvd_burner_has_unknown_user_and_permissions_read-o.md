---
title: "dvd burner has unknown user and permissions read-only"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by coldguy on 2007-12-03
I've removed an ide cd-rw and replaced it with a lite-on DVD+-rw,r,dl sata drive. I can read disks, but can't burn anything. Brasero or any other software will correctly identify the blank media, but when I try to burn will tell me the disk is not big enough, please insert a disk with at least xxxmB free space, where xxx is far less than a blank DVD-RW. 

If I go to places/computer it shows both a cd-rom 1 (which was removed, right?) and a cd-rw/dvd+-rw drive. Checking the properties/permissions of the cd-rom shows owner and group is root. On the CD-rw/DVD+-rw, the owner and group is unknown, the permissions are set to read only, and I can't change them. I think the problem is the owner is unknown. If I put a blank DVD-RW in the drive, I seem to be able to change the folder access and file access, but I still get the same result.

I'm still a complete newb at this, and I'd appreciate any help. I've checked other posts with I think identical problems, but they remain unsolved.

---

### Post by speed145a on 2007-12-03
do me a favor and try opening a terminal and typing:```
sudo brasero
```

let me know if this fixes your symptoms and i will tell you how to fix it permanently (without opening brasero as sudo)

---

### Post by coldguy on 2007-12-03
Thank you so much for your response!

I get this-

libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(brasero:6300): Pango-CRITICAL **: pango_layout_set_markup_with_accel: assertion `markup != NULL' failed
I/O warning : failed to load external entity "/root/.gnome2/brasero.session"

-and then brasero opens, but attempting to burn yields the same results-ejected disc.

my trouble seems similar to this thread, which is unsolved

[http://ubuntuforums.org/showthread.php?t=623364&highlight=dvd+permissions](http://ubuntuforums.org/showthread.php?t=623364&highlight=dvd+permissions)

except that I can mount and read any disc with something on it. I also found this poor guy

[http://ubuntuforums.org/showthread.php?t=622210&highlight=dvd+permissions](http://ubuntuforums.org/showthread.php?t=622210&highlight=dvd+permissions)

who sounds like we have something in common.

I haven't the faintest idea how to do it, but I think I need to chown something, as the DVD burner claims the owner is unknown, while the cd-rom (which I thought I removed) owner is root.

---

### Post by speed145a on 2007-12-03
well, i will look into it.

just so you know i right clicked on my mounted cdrom and it said it is owned by root as well and brasero works great for me

have you tried removing and reinstalling brasero?

---

### Post by coldguy on 2007-12-07
When I removed the CD-RW, was I supposed to do something to let Ubuntu know its gone, or would the fact that its no longer there be sufficient. I really don't understand why in places/computer it shows both a CD-ROM 1 and a DVD+-RW, when I only have the DVD burner installed, and I think thats part of the problem.

---

### Post by jackn on 2008-04-19
Brasero doesn't work in my hands either. It does exactly what the original message described.

I'd like to add the following observations:
[LIST]
[*]Brasero used to work just fine in my hands. Don't know what's happened to make it stall.
[*]Here is the terminal output while it's trying to run. ```
~$ sudo brasero
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Sense key: 0x72 0x0b 0x00 0x00 0x00 0x00 0x00 0x0e 0x09 0x0c 0x00 0x00 0x00 0x03 0x00 0x00 0x00 0x00 0x00 
I/O warning : failed to load external entity "/root/.gnome2/brasero.session"

(brasero:12984): Gtk-CRITICAL **: gtk_tree_model_get_iter: assertion `path != NULL' failed

(brasero:12984): Gtk-CRITICAL **: gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed

(brasero:12984): Gtk-CRITICAL **: gtk_tree_model_get_iter: assertion `path != NULL' failed

(brasero:12984): Gtk-CRITICAL **: gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed
``` I can't make heads or tails out of these messages. Can someone else?[*]Here is my long listing of my CD burner: ```
lrwxrwxrwx 1 root root    6 2007-04-28 10:32 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-04-28 10:32 cdrom0 
```Ownership and permissions don't seem to be an issue, as I get the same results with 'sudo Brasero'.
[*]Finally, I've reinstalled Brasero. No honey.
[/LIST]

---

