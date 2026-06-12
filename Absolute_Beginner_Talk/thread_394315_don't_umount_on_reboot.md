---
title: "don't umount on reboot"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by sushii. on 2007-03-26
Is there any way that I can stop a file from umounting on reboot/shutdown? Thanks. If you need any more info just tell me (obviously).

---

### Post by sushii. on 2007-03-26
bummmp.. I really need help!

---

### Post by dacool25 on 2007-03-26
do you mean a hard drive from unmounting?

If so, you'll have to mess around with the fstab file.  Its located in /etc/fstab.  I'd also reccomend you search the forums for some help, you might be able to get a more exact procedure.

---

### Post by sushii. on 2007-03-26
Actually I'm trying to install windows vista through an ISO, so  I need the iso mounted at boot. Like, a virtual disk drive.

EDIT: Not install windoez over ubuntu, just on a seperate partition to screw around with.

---

### Post by sushii. on 2007-03-26
bumpz.

---

### Post by sushii. on 2007-03-27
anyone?

---

### Post by benfindlay on 2007-03-27
As far as I know it won't work. In order to mount an iso you have to boot the operating system responsible for mounting it. Perhaps someone else can correct me if I am wrong, but I think you will simply have to burn it to disc and then install it.

---

### Post by sushii. on 2007-03-27
Ok, thanks.

---

### Post by sushii. on 2007-04-24
Bump. Is there any way at all? I don't have a DVD burner and I don't have any blank discs.

---

### Post by sushii. on 2007-04-25
Bump

---

### Post by Amenemhet on 2007-04-25
Sushi, your being all that clear...do you want to boot to vista after booting to linux? If so download the linux version of VMWare or one of the other emulators. Then point the 'virtual' cd drive to where the ISO is and boot from that in VMWare.
Otherwise no, you must burn the iso to disk.
Vista is pretty resource heavy, and unless you have at least the minimum specs (at the very least) I wouldnt bother trying through a virtual machine. It will be slow as molasses.

---

### Post by NicoleM on 2007-04-25
looks like you already have your answer.  there's no way you can mount an ISO if you're not booted into an OS.  mounting is something that can't be done while the computer is off.

you don't have your original vista dvd still?  if not, then your best bet is to borrow a vista disc from a friend and use your own serial (probably still not legal by microsoft standards so do so at your own risk) or send your backup image to a friend to burn for you.

---

