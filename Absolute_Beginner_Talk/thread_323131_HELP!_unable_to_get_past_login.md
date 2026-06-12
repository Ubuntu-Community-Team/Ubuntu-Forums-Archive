---
title: "HELP! unable to get past login"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-12-21
After having worked with ubuntu on my new computer ofr about 1 week, all of a sudden now I cannot get past the login screen.  I will enter my name and password, the screen will dissapear and the same login screen will reappear.  

The only system changes I made before encountering this problem was editing my xorg.conf file (X server), in hopes to reset some default resolution settings.  

Does anyone have any idea why this is happening?

---

### Post by taurus on 2006-12-21
See if your usrname and password are any good from a console.  At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password!  

Can you log in at all?

---

### Post by oscar78 on 2006-12-21
yes, my login at the console works, and I'm at the console right now.  there must be something wrong with my graphics settings, no?

---

### Post by taurus on 2006-12-21
What's the output of this command then?

```
ls -la
```

---

### Post by oscar78 on 2006-12-21
I have a whole list of programs

---

### Post by taurus on 2006-12-21
I just want to see the permissions of a few files, especially ~/.dmrc...

---

### Post by oscar78 on 2006-12-21
~/.dmrc is too far up on the list that I cant see it on the screen, is there a way to scroll up?

---

### Post by oscar78 on 2006-12-21
nevermind, so i got it.

I have 

-rw------- 1 andy andy.. date... /home/andy/.dmrc

---

### Post by annda on 2006-12-21
it looks like your Xserver crashes every time you start it.  have you backed up your xorg.conf? if so, overwrite it with the backup and carefully look at the changes you've made.

if you can't come up with what the problem is, you might post the changed sections so someone may help.

---

### Post by gentlemanmasher on 2006-12-21
This might not be it but I filled up my drive and had the same problem.  It just would continually re-boot.  I deleted some files and it started working again.

I thought it was my X-Server but it ended up me being an idiot.

---

