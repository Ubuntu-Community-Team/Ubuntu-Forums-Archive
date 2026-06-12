---
title: "[SOLVED] Could not download all repository indexes"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Dwiman89 on 2007-10-03
Hey for some reason im getting this when I try  to reload Synaptic...

Could not download all repository indexes;
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)

I have tried to change the sources.list by copying and pasting other sources list from elsewhere and got the same effect. My internet connection is fine and i dont think the servers would be down for weeks now. There are 2661 packages listed and 1072 installed. can you please help me?

---

### Post by rsambuca on 2007-10-03
Post the output of 

cat /etc/apt/sources.list

---

### Post by Dwiman89 on 2007-10-03
$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

### Post by rsambuca on 2007-10-03
The repos look OK for me, sorry I don't know how to fix this.  My guess is that one of the packages you already have installed is not longer in the repos for some reason, and there is a problem trying to check it for updates.

---

### Post by greenstar on 2007-10-03
Let's try the terminal:

First let's test the repo, your connection, Packages.gz and gzip:
```
wget -nv http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz
```Then open your home directory and click on Packages.gz to open with archive manager to verify contents. Inside should be a single text file named Packages. Click <Extract>, then <Extract> on the next dialog. Open the Packages file in your /home. The first four lines should be:

Package: abiword
Priority: optional
Section: gnome
Installed-Size: 7004

If things are ok so far, then let's do:

To clear your partial apt lists:
```
 sudo rm /var/lib/apt/lists/partial/*
```Then try these to test the fix:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude -f install
```If this doesn't help, try changing the protocol on your repos in sources.list from http:// to ftp://

Do:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.gzerror
sudo gedit /etc/apt/sources.list
```Then use gedit's Search->Replace
Search for: http
Replace with: ftp
Make sure Wrap Around is checked
Click <Replace All>

Then do again:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude -f install
```Hope this helps,
Greenstar

If this helps, th[COLOR=Black]e [/COLOR][COLOR=Black]credit goes to the folks who contributed to [/COLOR][COLOR=Black]the following thread f[/COLOR]or sharing their experience & knowledge:
[http://ubuntuforums.org/archive/index.php/t-9944.html](http://ubuntuforums.org/archive/index.php/t-9944.html)

---

### Post by hyper_ch on 2007-10-03
Could be that the repo server is currently down, then you'll get a message like that.

---

### Post by Dwiman89 on 2007-10-03
It worked thank tou for your help. :)

---

### Post by greenstar on 2007-10-04
It would be of use to the community if you would share which steps corrected your problem. If you don't post your experiences, this thread won't be as helpful to those who come after you. 

Thanks,
Greenstar

---

### Post by Dwiman89 on 2007-10-04
> **greenstar said:**
> It would be of use to the community if you would share which steps corrected your problem. If you don't post your experiences, this thread won't be as helpful to those who come after you. 

Thanks,
Greenstar

Well I just followed your directions above and it worked. I dont really know how all of this works or what was really wrong with it in the first place...

---

### Post by Malibu Illusion on 2007-10-04
> **greenstar said:**
> 
```
 sudo rm /var/lib/apt/lists/partial/*
```

This was all that was needed here.  These errors are typically the result of partial files that cannot be dealt with by gzip.

---

### Post by greenstar on 2007-10-07
Thanks for wrapping that up, Malibu. 

Greenstar

---

