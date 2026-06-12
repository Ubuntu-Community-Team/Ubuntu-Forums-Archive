---
title: "[SOLVED] clam av  out of date?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-04-12
ive read through a bunch of posts here about clam av but i can find any that have the same problems i have

i installed clam av a few months ago and have been using it once in a while without problems

my problem now is i went to start clamscan  and it told me my clam av is out of date, so i figured no problem,  ill just do a complete removal of everything in synaptic

But after i removed everything and reinstalled it again i got the same message when i went to run clamscan 

In the message telling me my clam av was out of date, it gave me a website to go to [http://www.clamav.net/support/faq]("http://www.clamav.net/support/faq")
at this website i read down the page and was troubleshooting problems untill i got to this part
> Also make sure that you haven’t got old libraries (libclamav.so*) lying around your filesystem. You can verify it using: $ ldd `which freshclam`
when i did that i got this
```

tj@tj-laptop:~$ ldd `which freshclam`
        libclamav.so.2 => /usr/lib/libclamav.so.2 (0x00002b73cd56d000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x00002b73cd80c000)
        libresolv.so.2 => /lib/libresolv.so.2 (0x00002b73cda25000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b73cdc3a000)
        libc.so.6 => /lib/libc.so.6 (0x00002b73cde56000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00002b73ce1b1000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00002b73ce3c8000)
        libgmp.so.3 => /usr/lib/libgmp.so.3 (0x00002b73ce5d9000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b73cd34f000)
tj@tj-laptop:~$ 

```

i dont know if this is what it was talking about if it is how do i remove them?

If this isnt what you think the problem is,  then what is the problem and how do i fix it?

---

### Post by spydon on 2008-04-12
```
sudo rm -rf /usr/lib/libclamav.so*
``` That should do it and then just purge and reinstall. :)

---

### Post by tjwoosta on 2008-04-16
thanks, that seemed to work because now i can scan my computer, but when i run freshclam i get this message
```

ClamAV update process started at Wed Apr 16 03:11:30 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.91.2 Recommended version: 0.93
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 46, sigs: 231834, f-level: 26, builder: sven)
daily.inc is up to date (version: 6793, sigs: 26775, f-level: 26, builder: ccordes)

```
this was after i did a complete removal and a fresh install from synaptic package manager 

 how can i get an upgraded calmav?

---

### Post by spydon on 2008-04-16
Check here[ http://wiki.clamav.net/Main/UpgradeInstructions]("http://wiki.clamav.net/Main/UpgradeInstructions")

---

### Post by tjwoosta on 2008-04-17
hmmm well.. i uninstlled everything again and installed the stuff on that link but i still get the same error

thanks for all your help but i guess im just not  even goin to worry about it since i read somewhere that clamscan only picks up windows viruses anyway

---

### Post by SunnyRabbiera on 2008-04-17
yup, and really none of the viruses in the works for linux wont effect you unless you run as root.

---

### Post by Tatty on 2008-04-17
You dont need an anti-virus for linux because there are currently no working viruses for linux.

If you are installing clamav from the repos then there is a good chance that it is not the latest version, as only security patches are made to the repos between ubuntu releases.

You will need to install clamav directly from the official site if you want the latest version.  But as has been said, this is unessesary on a linux machine.

---

### Post by Don Giovanni on 2008-04-17
Not needed for linux yes, but its not a bad idea to have it if you share files with Windows boxes in your home or with others who might be using Windows.

---

