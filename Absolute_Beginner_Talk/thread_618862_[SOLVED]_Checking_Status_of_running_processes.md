---
title: "[SOLVED] Checking Status of running processes?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-20
I am very new to linux, but I am eager to learn, as I want to break free from the evil grasp of M$.  So far I have successfully setup a box with KTorrent (easy enough) and the more difficult (No Add/Remove for this little app ;)) Usenet client hellanzb w/ hellahella (webGUI for hellanzb)... I also added these as functions of the "Settings->Autostarted Applications", instead of having to open up the terminal and running: ```
hellanzb.py
paster serve hella.ini
``` each time the computer reboots.  What I am having a hard time grasping is how to get access to these two processes again from the terminal?

Normally when you run **hellanzb.py** from the terminal it displays a nice little (auto-updating) chart with information on what it is currently doing (i.e. Downloading, Un-RARing, etc), but because i have these processes in the "Autostarted Applications" I never see the terminal, how can I re-gain access to the status of **hellanzb.py** and the likes when they are being run from the "Autostarted Applications" function?
Also when I ran these from the Terminal I could simply close the terminal window and it would close the process, but now that I don't have a terminal I don't have a way to close the process :(

I am sure this is simple for most Linux Novices, but for little ole me (ex-winblows user) it's hard to to grasp this. 
Thanks in advance,
-BassKozz

---

### Post by coolguy2006delhi on 2007-11-21
In the terminal , type 

$pe -e | grep hell

You can see the 4 digit code of the running hellanzb.py 

Next type 

$sudo kill <no>

This will stop that process. This process can be applied to any process to kill it. Instead of 'hell' in above command , just write a matching regular expression of the app you want to close. That's it. Also you wanna try the command 

$ top

to see the current processes running.

---

### Post by Inxsible on 2007-11-21
you could also go to System>Administration>>System Monitor. Go to Processes tab and kill the process in question. This however, should be done only if it is not responding. Its not safe to use the kill command or the system monitor to kill processes every now and then.

This may be a bit more advanced that you would care to do, but

About seeing what it does,  you can use conky to create scripts which will display whatever information you want from the computer with respect to a particular process, or the entire computer in general. Click the link to see what [conky]("http://conky.sourceforge.net/") is all about.

---

### Post by BassKozz on 2007-11-21
> **coolguy2006delhi said:**
> In the terminal , type 

$pe -e | grep hell
Output:
```
bash: -e: command not found
```
:(
> **Inxsible said:**
> About seeing what it does,  you can use conky to create scripts which will display whatever information you want from the computer with respect to a particular process, or the entire computer in general. Click the link to see what [conky]("http://conky.sourceforge.net/") is all about.
I don't think you understand what I am looking for here... For example when I run ***hellanzb.py*** from the terminal it displays the following ```
hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
(NewsHostin) Opening 8 connections...
hellanzb - Now monitoring queue...
hellanzb v0.13 (config = /usr/etc/hellanzb.conf)
(NewsHostin) Opening 8 connections...
hellanzb - Now monitoring queue...

``` to show me its up and running and monitoring my Queue folder for NZB's... Once an NZB is introduced (either by placing it in the Queue folder, or by uploading via the hellahella WebGUI) it shows the following:
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/th_hellanzb-working.png[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/xubuntu/hellanzb-working.png)[[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/th_hellanzb-working2.png[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/xubuntu/hellanzb-working2.png)[[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/th_hellanzb-working3.png[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/xubuntu/hellanzb-working3.png)
*(Click to see larger format)*
In these screenshots you can see the information hellanzb is showing as I download Kubuntu from Usenet.  Now because I have **hellanzb.py** setup as an "Autostarted Application" I never get to see the terminal window.  So I need to know how to get back to this view?

Thanks for the help,
-BassKozz

---

### Post by BassKozz on 2007-11-23
Can someone help me out with this?

---

### Post by markusf21 on 2007-11-23
I want to make sure I understand what you are asking. Are you wanting this to auto start in a terminal?

---

### Post by BassKozz on 2007-11-23
> **markusf21 said:**
> I want to make sure I understand what you are asking. Are you wanting this to auto start in a terminal?
Yes, I guess that would work...
Really I was looking for getting back to the terminal/status screen that is shown when **hellanzb.py** is first run, but I guess if I could autostart with terminal that would solve it.

---

### Post by BassKozz on 2007-11-25
Anyone?

---

### Post by PeterJS on 2007-11-25
> **B/-\ssKozz said:**
> Anyone?

First install screen with:
```

sudo apt-get install screen

```

Then try changing your auto start command to:
```

screen -dmS hellanzb hellanzb.py

```
Which will start it in a detatched screen session.

And then then when you want to check on it open up a terminal and enter:
```

screen -r hellanzb

```
to attach the screen session to the current terminal. When you're done monitoring it press ctrl+a and then d to detach the session again. The nice thing about screen is that the program keeps running even when detached.

---

### Post by BassKozz on 2007-11-26
> **PeterJS said:**
> First install screen with:
```

sudo apt-get install screen

```

Then try changing your auto start command to:
```

screen -dmS hellanzb hellanzb.py

```
Which will start it in a detatched screen session.

And then then when you want to check on it open up a terminal and enter:
```

screen -r hellanzb

```
to attach the screen session to the current terminal. When you're done monitoring it press ctrl+a and then d to detach the session again. The nice thing about screen is that the program keeps running even when detached.
EXACTLY what I was looking for, Thanks PeterJS :D

---

