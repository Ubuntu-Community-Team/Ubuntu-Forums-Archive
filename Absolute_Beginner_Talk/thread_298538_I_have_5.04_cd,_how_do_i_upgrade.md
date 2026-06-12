---
title: "I have 5.04 cd, how do i upgrade?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by kjaonline on 2006-11-12
Hello
is there any way that I can upgrade for 5.04 with out cd's and withou reformatting my system? Thanks

Do I still use this command?
```

gksu "update-manager -c"
```

---

### Post by loell on 2006-11-12
i think its better installing a fresh ubuntu install
you can choose ubuntu 6.6.1
or the newly release 6.10

---

### Post by kjaonline on 2006-11-12
Anyone? Please help.. :confused: 
i wanna install this now and am afraid that many packages wont support ubuntu 5.04

(sorry for the double post)

---

### Post by kjaonline on 2006-11-12
The problem is I'm on dial-up and it will take a loooong time to download the iso image.. That and I don't have a CD burner... ](*,) ](*,)

---

### Post by loell on 2006-11-12
> **kjaonline said:**
> The problem is I'm on dial-up and it will take a loooong time to download the iso image.. That and I don't have a CD burner... ](*,) ](*,)

you can order for free the 6.6.1 version from [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

it may take a little while though to arrive there, but i think that's the way to go :)

---

### Post by kjaonline on 2006-11-12
Hello everone I have a problem.. I want to install ubuntu but i have the 5.04 cd with me... Is there anyway i can upgrade without the need of a newer version cd?
Thanks

---

### Post by aysiu on 2006-11-12
> **kjaonline said:**
> Hello everone I have a problem.. I want to install ubuntu but i have the 5.04 cd with me... Is there anyway i can upgrade without the need of a newer version cd?
Thanks
Depends.

How fast is your internet connection?

---

### Post by kjaonline on 2006-11-12
Like there's really no way I can upgrade from 5.04 huh?
This sucks... :mrgreen:

---

### Post by kjaonline on 2006-11-12
512 kbps and note also that I dont have a cd burner lol..

---

### Post by BarfBag on 2006-11-12
Since you don't have a CD burner, you have two options.

1.  Order the free shipit CD's from ubuntu.com.  This takes a while to get to you, but it's an option.  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

2.  There's an apt-get command that upgrades your entire system (I think...).  Can someone verify this and post how to do it?  Edit - found it.  Fire up a terminal, and type sudo apt-get dist-upgrade.

---

### Post by loell on 2006-11-12
oh i see you've got a duplicate thread?

---

### Post by kjaonline on 2006-11-12
Do i use this command?

```
gksu "update-manager -c"
```

---

### Post by kjaonline on 2006-11-12
oh errr I'm really sorry.. 
Im a beginner so I figured I'd post here as well..
I apologize..
](*,)

---

### Post by loell on 2006-11-12
yeah, even if your in broadband, its difficult to upgrade form 5.04 to 6.6 or 6.10 without doing 1,000 encantations and magic spells ;)

---

### Post by kjaonline on 2006-11-12
and why is that? aint it just one command and poof?

---

### Post by loell on 2006-11-12
;)  that's jut okay

---

### Post by aysiu on 2006-11-12
> **kjaonline said:**
> oh errr I'm really sorry.. 
Im a beginner so I figured I'd post here as well..
I apologize..
](*,)
Apology accepted. Don't do it again, though.

In the meantime, I've merged the two threads.

---

### Post by kjaonline on 2006-11-12
> **BarfBag said:**
> Since you don't have a CD burner, you have two options.

1.  Order the free shipit CD's from ubuntu.com.  This takes a while to get to you, but it's an option.  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

2.  There's an apt-get command that upgrades your entire system (I think...).  Can someone verify this and post how to do it?  Edit - found it.  Fire up a terminal, and type sudo apt-get dist-upgrade.

So It will upgrade to which version when I type in the command?

```
sudo apt-get dist-upgrade
```

How long would this take?

---

### Post by Velotix on 2006-11-12
It'll upgrade to the next version, which in your case is v5.10. Then when you're running 5.10, run the command again and you'll be up to 6.06. Then run it *again* and you'll finally be at 6.10.

Either way you do it, you're in for a looong wait. :???:

---

### Post by kjaonline on 2006-11-12
like how many hours would it take? So that i can leave the PC overnight lol... (it's day here)

---

### Post by kjaonline on 2006-11-12
Finished installing Kubuntu lol
that was quick but I have a problem with the command you gave me

this error comes out
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by kjaonline on 2006-11-12
I have another question my internet gets disconnected all the time.. if my internet gets disconnected and connects again will the download resume?
Will it bug my system if that happens?

---

### Post by kjaonline on 2006-11-13
Hello again.. I've finished updating my version of ubuntu but it still says that i have 5.04 and when I update it says that I have the most upto date version of ubuntu..

---

### Post by aysiu on 2006-11-13
> **kjaonline said:**
> Hello again.. I've finished updating my version of ubuntu but it still says that i have 5.04 and when I update it says that I have the most upto date version of ubuntu..
Can you post the output of these two commands? ```
cat /etc/issue
cat /etc/apt/sources.list
```

---

### Post by kjaonline on 2006-11-13
For cat /etc/issue
```
Ubuntu 5.04 "Hoary Hedgehog" \n \l
```



for  cat /etc/apt/sources.list
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://ph.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ph.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://ph.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```

Thanks ^_^

---

### Post by aysiu on 2006-11-13
Well, you're still using Hoary, and it's no surprise, seeing as how all your repositories are Hoary repositories.

Theoretically, you could jump from Hoary to Edgy, but I've heard that jumping versions is very likely to end in a big mess. However, if you go from Hoary to Breezy, Breezy to Dapper, and then Dapper to Edgy, it'd take you a long time to upgrade, even on a fast connection.

My suggestion is that you back up your current installation using either [this method](http://ubuntuforums.org/showthread.php?t=81311) or [this method](http://www.psychocats.net/ubuntu/partimage). That way, if things get messed up, you have an easy way of restoring back to Hoary.

After backing up everything, I would upgrade to Edgy with this method:

**Make sure you have the appropriate metapackage(s) installed**
For example, if you're using Gnome, you should do this: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` **Change your sources.list to Edgy**
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.hoary
gksudo gedit /etc/apt/sources.list
``` When Gedit opens, paste this code in: ```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ edgy main restricted


deb http://ph.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ph.archive.ubuntu.com/ubuntu edgy universe
# deb-src http://ph.archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
``` Save and exit Gedit.

**Do the actual upgrade**
The log out of Ubuntu. Press Control-Alt-F1. Log into the terminal. Stop GDM: ```
sudo /etc/init.d/gdm stop
``` Do the upgrade ```
sudo aptitude update
sudo aptitude dist-upgrade
``` Once the upgrade is done, reboot: ```
sudo reboot
``` If you're logged into terminal mode again, relaunch GDM: ```
sudo /etc/init.d/gdm restart
```

All of these instructions assume you're using Gnome. If you're using KDE or XFCE, let me know, and I'll tell you what to modify.

**Please back up Hoary before you do any of this upgrade**.

---

### Post by kjaonline on 2006-11-13
Okay.. I'll try those.. will update you as to what happened.. Thanks

---

### Post by kjaonline on 2006-11-13
When i typed this command in

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.hoary
```

This is what comes out

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.hoary
```

I went on with th upgrade even with that error because I figured that it's minor but when you told me to stop gnome

```
sudo /etc/init.d/gdm stop
```

It says that the command could not be found..
So I didn't go on with the upgrade and went back to the forums..
Anything you need to revise?
You're really a big help and I really appreciate this..
I'm using gnome... ^_^

---

### Post by aysiu on 2006-11-13
You're telling me that when you paste in the code I gave you, you see something like this? ```
kjaonline@ubuntu~$ **sudo mv /etc/apt/sources.list /etc/apt/sources.list.hoary**
sudo mv /etc/apt/sources.list /etc/apt/sources.list.hoary
kjaonline@ubuntu~$
``` In other words, what I asked you to paste into the terminal shows up as output, too? Can you post a screenshot of what that looks like, because it doesn't sound like an error message to me.

---

### Post by kjaonline on 2006-11-13
oh my bad..
I got around that i made a new file as
/etc/apt/sources.list
and pasted what you told me to paste..
Did I do it right?
when I 
```
cat /etc/apt/sources.list 
```
what you told me to paste comes out


Now my problem is the kill GDM thing
It says there is no command could not be found

---

### Post by kjaonline on 2006-11-13
Err I ran the command without logging out and closing gnome... 
Will it bug something if I continue this?

---

### Post by aysiu on 2006-11-13
> **kjaonline said:**
> Err I ran the command without logging out and closing gnome... 
Will it bug something if I continue this?
No it shouldn't, but with this serious an upgrade, I just thought it'd be good to play it on the safe side.

---

### Post by kjaonline on 2006-11-13
errr this time it tells me that I have broken packages..
tried
sudo apt-get dist-upgrade
```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu15) but 2.4-1ubuntu12 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu15) but 2.4-1ubuntu12 is installed
  linux-image-2.6.10-6-386: Depends: initrd-tools (>= 0.1.75ubuntu2) but it is not installable
  lsb: Depends: lsb-graphics but it is not installed
       Depends: lsb-cxx but it is not installed
       Depends: lsb-desktop but it is not installed
  volumeid: Depends: initramfs-tools (>= 0.40ubuntu30) but it is not installed

```

cat /etc/apt/sources.list

```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ edgy main restricted


deb http://ph.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ph.archive.ubuntu.com/ubuntu edgy universe
# deb-src http://ph.archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```
errrr still says i have hoary 5.04

---

### Post by aysiu on 2006-11-13
Well, I never had much hope for a Hoary-to-Edgy upgrade in the first place, which is why I asked you to do a full backup of Hoary before doing anything.

Before we continue, please log out of Gnome and do the ```
sudo /etc/init.d/gdm stop
```

Then let's try following the instructions: ```
sudo apt-get -f install
``` After that, do this--and please for this use *aptitude* and **not** *apt-get*: ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

