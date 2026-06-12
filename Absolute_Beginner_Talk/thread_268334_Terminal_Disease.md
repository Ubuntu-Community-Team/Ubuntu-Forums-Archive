---
title: "Terminal Disease?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-09-30
Whenever I try to install anything using the "sudo apt-get install" for anything, I get here: Connecting to us.archive.ubuntu.com (1.0.0.0), but I guess I'm not connected to the internet ](*,) YES I AM! CONNECT!  Why wont it connect and let me download?

---

### Post by K.Mandla on 2006-09-30
I'm not sure because I'm at work, but I'm guessing the repositories are bogged down with requests. 

You can, if you like, switch to repositories elsewhere in the world and see if they're of any use to you.

You'll need to directly edit your sources.list file to do that. Back it up first, just to be safe.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bkp
```
Then edit the file directly.

```
sudo nano /etc/apt/sources.list
```
Change anything that starts with "us." to "uk." (for the UK) or maybe "de." (for Germany) or "be." (for Belgium ... hey, it worked for me once when nothing else would ;) ). Of course, if you're not in the US, you'll have a different country there to start with.

Save the file with CTRL+O and exit with CTRL+X.

Then

```
sudo aptitude update
```
and try your install command again. Good luck! ;)

P.S.: If you make a mistake or you want to revert to the old list, enter

```
sudo cp /etc/apt/sources.list.bkp /etc/apt/sources.list
```
and *sudo aptitude update* again. ;)

---

### Post by Zyzzyx on 2006-09-30
Could be a problem with your sources.list file.  Post the output of *cat /etc/apt/sources.list* and that'll give folks a good start on something to look at.



*edit: ok, so K.Mandla beat me to it, with some better commentary too*

---

### Post by OptimusPrime on 2006-09-30
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by morphodone on 2006-09-30
Someone else had this problem...

[http://www.ubuntuforums.org/showthread.php?t=268302](http://www.ubuntuforums.org/showthread.php?t=268302)

---

### Post by Zyzzyx on 2006-09-30
I think I'd follow K.Mandla's instructions, but one thing you could do as well is to just remove the "us." from the URLs there. Looking at my sources file, I don't have 'us', 'uk', or anything. Just *[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)*.

---

### Post by K.Mandla on 2006-09-30
> **Zyzzyx said:**
> I think I'd follow K.Mandla's instructions, but one thing you could do as well is to just remove the "us." from the URLs there. Looking at my sources file, I don't have 'us', 'uk', or anything. Just *[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)*.
Really? Almost all of mine are prefixed with "us." ... that's funny. I wonder ... do you use the straight Ubuntu CD to install? I usually start with the Xubuntu 6.06.1 install CD. 

Curiouser and curiouser. :-k 

EDIT: ACK! I know what it is. I built a custom sources.list file at [www.ubuntulinux.nl](www.ubuntulinux.nl), and I've been using that. That's why. Cheers. :mrgreen:

---

### Post by _duncan_ on 2006-09-30
The suggestion of Zyzzyx might work. I remember having the same problem a month ago. I checked the sources.list file, removed "ph." from all the URLs, then reloaded the package list via synaptic. It worked and I was able to install packages from the repo.

BTW, I think the Ubuntu installer customizes the sources.list file according to the time zone entered by the user during installation. In my case, I entered Asia/Manila (Philippines) as my time zone during install, hence the "ph." prefix on some URLs. I could be wrong though...

---

