---
title: "The setup went wrong :( + a question."
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Nordoelum on 2006-03-31
When I installed the Ubuntu 5.10 the installation stopped when I initzilation the plugins for the first time.

I just rebooted and afterward I didn't have any desktop. Did some coding forth and back and finally I got GNOME to run. But it seams like the plugins after the error wasn't installed. I encountered some error with dpkg too, some error 4 shit. But I got that sorted out too. Updated some stuff and got the autometrix(whatever its called).

The question is, can I type a code to get the installation to "reinstall" the whole plugins thing again?

NB! Was some problems with gstreamer I think.

Question: Can't get this to work: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

I don't have a settings button :(

---

### Post by firehead on 2006-03-31
well can't help you on the first one, but you can add universe and multiverse repos quite easily by hand...if you're not afraid to use the konsole ;-)
just edit the file /etc/apt/sources.list (you might want to backup it first,just in case). then to add multiverse repos just remove the ## in front of the repositories you want to enable (it's explained in the file itself...) i.e. change ```
## deb http://security.ubuntu.com/ubuntu breezy-security universe
## deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```
to
```
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

``` there are also lots of threads in this forum about adding extra repositories etc on this forum...e.g.here:[http://www.ubuntuforums.org/showthread.php?t=92672]("http://www.ubuntuforums.org/showthread.php?t=92672")

---

### Post by Mustard on 2006-03-31
If you think part of the installation was incomplete, you could try this..

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Nordoelum on 2006-03-31
Thank you for the help :D

I just reinstalled Ubuntu. And the installation worked just fine now. And jesus how many modules that was left out :(

Hehe..

---

### Post by Mustard on 2006-03-31
[QUOTE=Nordoelum]Thank you for the help :D

I just reinstalled Ubuntu. And the installation worked just fine now. And jesus how many modules that was left out :(

Hehe..[/QUOTE]

Did you install from scratch or using the command I mentioned above?

I'm glad its working now, anyway. :D

---

### Post by Nordoelum on 2006-03-31
[QUOTE=Mustard]Did you install from scratch or using the command I mentioned above?

I'm glad its working now, anyway. :D[/QUOTE]
Scratch!

I honest think the installation was fucked up.. :)

---

