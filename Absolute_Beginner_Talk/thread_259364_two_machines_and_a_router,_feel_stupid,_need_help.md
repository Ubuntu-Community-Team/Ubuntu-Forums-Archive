---
title: "two machines and a router, feel stupid, need help"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by benner on 2006-09-17
i have a desktop running kubuntu (192.168.1.6).  i have a notebook with kubuntu/windows dual boot that i usually run windows on (192.168.1.4).  they are connecting to the internet via a router (192.168.1.1).  both can connect to the internet with no problems.  when the notebook is running windows, i can check the remote places/samba shares folder on the kubuntu desktop and i can see that it is there on the network (mshome/ben_notebook).  when i try to access that machine, konquerer asks me for a password and nothing works.  i never set up a password on the windows machine.  when i open 'network services' in konqueror, i get 'The Zeroconf daemon (mdnsd) is not running.'  

going the other way, the kubuntu_desktop does not even appear when i look at the network places in windows.  

when i have kubuntu running on both machines, they don't seem to see one another.

erring on the side of caution, let's assume that i know next to nothing about networks etc..., what is the simplest way for me to have these two machines recognize one another and transfer files back and forth?  i have a printer connected to the kubuntu desktop and the notebook is sometimes connected via ethernet and sometimes wireless LAN card.  i have been reading everything that i can find and having no luck.  i am a teacher and have taken a chance (contrary to all advice) and installed kubuntu on all of the 3 student machines in my class.  if i can get them networked properly, it would go a long way to enlisting the support of others in getting us off of the windows bandwagon.  i am starting at home. i thought i was a pretty competent windows user but linux makes me feel like i'm starting again from scratch.  it can be very frustrating.  please help.

---

### Post by benner on 2006-09-17
p.s. I was able to ping the kubuntu_desktop machine from the windows machine.  so it knows that it's there.  i have no idea what to do next to set up the network.  i hope somebody gets around to reading this...  i would have figured that this is a no brainer for a lot of people.

---

### Post by buffy^ on 2006-09-17
The reason why is that the use of blank password is restricted to the local machine, what you need to do is hit the control pannel and then into admin tools then security policy and disalbe the limitation.

let me know if this works.

---

### Post by halitech on 2006-09-17
question 1. are both machines on the same network?

question 2. did you create a user on the windows box with the username and password of your linux box?

question 3. did you install samba on the linux box?

Don't worry about feeling like you are starting all over from scratch. I felt pretty much the same way about 8 months ago when I first started. Been using windows since back in the 3.1 days and figured I would sort it out with no problems. Ubuntu showed me how little I actually knew about computers and it was very humbling but I've gotten past that and learned alot from reading here.

---

### Post by benner on 2006-09-18
are both machines on the same network?  i have no idea.  i created a network on the windows machine and called it MSHome (default).  i never set up a network on the Kubuntu machine (i wouldn't know how.)  when i installed it, it was able to connect to the internet without any problems so i didn't change anything.  as fot the login... no, there is no login on the windows machine that matches the login/password on the kubuntu_desktop.  should there be?  samba is installed.  it is stock with kubuntu.  if i'm supposed to set it up in some way, i haven't.  suggestions?  thanks in advance to anyone with a minute to spare...

-benner

---

