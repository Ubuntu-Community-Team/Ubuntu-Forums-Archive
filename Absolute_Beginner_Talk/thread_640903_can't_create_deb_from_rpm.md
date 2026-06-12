---
title: "can't create deb from rpm"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Muscar on 2007-12-14
when i do: 
cd home/******/desktop
sudo alien -d  ImageMagick-6.3.7-4.i386.rpm

it says:
mkdir: cannot create directory `ImageMagick-6.3.7': File exists
unable to mkdir ImageMagick-6.3.7:  at /usr/share/perl5/Alien/Package.pm line 257.


what is wrong?!  :confused:

---

### Post by taurus on 2007-12-14
Try the **D**esktop instead of desktop since Unix/Linux is case sensitive.  On the other hand, imagemick is available from the repos so why even bother with the rpm file!

---

### Post by Joeb454 on 2007-12-14
Also check what the *-d* flag does, because your error is saying it can't create a directory, which is a bit odd IMO

---

### Post by rsambuca on 2007-12-14
Is the version of imagemagick in the repos not good enough for your needs?

---

### Post by Muscar on 2007-12-14
i've tried to instal the repos, but it won't work. and the one im trying to instal is the latest one so.

as soon a i trped make install from the repos it gave me an error. i've never been able to instal from repos for some reason.

---

### Post by Muscar on 2007-12-14
nvm, i fixed it, thanks for the help :lolflag:

---

### Post by llamakc on 2007-12-14
Please mark thread as SOLVED using the thread tools.

---

### Post by daengbo on 2007-12-14
Even though this is solved, I'd like to chime in that it's generally a bad idea to install software from outside the repositories, especially using a binary converter like alien.

Muskar, you'd be better off trying to figure out what you did wrong in order to get the repo to work than to destabilize your machine by installing a package not designed for it. Add/Remove should install ImageMagick with no problem.

---

### Post by rsambuca on 2007-12-14
> **Muscar said:**
> i've tried to instal the repos, but it won't work. and the one im trying to instal is the latest one so.

as soon a i trped make install from the repos it gave me an error. i've never been able to instal from repos for some reason.

If you have never been able to install from the repos, then perhaps your repositories aren't set up properly.  Post the output of

cat /etc/apt/sources.list

---

### Post by resma on 2007-12-17
> **rsambuca said:**
> Is the version of imagemagick in the repos not good enough for your needs?

I'm also having problems with the ImageMagick version (6.2.4) that is in the repos. The convert commandline tool seems buggy to me. For example the -extent option should extent images with the background color, but instead black is used always. Also, tiffs are written with min-is-black always.

The version in the repos is over two years old, whilst ImageMagick is still being actively developed. The usage of a newer ImageMagick version solves these issues.

---

### Post by stchman on 2007-12-17
Yes imagemagick is in the Gutsy repos.

```
sudo apt-get -y install imagemajick
```

Granted it is V6.2.4.5 and you have V6.3.7 but I would go with the repo version.

You can try building it from the source:

get the file from here:

[ftp://ftp.imagemagick.org/pub/ImageMagick/ImageMagick.tar.gz](ftp://ftp.imagemagick.org/pub/ImageMagick/ImageMagick.tar.gz)

place the downloaded file in your home directory and do the following in a terminal:

```

cd ~
tar -vxzf ImageMagick.tar.gz
cd ImageM*
./configure
make
sudo make install

```

The program will be installed in your /usr/local/bin folder.

---

