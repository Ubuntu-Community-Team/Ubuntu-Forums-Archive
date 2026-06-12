---
title: "how to install apps"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by feest on 2006-08-04
just as says above... how to install apps, no matter what extenstion i got to know the basics of them all right? so how do i install apps...

---

### Post by patrick295767 on 2006-08-04
> **feest said:**
> just as says above... how to install apps, no matter what extenstion i got to know the basics of them all right? so how do i install apps...

[http://ubuntuforums.org/showthread.php?t=229406](http://ubuntuforums.org/showthread.php?t=229406)

---

### Post by rck_hitokiri on 2006-08-04
you can go to this website.
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

or just google everythin you wanna ask about things.
it helps... thx

---

### Post by Jagot on 2006-08-04
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by em3raldxiii on 2006-08-04
Here's a super brief outline too:
 
Apps come as "packages". There are several ways to install them.
 
1. Using an installation manager such as Synaptic. Open the program, find your app, install it. Synaptic will automatically download/install the app.
2. Using apt-get in the command line. You would be surprised how many cool apps you can install with little trouble. If you find reference to an app (such as **gxine** which is a great media player). You simply open your terminal program, type in: **sudo apt-get install *appname*** and voila! It downloads & installs. Then it's (usually) in your programs menu.
 
3. Download the appropriate package (usually a .deb file), and double-click it. If you have **gdebi** it should run and automatically install. (if you don't have gdebi, then type this in your terminal: sudo apt-get install gdebi)
 
That's the quick & dirty. Now go read all the tutorials that were linked for more information. It's WAYYYY easier (IMO) than in Windows. :D
 
Mike
 
PS. As always, please feel free to correct me!

---

### Post by Jagot on 2006-08-04
If you're installing from repositories though try and use aptitude rather than apt-get.  Read about it here:

[http://psychocats.net/ubuntu/aptitude.php](http://psychocats.net/ubuntu/aptitude.php)

---

### Post by em3raldxiii on 2006-08-04
Yeah, you're definitely right.  Unfortunately, I started the bad apt-get habit long before I knew of the existance of the aptitude command.  I'm still just breaking out of newbieness, so perhaps i still have a chance :D

---

### Post by feest on 2006-08-05
but what if i find a random linux application on the net how do i install it if i don't have the source yet?

for example:

[http://www.ac3d.org/downloads.html](http://www.ac3d.org/downloads.html)

how do i install that?

---

### Post by em3raldxiii on 2006-08-05
I had a look. Okay, here's the scoop (you can click their More Info link by the AC3d for Linux download link for more information).
 
1. The original package appears to be in .RPM format which is a package originally designed for Red-Hat oriented Linux distributions. This may mean nothing to you, and that's okay. Ubuntu is based on Debian (there are several "grandfather" distributions - Red Hat and Debian are two of these), so you need a .DEB package. (actually, others will argue that you can use probably RPM just fine, but I've never done so).
 
2. In their little forum, there may indeed be a link to a .deb package, in which case you *should* be able to just download it and double-click it to install it, and that could potentially be all you need to do.
 
3. If you HAVE to use the RPM package, there are likely several ways. I don't necessarily know the "easiest" way, but here's my method: I installed a program called **alien** which allows you to use RPMs ... in your terminal or command line editor, do this after you've downloaded the RPM file.  Remember where you saved it.  Remeber that pressing <tt>TAB</tt> will auto-complete when you are using the terminal to type long addresses.
```
sudo apt-get install alien
sudo alien -i /your/directory/name_of_package.rpm
```
 
Alien might also be in Synaptic ... I've never checked.

---

