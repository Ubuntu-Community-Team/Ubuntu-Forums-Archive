---
title: "[SOLVED] Help! Urgent! Filesystem Error!!!"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2007-10-01
HELP!

When I booted up my computer today it began to boot as normal. However... it stopped and said this:

```
fsk 1.40-WIP (14-Nov-2006)
/dev/sda2 contains a file system with errors, check forced.
/deb/sda2:
Inodes that were part  of a corrupted orphan linked list found.

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsk MANUALLY.
             (i.e., without -a or -p options)
fsk died with exit status 4
                                                                          [fail]
*An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be preformed in maintenance mode with the root filesystem
mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After preforming system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Give root password for maintenance
(or type Control-D to continue):
```

If I type in my root password, it goes

```
bash: no job control in this shell
bash: groups: command not found
bas: lesspipe: command not found
The program 'apt-get' is currently not installed. you can install it by typing:
apt-get install apt
bass: apt-get: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing:
apt-get install apt
bash: apt-get command not found
root@gTOP:`#
```

From there I can browse my files, but I'm not sure how to boot up into the real OS?!

(oh by the way, if I press Control-D, it just reboots).

What is going on?! And how do I fix this easily?

Thanks.

---

### Post by hotweiss on 2007-10-01
I also had this error, but I solved it by editing menu.lst.

At the command prompt type:

> sudo nano /boot/grub/menu.lst

Or if you have to:

> cd /boot


> cd grub

> sudo nano menu.lst

Then delete all of the mounting entries that you added in yourself.

If you messed around with your fstab:

> cd /etc

> sudon nano fstab

Delete the entries that you added in and press CTRL-O to save.

---

### Post by christhemonkey on 2007-10-01
Or you can just do what it asks and try repairing the filesystem manually:
```
fsck /dev/sda2 
```

---

### Post by sirgogo on 2007-10-01
Thanks for your posts.

hotweiss: I tried using your code, however it told me that "sudo" wasn't a valid command (bash:.....)

christhemonkey: Awesome :). It worked like a charm. I really wasn't sure what to do, or what it was asking me to do. You really helped.

Now I'm rockin' :guitar:.

Thanks a bunch. (both of you)

---

### Post by Gwasanaethau on 2007-10-01
> **christhemonkey said:**
> Or you can just do what it asks and try repairing the filesystem manually:
```
fsck /dev/sda2 
```

Is that not dangerous? Isn't there a risk of losing data that way? :confused:
Just wondering…

---

### Post by philinux on 2007-10-01
fsck will run every so many boots depending on the disk size so running fsck /dev/hdawhatever is going to get run anyway by the system.

---

### Post by hotweiss on 2007-10-01
> **sirgogo said:**
> Thanks for your posts.

hotweiss: I tried using your code, however it told me that "sudo" wasn't a valid command (bash:.....)

christhemonkey: Awesome :). It worked like a charm. I really wasn't sure what to do, or what it was asking me to do. You really helped.

Now I'm rockin' :guitar:.

Thanks a bunch. (both of you)

Maybe I did it without sudo, I forgot now.

---

### Post by Gwasanaethau on 2007-10-01
> **philinux said:**
> fsck will run every so many boots depending on the disk size so running fsck /dev/hdawhatever is going to get run anyway by the system.

Ahh. I'm always worried about anything to do with the file systems. I know it'll be just my luck that I'll choose the wrong command and *poof*, I lose everything! :lolflag:

---

### Post by christhemonkey on 2007-10-02
**@hotweiss**the recovery shell doesnt have sudo, as it logs you in as root user anyway, so it just becomes unnecesary code.

**@Gwasanaethau** fsck only performs a **f**ile **s**ystem che**ck** (and optionally if it finds anything wrong can repair it) so you cant really do anything wrong particularly.

---

### Post by FuturePilot on 2007-10-02
> **christhemonkey said:**
> Or you can just do what it asks and try repairing the filesystem manually:
```
fsck /dev/sda2 
```

Careful with that command. You never want to do that on a mounted drive as it will totally mess it up big time. Doing in from the live CD on an unmounted drive is the safest.

---

### Post by Gwasanaethau on 2007-10-02
> **christhemonkey said:**
> …**@Gwasanaethau** fsck only performs a **f**ile **s**ystem che**ck** (and optionally if it finds anything wrong can repair it) so you cant really do anything wrong particularly.

Ahh! Thanks for clearing that up for me! Makes sense.

---

