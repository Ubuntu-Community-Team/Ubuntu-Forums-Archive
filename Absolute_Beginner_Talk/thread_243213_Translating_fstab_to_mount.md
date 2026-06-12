---
title: "Translating fstab to mount"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Sea Moose on 2006-08-24
Hi, I'm a complete newbie, but I'm trying to get a complete understanding of the mount statement. In my fstab, I have a statement that mounts my external usb hard drive, which is:

/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

I'm trying to get myself acquainted with the shell, and I don't want to have to rely on "sudo mount -a". Could anybody help me with translating the statement in fstab to what I should enter in the terminal? Thanks in advance..

---

### Post by LadyDoor on 2006-08-24
I don't mean this in a brush-off sort of way--you say you're new to the shell, and so this is general advice. The best advice I ever got about using non-GUI programs was "read the man page."

```
$ man programname
```

So you would enter **man mount** to pull up the **mount** manual. Manuals can be tedious, but they are a useful and educational resource and are readily available in most cases. I would help you out more, but that's the best I can do, I'm afraid.

--Door

---

### Post by 5-HT on 2006-08-24
With that entry in /etc/fstab the following should work:

i. To mount ```
 mount /media/sdb1 
``` ii. To unmount ```
 umount /media/sdb1 
```

---

### Post by Sea Moose on 2006-08-25
To LadyDoor & 5-HT

thanks guys. Apologies for the complete noobiness of me. I did try to look through the man 8 mount section, but I got completely lost. I just probably didn't look hard enough. Thanks to both of ye.. oh and LadyDoor, love the gouram "Shiny" :-D

---

### Post by anaconda on 2006-08-25
> **5-HT said:**
> With that entry in /etc/fstab the following should work:

i. To mount ```
 mount /media/sdb1 
``` ii. To unmount ```
 umount /media/sdb1 
```

Yes that will work, but ONLY if the entry is already in fstab. 

If you want to learn how to mount manually, I dont think you want to be able to mount only those partition, which are already in the fstab-file!

the whole command would be:
```

sudo mount -t ntfs /dev/sdb1 /media/sdb1 
```

And the 'sudo' is needed if the partition isn't listed in fstab -file. Only root can mount things that aren't mentioned in fstab

---

### Post by Sea Moose on 2006-08-25
Thanks Anaconda. What I was trying to figure out was how and where to place the options mentioned in the fstab statement into a mount statement.

---

### Post by anaconda on 2006-08-25
Do you mean these?

... defaults,nls=utf8,umask=007,gid=46 0 1

you dont have to put these to mount command.

It is enough to know filesystem type (can also be '-t auto') and "what to where" 

Root can change the access rights after mounting, by using chmod-command to give rights to normal user...

---

### Post by Sea Moose on 2006-08-25
Thanks Anaconda.

---

