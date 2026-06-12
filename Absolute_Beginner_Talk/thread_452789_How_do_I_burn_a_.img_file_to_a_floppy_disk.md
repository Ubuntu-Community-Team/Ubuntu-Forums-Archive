---
title: "How do I burn a .img file to a floppy disk?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-05-23
This is the command I have:

```

dd if=boot.img of=/dev/fd0 bs=1440k

```

and I get:

```

dd: opening `/dev/fd0': Read-only file system

```


:(


Any ideas here?

---

### Post by Sparkster185 on 2007-05-23
Why can't you just drag and drop it using the GUI?

---

### Post by steve.horsley on 2007-05-23
try:
**sudo dd if=whatever.img of=/dev/fd0**

---

### Post by ubunik on 2007-05-23
Has the floppy got its write protact tab open?

---

### Post by Neon_Knight on 2007-05-23
@Sparkster
no, that just saves the image file onto the floppy, I want to burn the image to the disk.

(I presume they are different?)

@Steve
That's exactly what I did afterwards. It didn't work.

@ Ubunik
Nope, it doesn't.

---

### Post by Neon_Knight on 2007-05-23
Come on, pleeeeeeeeasssssssssseeeeeeeeeeeeeeeeee somebody reply

=[

I need to fix my GRUB really really badly...

---

### Post by jfinkels on 2007-05-23
> **Neon_Knight said:**
> Come on, pleeeeeeeeasssssssssseeeeeeeeeeeeeeeeee somebody reply

=[

I need to fix my GRUB really really badly...

What are the permissions on /dev/fd0? Type the following:
```

ls -l /dev/fd0

```

You may not have proper permissions to perform that operation on this device.

---

### Post by Neon_Knight on 2007-05-23
```

brwxrwxrwx 1 root floppy 2, 0 2007-05-23 19:17 /dev/fd0

```

Seems fine to me...

---

### Post by Neon_Knight on 2007-05-23
Any thoughts?

---

### Post by jfinkels on 2007-05-24
> **Neon_Knight said:**
> Any thoughts?

Beats me. Is there another program out there that can burn .img files to floppy disks? Take a look around.

---

### Post by wormser on 2007-05-24
> **Neon_Knight said:**
> @Sparkster
no, that just saves the image file onto the floppy, I want to burn the image to the disk.

(I presume they are different?)

@Steve
That's exactly what I did afterwards. It didn't work.

@ Ubunik
Nope, it doesn't.

Yes saving and creating an image are different.  By the way, it is not 1995.  Why are you using a floppy?  Why don't you just burn it to a CD?  

Sorry I cannot help you because I don't know.  [This]("http://articles.techrepublic.com.com/5100-6345-5034501.html") might work, I did not read it.

---

### Post by Neon_Knight on 2007-05-24
> **jfinkels said:**
> Beats me. Is there another program out there that can burn .img files to floppy disks? Take a look around.

Well I don't know =[[

There's a reason I'm in the "Absolute Beginner's Forums"...

I tried googling it, but it just keeps coming up with download links to linux distros.

@Wormster: My cd drive is broken. I could take the hassle of taking out of my other computer and putting it in here and booting with it and then burning a CD and booting from that,but I thought it'd just be simpler to do it this way.

But maybe not...I seem to remember having trouble booting from USB floppies..

and I tried that link, but all of the download links return a 404.

---

### Post by tkjacobsen on 2007-05-24
In order to use dd the device has to be unmounted and you have to use sudo...


#sudo umount /dev/fd0 
#mount            % to make sure it is unmounted
#sudo dd if=boot.img of=/dev/fd0

---

### Post by Neon_Knight on 2007-05-24
```

david@david-desktop:~/Desktop/Stuff$ sudo unmount /dev/fd0
Password:
sudo: unmount: command not found

david@david-desktop:~/Desktop/Stuff$ sudo dd if=boot.img of=/dev/fd0 bs=1440k
dd: opening `/dev/fd0': Read-only file system

```

No dice, son.

```

david@david-desktop:~/Desktop/Stuff$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-686/volatile type tmpfs (rw)
/dev/hda2 on /media/hda2 type fuse (rw,nosuid,nodev,noatime,allow_other)
/dev/sda on /media/floppy type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=david)

```

somehow, I don't think it's mounted...

---

### Post by Rinzwind on 2007-05-24
It's umount not unmount :)


edit: hmm both appear to work. Cool :D

---

### Post by Neon_Knight on 2007-05-24
Oh god...


I feel like an idiot =[

edit:

okay, here's the result:

```

david@david-desktop:~/Desktop/Stuff$ sudo umount /dev/fd0
umount: /dev/fd0: not mounted
david@david-desktop:~/Desktop/Stuff$ sudo dd if=boot.img of=/dev/fd0 bs=1440k
dd: opening `/dev/fd0': Read-only file system

```

I was right, it wasn't mounted.


Does the fact that it's a USB floppy change anything?

---

### Post by Neon_Knight on 2007-05-24
Okay, I just solved two problems at the same time.

I managed to burn the img to sda instead of fd0 (I found out somehow that it was there instead)

And, when I restarted to use the floppy, I noticed that my keyboard was infact plugged into the mouse plug, which was causing the GRUB problem all along so I didn't need it anyway. :D

Thanks, guys.

---

### Post by jfinkels on 2007-05-24
> **Neon_Knight said:**
> Okay, I just solved two problems at the same time.

I managed to burn the img to sda instead of fd0 (I found out somehow that it was there instead)

And, when I restarted to use the floppy, I noticed that my keyboard was infact plugged into the mouse plug, which was causing the GRUB problem all along so I didn't need it anyway. :D

Thanks, guys.

Burning the image to /dev/sda does the data dump directly to your hard drive, which is not advisable, because it may overwrite some crucial information. Oh well.

Also, a hint on unmounting: you should use ```
umount /path/to/mountpoint
``` where */path/to/mountpoint* is the directory at which the drive is mounted. Read more about umount and mount and dd like this:
```

man mount
man umount
man dd

```

---

### Post by psusi on 2007-05-24
Outch, yea... you hosed up your hard disk by doing that. As for the floppy, it seems to think the write protect tab is open.

---

### Post by compmodder26 on 2007-05-24
It seems that the OP has resolved the problem which would suggest that he/she has not hosed his/her system.  I would venture a guess that the hard drive is an IDE device and would be using the identifier /dev/hda instead of /dev/sda.  The floppy drive, being a USB device would thus be given a device name of /dev/sda instead of the typical /dev/fd0 given to ide floppy drives.

---

### Post by dannyboy79 on 2007-05-24
very true! he told us it was a usb drive also. this would be simple to fix, he just needs to change the symlink in /dev/ and or his fstab so that it's fd0 if he wants that is. since he'll always having people tell hiim fd0 which is where almost everyones floppy is since I didn't even know they made usb floppies. he he he 
And to the person that said, it's not 1955, use a cd. I only have 1 thing to say to that, next time some1 asks for help, help them if you're going to post or don't post at all. It wastes space on the servers, waste's people time having to read an unhelpful comment and also people who get emails when some1 posts here don't want to read your comment if it isn't helpful in anyway.

---

### Post by jfinkels on 2007-05-24
> **compmodder26 said:**
> It seems that the OP has resolved the problem which would suggest that he/she has not hosed his/her system.  I would venture a guess that the hard drive is an IDE device and would be using the identifier /dev/hda instead of /dev/sda.  The floppy drive, being a USB device would thus be given a device name of /dev/sda instead of the typical /dev/fd0 given to ide floppy drives.

You're very right, sorry! I'm unobservant.

To make a symbolic link from /dev/fd to /dev/sda, as the above poster suggests, type the following:
```

sudo ln -s /dev/sda /dev/fd

```

---

### Post by eldragon on 2007-05-28
did you try with a different diskette? or even a different FDD?

have you tried reading anything from the FDD? did it succeed?

---

### Post by CafeRay on 2008-05-29
> **eldragon said:**
> did you try with a different diskette? or even a different FDD?

have you tried reading anything from the FDD? did it succeed?

Try this website:
[http://www.debian.org/releases/stable/powerpc/ch04s03.html.en](http://www.debian.org/releases/stable/powerpc/ch04s03.html.en)

Windows Application:
[http://www.winimage.com/winimage.htm](http://www.winimage.com/winimage.htm)

---

### Post by Joeb454 on 2008-05-29
I'm not 100% sure people from March 2007 will need a response now (though I could be wrong ;))

---

### Post by bapoumba on 2008-05-30
No need to keep bumping old threads :)

---

