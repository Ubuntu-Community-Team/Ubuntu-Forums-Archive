---
title: "Sharig a printer"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by cb03BoilerUp on 2006-03-17
When I try to share an HP 5610 on a WinXP machine I get the following error message in the printer properties on Ubuntu:

' Ready: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR: Connection failed with error NT_STATUS_ACCESS_DENIED'

The frustrating thing is that when I try to print, I watch the print queue on the XP desktop; and it shows the print job, but only ~64K loads, and then it stops.

---

### Post by Pragmatist on 2006-03-17
What version of Ubuntu are you using?  Try doing an upgade:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by cb03BoilerUp on 2006-03-17
I'm using 5.10, and I updated immediately after installation...

I'm not at the computer now, but will try your suggestion later tonight.

---

### Post by cb03BoilerUp on 2006-03-17
Would it be easier to install the printer on the Ubuntu box, and then share with the network?  The printer doesn't have to be on the XP machine..

---

### Post by Pragmatist on 2006-03-17
[SIZE=2]As I understand it, it is easier the way you have it.  From some of the posts I read, I think your problem may have to do with upgrading.  If not, the next thing I would try is following these instructions:

For sharing Windows Printer:
[https://wiki.ubuntu.com/WindowsXPPrinter?highlight=%28printer%29](https://wiki.ubuntu.com/WindowsXPPrinter?highlight=%28printer%29)

For sharing Linux Printer type this in a terminal and read:
```
man cupsaddsmb
```

Let us know what happens.[/SIZE]

---

### Post by cb03BoilerUp on 2006-03-19
I tried the upgrade, recreated the printer, and restarted both machines.  It still does the same thing.  I have tried using both a login, and guest settings for the printer with no success.  My next attempt will be to share it from Ubuntu using cups.  I can't figure out what is wrong....:-k

---

