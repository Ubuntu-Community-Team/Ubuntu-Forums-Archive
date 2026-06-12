---
title: "xubuntu-desktop"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-02
Hi all.
I'v installed drapper drake on a pc (with 128 RAM) which is not connected to internet; from the terminal I wrote 

sudo aptitute install xubuntu-desktop 

I got back this message: couldn't find package xubuntu-desktop 

How can I install it? Can I download the package on a usb pen and install it on the new pc?

Thanks for any hint.

---

### Post by missmoondog on 2006-12-02
don't mean to sound like a wise guy, but what did you think was going to happen when you typed that in without an internet conection? that's dapper drake also. wouldn't hurt to get at least another 128mb's memory too.

to answer your question though, yes, you can.

---

### Post by helphope on 2006-12-02
> **missmoondog said:**
> don't mean to sound like a wise guy, but what did you think was going to happen when you typed that in without an internet conection? that's dapper drake also. wouldn't hurt to get at least another 128mb's memory too.

to answer your question though, yes, you can.

Thanks for answering. The point is that I thought the xubuntu-desktop package was already in the repos.

---

### Post by funkydan2 on 2006-12-02
xubuntu-desktop is what's called a "meta package" in that it doesn't have any files in the package rather it just has a list of other packages (like xfce, abiword etc.) to install.

Without Internet access on that machine, I'd recommend downloading the [xubuntu cd]("http://xubuntu.org/get") and starting again.

Alternatively, if you can take your machine somewhere where it can get on the net, then you'll need to [activate "universe"]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html") and then "sudo apt-get install xubuntu-desktop"

---

### Post by funkydan2 on 2006-12-02
> **helphope said:**
> Thanks for answering. The point is that I thought the xubuntu-desktop package was already in the repos.

It is - but a "repository" (normally) means a server on the internet.  Unfortunately the packages required to install xubuntu-desktop aren't provided on the Ubuntu install CD.

Also, Xubuntu has improved dramatically between 6.06 (Dapper) and 6.10 (Edgy).  I'd recommend running the newest version of Xubuntu anyday.

---

### Post by helphope on 2006-12-02
Things are getting clearer. Thanks.

What about if I install Xubuntu along with windows '98 and Ubuntu?

At the moment at the bootstrap I can choose between windows and drapper, is that possible to add a third option, that is Xubuntu?
:confused:

---

### Post by lamego on 2006-12-02
If you are planning to use xubuntu because you have an older hw you should not install the "usual" ubuntu in the first place, you should start with a fresh xubuntu install cd.

---

### Post by seshomaru samma on 2006-12-02
Do you find Ubuntu slow?
If you want Xubuntu without reinstalling you can try this :
take the Ubuntu live CD to a computer with an internet connection . Install XFCE (the Xubuntu desktop environment) like this:
```
sudo apt-get install xubuntu-desktop
```
Ubuntu will download a bunch of packages which you can later find in this directory:
/var/cache/apt/archives
you can then copy them to a USB flash or CD and then install them manually (by clicking on them) on your internet-less Ubuntu.
Now you will have an Ubuntu with two desktop environment: Gnome (=the default environment ) and XFCE (=Xubuntu). You can choose which one to log into by clicking the 'sessions' bar in the login screen. You will not need to install both Xubuntu and Ubuntu.
If you find Xubuntu to be still slow I recommend trying Puppy Linux ,it is very very fast and easy to configure . It's ideal for low-specs machines with no internet connection .
Good Luck

---

### Post by Bachstelze on 2006-12-02
You could also get a Xubuntu CD and install xubuntu-desktop from it.

---

### Post by helphope on 2006-12-02
Thanks for replying.
What about Xubuntu 6.10 along with Drapper? Any hint?
Thanks

---

### Post by Caraibes on 2006-12-02
I have Xubuntu Dapper on my laptop (Celeron 496Mhz, 192 megs of ram...).

I tried Xubuntu Edgy, but came back to Dapper with a clean install because it is just more stable : FF doesn't crash, Skype doesn't freeze the PC when turned on, Real Player installs just fine...

What I did was a clean install of the alternate CD of Xubuntu 6.06.1, then used Automatix, to install the rest... Automatix works really well !

I also use Nautilus in Xubuntu as it provides a wonderfull GUI tool to share files between Linux & Windoze PC's...

I feel I have now the perfect distro for an older laptop !

(I have a PCMCIA wireless card, RTL8180, it works out of the box !)

8)

---

### Post by mephcpp on 2006-12-02
I had dapper then upgraded to edgy and now I'd like to try xfce. Here is what I get when trying to install this meta package:

> #apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xubuntu-desktop: Depends: xorg but it is not going to be installed
E: Broken packages

any hints?

---

### Post by seshomaru samma on 2006-12-03
mmmm
can you post your sources list?

---

### Post by maddog39 on 2006-12-03
I would try:
```

apt-get install xfce

```
instead because thats what I did and it worked fine. It also downloaded all the packaged applications with Xfce, such as abiword and stuff. Also, just and FYI, I ran Xubuntu on my Pentium D 930 (Dual Core 3.0GHz) with 1GB of RAM for ages until deciding to go back to Ubuntu. But the point is Xubuntu isn't just for slow/older PCs, it also works extremely well as a high performance OS on newer machines. Just a misconception by many people.

---

### Post by aysiu on 2006-12-03
> **HymnToLife said:**
> You could also get a Xubuntu CD and install xubuntu-desktop from it.
Make sure you use the Alternate CD, though, instead of the Desktop CD.

You cannot do ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` with the Desktop CD.

---

### Post by mephcpp on 2006-12-03
# cat /etc/apt/sources.list |grep -v "#"

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://ftp.iasi.roedu.net/ubuntu](http://ftp.iasi.roedu.net/ubuntu) edgy main restricted universe multiverse
deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious

---

### Post by helphope on 2006-12-03
this seems to be great.

> **aysiu said:**
> Make sure you use the Alternate CD, though, instead of the Desktop CD.

You cannot do ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` with the Desktop CD.

I've got the alternate CD (both drapper and 6.10); if I understand well

from terminal I must write 

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` 

I've got Ubuntu drapper; can I install xubuntu-desktop 6.10?

thanks

---

### Post by aysiu on 2006-12-03
> **helphope said:**
> this seems to be great.



I've got the alternate CD (both drapper and 6.10); if I understand well

from terminal I must write 

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` 

I've got Ubuntu drapper; can I install xubuntu-desktop 6.10?

thanks
Yes.

The first command will allow you to add the Alternate CD as a repository source.

The second command checks to see what's in the source.

The third command installs Xubuntu from the source.

---

### Post by helphope on 2006-12-03
Thanks a lot aysiu.

Your answers are very clear. Compliments

---

### Post by bobbybobington on 2006-12-15
Hi all, I tried installing XFCE (from ubuntu dapper) with 'sudo aptitude update&&sudo aptitude install xubuntu-desktop' command and everything ran great utill it got to 'Setting up abiword-help (2.3.3-0ubuntu5) ...' then it just hangs there. So i quit the terminal, fired it up again and tried the installation command again. I ran 'sudo dpkg --configure -a' to continue but again it hangs when setting up abiword-help. The help for abiword sounds like a trivial thing, is there a way to skip that package? Any help would be much appreciated.

---

