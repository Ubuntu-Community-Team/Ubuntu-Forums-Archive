---
title: "Problem with HP 1020 printer."
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-04-18
I bought a new HP 1020 laser printer some weeks ago.  It works flawlessly in Win XP partition and I could even do a perfect test print on Ubuntu.

But this week when I tried to print on Ubuntu nothing happens.  How can I make it work?
I think it has something to do with me updating the latest suggested Linux kernel via Synaptic.  I'm not really sure if it's true.
But I don't know what else to do, other than boot into good OL' Windows XP and print my stuff.  But then I would have yet another factor keep me addicted to Micro$oft.

What can I do? :(

---

### Post by xboxbman on 2007-04-18
> **jingo811 said:**
> I bought a new HP 1020 laser printer some weeks ago.  It works flawlessly in Win XP partition and I could even do a perfect test print on Ubuntu.

But this week when I tried to print on Ubuntu nothing happens.  How can I make it work?
I think it has something to do with me updating the latest suggested Linux kernel via Synaptic.  I'm not really sure if it's true.
But I don't know what else to do, other than boot into good OL' Windows XP and print my stuff.  But then I would have yet another factor keep me addicted to Micro$oft.

What can I do? :(

Does ubuntu "see" the printer.  Go to System>Administration>Printing and click on add new printer.  Should work.

---

### Post by jingo811 on 2007-04-19
Yeah it can see the printer and the printer popup thingy comes out but it just says sending file to printer indefinitely with the printer not moving an inch. 

I'm using the: HP, Laserjet 1020, foo2zjs (recommended) (Suggested) driver).
Printer Type: Local Printer.
But still the printer doesn't respond.

Maybe I should uninstall it and re-install since I had another Canon printer on before which was connected as Network printer.....
......OK I uninstalled all printers on Ubuntu rebooted re-installed at least twice.  Trying to use the
HP 1020 and HP 1022 drivers still nothing the printer won't move :-(

I tried to find some *.ppd files on the HP CD but didn't find any.  What else can I do?

---

### Post by mmikee66 on 2007-04-19
What is in your System-> administion->system logs -> cups error log?

I have the same problem with a HP1000 and it refuses to pring even though it sees the printer in the printer manager. The cheap HP that do not contain their own firmware (is part of the driver I believe is how they do it) have historical problems with not working often for unknown reasons.

Mine was also working until the last bug regarding the libimage file and has never came back on line even though the bug fix seemed to work for 99% of the people. My HP1000 just refuses to print in Ubuntu. I have Xandros and Suse installs that both print to it but Ubuntu just hates it.

---

### Post by jingo811 on 2007-04-19
/var/log/cups/error_log (monitored)

displays this long list:
```

[COLOR="Red"]E [19/Apr/2007:07:38:58 +0200] CUPS-Delete-Printer: Unauthorized[/COLOR]
E [19/Apr/2007:07:39:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:39:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:39:37 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:39:42 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:39:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:39:52 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:39:57 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:07 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:22 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:37 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:42 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:52 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:40:57 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:02 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:07:41:05 +0200] CUPS-Add-Modify-Printer: Unauthorized[/COLOR]
E [19/Apr/2007:07:41:07 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:07 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:10 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:10 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:22 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:22 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:37 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:37 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:07:41:40 +0200] [Job 42] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:07:41:42 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:42 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:52 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:52 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:57 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:41:57 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:00 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:06 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:07 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:07 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:09 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:09 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:09 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:07:42:10 +0200] [Job 43] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:07:42:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:12 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:15 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:15 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:15 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:18 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:21 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:21 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:21 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:22 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:22 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:37 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:37 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:42:38 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:07:42:38 +0200] Pause-Printer: Unauthorized
E [19/Apr/2007:07:44:17 +0200] Creating missing directory "/var/run/cups/certs"
E [19/Apr/2007:07:45:13 +0200] Resume-Printer: Unauthorized
E [19/Apr/2007:07:45:20 +0200] [Job 44] No %%BoundingBox: comment in header!
E [19/Apr/2007:07:46:19 +0200] [Job 45] No %%BoundingBox: comment in header!
E [19/Apr/2007:07:48:08 +0200] Creating missing directory "/var/run/cups/certs"
E [19/Apr/2007:07:49:22 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Apr/2007:07:49:54 +0200] [Job 46] No %%BoundingBox: comment in header!
E [19/Apr/2007:07:55:03 +0200] CUPS-Delete-Printer: Unauthorized
E [19/Apr/2007:07:56:21 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Apr/2007:07:57:26 +0200] [Job 47] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:07:58:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:58:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:58:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:58:27 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:58:28 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:07:58:28 +0200] cupsdAuthorize: Local authentication certificate not found!
.....
.....
.....
E [19/Apr/2007:08:02:33 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:36 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:42 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:08:02:42 +0200] [Job 48] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:08:02:43 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:43 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:45 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:45 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:45 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:51 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:51 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:51 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:56 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:02:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:04 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:04 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:05 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:09 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:09 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:11 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:08:03:14 +0200] [Job 49] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:08:03:14 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:14 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:20 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:26 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:08:03:27 +0200] [Job 50] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:08:03:29 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:29 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:29 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:29 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:29 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:35 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:35 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:35 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:08:03:38 +0200] [Job 51] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:08:03:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:41 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:41 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:41 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:44 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:44 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:44 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:08:03:47 +0200] [Job 52] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:08:03:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:47 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:49 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:49 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:50 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:54 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:56 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:03:59 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:04 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:04 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:05 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:05 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:05 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:09 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:09 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:11 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:11 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:11 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:14 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:14 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:14 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:08:04:15 +0200] [Job 53] No %%BoundingBox: comment in header![/COLOR]
E [19/Apr/2007:08:04:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:20 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Apr/2007:08:04:26 +0200] cupsdAuthorize: Local authentication certificate not found!
[COLOR="Red"]E [19/Apr/2007:09:30:11 +0200] Creating missing directory "/var/run/cups/certs"
E [19/Apr/2007:11:51:30 +0200] Creating missing directory "/var/run/cups/certs"
E [19/Apr/2007:13:25:40 +0200] Creating missing directory "/var/run/cups/certs"[/COLOR]
```

---

### Post by olofcadiz on 2007-04-20
I have the same problem with my HP 1200 laserjet
After last update the printer did not print out
Then I tried with another computer with ubuntu 6.10 but not updated.
With this computer there where no problems to print out.
Before changing computer I tried to reinstall the HP 1200 on different ways.
There where no solution for the updated ubuntu 6.10
Updating is very handy but also risky son now I use my old slackware linux instead.

---

### Post by jingo811 on 2007-04-20
Hmm..so is there a way to revert back to the previous kernel version without breaking too much configurations in Ubuntu?

---

### Post by eyelessfade on 2007-04-20
if you haven't deleted the old kernel it should be there. you can just boot from it with grub

---

### Post by kitch on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/65618](https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/65618) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same problem. Searched google and I have found this and followed the link but really have no idea where to start!

[http://kirksblog.steffensenfamily.com/archives/13](http://kirksblog.steffensenfamily.com/archives/13)

also found a bug report but again as a new user am completely confused

:confused:

---

### Post by jingo811 on 2007-04-21
Nice googling kitch, your future with Linux will be bright I can tell! =D>
[http://kirksblog.steffensenfamily.com/archives/13](http://kirksblog.steffensenfamily.com/archives/13)
I'll follow the instructions later and donate even don't have time right now.  But the instructions are class A.

**@kitch**
Just follow the white rabbit man!  And when you come to the Download and Install section use the program [COLOR="Red"]TERMINAL[/COLOR] to copy and paste the suggested commands:
 > 
Download and Install

   Click the link, or cut and paste the whole command line below to download the driver.

          ```
  jingo811@ubuntu:~$ **wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz**
```

....yadda....
....yadda....
....yadda....


---

### Post by ubu-for on 2007-05-01
We have the same problem [here](http://ubuntuforums.org/showthread.php?p=2572163#post2572163).

```

$ cd foo2zjs
$ sudo make uninstall
$ make
$ sudo make install install-hotplug cups
$ sudo gnome-cups-manager
$ sudo make cups

```

```

E [01/May/2007:17:52:46 +0200] CUPS-Delete-Printer: Unauthorized
E [01/May/2007:17:56:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:56:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:56:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:56:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:56:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:56:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:56:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:08 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:13 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:13 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:13 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:13 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:18 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:18 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:18 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:18 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:28 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:28 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:28 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:28 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:33 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:33 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:33 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:33 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:43 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:43 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:43 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:43 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:48 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:53 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:57:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:58:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:58:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:58:03 +0200] cupsdAuthorize: Local authentication certificate not found!
E [01/May/2007:17:58:05 +0200] cupsdAuthorize: Local authentication certificate not found!

```

It's not working! What's wrong?

Thank you very much!

---

### Post by xlinuks on 2007-08-10
Pitty that it ain't working in Fiesty either, although there are open source, free and working drivers on the net. Hopefully the developers pay attention to this by the release of Gutsy Gibbon.

---

### Post by Maxtorm on 2007-08-12
This printer works on Feisty using these directions:
[http://benaiah41.wordpress.com/2007/07/06/installing-a-hp-laserjet-1020-on-ubuntu-feisty/](http://benaiah41.wordpress.com/2007/07/06/installing-a-hp-laserjet-1020-on-ubuntu-feisty/)

The short version:
```

$ sudo apt-get install build-essential
 $ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
 $ tar -zxvf foo2zjs.tar.gz
 $ cd foo2zjs
 $ sudo make uninstall
 $ make
 $ ./getweb 1020
 $ sudo make install install-hotplug cups
```

---

### Post by jingo811 on 2007-08-13
Just the fix I was looking for tnx hopefully I won't have to boot into Win XP just to print anymore...

---

### Post by dugh on 2007-08-13
According to this the hp 1020 isn't supported by hplip unfortunately, although the 1022 is:
[http://hplip.sourceforge.net/supported_devices/laser.html](http://hplip.sourceforge.net/supported_devices/laser.html)

Anyone recommend a good cheap black & white laser printer to use with ubuntu?  Is the 1022 working fine for people?

---

### Post by Pish on 2007-08-15
Hi strangly im also having these same problems after following these instructions. Even after I follow them im still getting the certificate error in the CUPS logs. 

And when I go to print the job appears in cups job logs then disappears into thin air. However the printer has just been sitting idle and nothing happens. 

Where should I look to see whats going on? 

some logs from cups error log 

```
E [16/Aug/2007:11:06:41 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:43 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:43 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:43 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:46 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:46 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:46 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:49 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:49 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:49 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:51 +1000] cupsdAuthorize: Local authentication certificate not found!
E [16/Aug/2007:11:06:51 +1000] cupsdAuthorize: Local authentication certificate not found!
```

its pretty much only that and even when im not doing anything it just keeps generating those lines

From lpr.log

```
Aug 16 10:00:46 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:00:56 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:00:56 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:03:23 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:03:27 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:03:27 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:11:03 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:11:07 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:11:07 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:11:33 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:11:37 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:11:37 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:12:43 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:12:48 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:12:48 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:16:33 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:16:36 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:16:36 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:18:49 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:18:53 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:18:53 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:25:18 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:25:23 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:25:23 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:26:04 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:26:07 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:26:07 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:29:29 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:29:33 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw  
Aug 16 10:29:33 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:34:48 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:34:51 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Aug 16 10:34:51 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:36:14 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:36:18 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Aug 16 10:36:18 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:49:43 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:49:46 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Aug 16 10:49:46 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:50:03 andrews foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1
Aug 16 10:50:06 andrews foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Aug 16 10:50:06 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 
Aug 16 10:50:25 andrews foo2zjs-wrapper: foo2zjs-wrapper -L0 -z1 testpage.ps
Aug 16 10:50:26 andrews foo2zjs-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Aug 16 10:50:26 andrews foo2zjs-wrapper: foo2zjs -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0      
```

Some more output
```

$ sudo grep DeviceURI /etc/cups/printers.conf
Password:
DeviceURI usb://HP/LaserJet%201020

```

I am at a total loss here ....

---

### Post by ramjet_1953 on 2007-08-15
I have had succes with HP printers, if instead of just using the Add Printer function, I use [COLOR="Red"]hp-toolbox[/COLOR].

This is a part of the [COLOR="Blue"]hplip[/COLOR] package.

You also need to install  [COLOR="Blue"]python-qt3[/COLOR] to use it.

Check, using the Synaptic Package manager if the following packages are installed:

[COLOR="Blue"]hpijs
hplip
hplip-data
python-qt3[/COLOR]

Once all of that is installed, use the standard print manager to remove your printer first.
Look in [COLOR="Blue"]System>Preferences[/COLOR] for [COLOR="Blue"]HPLIP Toolbox[/COLOR] and click on it. It will then guide you through your printer install.

If the item isn't listed in your menus, just type [COLOR="Red"]hp-toolbox[/COLOR] in a terminal.

I hope that this helps.

Regards,
Roger :cool:

---

### Post by Pish on 2007-08-16
Hrmmmm, This is really quite strange... 

I NEEDED to print something and i had a gutsy gibbon Tribe 4 cd on hand so i thought i would give it a whirl on there. 

Strangely no joy there either, (keeping in mind it worked fine on Ubuntu 6.10) 

After mucking about with the beryl settings because ... well just because i could... I rebooted back into Ubuntu 7.04 while booting the printer decided that it wanted to initialise. 

This is after numerous reboots - driver playing - turning on and off the printer etc. 

It just printed a page out of firefox ... so I have no idea.... WHY it wasn't working before. 

Anyway im not going to argue. It works. 

Oh and I think the HP tools your referring to don't support the 1020.

---

### Post by jingo811 on 2007-08-16
> This printer works on Feisty using these directions:
[http://benaiah41.wordpress.com/2007/...ubuntu-feisty/](http://benaiah41.wordpress.com/2007/...ubuntu-feisty/)

The short version:

```
$ sudo apt-get install build-essential
 $ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
 $ tar -zxvf foo2zjs.tar.gz
 $ cd foo2zjs
 $ sudo make uninstall
 $ make
 $ ./getweb 1020
 $ sudo make install install-hotplug cups
```


Nope that didn't work for me :( and on top of things I can't delete/remove the printer the ( - ) minus symbol is transparent and unclickable.
....
....
....
Ah now I see you had to become administrator to remove the printer.  Now I'll try that other suggested fix.....

---

### Post by jingo811 on 2007-08-16
Correction the above CLI procedure does indeed work.  I just chose the wrong USB connection there was 2 my first try I chose HPLIP something it didn't work.  Then I chose the other USB conncection with no specific name it worked :lolflag:

---

### Post by 56phil on 2007-08-16
I just bought a HP 1020 less than two weeks ago because of my past success with HP printers on Linux.

It works great so far on both fiesta and vista. [COLOR="Red"]So far[/COLOR] so well.

Thanks for the heads up.

---

### Post by toro430 on 2007-08-23
I was having the same problem with my HP Laserjet 1020 connected to a Feisty box. After some research, I was referred to this [site]("http://foo2zjs.rkkda.com/") in which I found this [file]("http://foo2zjs.rkkda.com/INSTALL") . I followed the general steps at the beginning and the special UBUNTU steps towards the end. When I am done, I added the printer and it has been working like a charm ever since. Hope this helps.

---

### Post by toro430 on 2007-08-23
Just want to add that I removed the HP Laserjet 1020 from my system before going through the above steps.

---

### Post by HermanAB on 2007-08-23
My fix for the fsck'ing HP1020:
Pull the USB plug, count to ten and plug it back in again.  After that it usually works again.

Cheers,

Herman

---

### Post by jingo811 on 2007-08-24
> fsck'ing
Is that a technical Linux term or are you just trying to swear?

---

### Post by alan tait on 2007-09-05
Thank you everyone. I too have been trying everything on this string, and HermanAB's finally got my HP1018 working.:popcorn:

---

