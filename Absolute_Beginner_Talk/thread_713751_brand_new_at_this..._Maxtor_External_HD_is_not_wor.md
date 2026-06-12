---
title: "brand new at this... Maxtor External HD is not working?!... HELP"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by christabel3000 on 2008-03-03
Just got Ubuntu and I really am totally new at this.
Trying to get the bugs out and a big one is my Maxtor External HD with all my pics and music is not working.
It's a One Touch III
Do I need a magic spell or something?

---

### Post by hyper_ch on 2008-03-03
I guess the format of the drive is NTFS and I guess you did not plug it in while installing Ubuntu?

---

### Post by smo0th on 2008-03-11
I have the same problem with the exact same hdd, is there any workaround for this? :3

---

### Post by smo0th on 2008-03-11
Okay folks, I jut mounted my 750 gb maxtor one touch III :)

first of all, I connected the drive and received a 'Cannot mount volume' msg, then I went and read the details, it suggest to do the following:

mount -t ntfs-3g /dev/sdb5 /media/Maxtor -o force

so I did:
sudo mount -t ntfs-3g /dev/sdb5 /media/Maxtor -o force

it shows:
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Maxtor: No such file or directory

I waited a couple of minutes checking email then I saw it was mounted, so I clicked to open the drive and it works sweet~ :guitar:

P.S. You may also want to add "/dev/sdb5 /media/Maxtor ntfs-3g defaults,force 0 0" to your /etc/fstab file =)

---

### Post by Tews on 2008-03-11
I had this problem with my Maxtor 500GB usb drive after a BSOD crash in Vista.  I rebooted Vista, then shut down then booted back into Ubunto.  That solved everything.  Moral of the story,  dont use Vista!  :lolflag:

---

