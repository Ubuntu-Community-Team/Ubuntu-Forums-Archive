---
title: "Re install GDM?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-02-18
Hi All

My GDM has gone after trying to remove  the KDE 4  core from my gutsy 7.10.

I tried this but it did not work :

steve@steve-desktop:~$ sudo dpkg-reconfigure gdm
[sudo] password for steve:
* Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
steve@steve-desktop:~$ 

Also tried " sudo apt-get install --reinstall gdm" but failed also :

steve@steve-desktop:~$ sudo apt-get install --reinstall gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1867kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 145129 files and directories currently installed.)
Preparing to replace gdm 2.20.1-0ubuntu2 (using .../gdm_2.20.1-0ubuntu2_i386.deb) ...
Unpacking replacement gdm ...
Setting up gdm (2.20.1-0ubuntu2) ...
* Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.


Can someone please advise me what to do?

Thanks Steve

---

### Post by MasterJS on 2008-02-18
Go to SYSTEM > ADMINISTRATION > SERVICES and see if the GDM is checked. It should appear as Graphical Login Manager (gdm)

---

### Post by bossa on 2008-02-18
> **MasterJS said:**
> Go to SYSTEM > ADMINISTRATION > SERVICES and see if the GDM is checked. It should appear as Graphical Login Manager (gdm)

yes it is checked ,also the KDM is there and checked.Still not happening

---

### Post by bossa on 2008-02-18
bump

---

### Post by harold4 on 2008-02-18
```
sudo apt-get install --reinstall gdm && sudo apt-get -f && sudo dpkg-reconfigure kdm && sudo dpkg-reconfigure gdm
```

For the last 2 commands, select gdm when giving the option of gdm or kdm.

Either reboot, or...

```

ctl + alt + f1.
log in
sudo /etc/init.d/kdm stop
sudo /etc/init.d/gdm restart
exit
ctrl + alt + f7

```

---

### Post by bossa on 2008-02-18
Thanks harold4
Terrific that worked a like a charm :)  KDE 4 was so slow and buggy I had to get rid of it
Thanks again

---

### Post by harold4 on 2008-02-18
Not a problem.  Yeah, I like KDE 3.5.8 much better than 4.0. 

Maybe when 4.0 matures a bit more and apps are fully ported to QT4 it'll be as good as the hype :-P

---

