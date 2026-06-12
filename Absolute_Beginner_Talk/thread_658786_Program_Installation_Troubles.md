---
title: "Program Installation Troubles"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by x02flash on 2008-01-05
Hello All, i've just begun using Linux today, and am really confused.  

So, i went to go install skype for xubuntu (i'm currently running the latest version avalible of Xubuntu) and chose to open with the application installer, which ran for a second, then told me i needed the QT 4.2.1 or something like that. I was playing with Mandriva this morning and had the same problems.

Can someone please help me? I've been unable to install anything on my laptop since I installed linux, and am really confused.


Thanks In Advanced

-Alex

---

### Post by nitro_n2o on 2008-01-05
Check this out.. it is a good src [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by PeterJS on 2008-01-05
Here's the community guide to installing software:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

The 30 second guide is1) use the repositories 2) find third party repositories 3) find loose debs 4)use source only as a last resort.

Specifically for installing Skype medibuntu is the way to go:
[http://medibuntu.org/](http://medibuntu.org/)

Thanks nitro_n2o that was the guide I really wanted to link to.

---

### Post by the_sorrow on 2008-01-05
Welcome to UBUNTU, you can try to get a book called the UBUNTU Bible (llegally of course) or aks around to help you.

---

### Post by PeterJS on 2008-01-05
One thing to keep in mind coming fresh off the windows boat is that because of licensing software management is entirely different. In windows (most) everything is under a closed and restrictive license which makes it practically impossible and legally questionable to try and build any sort of centralized index of software. Where as under open source licensing it is permissible to redistribute software, since redistribution is permissible it's quite easy for a central group, like say ubuntu, to create a master source and index of all compatible software, these centralized sources are called repositories. The ubuntu (main) repositories are broken in to four groups based on the level of support Canonical provides for them, only the first two (main and restricted) are enabled by default, while the other two (universe and multiverse) receive less support and are disabled by default but very useful and enabling them is one of the first things most people do.

The other thing about open licensing is that it's far easier to make things the work tightly together, which has far reaching consequences in how things are organized. In windows each program has all of it's files in one directory, and interaction between programs is very minimal because no program can make any assumption about what other programs and libraries are available and how to interact with them. Linux is the exact opposite the operating system itself manages what is installed and each program knows what other programs it will need for it to work correctly when installed, and so can request that the OS install the helper software and libraries that it needs. Another way this manifests itself is that files are sorted by function rather than what program they are associated with all the documentation is in /usr/share/doc/ and programs are in /usr/bin, and libraries in /usr/lib.

Another big change is a real permission and security system. Even an admin user on linux is confined to their home directory unless they explicitly request root (super user) rights for a given action. If you want to edit a configuration file outside of your home directory you will need to use sudo to do so. This is for your protection, the need to circumvent the system are few and far between, if you feel you need to do so it's best to ask around first, there's probably a safer way to accomplish the same goal. The reason this adds to security is that if something bad happens, and your system gets compromised the damage can't extend beyond your user account. You may lose files, but your system itself will be fine.

---

### Post by x02flash on 2008-01-05
> **PeterJS said:**
> Here's the community guide to installing software:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

The 30 second guide is1) use the repositories 2) find third party repositories 3) find loose debs 4)use source only as a last resort.

Specifically for installing Skype medibuntu is the way to go:
[http://medibuntu.org/](http://medibuntu.org/)

Thanks nitro_n2o that was the guide I really wanted to link to.

First off, thanks to all of you guys, the response was tremendous

There is one problem though.  I connected to the medibuntu repository and went to install the skype files, but i got this error about something qt again

```
skype:
 Depends: libqt4-core (>=4.3.2) but it is not installable
 Depends: libqt4-gui (>=4.3.2) but it is not installable
```

what do i do from here?

---

### Post by PeterJS on 2008-01-05
What version are you running, and was your machine connected to the internet when you installed Ubuntu?

So I'd bet you're wondering what QT is? Well I'll tell you. Qt is the library that KDE uses to to draw buttons and other graphical elements on programs. I had never paid much attention to it before, but it looks like skype use QT to draw itself.

---

### Post by x02flash on 2008-01-05
The latest one, but no, it wasn't connected when I installed--at least i don't think so.
It wasn't connected while live was running, if that's what needed to happen

---

### Post by PeterJS on 2008-01-05
Yeah, that's a new "feature" of 7.10 when it installs it tries to connect to the internet to check for updates, and if it fails it make the rather stupid assumption that it will never have an internet connection and can safely disable the online repositores. If you go to System > Administration > Software Source, you want to make sure that the 4 main repositories are checked, the fifth box source is optional and really only used if you're planning on writing your own patches for ubuntu software.
.
After fixing that re-try installing skype

---

### Post by x02flash on 2008-01-05
> **PeterJS said:**
> Yeah, that's a new "feature" of 7.10 when it installs it tries to connect to the internet to check for updates, and if it fails it make the rather stupid assumption that it will never have an internet connection and can safely disable the online repositores. If you go to System > Administration > Software Source, you want to make sure that the 4 main repositories are checked, the fifth box source is optional and really only used if you're planning on writing your own patches for ubuntu software.
.
After fixing that re-try installing skype

Wow.

I set that up and it asked to update and installed 29 new packages.

Thanks **so** much man.  I think i've finally got this down.  Just two last questions for the time being, could someone link me on a .tar setup guide, and how do you access a 'control panel'-esque feature, I'd like to make sure my speakers are set up

---

### Post by PeterJS on 2008-01-05
> **x02flash said:**
> Wow.

I set that up and it asked to update and installed 29 new packages.

Thanks **so** much man.  I think i've finally got this down.  Just two last questions for the time being, could someone link me on a .tar setup guide, and how do you access a 'control panel'-esque feature, I'd like to make sure my speakers are set up


What do you need a source install guide for (that's what's in side a tar.gz usually)? It's usually a hit or miss pain in the back side best avoided if possible. The cliff notes are:
1)extract it
2)run ./configure
3)install a bunch of development files needed to compile the app
4)go back to step 2 until all the errors are taken care of
5)run make
5.5)hopefully nothing will break, if something does it's google/forum time
6)run sudo checkinstall

Most control panel-esque stuff is under the system menu. Looks like in this case you're looking for System > Preferences > sound.

---

### Post by x02flash on 2008-01-05
> **PeterJS said:**
> What do you need a source install guide for (that's what's in side a tar.gz usually)? It's usually a hit or miss pain in the back side best avoided if possible. The cliff notes are:
1)extract it
2)run ./configure
3)install a bunch of development files needed to compile the app
4)go back to step 2 until all the errors are taken care of
5)run make
5.5)hopefully nothing will break, if something does it's google/forum time
6)run sudo checkinstall

Most control panel-esque stuff is under the system menu. Looks like in this case you're looking for System > Preferences > sound.

I have to preferences choice in the system folder

---

### Post by PeterJS on 2008-01-05
I was referring to the System Menu up at the top of the screen.

---

### Post by x02flash on 2008-01-05
> **PeterJS said:**
> I was referring to the System Menu up at the top of the screen.
 
I'm sorry, I don't see one anywhere

---

### Post by PeterJS on 2008-01-05
Which version of ubuntu are you running, I assume you're running vanilla ubuntu with Gnome.

---

### Post by x02flash on 2008-01-05
I'm running Xubuntu or Ubuntu (i'm not sure which one to call it) v. 7.10.18

---

### Post by PeterJS on 2008-01-05
If it looks like the picture above it's Ubuntu with Gnome, if not it's xfce. If it's xfce I'm kinda at a loss to find a good sound control/mixer. You might want to look at installing Kmix or figuring out what the gnome mixer is called and installing that.

---

### Post by x02flash on 2008-01-05
> **PeterJS said:**
> If it looks like the picture above it's Ubuntu with Gnome, if not it's xfce. If it's xfce I'm kinda at a loss to find a good sound control/mixer. You might want to look at installing Kmix or figuring out what the gnome mixer is called and installing that.

  It's allright, you've still helped a lot tonight.  Anyways, thanks much for all the support, I'm really liking Ubuntu, and I think I'm starting to get the hang of it.

Once again, thanks much.

---

