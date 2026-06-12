---
title: "Installation issues"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by skale on 2006-06-25
Whenever I install something, this crap happens:
> Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)' in the drive '/cdrom/' and press enter
and, once I press ENTER
> 
aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted
whether I put in the CD or not.

It worked a few days ago, and I really haven't done anything to it. All the repositories are enabled as far as I can tell, I checked.

---

### Post by taurus on 2006-06-25
You need to edit your /etc/apt/sources.list and comment out the first two lines, for the source CD, by placing a # in front of them...
```

sudo gedit /etc/apt/sources.list

```
Then, update it...
```

sudo apt-get update

```

---

### Post by tonyr on 2006-06-25
Are you expecting to use the CD as one of the repos? If not,  remove it.  Use
the Synaptic access to the list of repositories, or edit **/etc/apt/sources.list**
as root) and comment out the first repo definition that has cdrom
mentioned.  Mine look like this:

```

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

```

Yours may look slightly different.  You will then need to update the repos in 
Synaptic or using **apt-get** on the command line.

I don't know why it should have suddenly started asking for the CDROM if you
had already removed it.

---

### Post by skale on 2006-06-25
Thanks! 

It worked. :KS

---

