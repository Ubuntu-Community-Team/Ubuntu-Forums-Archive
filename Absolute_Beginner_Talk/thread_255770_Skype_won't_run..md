---
title: "Skype won't run."
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-11
Hello,

I've downloaded skype_1.2.0.18-2_i386.deb and installed by package installer of itself. Skype is there ,applications>internet>skype, but when I click that skype won't run. What should I do?
Can anyone help?

---

### Post by wieman01 on 2006-09-12
Can you run Skype from a terminal and post the output? Perhaps that's hinting us in the right direction.

---

### Post by harerama on 2006-09-12
Can you tell me how I can run application from terminal?

---

### Post by wieman01 on 2006-09-12
Just open a terminal windows (I think it is under "applications", not sure though as I am using KDE, not Gnome), type "skype" and press "enter".

The terminal is the command line.

---

### Post by Najand on 2006-09-12
Click Application => Accessories => Terminal

---

### Post by harerama on 2006-09-12
Thank you. It won't say anything.Just blank
-----------------
~$ skype

-----------------

Just like this.

---

### Post by harerama on 2006-09-12
Oh no this time(second time) it says
--------------------------------------------------------------
*** glibc detected *** free(): invalid pointer: 0x08a1c4c0 ***
Aborted
--------------------------------------------------------------

---

### Post by harerama on 2006-09-12
It took sometime to get response.

---

### Post by Najand on 2006-09-12
> **harerama said:**
> Thank you. It won't say anything.Just blank
-----------------
~$ skype

-----------------

Just like this.

It takes time, something between 1 to 5 minutes for skype to star for the first time... You better not closing the terminal and wait.

---

### Post by wieman01 on 2006-09-12
Yeah, just wait and see what happens. The Linux implementation of Skype is fairly lousy so it takes quite a while to start up. Let us know how it goes... I am sure Skype is useable on your computer as well.

---

### Post by harerama on 2006-09-12
Thank you. This is what the terminal says

*** glibc detected *** free(): invalid pointer: 0x08a1ba28 ***
Aborted

---

### Post by Najand on 2006-09-12
Hmm, seems to be like an Alsa Bug. I recommend you to reinstall skype and try again.
For removing package
```

sudo apt-get remove skype

```
in terminal is enough. Then try to download skype from:
[http://www.skype.com/go/getskype-linux-beta-deb](http://www.skype.com/go/getskype-linux-beta-deb)

---

### Post by Leeghoofd on 2006-09-12
Why download?

Try one of the alternative ways of installation:

1. Synaptic.

2. Automatix.

Both do a pretty good job of installing Skype.

Instructions should be available on this forum.

---

### Post by Najand on 2006-09-12
> **Leeghoofd said:**
> Why download?

Try one of the alternative ways of installation:

1. Synaptic.

2. Automatix.

Both do a pretty good job of installing Skype.

Instructions should be available on this forum.

Hmm, in case if you add skype repository to your /etc/apt/sources.list which I don't know what it is... and it downloads and installs the same deb package.

---

### Post by harerama on 2006-09-12
Umm...
I tried both
[http://www.skype.com/go/getskype-linux-beta-deb](http://www.skype.com/go/getskype-linux-beta-deb)
and synaptic
they did the same. I would probably give up for sometime. 

Thanks very much for your help though.

---

### Post by seshomaru samma on 2006-09-12
Do you have SCIM installed?
I found SCIM's libraries to conflict with Skype (In Ubuntu only , they get along fine in Fedora)
I get the same error as you . I tried all known versions of Skype
It happens with VMware as well...

---

### Post by harerama on 2006-09-12
Hello ,seshomaru samma

Yes SCIM is installed in my machine. You might remember me as you helped me when I was struggling to input Japanese into my machine. So SCIM might be the  
 reason? So you haven't succeeded installing skype have you?

---

### Post by Najand on 2006-09-12
Hmm, and you may remember me when I told you SCIM has conflict with some software's libraries... 
Anyway if it is just the problem I have a solution:
Try to run:
```

export GTK_IM_MODULE=xim

```
and then start skype by:
```

skype &

```

---

### Post by seshomaru samma on 2006-09-13
Strangely , I just installed both SCIM and Skype on anothe machine and they get along fine. Maybe it isn't SCIM's fault but another application?

---

