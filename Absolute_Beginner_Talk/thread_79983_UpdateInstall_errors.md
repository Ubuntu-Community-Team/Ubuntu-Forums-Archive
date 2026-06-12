---
title: "Update/Install errors"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-21
After running apt-get update:

> Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Then, trying to install something with Synaptic (don't know if this this related):

> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

PS: I've been working with Ubuntu 5.04 for a month, and I have never managed a completely successful update, so there may be something buggered somewhere. Right now, my sources.list which I got from [www.psychocats.net/sources.html](www.psychocats.net/sources.html) reads:

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-backports main universe multiverse restricted

Any help would be appreciated.

---

### Post by Kyral on 2005-10-21
Well, the GPG errors are happening all over, so I doubt they are related.

As for the lock issue. There are two ways to fix it. One way is brute force, the other is not. Basically a lockfile is used to say "HEY! I'm using this here!" to prevent apps from using the same file at once (writing that is). You can imagine what would happen. Anyway make SURE Synaptic/Apt/Dpkg isn't running, then try to upgrade. THEN I'll tell you the brute force method

---

### Post by editrix on 2005-10-21
[QUOTE=Kyral]Well, the GPG errors are happening all over, so I doubt they are related.

As for the lock issue. There are two ways to fix it. One way is brute force, the other is not. Basically a lockfile is used to say "HEY! I'm using this here!" to prevent apps from using the same file at once (writing that is). You can imagine what would happen. Anyway make SURE Synaptic/Apt/Dpkg isn't running, then try to upgrade. THEN I'll tell you the brute force method[/QUOTE]

Well, I knew about the Synaptic/Apt thing, and according to the system monitor, dpkg isn't running. I guess I'd better warn you, I'm a little old lady, and I *love* brute force--I so rarely get a chance at my age. ;)

---

### Post by nitricacid on 2005-10-21
Maybe this redirect will help.
[http://www.n-sider.com/media/profiles-032604-snescd031.jpg](http://www.n-sider.com/media/profiles-032604-snescd031.jpg)

---

### Post by Kyral on 2005-10-21
What? A Genesis with a Mega CD?

Anyway. By deleting the lockfile it MIGHT unlock it. I'd back it up first just in case....

---

### Post by editrix on 2005-10-21
[QUOTE=Kyral]What? A Genesis with a Mega CD?

Anyway. By deleting the lockfile it MIGHT unlock it. I'd back it up first just in case....[/QUOTE]

Didn't understand the jpg or your comment on it, sorry. 

Will try renaming rather than deleting (that way it back up, too). Will try to get online again tomorrow--I'm on limited hours here--and let you know. Thx so far.

---

### Post by nitricacid on 2005-10-21
sorry, my bad. I posted the wrong URL. I was in a rush and thought that I had copied and pasted the rite one.

Here is what I ment to post 
[http://ubuntuforums.org/showthread.php?p=421472#post421472](http://ubuntuforums.org/showthread.php?p=421472#post421472)

---

### Post by editrix on 2005-10-23
[QUOTE=Kyral]What? A Genesis with a Mega CD?

Anyway. By deleting the lockfile it MIGHT unlock it. I'd back it up first just in case....[/QUOTE]

Kyral, this is the first time in over a month I have typed in sudo apt-get update
that I have not gotten an error message. Thank you!!

And, as to why it took so long, my ISP's been giving me grief.

---

