---
title: "Converting Ubuntu editions"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by dlehman on 2006-09-12
Hello everyone, I apologize if I missed this somewhere else.  I am not a complete noob but will be new to Ubuntu.  I am currently using Gentoo and just don't have the time to mess with it any more.  I hope the following does not sound like a stupid question but, can I covert between Ubuntu editions.

I have currently download Ubuntu Christian edition and they have a script that will keep you up to date or allow you to convert if you download the standard version.  I am also interested in the educational software with edubuntu, I have a little one where that will be nice in a year or so.  I also like KDE over Gnome but still like Gnome for some things, can I switch back and forth as with gentoo and have booth installed?

The main thing holding me back however is 100GB's of stuff on Gentoo that I don't want to loose and don't have enough space to back it all up when I wipe the slate clean for Ubuntu.

I thank you for your answers in advance.

---

### Post by Metacarpal on 2006-09-12
Hi, welcome to Ubuntu!  Let me help clear up some confusion all these different so-called "editions" of Ubuntu may be causing you.

Basically, Ubuntu comes in three flavors: Ubuntu (which uses the Gnome desktop), Kubuntu (which uses KDE), and Xubuntu (which uses XFCE).

Everything else is just a variation on one of these three.  Edubuntu just installs Ubuntu with a collection of educational apps and a child-friendly theme.  The other "editions" are simply Ubuntu with certain packages installed that the person who created the edition thought a lot of people want to have.

These editions are generally created through use of something called a "meta-package".  This isn't an actual package/program in and of itself, it just has all the other packages listed as dependancies - that is to say, it causes them all to be installed along with it.  For instance, the ubuntu-desktop metapackage will install all the files you need to run Ubuntu with the Gnome desktop, just as if it had been installed from CD.

If you install Ubuntu, then add the kubuntu-desktop and/or xubuntu-desktop packages, you can easily switch between the Gnome, KDE, and XFCE desktops at the login screen by choosing "select session" before you enter your password.

Everything else is just add-on software, which you'll be able to access from any of those three desktop environments.

---

### Post by coffeecat on 2006-09-12
And if you install Ubuntu (say) and get to like the orange-brown usplash and then install kubuntu-desktop in order to get kde, but dislike the blue kubuntu usplash that now appears, you can choose which usplash you want by [following the instructions here]("http://doc.gwos.org/index.php/Different_usplash").

---

### Post by Najand on 2006-09-12
For converting to Ubuntu (with gnome), use:
```

sudo apt-get install ubuntu-desktop

```
For converting to kUbuntu (with KDE), use:
```

sudo apt-get install kubuntu-desktop

```
For converting to xUbuntu (with XFCE), use:
```

sudo apt-get install xubuntu-desktop

```
For converting to Edubuntu, use:
```

sudo apt-get install edubuntu-desktop

```

Anyway, I didn't know there is a Christian Ubuntu... What special things does it have? Free Bible or something similar? 

To be honest, I cannot understand the relationship between religion and OS. I would appreciate it if you can help me with that issue.

---

### Post by jdr00ejr on 2006-09-12
I'm curious as well....what is packaged in the Christian Ubuntu and where did you get it?

Thanks.

---

### Post by ser1alsn1per on 2006-09-12
666

---

### Post by jdr00ejr on 2006-09-12
> **ser1alsn1per said:**
> 666

Now that is an informative, helpful, reply.  Thank you for your contribution to this thread.:rolleyes:

For those interested I found this website that I'm review now to see what packages are included.

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html)

---

### Post by dlehman on 2006-09-12
Thanks everyone for the quick response.  Metacarpal, that is how I thought it might work but was not sure, thanks for clearing that up.  Najand I don’t quite understand what you mean I am farmailir with the apt-get command I have used it in other distros.  But are you suggesting I use that program from within my current Gentoo install to convert to Ubuntu? If so wouldn’t that cause a lot of problems there are fundamental differences between the 2.  to start gentoo is based on a bsd portage package system  and I believe Ubuntu is based on debin.  

Jdr00ejr, and to the others that asked, when I was on distro watch looking at some reviews one of the newest listed was Ubuntu CE so I looked at it. It is a basic Ubuntu with the sword project and parental controls, I have not looked that deep into I just ran the live CD on my old pc.  

Thanks

---

### Post by ramcosca on 2006-09-12
This is found on the main page, under 3rd party Ubuntu forums: [Ubuntu Christian Edition]("http://www.ubuntuforums.org/forumdisplay.php?f=168")

---

### Post by fotogogo on 2006-09-12
I'm looking to do thing same basic thing, install KDE on Edubuntu.  The only catch is the computer running Edubuntu is not online.  I thought I could install KDE using the Kubuntu CD as a repository, but it only shows like 33 uninstall packages and none of them are kde-desktop.

Am I missing something?  Can this be done?

Thanks!

---

### Post by halitech on 2006-09-12
I don't think you can, pretty sure the only way to add packages without the dvd repo is by havin git online.

---

### Post by radiant chains on 2006-09-12
> **fotogogo said:**
> I'm looking to do thing same basic thing, install KDE on Edubuntu.  The only catch is the computer running Edubuntu is not online.  I thought I could install KDE using the Kubuntu CD as a repository, but it only shows like 33 uninstall packages and none of them are kde-desktop.

Am I missing something?  Can this be done?

Thanks!

This works if you're using the Alternate Install CD, rather than the regular Live/Install CD.

---

### Post by andb on 2006-09-13
dlehman:
But are you suggesting I use that program from within my current Gentoo install to convert to Ubuntu? If so wouldn’t that cause a lot of problems there are fundamental differences between the 2. to start gentoo is based on a bsd portage package system and I believe Ubuntu is based on debin.

No. If you install one flavor of Ubuntu, these commands will work to install the other desktop environments. Keep in mind, one is usually enough :) The simpler you keep your machine, the less headache down the line. Find the one you like and stick with it, I'd recomend.

---

