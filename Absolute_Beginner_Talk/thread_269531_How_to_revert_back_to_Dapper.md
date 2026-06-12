---
title: "How to revert back to Dapper?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by bollocks00 on 2006-10-01
I had Dapper Drake running okay.  I still needed SD card slot and printer support, so I tried installing Edgy Eft and a new kernel by replacing all the references to 'dapper' in /etc/apt/sources.list to 'edgy'.  Then I ran:

```

#sudo apt-get update 
#sudo apt-get upgrade
#sudo apt-get install linux-image-2.6.17-10-generic

```

Now whenever I log on, I get the error 'The Application "nautilus" has quit unexpectedly.'  The system is mostly functional still, but I get this message regardless of which kernel I boot into.  How can I go about undoing this mess?

I would just like to get back to Dapper.  I've already tried replacing the 'edgy' references with 'dapper' again and then running apt-get update and upgrade commands, but this does not work.  Also, when I upgraded it went mostly smoothly except for errors along the lines of:

```

dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on gsfonts-x11; however:
  Package gsfonts-x11 is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gsfonts-x11
 flashplugin-nonfree

```

Does anyone know what I should do to get back to normal?

---

### Post by Jussi Kukkonen on 2006-10-02
There is no 'official' way to downgrade in apt. People have done it though, google for "downgrading Debian".

Have you reported a bug on the "nautilus has quit unexpectedly" issue?


EDIT: I just noticed: Was this a typo?
> #sudo apt-get upgrade
OS upgrades are done with apt-get dist-upgrade...

---

### Post by hyper_ch on 2006-10-02
For testing Edgy I did create a new partition and installed it there...
Maybe you should have done the same next time :) Just a little advice :)

---

### Post by bollocks00 on 2006-10-02
> **sjau said:**
> For testing Edgy I did create a new partition and installed it there...
Maybe you should have done the same next time :) Just a little advice :)

It's working now.  I'm a big boy ;)

---

### Post by ThomasU on 2006-10-03
So how did you solve the problem?
Thanks.

---

### Post by Sef on 2006-10-03
Did you set up a new partition?

---

### Post by bollocks00 on 2006-10-03
I'm pretty sure I set up the newest kernel (2.6.17.10) after installing Eft, so I just redid the Eft install from the terminal.  I'm not sure exactly why this solved the problem, I guess you have to rebuild some things upon upgrading?

Edit: also, I used apt-get dist-upgrade, not apt-get upgrade as I had mentioned.

---

