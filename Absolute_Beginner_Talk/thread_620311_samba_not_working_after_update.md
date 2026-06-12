---
title: "samba not working after update"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-11-22
Running 7.10 I did the latest update of samba. Prior I could access both my windoze boxes and they could access Gutsy. Now I can access Gutsy from windoze but not the other way. When I try, I get the windows network but then it says it cannot display the contents of the home folder. Can someone steer me as to what to check?

---

### Post by gigaferz on 2007-11-22
since it is not working anymore, either you could uninstall it, and remove your hidden folder .samba, then install again.

  or I've heard that most of the programs create a backup copy of your old settings, so you could replace them, sounds like your config files are gone.

(i always do the firts option)

and go thorugh the same steps  you took to make it work as you had it before. (see i have like hundreds of updates wich honestly i just ignore..)

---

### Post by nikoPSK on 2007-11-22
there was an update problem, maybe you got a dirty update?

---

### Post by rsnow on 2007-11-23
Here is where things stand now:

I can bring up the other computers on my lan from Gutsy but when I click on one of them I get a message saying the contents of the folder 'name of computer' cannot be displayed. I admit to not being very smart about these things but why would it consider another computer as a folder?

I can ping the other computers so it is not a problem with eth0. My samba.conf shows the proper work group. It appears to me as if it is permission or security setting somewhere.

---

### Post by The Pinny Parlour on 2007-11-25
I just discovered my freshly installed Gutsy that had (networking to windows WORKING) now isn't.

These updates recently, I believe, have borked it.  I'm constantly being bitten by Ubuntu "CRAPPY UPDATES"  that bork the system.  Fair Dinkum.

Anyone know how to make it all work again?

Thank you

---

### Post by rsnow on 2007-11-27
Well, it looks like there won't be much help here. So, I guess I'll try somewhere else.

---

### Post by nikoPSK on 2007-11-27
Well, I hope you eventually resolve the issue, good luck.

---

### Post by The Pinny Parlour on 2007-11-28
> **rsnow said:**
> Well, it looks like there won't be much help here. So, I guess I'll try somewhere else.

Try setting a Static IP on your windows PC, (say 192.168.1.10)  Go into Places>Network>...Press the button next to where it says network, (near / on the address bar) to change it to an address field. 

Click on Windows Network icon and then in the address bar you should have something like this:
**smb:///**
Change it to:
**smb://192.168.1.10**  <----IP of your windows box.  See if it comes up then.

---

### Post by rsnow on 2007-11-29
Yeah, it worked! Thanks, now I can access both of my xp machines. I don't understand the why but at least I can now use my network. Thanks again.

---

### Post by nikoPSK on 2007-11-29
good for you! Glad we could (somewhat) help.

---

### Post by The Pinny Parlour on 2007-12-02
> **rsnow said:**
> Yeah, it worked! Thanks, now I can access both of my xp machines. I don't understand the why but at least I can now use my network. Thanks again.

Your welcome.   I know this as this frustration has plagued my Ubuntu experience.  Something to do with the Dreaded SAMBA.  Oh how SAMBA is rubbish sometimes.  I have NEVER had it working properly in all the time I have been using Ubuntu.  I have had many fresh installs too.

---

### Post by nikoPSK on 2007-12-02
It's working? Good! Please mark this thread as solved.

---

