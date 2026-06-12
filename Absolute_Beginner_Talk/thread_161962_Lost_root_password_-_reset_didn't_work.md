---
title: "Lost root password - reset didn't work"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by peteremcc on 2006-04-18
Hey, very new to Ubuntu but am comfortable around computers etc...

However my friend set up my Ubuntu so i'm not quite sure what he did...
(I did choose the root password however i have forgotten it)

From browsing the web i learnt I should boot Ubuntu into single user mode so i did this:

edited GNU GRUB an added "single init=/bin/bash" to the end of the kernal line.

then i booted and used passwd (hopefully correctly) and it asked me to enter a new Unix password and then verify it.

but once i rebooted it still wasn't working.

Hope someone can help,

Thanks,

Peter

---

### Post by Darkriser on 2006-04-18
boot from Ubuntu install CD and choose "rescue" on prompt. this will bring you to console with root rights. from there you can change any password.

---

### Post by peteremcc on 2006-04-18
ok i will give that a try...
however is that any different from what i did earlier? i think i was logged in as root... it said root@ at the front of the command line

---

### Post by carverj on 2006-04-18
So thats pretty handy

> "single init=/bin/bash" 

Does that allow you to boot from a bash shell?
:-k

---

### Post by Darkriser on 2006-04-18
for more info look here

[https://wiki.ubuntu.com/LostPassword](https://wiki.ubuntu.com/LostPassword)

or 

[http://www.ubuntuforums.org/showthread.php?t=133102](http://www.ubuntuforums.org/showthread.php?t=133102)

---

### Post by peteremcc on 2006-04-18
carverj:

I'm not sure exactly what I did but I followed the info at this site...
[http://linuxgazette.net/107/tomar.html](http://linuxgazette.net/107/tomar.html)

When i did it, it seemed to not load Ubuntu at all but gave me a full screen terminal. Sorry for not being able to explain it properly, hopefully you guys can understand that website better than me :D

I will try using the disc to boot but I don't actually have the disc with me at the moment (and won't for a few days) so if there is another way that would be good ;)

---

### Post by peteremcc on 2006-04-18
will have a look at that Darkriser, thanks.

---

### Post by peteremcc on 2006-04-18
i just had another go using the /bin/bash thingy and it all seemed to be working (i got prompted to enter the new unix password and verify it) but once i did this it said:

"Authentication token lock busy"

any ideas?

Thanks

---

### Post by peteremcc on 2006-04-18
i had a bit more progress with this.

some more googling suggested i should try the following before changing the password...

mount -o remount,rw /

i tried this and then this time when i changed the password it said it had worked!

unfortunately when i rebooted, logged in and then tried to do something using root, it still didn't work :(

---

### Post by steve.horsley on 2006-04-18
Can you give us more detail on what you are doing when you "logged in and then tried to do something using root" and it still didn't work? 

I presume that when you log in you are logging in as someone other than root. I also pesume that when you "try to do something as root" it asks for a password. Remember that the default install is asking for you USER password, not the root password at this point. If this isn't the problem, please post more details on what you try to do and what the resonse is.

---

### Post by peteremcc on 2006-04-18
hey, i just tried changing the password again... previously the root password was the same as my user password (just to keep it simple).

so this time through changing it i set it to something different.

by doing something like root, i mean say going into the system settings and then say the user settings and clicking the admin button at the bottom.

it then prompts for a password and i have just tried both my user password and the new root password i just set

the reply i got was "conversation with su failed"... i assumed this meant a wrong password though i just realised this might not actually be the case.

Peter

---

### Post by peteremcc on 2006-04-18
made some more progress... seems that the above error meant my account wasn't listed in the /etc/sudoers file... thought my accont was never in this file, %admin WAS... so i assume this means my user account isn't being considered an admin account at the moment (which could explain some of these errors).

So i am now able to run some programs as root (by using the run as another user) however as i mentioned above, if i try and activate the admin things in the system settings, i get a different error now... "su returned with error"

Peter

---

### Post by peteremcc on 2006-04-18
just deleted my user account and created a new one to see if this would solve the problem... doensn't seem to have.

is there any easy way to reset all the user accounts / permissions etc etc or should i re-install ubuntu (when i get my cd back)?

peter

---

### Post by peteremcc on 2006-04-18
bump, tried again this morning, even tried assigning my user account to the admin and root groups but still the same

---

### Post by htinn on 2006-04-18
Sorry, but fixing su is way over my head.

---

### Post by Madpilot on 2006-04-18
peteremcc,  at this point it might be simplest to just re-install Ubuntu, using the default install, and have a look at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) to see how Ubuntu handles admin privs. by default - there is no root pw...

---

### Post by peteremcc on 2006-04-19
alright i'll do that once i've got the cd back.

thanks,
peter

---

