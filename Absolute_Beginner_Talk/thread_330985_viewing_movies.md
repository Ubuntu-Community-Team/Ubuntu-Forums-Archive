---
title: "viewing movies"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by RHS on 2007-01-03
Help!  I cannot view any of the traditional movie clips, wmv, avi, etc. with the totem movie player.  I have done my level best to try and understand plug ins, etc and I am really feeling frustrated at this point.  Will this be easy or hard to solve for someone like me?  PLEASE help!
Thanks in advance

---

### Post by taurus on 2007-01-03
You need to install the codecs first.  You can do that with automatix2.  So, install automatix2 first and use it to install everything else you need for the multimedia stuff...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by scrooge_74 on 2007-01-03
You can also install them using synaptics and install the codecs from the repositories

---

### Post by borris.morris on 2007-01-03
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
 works to get all the stuff *at least i think so.*

---

### Post by Hendrixski on 2007-01-03
even easier
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

This site has everything you need, including the following:
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

and this for DVD's

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

It's all in the manual

---

### Post by RHS on 2007-01-03
Help again!  I accidentally installed the version for 6.10 and my version is 6.06 and it wont let me reinstall until I delete the 6.10 version.  I don't even know how to get to this "terminal mode"!  What do I do?  Thanks!

---

### Post by zmuth734 on 2007-01-04
I tried setting everything up and I'm getting these lines and it seems like its a bad quality video but I'm playing a retail dvd.
Screenshot:
[http://img518.imageshack.us/img518/3783/screenshot0jx4.png](http://img518.imageshack.us/img518/3783/screenshot0jx4.png)

---

### Post by taurus on 2007-01-04
> **RHS said:**
> Help again!  I accidentally installed the version for 6.10 and my version is 6.06 and it wont let me reinstall until I delete the 6.10 version.  I don't even know how to get to this "terminal mode"!  What do I do?  Thanks!

Are you talking about automatix2?

Applications -> Accessories -> Terminal
```
sudo aptitude remove automatix2
```
Then, edit your /etc/apt/sources.list and replace the word edgy to dapper and install it again...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by RHS on 2007-01-04
where do you type it in at???????????

---

### Post by taurus on 2007-01-04
Applications -> Accessories -> Terminal

---

### Post by RHS on 2007-01-04
ok i found the terminal mode and remove automatix2. now where do i find "/etc/apt/sources.list"?

---

### Post by taurus on 2007-01-04
From a terminal, edit your /etc/apt/sources.list with this command.

```
gksudo gedit /etc/apt/sources.list
```
Then, replace the word **edgy** with **dapper** for automatix's site and save it.  Then run

```
sudo aptitude update
sudo aptitude install automatix2
```

---

