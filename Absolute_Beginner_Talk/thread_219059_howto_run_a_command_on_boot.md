---
title: "howto run a command on boot??"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-07-19
I need to run a command
xvattr -a XV_GAMMA5 -v 13027014

on boot..
i have no idea of how t do this..
please help

---

### Post by ahaslam on 2006-07-19
I'm not sure, but try going to System, Preferences, Sessions. Then go to  Startup Progrmas & Add, then paste in your command ond click ok.

Got to be worth a try ;)

Tony.

---

### Post by harisund on 2006-07-19
Hmm, do you want to run that every time you login to your machine, or every time your machine simply reboots? What Anthony Haslam here suggested would work only every time you actually login to the machine. Now if it is your desktop machine and you do login every time you boot it is fine. 

However, if it is a headless machine, or a server, or something that just sits in one corner and you don't actually login to it directly, then you could put the command in /etc/rc.local I think which will start it during "boot"

---

### Post by hellmet on 2006-07-19
oh..that was easy...he he
thanks a lot people..
that got rid of my last bug on dapper!!

---

### Post by harisund on 2006-07-19
What did you do? The session one or the boot time one?

---

### Post by Baasha on 2006-07-19
i have wondered how to do this as well.  Now that I know, can anyone tell me what the command would be to turn on the F Lock?  I am getting tired of the extra keystrokes every time I boot up.

Bob

---

### Post by hellmet on 2006-07-21
I did the session one..

@baasha
what is the F lock??

---

### Post by ReyJames on 2008-03-16
thanks - I was about to start searching for an answer on this as well.

---

