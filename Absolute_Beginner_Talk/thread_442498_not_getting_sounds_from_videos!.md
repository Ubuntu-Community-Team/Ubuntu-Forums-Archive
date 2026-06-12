---
title: "not getting sounds from videos!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-13
I can listen to the music, but the videos on internet such as videos on Youtube, I'm not getting

any sounds..what's the problem?

---

### Post by dbott67 on 2007-05-13
Check this thread, which has a link to a comprehensive sound guide:
[http://ubuntuforums.org/showthread.php?p=2642648](http://ubuntuforums.org/showthread.php?p=2642648)

-Dave

---

### Post by rocketboys on 2007-05-13
> **dbott67 said:**
> Check this thread, which has a link to a comprehensive sound guide:
[http://ubuntuforums.org/showthread.php?p=2642648](http://ubuntuforums.org/showthread.php?p=2642648)

-Dave

Hey thank you for your response!

I was trying to do this:        

In a shell type these commands:

Make a directory to store the alsa source code in.

        cd /usr/src
        mkdir alsa
        cd alsa
        cp /downloads/alsa-* 

but then I got this :

danny@Dan:~$ cd /usr/src
danny@Dan:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': Permission denied

I'm tired of that permission thing..why is this keep happening? :'(....

help me please...?..

---

### Post by mendingo84 on 2007-05-13
you must be root to be allowed to do certain types of operations in directories different from your home directory, which is /home/youruser. you should "sudo mkdir". that way you will be root and will be granted any type of operation. Permissions are a very good thing which allow you to protect your OS...

---

### Post by Sef on 2007-05-13
1) What version of Ubuntu are you using?

2) What version of flash are you using?

3) This is from the [archieves]("http://ubuntuforums.org/archive/index.php/t-233751.html"):

```
sudo apt-get install alsa-oss
sudo gedit /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss" 
```

---

### Post by rocketboys on 2007-05-13
> **mendingo84 said:**
> you must be root to be allowed to do certain types of operations in directories different from your home directory, which is /home/youruser. you should "sudo mkdir". that way you will be root and will be granted any type of operation. Permissions are a very good thing which allow you to protect your OS...

Thank you for the response!

I typed sudo mkdir .. but I get this message :

 mkdir: missing operand
Try `mkdir --help' for more information.

---

### Post by rocketboys on 2007-05-13
> **Sef said:**
> 1) What version of Ubuntu are you using?

2) What version of flash are you using?

3) This is from the [archieves]("http://ubuntuforums.org/archive/index.php/t-233751.html"):

```
sudo apt-get install alsa-oss
sudo gedit /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss" 
```

Thank you for the response!

I'm using 7.04 version of Ubuntu and I'm not sure what flash is..

and I did what you told me to do..

I'm not quite sure what it was but thanks anyway!

---

