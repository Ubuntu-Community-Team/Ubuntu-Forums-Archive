---
title: "updated ubuntu 5.04 using synaptic"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by beej101 on 2006-03-15
i did the above and clicked on "Apply" button and I chose the remove and upgrade options in one of the pop-ups that well popped up... problem is when the dialog that says changes are being applied came up it said that process may take awhile... so i waited... and waited... the dialog message was right in that i had to leave it overnight... and when i woke up it still was not finished... i remember the library being updated is libc6.  what could be wrong why it was taking too long or i believe actually hanged-up?
also just curious that while my install was 5.04, when i clicked "Apply" (to apply the changes) it asked for the 5.10 install cd?
thanks for any clarifications...

---

### Post by Pragmatist on 2006-03-16
What kind of internet connection do you have?

---

### Post by beej101 on 2006-03-16
broadband, is that what you meant?

---

### Post by Pragmatist on 2006-03-16
Please show us your /etc/apt/sources.list file:
```
cat /etc/apt/sources.list
```

---

### Post by beej101 on 2006-03-16
hi Pragmatist sorry for the delayed response... the following is my /etc/apt/source.list:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe


```

---

### Post by Pragmatist on 2006-03-16
Try this:
Backup your /etc/apt/sources.list file so you can roll back to it if you want to:
```
cp /etc/apt/sources.list $HOME
``` make sure it is there
```
ls -l $HOME/sources.list
``` Now go into /etc/apt and remove your sources.list
```
sudo rm /etc/apt/sources.list
``` Open an editor and put this in it and save it as /etc/apt/sources.list:
> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

Now try what you did the other night and see if it is faster.

---

### Post by aysiu on 2006-03-16
[QUOTE=beej101]
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted

```[/QUOTE] A couple of problems here.

First of all, you have almost no repositories enabled.

A # sign at the beginning of a line basically tells Synaptic "ignore the rest of this line."

You also have two CD-ROMs in there--one for Breezy, one for Hoary. Breezy and Hoary repositories should not be mixed.

Go here and get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Pick only Hoary _or_ only Breezy**--don't pick both!

---

### Post by beej101 on 2006-03-16
i've replaced the sources.list file and it seems to be working guys... thanks!

---

### Post by beej101 on 2006-03-16
now i'm screwed!

i followed everything and when I clicked "Apply" from Synaptic it always stops at the point where it's trying to replace kdevelop and something about replacing kdevelop3 with kdevelop3, i can't remember the exact error message cuz when synaptic stopped, i rebooted and now i can't log-in with the GUI anymore.  i don't want to reinstall or upgrade for now as i want to keep my previous settings etc. which i need and i have to finish something i am working on.  is there a way to fix the GUI without having to do anything drastic?

i think the only part where i made a mistake is leaving the ubuntu5.10 cd in the drive while upgrading with synaptic, instead of 5.04 which is what is installed.

thanks for any help

---

### Post by Pragmatist on 2006-03-16
> i rebooted and now i can't log-in with the GUI anymore. i don't want to reinstall or upgrade for now as i want to keep my previous settings etc.

So what do you get when you boot the computer?  A black screen with white text and a login prompt?

In the meantime, login using your regular username and type this:
```
startx
```

Then give us the output of this command:
```
ls /etc/init.d | grep dm
```

---

### Post by aysiu on 2006-03-16
My guess is that the mix of Hoary and Breezy repositories is what messed you up.

I know there's a way in Synaptic to tell apt-get to prefer a particular version, but I don't know how to do that from the command-line.

If no one else offers you advice on how to stick with Hoary, I'd do this:

```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace all the *hoary* references with *breezy* and save (control-x), confirm (y), and exit (Enter). ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by beej101 on 2006-03-16
guys, thanks for the effort... i've decided to re-install... :mad: 
why when i install with my 5.10 install cd i didn't get a GUI working as well? it was a complete install... so now i'm going back to reinstalling, this time with my 5.04 which i burned to cd from a mirror site. thanks heaps!

---

