---
title: "[SOLVED] need help installing vdrift from source"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-10-12
Trying to install vdrift from source. Have installed linux headers and also have a file called vdrift-2007-03-23-src. Where do I go to from here? Everything I try doesn't work. Have not tried compiling from source before. (I know there is a deb package from getdeb, but I want to learn how to install from source).

---

### Post by taurus on 2007-10-12
Usually, these are the steps that you need to do to build and install something from source.

```
tar xvzf filename.tar.gz
cd filename
./configure
make
sudo make install
```

---

### Post by bumanie on 2007-10-12
> **taurus said:**
> Usually, these are the steps that you need to do to build and install something from source.

```
tar xvzf filename.tar.gz
cd filename
./configure
make
sudo make install
```

I have been trying to follow those same instructions. Vdrift is a tar.bz2 file, however when I get up to the cd filename part, everything goes wrong. Maybe I am writing the wrong thing there. I don't know.
Here is a screen shot (I am not sure how to attatch a screen shot. Hopefully this is correct).
/home/ian/Desktop/Screenshot-ian@ian-: ~-Desktop.png
Obviously that is not how to attatch a screenshot!

---

### Post by taurus on 2007-10-12
If it's tar.bz2, then you need to uncompress/tar it with

```
tar xv**[COLOR="Blue"]j[/COLOR]**f filename.tar.bz2
```

If you tell me where you've download it, then I can have a look and tell you more precise how to build and install it.

p.s.  No pic!

---

### Post by bumanie on 2007-10-12
> **taurus said:**
> If it's tar.bz2, then you need to uncompress/tar it with

```
tar xv**[COLOR="Blue"]j[/COLOR]**f filename.tar.bz2
```

If you tell me where you've download it, then I can have a look and tell you more precise how to build and install it.

p.s.  No pic!

I have downloaded it to my desktop. The install was going well until I got to the point of cd filename.
Thanks for your help. How do I attatch a screenshot?

---

### Post by taurus on 2007-10-12
You need to replace filename with the actual name of the new directory that it creates.  

What's the output of this command from a terminal then?

```
ls -la ~/Desktop
```

In the [COLOR="Red"]Additional Options[/COLOR], click the **Manage Attachments** and **Browse** to where the image on your computer is located.

---

### Post by Dr Small on 2007-10-12
[quote=bumanie]Thanks for your help. How do I attatch a screenshot?[/quote]
Oh my goodness. Did you not read taursus' post ?
[quote=taursus]p.s. No pic![/quote]

Really, you were not installing it up to the point of Cd. You were extracting the archive. The real installation is when you configure it and make install it.

Dr Small

---

### Post by bumanie on 2007-10-12
> **taurus said:**
> You need to replace filename with the actual name of the new directory that it creates.  

What's the output of this command from a terminal then?

```
ls -la ~/Desktop
```

In the [COLOR="Red"]Additional Options[/COLOR], click the **Manage Attachments** and **Browse** to where the image on your computer is located.

Here is the original screenshot
Followed by the second you asked for (at least I hope this is working)

---

### Post by bumanie on 2007-10-12
> **Dr Small said:**
> Oh my goodness. Did you not read taursus' post ?


Really, you were not installing it up to the point of Cd. You were extracting the archive. The real installation is when you configure it and make install it.

Dr Small

I am trying to follow taurus' suggestions. I am new to this and am finding it difficult. When I input ./configure 'no such file or directory' appeared. That is why I  am lost now.

---

### Post by taurus on 2007-10-12
Try

```
cd ~/Desktop/**[COLOR="Blue"]vdrift-2007-03-23-src[/COLOR]**  <-- you need to change to that directory first.
sudo aptitude update
sudo aptitude install build-essential  <-- you need build-essential package if you want to build something from source.
./configure
make
sudo make install
```

---

### Post by bumanie on 2007-10-12
> **taurus said:**
> Try

```
cd ~/Desktop/**[COLOR="Blue"]vdrift-2007-03-23-src[/COLOR]**  <-- you need to change to that directory first.
sudo aptitude update
sudo aptitude install build-essential  <-- you need build-essential package if you want to build something from source.
./configure
make
sudo make install
```
As can be seen from the screenshot ./configure is not doing what it supposed to.

---

### Post by taurus on 2007-10-12
What about the output of the second command?

```
cd ~/Desktop/vdrift-2007-03-23-src
ls -la
```
Again, if you tell me where you downloaded that vdrift, I can have a look and tell you exactly how to install it instead of asking and trying to get an answer from you...

---

### Post by bumanie on 2007-10-12
> **taurus said:**
> What about the output of the second command?

```
cd ~/Desktop/vdrift-2007-03-23-src
ls -la
```
Again, if you tell me where you downloaded that vdrift, I can have a look and tell you exactly how to install it instead of asking and trying to get an answer from you...
Here's the screenshot

---

### Post by taurus on 2007-10-12
```
cd data
ls -la
```

---

### Post by bumanie on 2007-10-12
> **taurus said:**
> ```
cd data
ls -la
```

Here's the next screenshot

---

### Post by taurus on 2007-10-12
Maybe you need to look at this page.

[http://wiki.vdrift.net/Main_Page](http://wiki.vdrift.net/Main_Page)

---

### Post by bumanie on 2007-10-13
> **taurus said:**
> Maybe you need to look at this page.

[http://wiki.vdrift.net/Main_Page](http://wiki.vdrift.net/Main_Page)

Thanks for the wiki page. I have decided to download the getdeb package. It seems installing from source for vdrift is the least preferred method. Thanks for your help taurus. I think I had done things correctly but installing from source doesn't seem to be viable according to the wiki page. I will mark this as solved and try the getdeb package. Thanks again.

---

### Post by michwill on 2007-11-20
It appears that the source package is an SCONS package.  The "./configure" stuff doesn't apply.  I'm headed to bed, but I'll look more at it later.


Regards.



[http://www.scons.org/](http://www.scons.org/)

---

