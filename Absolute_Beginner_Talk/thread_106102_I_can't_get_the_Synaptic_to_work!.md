---
title: "I can't get the Synaptic to work!"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2005-12-19
So I'm trying to make it so I can run MP3s and DVDs.

I go to Synaptic Manager thing, and go through to settings to show all the packages and click universe and all that jazz.

Now, I get this message when I reload:

cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

And then,

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

So... What did I do wrong?

---

### Post by joshuapurcell on 2005-12-19
The CD was probably taken out of the drive, or the CD isn't mounted. You will get those errors since by default Synaptic (apt-get) has the CD listed as a repository.

If you don't want the CD included in the repositories, then take out the lines that contain **cdrom** from the top of your /etc/apt/sources.lst file. If you have any questions on which lines to take out (I think there are only two) then post the file and we can show you which ones.

The other alternative is to keep the CD in the drive when you perform an update.

---

### Post by SZF2001 on 2005-12-19
Well, this is what I get:

[b]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse[/b]

Delete the part that says cd?

---

### Post by invalid on 2005-12-19
Simple add a # in front of the cd line:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```
and choose update.

---

### Post by SZF2001 on 2005-12-19
This is wierd, it won't let me write anything in the list file yet I'm typing in this message box...

---

### Post by invalid on 2005-12-19
It is owned by the root user. You must open the editor with sudo.
```
sudo gedit
```

---

### Post by SZF2001 on 2005-12-19
Wow... You are my hero.

Not only have you helped me, but you've helped me realise how things go in the terminal and what sudo means and stuff.

I'm... Taking a first step... ^_^

---

