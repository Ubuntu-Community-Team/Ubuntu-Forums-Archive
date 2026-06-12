---
title: "Printer accepting, will not print"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Books on 2007-03-12
[SIZE="2"]I'm using Kubuntu Edgy. My printer, a Canon IP3000 using the BJC7000 driver - CUPS+Gutenprint v5.0.0 has stopped printing. It is accepting new jobs and test pages get queued to print but nothing happens. I was able to print three days ago, but nothing today.

The printer IPP report and it says...
```
printer-is-accepting-jobs:  True
printer-state-message:  Parallel port busy; will retry in 30 seconds...
printer-state-reasons:  none
```

The command ```
ls -l /dev/lp0
``` returns...
```
crw-rw---- 1 root lp 6, 0 2007-03-12 18:48 /dev/lp0
```

The permissions on my /dev/lp0 are:
permissions:  -rw-rw----
owner:  root
group:  lp

Something similar to this happened once before, and it got worse until I couldn't even get audio. It was some kind of permissions problem. I ended up having to reinstall Kubuntu to get it to work.

Questions:

What is "Parallel port busy; will retry in 30 seconds..." ? I don't have anything on my parallel port, and why would that have anything to do with a USB printer?

Is there a command that can check the connection to the printer?

Is there a way to test USB connection ability? I don't have any other USB devices so I'm not sure it's a printer issue or a USB issue.

Thank you!!!

Books[/SIZE]

---

### Post by Books on 2007-03-12
[SIZE="2"]Update: I uninstalled the printer in Kubuntu and reinstalled. No change.

I checked /var/log/cups/error_log and it shows:

```
E [12/Mar/2007:18:48:34 -0500] Creating missing directory "/var/run/cups/certs"
E [12/Mar/2007:19:54:06 -0500] Pause-Printer: Unauthorized
E [12/Mar/2007:19:58:30 -0500] cupsdAuthorize: Local authentication certificate not found!
E [12/Mar/2007:20:01:59 -0500] cupsdAuthorize: Local authentication certificate not found!
E [12/Mar/2007:20:01:59 -0500] CUPS-Delete-Printer: Unauthorized
E [12/Mar/2007:20:04:28 -0500] cupsdAuthorize: Local authentication certificate not found!
E [12/Mar/2007:20:04:28 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [12/Mar/2007:20:08:26 -0500] cupsdAuthorize: Local authentication certificate not found!
```

I tried logging into KDE's printer configuration tool using the 'Administrator' root mode and tried to test print... nothing.

Why would CUPS be saying that I'm "unauthorized"? I checked to see if my user account included permissions for 'lp' and it wasn't listed (I've been able to print until now.) I added my user account to 'lp' just to be on the safe side. No change.

Thank you!

Books[/SIZE]

---

### Post by Books on 2007-03-12
[SIZE="2"]Another update:

I tried using  **cat test.txt > /dev/lp0** to check to see if it would print a test page. It returned...

```
cat test.txt > /dev/lp0
bash: /dev/lp0: Permission denied
```

I tried the same command using sudo -- **sudo cat text.txt > /dev/lp0** -- and sudo didn't even ask for my password. (What is going on???)
```
sudo cat text.txt > /dev/lp0
bash: /dev/lp0: Permission denied
```

How can I tell that user 'myname' is added to /dev/lp0 ?

Also, I had a problem with permissions before and never found out why. I had to wipe the system and reinstall to fix it. I think it was caused by using "sudo" when I should have been using "kdesu"... I've heard that can cause permissions problems. But I haven't done any system changes except for using Synaptic to install whatever patches are released. I don't know if CUPS has been recently upgraded.

Can anyone help?

**Thank you!!!**

Books[/SIZE]

---

### Post by Books on 2007-03-12
[SIZE="2"]Ok, yet another update.

I tried switching the printer from the CUPS driver to the Foomatic driver. No change.

The KDE printer tool says the server is **/var/run/cups/cups.sock:631 **
I checked the permissions for /var/run/cups and it shows...
**certs**
permissions:  drwx--x--x
owner:  cupsys
group:  lpadmin

**cupsd.pid**
permissions:  -rw-r--r--
owner:  root
group:  root

**cups.sock**
permissions:  -rwxrwxrwx
owner:  root
group:  root

And under folder 'certs' it says...
**0**
permissions:  --w-r-----
owner:  cupsys
group:  lpadmin

Does anyone have an idea?

Thank you so much!

Books[/SIZE]

---

### Post by Books on 2007-03-13
[SIZE="2"]I was able to find the problem. An update to libgphoto2 caused an error with udevd. The solution was found in this thread:

**udevd add_to_rules**
[http://ubuntuforums.org/showthread.php?p=2275858]("http://ubuntuforums.org/showthread.php?p=2275858")

Thanks.

Books
[/SIZE]

---

