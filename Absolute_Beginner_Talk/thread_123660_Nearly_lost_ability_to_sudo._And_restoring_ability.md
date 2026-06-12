---
title: "Nearly lost ability to sudo. And restoring ability to sudo?"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by DonQuixote on 2006-01-30
In an attempt to allow myself to write to my /www directory I assigned myself to the "www-data" group doing this:

usermod -G www-data john

So, I went to execute a root command using sudo and was shown this error:

john is not in the sudoers file.  This incident will be reported.

Ouch!

So, I went and looked at my /etc/group file.  Now, I'd looked at it before, and noticed that "john" was included in several groups, however, THIS time when I looked at it, I was only in one group, "www-data".

Fortunately I had a terminal window that was open in which I'd "sudo -i"'d to so, at least in one window I still had root permissions.

I am curious to know, if this should happen to someone else who did not have a root access window open, how sudo access could be restored or reset, anyone?

Anyway, I added myself to every group listed because I could not remember in which groups I had been originally included.

Could someone post their unmodified /etc/group file here so that I could reset mine to the original configuration?

Thanks!

John

---

### Post by Mr Wrath on 2006-01-30
I had a similar problem that I still haven't figured out...If you want to see a detailed list of what happened to mine go to your 'search' bar and do a search on "sudo blasted"...My friend posted it (Ingurogl the Black).  It's a good read.  If you find anything let me know...because I am considering DBAN & start over.

---

### Post by Sutekh on 2006-01-30
[QUOTE=DonQuixote]
Could someone post their unmodified /etc/group file here so that I could reset mine to the original configuration?

Thanks!

John[/QUOTE]

The important one is 'adm'.  This allows you sudo privileges.

In future the better way to change groups (IMHO) is
```
sudo adduser <username> <groupname>
```

---

### Post by DonQuixote on 2006-01-30
Here is the thread that Mr. Wrath was refering to: [http://ubuntuforums.org/showthread.php?t=122113](http://ubuntuforums.org/showthread.php?t=122113)

Sutekh,

Thanks for pointing me to "adm" for sudo.  The other thing I was curious to know, is what other groups should I be part of in order to run Ubuntu as it was installed?  I don't think I need to be part of EVERY group to do that.  This is why I asked if someone could post their default /etc/group file, so that I could compare and change mine.

Thanks!

John

---

### Post by Sutekh on 2006-01-30
Yeah I'd love to tell you mine, but I'm at work.

Here's some I can remember.
adm audio cdrom dialup floppy plugdev scanner

Edit: from an old post of mine
```

user adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```
'user' is the same as your user name.

---

### Post by DonQuixote on 2006-01-30
I'm at work, too. :)  I can wait for later this evening, as I am now part of every group except root.  I don't anticipate any problems... (famous last words, eh!)

John

---

