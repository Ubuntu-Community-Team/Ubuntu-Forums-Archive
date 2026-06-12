---
title: "Skype"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by jadda on 2007-03-20
I am not a total n00b, but pretty close=)
Skype seems to be a real problem, and is for many (and me) a big problem and a reason to boot windows...
I kinda sorted it out by

sudo alsactl names
sudo alsactl store
sudo reboot

don't know what I did thou;)

but the problem is that it is not a stable solution to anything, it may or may not work. It can work at 1800 but at 2200 it don't...kinda frustrating...

any little would help, and this is my last reason to boot windows from time to time.

---

### Post by gerbman on 2007-03-20
What, exactly, is the problem? Are you getting error messages when running skype from the command line?

---

### Post by Kateikyoushi on 2007-03-20
Please note this isn't the right place to ask for help.
By th way if skype would depend on those packages those would have been installed with it, if you used synaptic or pt to install it.

---

### Post by bodhi.zazen on 2007-03-21
Skype is not too hard, it is not in the repositories ...

To install skype :

1. Add this to your repositories :

> deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Either open synaptic or, IMO easier, use the command line.

```
sudo echo "deb http://download.skype.com/linux/repos/debian/ stable non-free" >> /etc/apt/sources.list
sudo aptitude update
sudo aptitude install skype
```

You can cut-n-paste those commands to the terminal and viola.....

If you prefer you can use a GUI (synaptic), but it will take longer ...

Open syanptic, add deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free to your repositories, reload synaptic, search for skype, install skype

EDIT : Moving this thread to Absolute Beginners Talk ~ Better location for specific support questions ...

---

### Post by jadda on 2007-03-21
Sorry....
my first post was not very clear....:confused: 
The problem is that I can't record,or capture, anything. Not even any sound recorder or equals. 
I can hear myself in the speakers, but when I talk to people in skype they can't hear me. 

The idea of my first post was not to get help just for me, but to get a HOWTO from The Beginner Team on how to fix this, my problem is far from unique, and I can't find any solution to it anywhere.

---

### Post by bodhi.zazen on 2007-03-21
> **jadda said:**
> Sorry....
my first post was not very clear....:confused: 
The problem is that I can't record,or capture, anything. Not even any sound recorder or equals. 
I can hear myself in the speakers, but when I talk to people in skype they can't hear me. 

The idea of my first post was not to get help just for me, but to get a HOWTO from The Beginner Team on how to fix this, my problem is far from unique, and I can't find any solution to it anywhere.

Sorry, I did not catch that at all ...

There already a page on how to skype :

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

As far as your sound problem, hard to know.  Sounds like a problem either with your microphone settings or skype.

See if this helps : [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

If not, can you give a more detailed description of your problem ? What microphone ? What have you tried to set up ? Have you tried alsamixer ?

Last, have you looked into opensource solutions ?

From the wiki : > Open alternative SoftPhone's using open protocols include Ekiga, Twinkle and [WWW] Wengophone.

---

### Post by mahy on 2007-03-21
> **jadda said:**
> Sorry....
my first post was not very clear....:confused: 
The problem is that I can't record,or capture, anything. Not even any sound recorder or equals. 
I can hear myself in the speakers, but when I talk to people in skype they can't hear me. 

The idea of my first post was not to get help just for me, but to get a HOWTO from The Beginner Team on how to fix this, my problem is far from unique, and I can't find any solution to it anywhere.

I fixed my microphone by means of gnome-alsamixer. I slid the 'capture' slider to the top and checked the 'Rec' box. If that doesn't help, install the newest ALSA drivers. Feel free to ask more.

---

### Post by mikewhatever on 2007-03-21
From your second post, it appears that Skype works fine and you have a microphone problem. As far as my knowledge goes, Skype has no voice recording function, so, either your mic does not work, or you are trying to use a wrong program to record sound. If you want to solve the problem yourself, here is the guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
Otherwise post your audio specs.

---

