---
title: "The Most Important Question"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-07-20
I've never need help like I need it right now. I decided to do a complete reinstallation of Ubuntu, and when I did it, the first time I reinstalled, it wouldn't start up, and I couldn't understand why, so I reinstalled again, and this time, Nautilus wouldn't start up. When after 30 minutes waiting for it to load, the GNOME desktop finally showed up, it took a whole 5 minutes to get started.
I believe the CD I installed it with was corrupted or something, I'm not sure, but I've been using Ubuntu for 2 monthes now, and it's never done this to me. I tried just a moment ago to use G-Parted to delete the partition, but it seems to refuse to be deleted. I tried using G-Parted, and it claimed it was deleted, and then upon attemptng to install Xubuntu, it suddenly popped up and said "LOCKED". :(
I don't know what's going on, but does anyone know anything I can do to fix this problem? I really don't want to have to reinstall no more, and it seems G-Parted isn't even working. I'm currently typing this off of a Xubuntu LiveCD.

Please help :(

-Brandon

---

### Post by tcoffeep on 2007-07-20
~Bump~

---

### Post by Daveth on 2007-07-20
the standard live cd has a file integrity checksum option in the main menu from memory, a bit below the install option, so if you can fire that up you can test your hypothesis about it being damaged somehow. Your partition locked message is a consequence of having a mounted partition which cannot be resized, hence why one does it with a live cd.
This
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

might be quite useful for you.
Have you got a separate /home partition? Makes the install option less terrifying as you data remains untouched.

---

### Post by tcoffeep on 2007-07-20
No. I don't.

I did check the file integrity and it worked out great, and about the partition locked message, I've already deleted the partition using the G-Parted LiveCD.

Another question; is it possible to use the Ubuntu/Xubuntu LiveCD to restore the kernel in case in somehow got damaged due to the installation. (perhaps the file integrity was fine, but scratches on the CD somehow allowed it to skip something?)

---

### Post by AlexenderReez on 2007-07-20
> **tcoffeep said:**
> No. I don't.

I did check the file integrity and it worked out great, and about the partition locked message, I've already deleted the partition using the G-Parted LiveCD.

Another question; is it possible to use the Ubuntu/Xubuntu LiveCD to restore the kernel in case in somehow got damaged due to the installation. (perhaps the file integrity was fine, but scratches on the CD somehow allowed it to skip something?)

it possible ...backup kernel is  initrd.img-2.6.22-8-generic.bak in /boot/.....it is mean that is previous kernel that works incase when you upgrade kernel,your system get broken cause of that...you can use livecd to copy this backup kernel somewhere else then rename with delete .bak become initrd.img-2.6.22-8-generic and paste at /boot folder back

:)

---

### Post by tcoffeep on 2007-07-20
If anyone would care to know, this is what comes up when Nautilus fails :

> ===== BEGIN MILESTONES =====
0x8187480 2007/07/20 02:10:53.0155 (GLog): Failed to activate daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
0x8187480 2007/07/20 02:21:44.0322 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:21:54.4722 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:04.9542 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:15.6476 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:26.1301 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:36.4581 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:47.0812 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:57.8723 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:08.2707 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:19.1046 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:29.7993 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:40.2251 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:50.6648 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:01.1033 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:11.3894 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:21.8714 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:32.3650 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:42.7642 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:53.0757 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:03.5155 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:13.9130 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:24.3232 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:34.7220 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:45.1477 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:55.6143 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:06.1527 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:16.5515 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:26.9068 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:37.2902 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:47.7286 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:58.1425 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:08.5688 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:19.0502 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:29.4194 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:39.8594 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:50.3135 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:00.7958 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:11.2628 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:21.7451 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:32.1850 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:42.6383 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:53.0907 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:03.5875 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:14.1124 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:24.6499 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:35.0912 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:45.5862 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:56.0693 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:06.8451 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:17.5248 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:28.0793 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:38.6594 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:49.0708 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:59.5088 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:10.0202 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:20.5445 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:30.9284 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:41.3967 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:52.1314 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:02.6556 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:13.0671 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:23.8882 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:34.4390 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:44.9218 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:55.3171 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:05.9272 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:16.4092 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:26.9334 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:37.6395 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:48.0383 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:58.7457 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:09.3390 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:19.9350 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:30.4452 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:41.0971 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:51.6496 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:02.3278 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:12.7103 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:23.2355 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:33.8570 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:44.3685 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:54.9068 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:05.5438 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:16.2377 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:27.0449 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:37.5821 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:48.4431 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:58.9687 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:09.6344 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:20.2568 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:30.6552 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:41.0517 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:51.5483 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:02.1988 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:13.3131 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:23.8808 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:34.4616 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:45.0410 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:55.6512 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:06.0344 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:16.6157 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:27.1111 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:37.4949 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:48.0046 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:58.5993 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:09.2082 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:19.5913 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:30.0858 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:40.6378 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:51.1211 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:01.5468 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:12.1119 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:22.6387 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:33.1623 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:43.7716 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:54.4078 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:04.9739 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:15.3995 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:25.9660 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:36.4057 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:46.8300 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:57.3415 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:07.9786 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:18.5450 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:28.8437 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:39.2130 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:49.6386 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:00.0924 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:10.5745 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:21.0011 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:31.3270 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:41.7103 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:52.2345 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:02.7024 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:13.0717 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:23.6228 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:34.0779 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:44.4189 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:54.7037 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:05.3688 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:15.8367 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:26.5005 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:36.8851 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:47.2133 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:57.7358 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:08.1195 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:18.4897 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:28.8025 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:39.1864 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:49.6394 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:59.9672 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:10.2801 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:20.7606 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:31.2709 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:41.8079 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:52.1362 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:02.5337 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:12.9311 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:23.2722 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:33.6133 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:44.0798 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:54.3958 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:04.7218 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:15.0621 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:25.4300 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:35.8026 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:46.1438 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:56.4687 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:06.8507 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:17.2212 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:27.7019 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:38.0172 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:48.5121 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:59.4884 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:09.8417 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:20.2266 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:30.5540 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:40.9506 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:51.3341 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:01.7750 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:12.1291 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:22.4846 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:32.8535 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:43.1950 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:53.7333 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:04.1290 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:14.5269 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:24.8963 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:35.2656 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:45.8026 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:56.1591 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:06.5565 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:16.9808 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:27.3232 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:37.6783 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:48.0758 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:58.4445 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:08.7163 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:19.0435 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:29.4267 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:39.7264 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:49.9820 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:01.0545 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:12.0450 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:23.1190 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:33.4585 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:43.8573 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:54.2973 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:04.6237 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:15.0775 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:25.4318 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:35.7734 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:46.0587 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:56.5253 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:06.8254 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:17.1663 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:27.4507 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:37.8624 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:48.1618 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:58.4748 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:08.9136 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:19.2129 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:29.5117 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:39.9926 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:50.3753 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:00.6623 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:11.0168 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:21.3443 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:31.6981 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:42.0403 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:52.4509 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:02.8335 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:13.3024 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:23.6157 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:34.0263 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:44.4379 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:54.8066 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:05.2749 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:15.6168 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:25.9864 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:36.3252 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:46.6543 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:56.9676 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:07.2555 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:17.6472 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:27.9614 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:38.2321 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:48.6141 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:58.9411 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:09.2560 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:19.5699 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:29.8957 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:40.1523 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:50.4505 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:00.7494 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:11.1736 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:21.5579 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:32.5908 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:42.9033 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:53.2871 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:07:03.6143 (USER): debug log dumped due to signal 7
===== END MILESTONES =====
===== BEGIN RING BUFFER =====
0x8187480 2007/07/20 02:10:53.0155 (GLog): Failed to activate daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
0x8187480 2007/07/20 02:14:29.6302 (USER): window 0x8209030 open location: old="(none)", new="x-nautilus-desktop:"
0x8187480 2007/07/20 02:14:31.9663 (USER): finished loading window 0x8209030: x-nautilus-desktop:
0x8187480 2007/07/20 02:21:33.4313 (USER): create new navigation window=0x81ef5f8
0x8187480 2007/07/20 02:21:33.4314 (USER): window 0x81ef5f8 open location: old="(none)", new="file:///home/larocque"
0x8187480 2007/07/20 02:21:44.0322 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:21:54.4722 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:04.9542 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:15.6476 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:26.1301 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:36.4581 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:47.0812 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:22:57.8723 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:08.2707 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:19.1046 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:29.7993 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:40.2251 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:23:50.6648 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:01.1033 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:11.3894 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:21.8714 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:32.3650 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:42.7642 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:24:53.0757 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:03.5155 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:13.9130 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:24.3232 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:34.7220 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:45.1477 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:25:55.6143 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:06.1527 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:16.5515 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:26.9068 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:37.2902 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:47.7286 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:26:58.1425 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:08.5688 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:19.0502 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:29.4194 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:39.8594 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:27:50.3135 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:00.7958 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:11.2628 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:21.7451 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:32.1850 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:42.6383 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:28:53.0907 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:03.5875 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:14.1124 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:24.6499 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:35.0912 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:45.5862 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:29:56.0693 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:06.8451 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:17.5248 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:28.0793 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:38.6594 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:49.0708 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:30:59.5088 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:10.0202 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:20.5445 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:30.9284 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:41.3967 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:31:52.1314 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:02.6556 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:13.0671 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:23.8882 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:34.4390 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:44.9218 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:32:55.3171 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:05.9272 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:16.4092 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:26.9334 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:37.6395 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:48.0383 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:33:58.7457 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:09.3390 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:19.9350 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:30.4452 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:41.0971 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:34:51.6496 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:02.3278 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:12.7103 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:23.2355 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:33.8570 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:44.3685 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:35:54.9068 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:05.5438 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:16.2377 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:27.0449 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:37.5821 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:48.4431 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:36:58.9687 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:09.6344 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:20.2568 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:30.6552 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:41.0517 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:37:51.5483 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:02.1988 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:13.3131 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:23.8808 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:34.4616 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:45.0410 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:38:55.6512 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:06.0344 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:16.6157 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:27.1111 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:37.4949 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:48.0046 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:39:58.5993 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:09.2082 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:19.5913 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:30.0858 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:40.6378 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:40:51.1211 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:01.5468 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:12.1119 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:22.6387 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:33.1623 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:43.7716 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:41:54.4078 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:04.9739 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:15.3995 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:25.9660 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:36.4057 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:46.8300 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:42:57.3415 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:07.9786 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:18.5450 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:28.8437 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:39.2130 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:43:49.6386 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:00.0924 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:10.5745 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:21.0011 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:31.3270 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:41.7103 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:44:52.2345 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:02.7024 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:13.0717 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:23.6228 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:34.0779 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:44.4189 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:45:54.7037 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:05.3688 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:15.8367 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:26.5005 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:36.8851 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:47.2133 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:46:57.7358 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:08.1195 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:18.4897 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:28.8025 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:39.1864 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:49.6394 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:47:59.9672 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:10.2801 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:20.7606 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:31.2709 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:41.8079 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:48:52.1362 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:02.5337 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:12.9311 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:23.2722 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:33.6133 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:44.0798 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:49:54.3958 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:04.7218 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:15.0621 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:25.4300 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:35.8026 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:46.1438 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:50:56.4687 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:06.8507 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:17.2212 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:27.7019 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:38.0172 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:48.5121 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:51:59.4884 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:09.8417 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:20.2266 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:30.5540 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:40.9506 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:52:51.3341 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:01.7750 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:12.1291 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:22.4846 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:32.8535 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:43.1950 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:53:53.7333 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:04.1290 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:14.5269 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:24.8963 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:35.2656 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:45.8026 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:54:56.1591 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:06.5565 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:16.9808 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:27.3232 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:37.6783 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:48.0758 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:55:58.4445 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:08.7163 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:19.0435 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:29.4267 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:39.7264 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:56:49.9820 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:01.0545 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:12.0450 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:23.1190 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:33.4585 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:43.8573 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:57:54.2973 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:04.6237 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:15.0775 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:25.4318 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:35.7734 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:46.0587 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:58:56.5253 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:06.8254 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:17.1663 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:27.4507 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:37.8624 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:48.1618 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 02:59:58.4748 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:08.9136 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:19.2129 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:29.5117 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:39.9926 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:00:50.3753 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:00.6623 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:11.0168 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:21.3443 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:31.6981 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:42.0403 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:01:52.4509 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:02.8335 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:13.3024 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:23.6157 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:34.0263 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:44.4379 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:02:54.8066 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:05.2749 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:15.6168 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:25.9864 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:36.3252 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:46.6543 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:03:56.9676 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:07.2555 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:17.6472 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:27.9614 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:38.2321 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:48.6141 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:04:58.9411 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:09.2560 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:19.5699 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:29.8957 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:40.1523 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:05:50.4505 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:00.7494 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:11.1736 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:21.5579 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:32.5908 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:42.9033 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:06:53.2871 (USER): debug log dumped due to signal 7
0x8187480 2007/07/20 03:07:03.6143 (USER): debug log dumped due to signal 7
===== END RING BUFFER =====


This configuration for the debug log can be re-created
by putting the following in ~/nautilus-debug-log.conf
(use ';' to separate domain names):


[debug log]
max lines=1000


Any ideas what it means?

---

### Post by Daveth on 2007-07-20
I suppose you could but in the instance of rogue and random errors, who knows what else might have got taken out. In light of that I would do a complete build, make yourself a /home beforehand which you will never regret and start afresh. I must say I had problems with Gparted on the Feisty live cd, especially on my SATA disk, and ended up using my Dapper live cd to set up the partitions.
This
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

is invaluable for /home setup.

---

### Post by tcoffeep on 2007-07-20
Thanks for the linkage, I'll be sure to check it out, once I figure out all this mess :)

---

### Post by tcoffeep on 2007-07-20
Upon installation, this is what pops up :

> The ext3 file system creation in partition #1 of IDE1 master (hda) failed.

After that pops up, I push OK and it sends me back to partition tables. (I clicked on use entire drive this time to test it out). Forgot to mention that when the little error message pops up, so does a file package called disk. In it is : etc, initrd, lost+found, opt, root, sbin, var, cdrom, initrd.img, and finally vmlinuz. Any idea why this folder pops up during installation?

---

### Post by tcoffeep on 2007-07-20
bump

---

### Post by tcoffeep on 2007-07-20
Well, I guess noone responded. But the faithful Ubuntu gods were looking down on me, and I guess they pitied me. After the fifth reinstallation, it worked :)

---

### Post by darren1270 on 2007-07-20
Congrats on getting up and running again.  I may have gone about this a little different.

1.  You may have a failing HD.
2.  With all the failed attempts I would have used killdisk you can get it by following this link [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm) this will wipe out all data on your drive thus leaving you with a clean slate to start with.  
3. By all means use the link mentioned above to create a seperate /home partition.  It'll make life easy if something goes wrong.

Just my 2 cents work...LOL

Have A Good One!
Darren

---

