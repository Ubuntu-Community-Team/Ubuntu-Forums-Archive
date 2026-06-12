---
title: "Help installing Ubuntu Desktop from Kubuntu Edgy"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2007-04-18
I'm trying to install Ubuntu via the internet but when I type in the code ```
sudo apt-get install ubuntu-desktop
``` it asks me to insert the Kubuntu Edgy CD but I didnt install with the CD, so I don't have it. So what do I do?

---

### Post by BarfBag on 2007-04-18
Try enabling all of your repositories and an apt-get update.

---

### Post by Narcoleptic_Insomniac on 2007-04-18
How do I enable my repositories and I always do a sudo aptitude update before I install something with sudo. Is there a difference between sudo apt-get update and sudo aptitude update?

---

### Post by BarfBag on 2007-04-18
> sudo gedit /etc/apt/sources.list

Remove the # from the beginning of the servers.

Aptitude is better then apt-get, actually.  I always use apt-get, though.  I find it more consistent with Synaptic.  Either one will work.

---

### Post by Narcoleptic_Insomniac on 2007-04-18
> **BarfBag said:**
> Remove the # from the beginning of the servers.

Aptitude is better then apt-get, actually.  I always use apt-get, though.  I find it more consistent with Synaptic.  Either one will work.

```
matt@ubuntu:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
matt@ubuntu:~$ 

```

:confused: Now what lol?

---

### Post by Bachstelze on 2007-04-18
Since you're in KDE, do this instead.

```
kdesu kate /etc/apt/sources.list
```

---

### Post by BarfBag on 2007-04-18
I'm sorry.  I forgot that you're on Kubuntu, and not Ubuntu.

> sudo kwrite /etc/apt/sources.list

---

### Post by Narcoleptic_Insomniac on 2007-04-18
Alright I got my sources opened but should I remove all the ##'s or just the single ones?

---

### Post by BarfBag on 2007-04-18
Just the single ones in front of each server link.  Every # that's in front of a deb or deb-src should be removed.

---

### Post by Bachstelze on 2007-04-18
And also add one in front of all the cdrom lines - or even delete them totally.

---

### Post by Narcoleptic_Insomniac on 2007-04-18
Alright I did that, I'm gonna try installing ubuntu again.

---

### Post by BarfBag on 2007-04-18
Remember to apt-get update or aptitude update.

---

### Post by Narcoleptic_Insomniac on 2007-04-18
Still no luck. This is what I get.
```
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Kubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)'
in the drive '/cdrom/' and press enter

```

---

### Post by Narcoleptic_Insomniac on 2007-04-18
> **BarfBag said:**
> Remember to apt-get update or aptitude update.

Yea I updated.

---

### Post by BarfBag on 2007-04-18
Did you comment out (add #) anything pertaining to a CD in sources.list?

---

### Post by Bachstelze on 2007-04-18
> **HymnToLife said:**
> And also add one in front of all the cdrom lines - or even delete them totally.

...

---

### Post by Narcoleptic_Insomniac on 2007-04-18
> **BarfBag said:**
> Did you comment out (add #) anything pertaining to a CD in sources.list?

No I didnt, did you mention to, if so I guess I missed that, I'll add the #'s in front of anything with CD in it.

---

### Post by BarfBag on 2007-04-18
HymnToLife said it.  Give him the credit.  lol

---

### Post by Narcoleptic_Insomniac on 2007-04-18
Ok I added the #'s in front of everything with CD in it, I ran the update command and now I'm going to try  this again...

---

### Post by Narcoleptic_Insomniac on 2007-04-18
Ok everything is working so far, so after this is finished downloading and installing, I want to remove KDE, do I remove KDE right from the same terminal or should I restart the computer and remove KDE from Gnome? The removal code is ```
sudo apt-get remove --purge kubuntu-desktop
``` right?

---

### Post by BarfBag on 2007-04-18
Reboot and do it from Gnome.  Be sure to do it through Gnome Terminal and not Konsole, though.

I think that's the command.  Not sure about the --purge part.  Someone should verify this.

---

