---
title: "Update Dapper to Edgy - failed - but why?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by kevmartin on 2007-03-04
I thought I would jump in and update my Dapper machine to Edgy, even though I'm very new because I saw that it was theoretically a one-line automated command to do so:
```
gksu "sh /cdrom/cdromupgrade"
```

But that isn't working for me - I get this response:
```
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```
Followed by a separate dialog stating "Your System is up-todate".

I checked in etc/lsb-release to be sure I wasn't already on Edgy:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
```

Can anyone advise?  Is there really any major advantage to Edgy anyway?  I was really only doing it for the sake of it - not a very good reason at all :)

Thanks
Kev

---

### Post by sunexplodes on 2007-03-05
I had the same trouble trying to use the CD to upgrade, too. I've always had much better luck with the update manager and the internet. try:
```
gksu &#8220;update-manager -c &#8221;
```

---

### Post by kevmartin on 2007-03-05
Oooops! My mistake.  That's what I was trying - I copied/pasted to my post wrongly from the instructions page here:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

```
gksu "update-manager -c"
```

I must have accidentally copied the cdrom upgrade command instead. Sorry about that :oops:

---

### Post by kevmartin on 2007-03-09
Found a resolution :-)

The failures were coming by running the update command from the Terminal command line.

I saw in the update instruction post you could also do it by Alt-F2, so I tried that, and it worked. Go figure I guess.

I left the system doing the update overnight and it was almost done by the time I got up this morning.  I think maybe deactivating the screensaver beforehand could have been a good idea (just guessing). So far everything seems OK.

Thanks.

---

### Post by avilance on 2007-03-12
I got the same problem, I received this message,


warnings.warn("apt API not stable yet", FutureWarning)


which I wonder what it is, or what to do about it.

but that's not the main problem. the main problem is: i tried to enter

gksu "update-manager -c "

but all I could see was an empty update list, with the message that it allready was upto date.

After that, I went searching, I stranded here, and I tried alt+f2.

but instead of working, it still gives the same result.

anybody knows what I could/should do?

---

