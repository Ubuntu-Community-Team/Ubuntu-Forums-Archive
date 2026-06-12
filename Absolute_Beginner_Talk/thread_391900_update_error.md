---
title: "update error"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by zrx1200 on 2007-03-23
when i go to the package manager at the top of screen i get the following message:eror :opening cache (e:type 'sudo'.is not known on line 35 in source list./etc/apt/sources.list,e:the list of sources could not be read.)...also when going to add remove.i get simular message and also in the synaptic package manager..I no i caused the prob as i typed in somewhere sudo nvidia-glx-config enable..trying to find or enable drivers for graphics card.i could reinstall but i would rather fix it..any help would be appreciated

---

### Post by taurus on 2007-03-23
I guess there is something wrong in line 35 of your /etc/apt/sources.list.  Can you post your /etc/apt/sources.list here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by zrx1200 on 2007-03-23
how do i copy the file to this post ?also the sudo nvidia is the last entry as you supected..how do i remove it?

---

### Post by taurus on 2007-03-23
Well, you can fix it by typing this command in a terminal.

```
gksudo gedit /etc/apt/sources.list
```
Scroll down until you get to line 35 and place a # in front of it to comment it out.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  You can post your /etc/apt/sources.list by using the left button on your mouse to cut (highlight) and the middle button to paste.

---

### Post by zrx1200 on 2007-03-23
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb cdrom:[disc2]/debs/ /
# deb cdrom:[disc3]/debs/ /
sudo nvidia-glx-config enable
ben@ben-desktop:~$ gksudo gedit /etc/apt/sources.list
GTK Accessibility Module initialized

(gedit:7171): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ben@ben-desktop:~$

well i've hit another snag,,i cant belive how helpful this forum is

---

### Post by taurus on 2007-03-23
You need to edit your /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and remove the last line from it.

```
sudo nvidia-glx-config enable
```
Save and exit with <Ctrl>o and <Ctrl>x.

The line the you just removed should be ran at the terminal to enable nvidia for your graphic card.

```
sudo nvidia-glx-config enable
```

---

### Post by zrx1200 on 2007-03-23
ben@ben-desktop:~$ sudo nvidia-glx-config enable
Password:
sudo: nvidia-glx-config: command not found
ben@ben-desktop:~$

update manager working thanks heaps nvidia not?

---

### Post by taurus on 2007-03-23
```
sudo nvidia-xconfig
```

---

### Post by zrx1200 on 2007-03-23
ben@ben-desktop:~$ sudo nvidia-xconfig
Password:
sudo: nvidia-xconfig: command not found
ben@ben-desktop:~$

:(

---

### Post by taurus on 2007-03-23
Have you installed nVidia driver for your graphic card?  If you haven't, then you need to use envy since it does everything for you after you download and install it.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by zrx1200 on 2007-03-24
done the envy thing tells me it is installed..thanks again....now for my next challenge fire wire

---

