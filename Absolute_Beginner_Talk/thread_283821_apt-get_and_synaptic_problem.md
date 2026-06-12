---
title: "apt-get and synaptic problem"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-24
i just had a problem with my PC, ubuntu wouldnt recognize my password, so i reinstalled ubuntu. now the weird thing is i cant seem to find the old programs i once had.

sudo apt-get install wesnoth
sudo apt-get install automatix

i cant find them in synaptic either.

there are a few other programs i cant think of at the moment.

---

### Post by RKCole on 2006-10-24
Hello, sdubois92.

I hope that I can be of some help, as I am still learning.

It sounds to me like the Universe/Multiverse repositories are not enabled.  I think that's where the games and other programs are, if I am not mistaken.

To re-enable this (if you haven't done it already...I apologize if this is something you already are aware of) go to System->Administrative (sorry...on Windows right now, so the titles may not be exactly correct...)->Synaptic Package Manager.  Once this opens, go to the Settings->Repositories menu.  IN this you should be able to enable the Universe and Multiverse repositories.

I hope that this is of some help.

Please take care.

---

### Post by meng on 2006-10-24
Alternatively, drop to the command line and type:
cat /etc/apt/sources.list
and post the output here.

I agree with rkcole, it sounds like the enabled repositories have changed.

---

### Post by sdubois92 on 2006-10-24
now i can see the program in synaptic, but when i try to instaall something i get this

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by bukwirm on 2006-10-24
You probably let an aptitude running accidentally (closed the terminal without exiting aptitude). Type "ps -e | grep aptitude", then "kill [the number next to the output of the previous command]".

You may have use sudo.

Be VERY careful not to type the wrong number!

---

### Post by mrsdeath on 2006-10-24
Hi!!

I have a similar problem: I can't install amule because of a strange error which I paste here:

Depends: libc6 (>= 2.3.2.ds1-21) but it will be installed 2.3.2.ds1-20ubuntu15
         Depends: libwxbase2.4 (>= 2.4.3.1) but it will be installed 2.4.2.6ubuntu1
         Depends: libwxgtk2.4 (>= 2.4.3.1) but it will be installed 2.4.2.6ubuntu1


What can I do? I had to remove my amule completely because it didn't work properly.

Thanks a lot

---

### Post by meng on 2006-10-24
mrsdeath, your problem is actually not very similar. Would you start a new thread please and tell us what command you entered before you received that message? Also, are you still using Ubuntu 5.04, or have you upgraded?

---

### Post by mrsdeath on 2006-10-24
How do I start a new thread?

---

### Post by Abhi Kalyan on 2006-10-25
Hi mrsdeath,
[http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)
Choose the forum of your choice-(If you are a new here, "Absolute Beginner Talk" would be a great choice)
else pick on the link below, it will take you right there, Its better if you move around-helps a tonne
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)
There you find 
"New Thread"
Pick on it and Viola you got a new thread.

you could subscribe to any thread and later, search for post / threds by your user name, In search-Advanced search.

Cause in a feww minutes you will be so many threads that keeping track of your posts can be a job indeed.

Cheers all the best,
Please post back if you need anything more.
You could mail me [email]abhi.kalyan@gmail.com[/email]
or just post here/ private message.
Stick here for a while and you will be made a wizard, cause there are loads of wizards here. ( And only a newbie=noob )
Thank you mrsdeath
Sinceraly
Abhi Kalyan

---

### Post by Abhi Kalyan on 2006-10-26
another thing you could do to find out the thread you have subscribed is get to
"User CP"
there on the left pane you can find
" Threads subcribed to"
Cheers all the best

---

