---
title: "[SOLVED] Missing Packages"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by gyrene2083 on 2007-12-10
I have installed ubuntu 7.10, and I seem to be missing packages. I went to the repository, and first I tried a search on cardctl, that was missing. 

I then did a search on ndisgtk, and that was missing. I downloaded ndisgtk, but how do you install that from a thumb-drive?

---

### Post by forestpixie on 2007-12-10
another case of sources being commented out I suspect

post you sources list - unless you know how to deal with it 

```
cat /etc/apt/sources.list
```

---

### Post by gyrene2083 on 2007-12-10
The problem is that I am not attached to the internet, and I'm trying to get attached. Right now I'm using my main, computer. Ubuntu is installed on my laptop. Also tried to cat /etc/apt/sources.list, also, with app, and I got this error msg no such file or directory.

---

### Post by forestpixie on 2007-12-10
ok if you haven't got the file yet we can do it after you've got the net sorted.

1 - get internet sorted 

2 - do this in a terminal and you'll get an empty file to post the sources into 

```
gksudo gedit  /etc/apt/sources.list
```

3 - go [here]("http://www.ubuntu-nl.org/source-o-matic/") and you can get a new set of sources, fill the boxes to suit you and you'll get a list that you can copy and paste into the empty file, save it and close gedit

4 - in a terminal do this

```
sudo apt-get update
```

then you should have packages available to check - change 'packagename' to suit what you're looking for

```
sudo apt-cache search *packagename*
```

---

### Post by gyrene2083 on 2007-12-10
Don't I need an internet connection in order to get the update? The reason I ask is because after running the sudo apt-get update, everything failed

---

### Post by SOULRiDER on 2007-12-10
Yes, when you try to apt-get/aptitude update that will tyr to download the package lists so yes, you need to be connected.

---

### Post by gyrene2083 on 2007-12-10
Well the problem with that is that I am installing this on a laptop. That doesn't have access to the internet. I am trying to get internet access on it, but I need some packages, which for some reason, did not install when I did the ubuntu setup.

---

### Post by forestpixie on 2007-12-10
ok try to open software sources - in system > admin - if the livecd is there is it enabled if not try going to third party software and add cd-rom follow the prompts and add your livecd as a repo.

then it will want to reload - try getting your packages then from the cd

after you've done that hopefully you'll be able to get want you need doing 

- if you have edited the sources.list as from my previous post open it for editing again ```
gksudo gedit /etc/apt/sources.list
``` and put # in front of all the lines you pasted in - there should be a line that looks similar to this 
>  deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

you need that one

---

### Post by gyrene2083 on 2007-12-10
I followed the instructions, and then I did the following, 

```
sudo apt-get update
```

then you should have packages available to check - change 'packagename' to suit what you're looking for

```
sudo apt-cache search *packagename*
```[/QUOTE]

where I supplemented packagename, with ndisgtk, and nothing happened. Any ideas?!?

---

### Post by gyrene2083 on 2007-12-11
What I ended up doing was borrowing another link cable, and connecting it to the laptop, to run the updates. I then had to figure out how to get the wireless card to work. At first it was a pain in the neck, because I was running wpa, but then I used this format on the router, xxxx-xxxx-xxxxx, I rebooted the router, and laptop, and right now I'm typing away wirelessly. Thank you all for your help. Now, I'm going to install Ubuntu on my PS3. Wish me luck.

---

