---
title: "Extremely Odd Cd Drive Problem"
date: 2005-10-13
forum: Apple PPC Users
---

### Post by obama on 2005-10-13
Here's the story so far.

I recently installed Ubuntu 5.04 for PPC on my 733mhz PowerMac.  Everything worked fine until yesterday, when I inserted the install disc, out of curiosity.  Looking back, it was an extremely decision.  The computer waited for about 30 seconds and, without any visible signs that it had detected the cd, spit it out.  When I closed the drive bay, it repeated the process.  I then took the install cd out, and closed the bay.  A minute or so later, with no cd in the drive, the drive opened.  I closed the bay again.  A minute or so passed, and it opened again.  So on and so forth.

Frustrated, I put the install cd in and, before it could eject it, manually rebooted via the button on the face of the tower.  I held down "C" on the keyboard to boot from the cd, but that simply gave me an extended gray screen, and the drive opened again.  From there the computer booted as usual.  

Essentially, I cannot use my cd drive.  This is made more frustrating by the recent 5.10 release, which I cannot install.  Has anybody ever experienced anything like this?  Any help at all would be deeply appreciated.

---

### Post by swerner on 2005-10-13
Type this, then insert the CD:
```

tail -f /var/log/messages

``` 
Then what is your output from this command when you insert the CD, and is there any output when the CD is ejected again?
CTRL-C will cancel the command above.

---

### Post by obama on 2005-10-13
Oct 13 16:49:37 localhost kernel: eth1: New link status: Connected (0001)
Oct 13 17:03:05 localhost kernel: ide-cd: cmd 0x1b timed out
Oct 13 17:03:28 localhost kernel: cdrom: open failed.
Oct 13 17:03:44 localhost kernel: eth1: New link status: AP Out of Range (0004)
Oct 13 17:04:08 localhost kernel: cdrom: open failed.
Oct 13 17:04:36 localhost kernel: eth1: New link status: AP In Range (0005)
Oct 13 17:05:08 localhost kernel: ide-cd: cmd 0x1b timed out
Oct 13 17:05:31 localhost kernel: cdrom: open failed.
Oct 13 17:06:13 localhost kernel: cdrom: open failed.
Oct 13 17:33:09 localhost -- MARK -

---

### Post by obama on 2005-10-13
the drive first ejects in the middle of startup, at the sde_pmac (or something similar) line.  this is a major problem, and I would really appreciate any help.

---

### Post by obama on 2005-10-13
First of all, sorry for the triple-post.

Secondly, the exact wording for the message that comes up at the boot process where the drive ejects is

> ide_pmac: set UDMA timing for mode 4, reg:0x0c50038c

again, thanks much for the help.

---

### Post by swerner on 2005-10-13
hmmm... strange problem indeed.

Try turning off DMA mode on your CD-ROM, by default it's not on in Ubuntu.  At the command line
```

sudo hdparm -d 0 /dev/cdrom
```

make sure /dev/cdrom is actually your CD-Rom drive. You can change this setting permantely in /etc/hdparm.conf.  Also try turning off the Unmask IRQ flag.

```

sudo hdparm -u 0 /dev/cdrom
```

I had a look on google, but couldn't find anything either, see [URLhttp://www.google.com/search?q=ide-cd+cmd+%22timed+out%22+eject+-ide-cd.c[/URL]

---

### Post by obama on 2005-10-20
I did what you said, but the problem persists.  i did, however, notice a startup message which may be at the root of the problem.

```
/dev/cdroms/cdrom0: No such file or directory
```

Edit:

I changed hdparm.conf to read /dev/cdrom (a real file, unlike the one above) and got:

```
/dev/cdrom: No such file or directory
```

I assume that this means my cd drive is not fully recognized.  any advice?

---

