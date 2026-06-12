---
title: "Can't Upgrade to wine 0.9.33 :("
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by kingdave9 on 2007-03-18
Hello,

When I try to upgrade to the latest version of wine (0.9.33) in the Synaptic Package manager I get the following error:

wine:
  Depends: libgphoto2-2 (>=2.3.0) but 2.2.1-2ubuntu4 is to be installed
  Depends: libgphoto2-port0 (>=2.3.0) but 2.2.1-2ubuntu4 is to be installed

I've never encountered this before, and being a total linux noob I have no clue what to do.

Any help would be appreciated!

---

### Post by bruenig on 2007-03-18
Those packages are in the repo, are you sure you are updated.
```
sudo apt-get update && sudo apt-get upgrade
```

After you do that, try to install wine.

---

### Post by pins2u on 2007-03-18
i have the exactly same problem. and the help above did not work for me. any one please help!! I tried to install libgphoto again but no luck.

---

### Post by JediLow on 2007-03-19
same problem here...

---

### Post by bruenig on 2007-03-19
Ok well here are the debs that are in the repos which for some reason apt isn't seeing for you. You can install them manually like this.

```
wget http://archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.3.0-0ubuntu3~edgy2_i386.deb
sudo dpkg -i libgphoto2-port0_2.3.0-0ubuntu3~edgy2_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.3.0-0ubuntu3~edgy2_i386.deb
sudo dpkg -i libgphoto2-2_2.3.0-0ubuntu3~edgy2_i386.deb

```

After that you should be able to install wine
```
sudo apt-get install wine
```
or through synaptic or whatever else you use.

---

### Post by pixeldotz on 2007-03-19
nice. that worked perfectly for me. word of caution, install libgphoto2-port0_2.3.0-0ubuntu3~edgy2 or you will get an error from the other one.

thanks again.

---

### Post by Gathalimay on 2007-03-19
It worked! Thanks a lot. You :guitar:

---

### Post by M$LOL on 2007-03-19
Any chance of an AMD64 version?

---

### Post by pins2u on 2007-03-19
> **bruenig said:**
> Ok well here are the debs that are in the repos which for some reason apt isn't seeing for you. You can install them manually like this.

```
wget http://archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.3.0-0ubuntu3~edgy2_i386.deb
sudo dpkg -i libgphoto2-2_2.3.0-0ubuntu3~edgy2_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.3.0-0ubuntu3~edgy2_i386.deb
sudo dpkg -i libgphoto2-port0_2.3.0-0ubuntu3~edgy2_i386.deb
```

After that you should be able to install wine
```
sudo apt-get install wine
```
or through synaptic or whatever else you use.


Thank You!

But for me, I had to do libgphoto2-port0_2.3.0 first and then libgphoto2 so for me, the code was 

some reason apt isn't seeing for you. You can install them manually like this.

```
wget http://archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.3.0-0ubuntu3~edgy2_i386.deb
sudo dpkg -i libgphoto2-port0_2.3.0-0ubuntu3~edgy2_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.3.0-0ubuntu3~edgy2_i386.deb
sudo dpkg -i libgphoto2-2_2.3.0-0ubuntu3~edgy2_i386.deb

```

---

### Post by kingdave9 on 2007-03-19
Thanks, worked like a charm :)

---

### Post by YokoZar on 2007-03-19
Hi, I make the packages.  I'm trying to figure out the source of the problem here, as you should have the same libgphoto2-2 version that I do when I built the thing.

What repositories do you have enabled (other than winehq)?  Backports?  Universe?

---

### Post by bruenig on 2007-03-19
> **YokoZar said:**
> Hi, I make the packages.  I'm trying to figure out the source of the problem here, as you should have the same libgphoto2-2 version that I do when I built the thing.

What repositories do you have enabled (other than winehq)?  Backports?  Universe?

The libgphoto stuff is in ubuntu main.

---

### Post by jhardtone on 2007-03-20
Downloading the two mentioned packages and installing them via dpkg breaks kubuntu-desktop and digikam, so I'll stick with 0.9.32 for now.

---

### Post by bruenig on 2007-03-20
> **jhardtone said:**
> Downloading the two mentioned packages and installing them via dpkg breaks kubuntu-desktop and digikam, so I'll stick with 0.9.32 for now.

Breaking kubuntu-desktop doesn't matter, it is just a meta package. I don't know about digikam though.

---

