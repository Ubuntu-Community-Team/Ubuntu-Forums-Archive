---
title: "[SOLVED] HP printing issue"
date: 2013-03-30
forum: Any Other OS
---

### Post by ex_isp on 2013-03-30
Running Release 13 (maya) 64-bit, Kernel Linux 3.2.0-23-generic, GNOME 3.4.2, Mint

Installed a working HP Photosmart 7760 a week ago and the system picked it right up.
Printed test page in color.  2 mins later, went to print a simple text file and it just hangs.
Shows job in print que for about 5 mins then it gets purged.

Any help on this greatly appreciated!

Ex

---

### Post by Perfect Storm on 2013-03-30
Moved to Other OS/Distro Talk.

---

### Post by ex_isp on 2013-03-30
Not sure why you moved this AI... question IS hardware/driver related, NOT OS specific.

---

### Post by Perfect Storm on 2013-03-31
Yes, but the Hardware section is only for Ubuntu specifically (distros that Canonical supports - x/e/k/l/ubuntu and Ubuntu Gnome Remix). Other Distros have their own Hardware Section for that purpose, eg; 

Mint - [http://forums.linuxmint.com/viewforum.php?f=49&sid=23716f03aa704e2d8f0ee2e244a6cd44](http://forums.linuxmint.com/viewforum.php?f=49&sid=23716f03aa704e2d8f0ee2e244a6cd44)
Suse - [http://forums.opensuse.org/english/get-technical-help-here/hardware/](http://forums.opensuse.org/english/get-technical-help-here/hardware/)
Fedora - [http://www.forums.fedoraforum.org/forumdisplay.php?f=8](http://www.forums.fedoraforum.org/forumdisplay.php?f=8)
etc.

regards
A.I.

---

### Post by ex_isp on 2013-04-06
:wink:

---

### Post by tgalati4 on 2013-04-06
*In the end we are all terminal cases.*  Can you name the book?

The Photosmart typically has photo cartridges and color/black.  Is it possible that you don't have a black cartridge installed?

Also, look in /var/log/cups for messages.  There must be something in the log files.

Do you have *hplip* installed.  It gives you printer status information.

---

### Post by ex_isp on 2013-04-06
> **tgalati4 said:**
> *In the end we are all terminal cases.*  Can you name the book?

The Photosmart typically has photo cartridges and color/black.  Is it possible that you don't have a black cartridge installed?

Also, look in /var/log/cups for messages.  There must be something in the log files.

Do you have *hplip* installed.  It gives you printer status information.

Thanks so much for some input!  When first (1 month ago) plugged in, the kernal saw the printer right away.  Named it correctly 
as an HP 7700.  Printed a test page from within the printer software that was auto installed.  2 mins later, it would not repeat that
same fuction.

Will install hplip

Have 3 logs in /var/log/cups.

```
phuz@phuz-desktop /var/log/cups $ ls -l
total 12
-rw-r----- 1 root adm 662 Apr  6 19:47 access_log
-rw-r----- 1 root adm 563 Apr  6 16:01 error_log
-rw-r----- 1 root adm  90 Apr  6 19:44 page_log
phuz@phuz-desktop /var/log/cups $ more access_log 
localhost - - [06/Apr/2013:16:52:24 -0700] "POST / HTTP/1.1" 200 183 Renew-Subsc
ription successful-ok
localhost - - [06/Apr/2013:17:50:44 -0700] "POST / HTTP/1.1" 200 183 Renew-Subsc
ription successful-ok
localhost - - [06/Apr/2013:18:49:04 -0700] "POST / HTTP/1.1" 200 183 Renew-Subsc
ription successful-ok
localhost - - [06/Apr/2013:19:44:38 -0700] "POST /printers/photosmart-7700-serie
s HTTP/1.1" 200 290 Create-Job successful-ok
localhost - - [06/Apr/2013:19:44:38 -0700] "POST /printers/photosmart-7700-serie
s HTTP/1.1" 200 6255 Send-Document successful-ok
localhost - - [06/Apr/2013:19:47:24 -0700] "POST / HTTP/1.1" 200 183 Renew-Subsc
ription successful-ok
```


```
phuz@phuz-desktop /var/log/cups $ more error_log 
E [06/Apr/2013:16:01:22 -0700] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [06/Apr/2013:16:01:23 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'photosmart-7700-ser
ies-Gray..' already exists
W [06/Apr/2013:16:01:23 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'photosmart-7700-ser
ies-RGB..' already exists
W [06/Apr/2013:16:01:23 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-photosmart-7700-
series' already exists
E [06/Apr/2013:19:49:49 -0700] [Job 66] Stopping unresponsive job!
E [06/Apr/2013:19:55:10 -0700] [Job 66] Stopping unresponsive job!
E [06/Apr/2013:19:58:03 -0700] [Job 67] Stopping unresponsive job!
E [06/Apr/2013:20:00:31 -0700] [Job 66] Stopping unresponsive job!
E [06/Apr/2013:20:03:24 -0700] [Job 67] Stopping unresponsive job!
E [06/Apr/2013:20:05:52 -0700] [Job 66] Stopping unresponsive job!
```


```
phuz@phuz-desktop /var/log/cups $ more page_log 
photosmart-7700-series phuz 66 [06/Apr/2013:19:44:40 -0700] 1 1 - localhost Untitled1 - -
photosmart-7700-series phuz 66 [06/Apr/2013:19:50:00 -0700] 1 1 - localhost Untitled1 - -
photosmart-7700-series phuz 67 [06/Apr/2013:19:52:54 -0700] 1 1 - localhost Test page - -
photosmart-7700-series phuz 66 [06/Apr/2013:19:55:21 -0700] 1 1 - localhost Untitled1 - -
photosmart-7700-series phuz 67 [06/Apr/2013:19:58:14 -0700] 1 1 - localhost Test page - -
photosmart-7700-series phuz 66 [06/Apr/2013:20:00:42 -0700] 1 1 - localhost Untitled1 - -
photosmart-7700-series phuz 67 [06/Apr/2013:20:03:36 -0700] 1 1 - localhost Test page - -
photosmart-7700-series phuz 66 [06/Apr/2013:20:06:03 -0700] 1 1 - localhost Untitled1 - -
photosmart-7700-series phuz 67 [06/Apr/2013:20:08:56 -0700] 1 1 - localhost Test page - -
phuz@phuz-desktop /var/log/cups $ 
```

---

### Post by ex_isp on 2013-04-06
Printer software shows 2 jobs in cue, both in "held" state.

Additional: hplip installed

Additional: in this iteration, I am logged into an admin acct on the system, yet
in the printer software interface, it shows no allowed user...?

---

### Post by ex_isp on 2013-04-06
> **tgalati4 said:**
> *In the end we are all terminal cases.*  Can you name the book?

[h=1][SIZE=2][FONT=arial]'The World According to Garp'[/FONT][/SIZE][/h]

---

### Post by ex_isp on 2013-04-10
Bump...  Would sure welcome any suggestions here.  Thanks in advance!

---

### Post by Perfect Storm on 2013-04-10
I have found a bug report regarding your printer - [https://bugs.launchpad.net/hplip/+bug/414689](https://bugs.launchpad.net/hplip/+bug/414689) it goes a couple years back to now.
Some people mention different workarounds you could try.

---

### Post by ex_isp on 2013-04-11
Thank you for sourcing and posting this for me.  I tried the front USB port on the "media deck" and it is working!

---

