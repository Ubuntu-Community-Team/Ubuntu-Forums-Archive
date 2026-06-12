---
title: "No GUI for me?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by YeahBuntu on 2006-09-02
I am a total linux newb.  I decided to go with Ubuntu because a friend from work told me they have a great userbase of helpful people.  

I have a Sony Laptop 80Gb HD and 192 MB of ram.

I want to create my own webserver to learn PHP/Perl/ POSTgre

I attempted to install the graphical Ubuntu but the system would hang when asking for "where are you located in the US screen"

So I downloaded and burned a copy of the server version and it appeared to install just fine.

However, I have no idea how now to install a GUI.  I have a linux book coming from Amazon but it is not here yet.  

I forgot to tell you that I think XFC would be good since people say it uses less ram or something.

Thanks in advance for your help.  I hope I can become a helper too someday.

---

### Post by benfindlay on 2006-09-02
When you get to the command line after booting up type ```
sudo aptitude install ubuntu-desktop
```

This will download and install gnome, xserver etc for you and give you the GUI.

You could also try downloading an iso of the alternate-cd. This installs in a text based fashion but also puts the xserver on for you.

Hope this helps!

EDIT: just spotted you want to install XFCE, so type ```
sudo aptitude install xubuntu-desktop
``` for this! ;)

---

### Post by bulldog on 2006-09-02
Try sudo aptitude install gnome-desktop
Or if you prefer sudo aptitude install kde-desktop

I think this must do the tric.

---

### Post by YeahBuntu on 2006-09-02
Oh wow I thought I'd have to wait an hour or more for a response.. this truely is a great forumbase.  Thank you and will try your suggestion thanks again.

---

### Post by benfindlay on 2006-09-02
No problem matey!

Admittedly sometimes you can wait ages for a resonse, rarely you won't get one at all, but thats usually only if your question has been asked a million times before.

The best thing about this forum in my opinion is the sheer number of helpful people that use it! It's certainly making my linux experience much easier!

Anyways, laters!

---

### Post by SkyNet2029 on 2006-09-02
You could also try out fluxbox, as it is quite a bit lighter on the system resources it needs.

---

### Post by YeahBuntu on 2006-09-03
So .. If I get this right all I Have to do if I want to try the Fluxbox GUI is type

>sudo aptitdude install fluxbox-desktop 

Is that correct? :-D

---

### Post by blackened on 2006-09-03
I don't think there's a dummy package for a basic fluxbox install. I would suggest doing sudo apt-get install ubuntu-desktop, then sudo apt-get install fluxbox. After that follow [this]("https://help.ubuntu.com/community/Fluxbox") wiki.

---

### Post by SkyNet2029 on 2006-09-03
So long as the repository is enabled, 

```
$sudo aptitude install fluxbox
```

should be just as complete as an install of the ubuntu-desktop, but no there is no listing as a 'dummy' package for fluxbox.
...By 'dummy package', I can but assume (yes, I know what it means) you are referring to the listings under 'Tasks' in aptitude. (?)

---

### Post by jISh on 2006-09-03
Dummy package would be a blank package that has the proper dependencies set for what you are trying to install.

Eg. kubuntu-desktop has dependencies set for KDE and it's applications, but it it doesn't contain any of that itself.

---

### Post by SkyNet2029 on 2006-09-03
Yeah, that too. I just couldn't think of the exact way to put it in a non-technical jargon.

---

### Post by YeahBuntu on 2006-09-03
> **jISh said:**
> Dummy package would be a blank package that has the proper dependencies set for what you are trying to install.

Eg. kubuntu-desktop has dependencies set for KDE and it's applications, but it it doesn't contain any of that itself.

LOL what??

ok .. When are the Ubuntu 101 IM classes?  I need to sign up.:wink:

---

### Post by benfindlay on 2006-09-03
A dummy package is basically a package that itself contains nothing other than a list of instructions for other packages that you want to install. When you download one, you are basically downloading a list of instructions for other files your computer needs to download, and your computer just gets on and gets the files you need. With linux being made up of so many modules, it's easier to do it this way than it is to design a complete installer that does everything itself.

---

