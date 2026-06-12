---
title: "Rectifying File System permissions"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by DWE on 2007-05-13
While tidying my files I adventurously deleted the Examples folder in Home to Trash.

Immediately the whole of my File System permissions, except Temp, changed to root.

How do I rectify this?

Many Thanks in advance.

---

### Post by steve.horsley on 2007-05-13
Moving the Examples folder th Trash shouldn't do anything untoward. 

I don't understand what happened, and to be honest, I don't really know what you mean by the whole filesystem permissions changing to root. The top-level (if you do ls -l / for instance) is always owned by root. If files in your home folder have changed ownership to root, then something really nasty has happened, and I would suggest re-installing. You are unlikely to ever sort out the correct ownership and permissions on all the system files. If this is what happened, I think you must have accidentally done something other than deleting Examples.

---

### Post by Skrynesaver on 2007-05-13
Hi DWE,
root should own almost everything, except the files in /home/DWE.
If these files are now owned by root, you can change this by using the command
```

chown -R DWE /home/DWE

```
Obviously substituting your actual username on the system in place of DWE

---

### Post by DWE on 2007-05-13
Thank you both
Re reinstalling - please, no, surely, pleeeeeeeeeease.
Re normal - the symbol of the lock on all directories in File System was not there before the deletion - am I becoming paranoid?

---

### Post by Skrynesaver on 2007-05-13
Could you post the response to the following commands typed in to a terminal
```

ls -l /
ls -l /home

```
While root should own almost everything on the system outside the /home directories the users should be able to read these directories.  As Steve said earlier deleting the examples directory should have no effect on the rest of the file system.

---

### Post by DWE on 2007-05-13
here it is (and thanks again for your interest - much appreciated)

maggie@maggie-desktop:~$ ls -l /
total 112
drwxr-xr-x   2 root root  4096 2007-04-11 07:17 bin
drwxr-xr-x   3 root root  4096 2007-04-16 07:31 boot
lrwxrwxrwx   1 root root    11 2007-04-08 19:40 cdrom -> media/cdrom
drwxr-xr-x  13 root root 14100 2007-05-14 03:41 dev
drwxr-xr-x 116 root root  8192 2007-05-14 03:41 etc
drwxr-xr-x   3 root root  4096 2007-04-08 19:54 home
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 initrd
lrwxrwxrwx   1 root root    33 2007-04-14 08:21 initrd.img -> boot/initrd.img-2.6.20-15-generic
lrwxrwxrwx   1 root root    33 2007-04-08 23:34 initrd.img.old -> boot/initrd.img-2.6.20-14-generic
drwxr-xr-x  17 root root  8192 2007-04-19 19:09 lib
drwxr-xr-x   2 root root 49152 2007-04-08 19:40 lost+found
drwxr-xr-x   5 root root  4096 2007-05-14 03:41 media
drwxr-xr-x   2 root root  4096 2006-10-19 23:49 mnt
dr-xr-xr-x 102 root root     0 2007-05-14 04:41 proc
drwxr-xr-x  15 root root  4096 2007-05-06 19:17 root
drwxr-xr-x   2 root root  4096 2007-04-14 08:19 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 srv
drwxr-xr-x  11 root root     0 2007-05-14 04:41 sys
drwxrwxrwt  12 root root  4096 2007-05-14 03:50 tmp
drwxr-xr-x  11 root root  4096 2007-04-19 20:45 usr
drwxr-xr-x  15 root root  4096 2006-10-25 14:39 var
lrwxrwxrwx   1 root root    30 2007-04-14 08:21 vmlinuz -> boot/vmlinuz-2.6.20-15-generic
lrwxrwxrwx   1 root root    30 2007-04-08 23:34 vmlinuz.old -> boot/vmlinuz-2.6.20-14-generic
maggie@maggie-desktop:~$ ls -l /home
total 4
drwxr-xr-x 48 maggie maggie 4096 2007-05-14 03:41 maggie
maggie@maggie-desktop:~$

---

### Post by Nekiruhs on 2007-05-13
You could do it the GUI way and type gksudo nautilus and going to you home folder and changing its permissions.

---

### Post by Skrynesaver on 2007-05-14
That all looks exactly as it should. Ordinary users can read but not write system files as root owns them  and you own you home directory.  All is well ;)

---

### Post by DWE on 2007-05-14
thanks Skrynesayer for all your trouble - very impresiive - and indeed the pooter is functioning as per, but the iconogrraphy is different, ie the lock symbol on File System was not there before - is this normal?

---

### Post by steve.horsley on 2007-05-14
Like this (attached)? That looks normal to me. If it wasn't there before, then that would be the odd thing. No disrespect intended, but are you sure it's not that you only just noticed the padlock because you are paying close attention to what's there tight now?

If it's a padlock somewhre else that you don't think it should be, could you post a screenshot? Pressing PrintScrn should generate a file on your desktop.

---

### Post by DWE on 2007-05-15
Steve, apologies for the lateness of this reply, but work is all consuming just now.

Have used printscreen, but am unwilling to show all my files to public viewing and can't find a way to crop sufficiently - but, your own example is sufficient. I appear to be getting two variations on a theme when I use Main Menu-Places-Computer. One is your version, with File System only having a padlock and all others with purple folders (am using Crux theme). Two shows File System as purple folder (as I have come to expect) and all others, bin etc, with padlocks. Two is my concern - I haven't seen this prior to deleting Examples.

Having satd that, the system appears to be working normally (my partrner is the main user) and you et al may be correct and I am simply jumping the gun/ call it what you may, but it is strange to be getting two different views of the one File System.

---

### Post by steve.horsley on 2007-05-15
You can crop using the GIMP (installed by default). Use the tool that looks like a scalpel. Failing that, just paste a full screen - I'd be interested to see what you've got. Not that I think I can help much. Explore an innocuous directory if you don't want to show all your files. See my example

---

### Post by DWE on 2007-05-16
OK, here's the opening view of File System, and then after clicking File System – thanx for your patience Steve.

---

### Post by steve.horsley on 2007-05-16
I must have been having an off day when I posted that last screenshot - I posted an image of Places and not the Tree. It's a good job I'm not a pilot or a brain surgeon!

Anyway, Attached is an interesting image.At the back is your image of your tree. In front of that  is an image of my nautilus that I opened to compare with yours. Notice that my tree also shows locked folders everywhere, just like yours. So I thought to myself that this is normal then, and took a screenshot of those two together. Then I opened nautilus again to see what subfolders looked like, and to my surprise, all the locked and unlocked icons were transposed! So I opened the original screenshot to double-check that I was not going mad. In the image are three trees - from back to front:
1) your tree, in Firefox
2) my nautilus, opened for comparison 
(both 1 and 2 are in a screenshot opened in GIMP)
3) My other nautilus, opened only seconds later.

Try as I might, I don't seem to be able to persuade nautilus to transpose the icons and show everything locked again. I wonder if it's something to do with a long launch time for nautilus the first time you open it for a while (when it's not in cache any more). I will keep my eye in it now to see if I can catch it again and experiment with it. 

Another possibility is that last time I used nautilus (maybe half an hour ago) I had two nautilus windows open - one normal one and one running under root's id, (opened from a "sudo -i" terminal), and I had been copying files between the two. Maybe that confused nautilus a bit.

Does your nautilus correct itself if you close and reopen? Can you open those locked folders and see into them?

---

### Post by DWE on 2007-05-16
Yep, it's exactly the same- neither you nor I am mad? The question is, why?  Is this standard? Surely this is not the way it is meant to be? Thanx Steve, again. Do you have any idea of whom  to turn to to solve an evident mystery?

---

### Post by steve.horsley on 2007-05-16
I have no idea. It could have been happening for years without me noticing. But I'm on the lookout now, and will try to investigate if I see it again. I'm not going to lose sleep over it.

---

### Post by dondad on 2007-05-16
> **steve.horsley said:**
> Moving the Examples folder th Trash shouldn't do anything untoward. 

I don't understand what happened, and to be honest, I don't really know what you mean by the whole filesystem permissions changing to root. The top-level (if you do ls -l / for instance) is always owned by root. If files in your home folder have changed ownership to root, then something really nasty has happened, and I would suggest re-installing. You are unlikely to ever sort out the correct ownership and permissions on all the system files. If this is what happened, I think you must have accidentally done something other than deleting Examples.

Did you by any chance run a graphical app like nautilus with sudo rather than gksudo? That can cause these types of issues.

---

### Post by steve.horsley on 2007-05-17
No, that's not the issue. I have come to the conclusion that iis is something to do with the state of the cache. It does it if I open nautilus as the first thing I do after logging in after a reboot. It also happens after an extended time playing UT2004. I guess this also clears out the disk cache.

The icons all suddenly correct themselves as soon as I click into the filesystem, and if I have several nautilus windows open at once, they all fix their icons simultaneously. Once the icons have corrected themselves, it seems a long time before opening another nautilus gets it wrong again. This is what's making me think cache.

---

