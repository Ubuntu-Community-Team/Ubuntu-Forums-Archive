---
title: "Stuck in Ubuntu 6.06"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Notrium on 2007-07-07
Computer with Ubuntu 6.06 only. A "helper" created a problem and I am stuck.  The limited paths I can now use suggests among other ideas is that the X server failed to start. I can view detailed X server output > OK  > X server disabled > restart > GDM when configured correctly > Ok > ubuntu 6.06 bert desktop ttyl > bert desktop log in > failed to start X server.
experimenting with the command line produced no forward movement. I am stuck at  "bert-desktop login:_ "
How can I delete this Ubuntu and start anew from my disk?

---

### Post by Martje_001 on 2007-07-07
Why do you want to delete it? Login and run 'sudo dpkg-reconfigure xserver-xorg' and awnser the questions. You'll be fine ;)

---

### Post by Notrium on 2007-07-07
Many thanks. Followed suggestion. Did not know what the questions meant and ran into the brick wall very soon. These are my very first steps as a beginner. "Identifier for the video card?" and many more questions were asked to which I do not have a clue. Sorry about all that. :(
What help can I get?
Notrium

---

### Post by Martje_001 on 2007-07-08
What video card do you have? And what's the complete question (inclusive possible awnsers)? 
Just dump the questions here, we can awnser them ;)

---

### Post by Martje_001 on 2007-07-08
If you really want to reinstall ubuntu, you can download a cd from ubuntu.com, burn it an run it. Just awnser the install questions

---

### Post by bodhi.zazen on 2007-07-09
To restore X ;

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```


To re-install Ubuntu -> Insert CD into CD driver -> Reboot

---

### Post by Notrium on 2007-07-10
I followed "bodhi.zazen's" three step suggestion. Things have changed.
Starting computer and booting OK and arrive at Ububtu screen and am asked for user name and password.
Black line at bottom with correct user and time on right. On left is "Options" and I choose "select session" and I run through them all qwithout success. I use "failsafe terminal" and then entering name and password I arrive at a notice which says that this is where I can fix things - but I know not what to do. Click OK and I have a quarter sized white monitor screen with prompt.
As pure beginner, where can I go now?
Thanks to all.

---

### Post by bodhi.zazen on 2007-07-10
What videocard are you using ?

---

### Post by Notrium on 2007-07-10
I know nothing about video cards. I am a real beginner - my very first steps. Sorry about that.

---

### Post by Seisen on 2007-07-10
Put this in the terminal

```
lspci
```

---

### Post by bodhi.zazen on 2007-07-10
> **Notrium said:**
> I know nothing about video cards. I am a real beginner - my very first steps. Sorry about that.

LOL

No need to apologize, we understand and are here to help. You just have to tell us if we are talking above your head is all :-\"

---

### Post by Notrium on 2007-07-10
The reply to 1spci  is
 "bash: 1spci:  command not found" 
 followed by a new prompt

---

### Post by Happy_Man on 2007-07-10
No, that's not a "1", that's a lowercase "L".

---

### Post by Notrium on 2007-07-11
Thank you SEISEN.  Your suggested entry was read as numeral one (1) for the first letter and this produced nothing.  Changing the first letter to lower case (L)  to read (  lspci )  gave me a list. I have  photographed my monitor to record this information. What information do you need from this SEISEN?
I borrowed a book on Linux and at the chapter on working without the GUI I found some commands such as  ls  at the command line and there it was -- the files names on the hard drive that I had not seen for 10 weeks.  ls -l  gave me a lot more with the dates of origination.
How do I get these long lost files back on the Ubuntu GUI ?
I have made progress. Thanks to all.

---

### Post by Notrium on 2007-07-12
I have been concentrating so much on the answers to my queries that I have only noticed that with my name on the right hand side there is a note that I joined in April 07. My first contact was at the week-end; four or five days ago. How can both be valid?

---

### Post by Notrium on 2007-07-12
This yet another discovery of mine that is related to the statement that I joined in April 07 when I only started to ask questions five or six days ago.
Starting from boot and arriving at a brown Ubuntu asking for name and password, I go instead to left botton corner and choose "session" then enter name and password which gives me a command line on a quarter size image on the monitor. From my borrowed book I have been entering 
ls
ls -l
ls -l /etc
and discovered what is on my hard drive.
Now a chance discovery. While on the command line I use the Up Key and am given a tour back in time with the entries made to this command line; entries not made by myself - but by my "helper" back in April 07. This explains the "joined April 2007" in the top left of my messages. So it seems inescapable that my "helper" got himself into trouible and these entries were an effort to escape his predicament.
This man is an experienced computer teacher and if he could not solve the problem my Ubuntu was in at that time, and still is, then what hope have I got of solving it here when I do not know enough of the language to explain. 
This is yet another chapter in the story of my very first steps in learning Linux. If only I could go back and place my last three posts in the one envelope. Maybe I could. Thank you for your patience.

---

### Post by vincentvee on 2007-07-24
i wonder if that fixed the problem?

> **Seisen said:**
> Put this in the terminal

```
lspci
```

---

