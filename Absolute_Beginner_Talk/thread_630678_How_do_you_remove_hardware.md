---
title: "How do you remove hardware?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by mmccaule on 2007-12-03
How do you remove hardware in Gusty? When I installed Ubuntu my system had both a CD-RW and a DVD-ROM drive. Toady I replaced those 2 drives a single CD-RW/DVD-ROM. The new drive is recognized and fully functional. The problem is now when I look in Computer it still shows 2 drives. I've looked at the device manager and shows only 1 drive. What do I need to do to get it to show only 1 CD drive?

---

### Post by shadow-of-sin on 2007-12-03
To prevent the old drives from showing up just open up /etc/fstab file as root and remove the lines for the drives that you removed

---

### Post by mmccaule on 2007-12-03
SOF,

I've already tried that and the drive still shows?

---

### Post by ryanVickers on 2007-12-03
did you reboot afterwards? ;)  Normally rebooting isn't the Linux way, but... :p

---

### Post by mmccaule on 2007-12-04
rV,

Yes, I did reboot. From what I can see the only place the drive shows up is when you click on "Computer". Not a big issue, it's just odd to see a drive that's no longer on the system.

---

### Post by mmccaule on 2007-12-04
Well, I went back and edited fstab again and found that I had removed the wrong drive. I found this out by commenting out both drives. I did notice that with both drives commented out when I go to computer it still shows the one I have. Is it ok to leave fstab like that? Also, a reboot is not required to make the drive go away. Thanks for the help folks.

---

