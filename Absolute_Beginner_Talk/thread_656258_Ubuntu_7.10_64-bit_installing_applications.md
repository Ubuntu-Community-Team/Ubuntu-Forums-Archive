---
title: "Ubuntu 7.10 64-bit installing applications"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by teshne on 2008-01-02
I know there are quite a lot of topics about 64-bit editions but I have this question that I couldn't find an answer for.

I am planning to install Gusty 64-bit on my laptop  (possibly dual boot with 32-bit for a while until happy with it).
My question is, when I want to install applications (normal ones..say for example I want to install VLC) do I have to do anything different for the 64-bit version? Do i just go to synaptic package manager and install the packages or do i need to install from the terminal and add some switches?

Many thanks!.

---

### Post by LowSky on 2008-01-02
most stuff will install just fine. remember to enable all the repos

here is a few that i would do off the bat is add medibuntu to your install, it willgive you more programs and help to enable dvd and other codecs

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
dvd support
```
sudo apt-get install libdvdcss2
```

NOTE: this is installs codecs for 64bit only if you need 32bit change w64 to w32
```
sudo apt-get install w64codecs

```

---

### Post by Ub1476 on 2008-01-02
If there are x64 packages available (otherwise it will say this application can not be installed on amd64), it will install like it does on 32bit.

---

### Post by Perfect Storm on 2008-01-02
Well, so far the only diffrent/difficult I ran into is java in browser - but there's a solution to this. Soon when sun java 1.7 is out it will support 64-bit full.


Other than that everything is the same.

---

### Post by teshne on 2008-01-02
Thanks guys! I shall be installing it today then.

Cheers.

---

### Post by gn2 on 2008-01-02
You may want to look at this to get Flash working: [http://ubuntuforums.org/showpost.php?p=2863873&postcount=1](http://ubuntuforums.org/showpost.php?p=2863873&postcount=1)

I switched over to 64-bit yesterday and it's significantly less problematic than I had anticipated.

In fact there are no problems at all with it on my PC.

---

### Post by wasportamenteff on 2008-01-02
> **LowSky said:**
> most stuff will install just fine. remember to enable all the repos

here is a few that i would do off the bat is add medibuntu to your install, it willgive you more programs and help to enable dvd and other codecs

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
dvd support
```
sudo apt-get install libdvdcss2
```

NOTE: this is installs codecs for 64bit only if you need 32bit change w64 to w32
```
sudo apt-get install w64codecs

```

thanks. I should be watching dvd here shortly. I just installed this new Gusty Gibbon

---

### Post by teshne on 2008-01-02
I have just finished installing it and so far no problems. When booting with the live cd it wouldn't automatically detect my graphic card and started in low res, not a problem but the 32-bit edition worked fine, once installed this version seems to be ok though.
This is my 4th installation of Ubuntu in 4 days...messed up a few times when setting up dual boot with the windows partitions (it's a new laptop and until I can get all the hardware working in Ubuntu I want to keep my Vista partition installed, I would go for XP as my backup partition for Ubuntu but I can't get the drivers for XP neither!!), but hey! that's the way I learn.

Thanks

---

