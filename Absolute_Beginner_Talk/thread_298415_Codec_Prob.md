---
title: "Codec Prob"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Mrpelletier on 2006-11-12
I know there is at least 100 codes threads in the forums but i just cant seem to find out how to get any of them put to use i just need help on being able to play Mp4 and xvid . Is there somthing i can type in the terminal to get these codecs???? please help](*,)

---

### Post by jd65pl on 2006-11-12
Try getting automatix and installing the media codecs using it. Use the code below in terminal.

```
sudo aptitude update
sudo aptitude install automatix
```

---

### Post by kewldude606 on 2006-11-12
I typed this before the guy above me posted.  Follow his/her advice :).

The official Xvid site references the Debian Unofficial site to install the codec.

Installation instructions are here: [http://www.debian-unofficial.org/installation.html](http://www.debian-unofficial.org/installation.html)  For the ${DIST} thing, you can just put sarge.

Follow the 1st half of that, then do a sudo aptitude update.  Finally, do sudo aptitude install xvidcap xvidcore.

---

### Post by jd65pl on 2006-11-12
Note that debian pkgs may not be the same as the ubuntu supplied versions.

---

### Post by Mrpelletier on 2006-11-12
> **jd65pl said:**
> Note that debian pkgs may not be the same as the ubuntu supplied versions.

Yes i couldnt install that way also the first code did nothing i realy am having trouble installing these stupid codecs not stupid but it shouldnt be so hard. Is there a way to install divx player for linux i downloaded it but dont know how to install it.

---

### Post by jd65pl on 2006-11-12
> **Mrpelletier said:**
> Yes i couldnt install that way also the first code did nothing i realy am having trouble installing these stupid codecs not stupid but it shouldnt be so hard. Is there a way to install divx player for linux i downloaded it but dont know how to install it.

Aren't there instructions on the website you got it from? If you are just starting out in linux and want instant mpeg functionallity I recommend you use automatix as per my original post.

---

### Post by DannyG on 2006-11-12
I had the same troubles, and I tried to install a bunch of various codecs but none seemed to do the trick.

Instead I installed MPlayer, which had divx and xvid codecs built into it.

```
sudo apt-get install mplayer
```

Let me know if this works for you...

Daniel.

---

### Post by Mrpelletier on 2006-11-12
> **DannyG said:**
> I had the same troubles, and I tried to install a bunch of various codecs but none seemed to do the trick.

Instead I installed MPlayer, which had divx and xvid codecs built into it.

```
sudo apt-get install mplayer
```

Let me know if this works for you...

Daniel.

Nope something went wrong "its my frikin computer piece of crap since i baught it" the following message shows up or this is what went on in the terminal. "mrpelletier@mrpelletier-laptop:~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
":confused:

---

### Post by Mrpelletier on 2006-11-12
> **jd65pl said:**
> Aren't there instructions on the website you got it from? If you are just starting out in linux and want instant mpeg functionallity I recommend you use automatix as per my original post.

Ok i did type in youre code some activity went on if you would like what it said i can type it in again but nothing happend actualy some stuff did but little i went to applicatians and did not see it so i tryed playing an xvid in the default player and it didnt work. 

I thank you all for the help this is a first in these forums.

---

### Post by DannyG on 2006-11-12
Make sure you have all the repositories available. sudo vi ```
/etc/apt/sources-list
``` and remove the '#' from infront of ALL the URL-type lines.

Then do sudo ```
apt-get update
``` This will update your repository list and give you access to more software.

After you've done that try ```
sudo apt-get install mplayer
``` again.

Daniel.

---

### Post by jd65pl on 2006-11-12
See the information on this page on how to install automatix specifically the ubuntu section, it will help you get all the required codecs and media players.

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by Mrpelletier on 2006-11-12
mrpelletier@mrpelletier-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


that is what shows up :confused: :confused: :confused: it wont let me change sources eather:confused: :confused:

---

### Post by DannyG on 2006-11-12
Sorry that was my own fault, it should be ```
sudo vi /etc/apt/sources.list
``` and ```
sudo apt-get update
``` Incase you didn't know, putting "sudo" infront of a command runs that command in root mode (i.e. full administrative mode), which is why it will prompt you for your admin password the first time you run it per session.

---

### Post by kosmic on 2006-11-12
Just open a terminal and type :
```

wget -c -O /tmp/w32codecs.deb http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
wget -c -O /tmp/libdvdcss2.deb http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb
sudo dpkg -i /tmp/w32codecs.deb /tmp/libdvdcss2.deb
```

It will install all the codecs you need and also the library needed for you to watch encrypted DVDs (comercial Dvds)

---

### Post by Mrpelletier on 2006-11-12
I tried everything and still i can't play xvid:confused: :confused: :confused: :confused:  is it possable i just cant use codecs????

---

