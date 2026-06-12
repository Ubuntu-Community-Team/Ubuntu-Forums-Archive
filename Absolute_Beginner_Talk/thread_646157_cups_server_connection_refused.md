---
title: "cups server connection refused"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-12-20
I believe I am close to having the ability to print to a windows xp printer on my home network, but system daemon log keeps showing cups server refuses connection attempt. What am i missing?

---

### Post by [S|G] on 2007-12-21
Greetings!

Could you post the entries from your syslog? That would make easier to help :)

---

### Post by spiderbatdad on 2007-12-21
```
E [21/Dec/2007:07:37:15 -0500] Unable to find IP address for server name ""!
E [21/Dec/2007:08:38:37 -0500] [Job 40] No %%BoundingBox: comment in header!
E [21/Dec/2007:08:38:38 -0500] [Job 40] No ticket cache found for userid=0
E [21/Dec/2007:08:38:38 -0500] [Job 40] Can not get the ticket cache for root
E [21/Dec/2007:09:27:27 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:09:35:23 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:09:35:39 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:09:35:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:09:36:13 -0500] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [21/Dec/2007:09:36:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:09:36:44 -0500] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [21/Dec/2007:09:36:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:09:37:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:09:37:38 -0500] [Job 41] No %%BoundingBox: comment in header!
E [21/Dec/2007:09:37:38 -0500] [Job 41] No ticket cache found for userid=0
E [21/Dec/2007:09:37:38 -0500] [Job 41] Can not get the ticket cache for root
E [21/Dec/2007:11:29:17 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:30:04 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:30:17 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:30:34 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:31:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:31:12 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:31:23 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:31:39 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:31:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:32:58 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:33:11 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:33:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:34:43 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:34:56 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:35:08 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:35:24 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:36:08 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:37:32 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:44:53 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:45:42 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:42 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:42 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:42 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:56 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:56 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:56 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:56 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:56 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:56 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:45:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:12 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:12 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:12 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:12 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:12 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:12 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:46:52 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:48:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:48:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:49:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:49:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:49:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:49:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:49:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:49:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:58:13 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:58:34 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:11:59:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:38 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:11:59:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:18 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:18 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:18 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:36 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:00:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:02:55 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:03:12 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:04:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:01 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:11 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:20 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:20 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:20 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:20 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:20 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:20 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:04:59 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:17 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:17 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:17 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:05:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:37 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:37 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:37 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:43 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:43 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:43 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:06:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:10:15 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:10:29 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:11:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:25 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:11:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:12:41 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:12:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:49:27 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:49:43 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:49:55 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:49:55 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:49:55 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:49:55 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:52:49 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:54:19 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:55:35 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:56:48 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:12:57:32 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:32 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:32 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:32 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:12:57:45 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:06:14 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:13:11:02 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:13:12:07 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:13:12:38 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:13:14:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:21 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:22 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:24 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:40 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:40 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:40 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:40 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:40 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:14:40 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:15:00 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:15:00 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:15:00 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:21:54 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:13:22:12 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:13:22:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:13:22:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:43:12 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:14:43:43 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:14:44:05 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:05 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:05 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:14 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:15 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:15 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:15 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:15 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:15 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:15 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:47 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:49 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:50 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:52 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:44:58 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:06 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:45:07 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:01 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:14:57:09 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [21/Dec/2007:14:57:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:23 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2007:14:57:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
```

---

