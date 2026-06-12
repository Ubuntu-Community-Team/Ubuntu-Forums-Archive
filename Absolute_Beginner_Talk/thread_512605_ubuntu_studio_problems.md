---
title: "ubuntu studio problems"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by mrblack on 2007-07-29
Hey all,

I've had the oddest problem climb out of nowhere. I upgraded to Ubuntu studio about 2 weeks ago and everything was fine, until one day the system started freezing when i tried to go to the home folder or open anything in it. So i force quit the folder, and then my desktop was gone. Sometimes it would reappear, but if i tried to open any folders it would repeat all over. Add to that, I went to install some updates and it said
"Not all updates can be installed, Run a partial upgrade to install as many updates as possible"

Any suggestions?

---

### Post by FleetAdmiral74 on 2007-07-29
Does the same thing happen when you reboot? Is it completely random when it happens? Or will the computer even boot now.

PS: I am not sure that we offer official support for Studio, might have to visit their forums. Just not sure...

---

### Post by mrblack on 2007-07-29
nope, its fairly consistant everytime i reboot and go to my home folder and try to open another folder. it Freezes.  BUT if i have a shortcut to a certain folder [i.e. my music folder in the home directory] i can use that to get there. same with the updates too

---

### Post by mrblack on 2007-08-08
waaah i still need help

---

### Post by avik on 2007-08-08
Seems like an issue with Nautilus, the file manager as well as the desktop manager to some degree.  All I can say is that might be a bad update or something from before.

Don't hold me to this, and definitely wait for someone else on the forums to confirm that I might be on the right track, but I would do:

```
sudo dpkg-reconfigure nautilus
```

That's just pure speculation, though.  Anyone else have any ideas?

---

### Post by tgalati4 on 2007-08-09
Post relevant portions of dmesg and any unusual errors in /var/log.  Could be failing hardware.

---

### Post by mrblack on 2007-08-09
"Post relevant portions of dmesg and any unusual errors in /var/log. Could be failing hardware."

*quite noobish* 
where/how can i get to this dmesg thing? I've only heard of it but thats it

---

### Post by wPwLUi3N on 2007-08-09
Which update resulted into such a problem?

---

### Post by wPwLUi3N on 2007-08-09
Updates can be nasty so update only when it is required such as thier is bug or poor performance in loder version.

It is easy to get attracted to new version but they maybe highly unstable and rarely but possibly damage the OS.

If you are sure which update did it, you should report it in community.

---

### Post by mrblack on 2007-08-12
it wasnt an update that did it [i believe] 
I'm not even sure what caused it. It appeared
out of the blue, and because of it I can't update
as well as a variety of other things. surfing the web
is just about the safest thing this thing can do right now without it crashing

---

