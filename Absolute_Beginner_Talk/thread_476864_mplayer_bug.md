---
title: "mplayer bug"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by waxyfresh on 2007-06-17
im trying to fix this bug in mplayer

 [http://ubuntuforums.org/showthread.php?p=2843575](http://ubuntuforums.org/showthread.php?p=2843575) 

but i keep getting this error:

E: You must put some 'source' URIs in your sources.list

---

### Post by mitch.c on 2007-06-18
> **waxyfresh said:**
> im trying to fix this bug in mplayer

 [http://ubuntuforums.org/showthread.php?p=2843575](http://ubuntuforums.org/showthread.php?p=2843575) 

but i keep getting this error:

E: You must put some 'source' URIs in your sources.list
In the steps you are following, you issue the following command:
```
sudo apt-get source gstreamer0.10-pitfdll
```
This instructs apt-get to pull the source for the gstreamer package. My guess is you don't have any source URI's (just what the error says) in /etc/apt/sources.list

So, fire up a text editor like this:
```
gksudo gedit /etc/apt/sources.list
```
And then look for the universe source repository (that's where the gstreamer0.10-pitfdll lives) line, and remove the '#' at the front of the line. It should look like this:
```
# If you are using feisty, replace 'edgy' with 'feisty'
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe
```

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

