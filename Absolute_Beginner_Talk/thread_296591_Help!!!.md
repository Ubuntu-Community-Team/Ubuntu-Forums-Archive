---
title: "Help!!!"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by sindrum_murdnis on 2006-11-09
ok im in deep again, i think. when installing i put my user name as sindum instead of sindrum. so after setting everything up i decided to change the user name. well now i cant access anything. is there a command that will let me re set the old user name? or am i going to have to reinstall again?](*,)

---

### Post by professor_chaos on 2006-11-09
how did you change your username, and what can't you access?

usermod is the command you can use to change your username and other settings relating to your user.

---

### Post by BLTicklemonster on 2006-11-09
Don't give up, I have seen somewhere in here where you can do this. Perhaps you can boot to recovery and then come here and look around for how to add a user and give them admin priveleges and log on using that?

---

### Post by sindrum_murdnis on 2006-11-09
ok i went to systems/ administration / users and groups and changed the properties on my user and then went to advanced settings and changed my home directory . i noticed that i want able to goto anything it would start to load then would stop. so i logged out and tryed to log back in now it gives me a warning message ill reboot and get that if you need

---

### Post by professor_chaos on 2006-11-09
> **sindrum_murdnis said:**
> ok i went to systems/ administration / users and groups and changed the properties on my user and then went to advanced settings and changed my home directory . i noticed that i want able to goto anything it would start to load then would stop. so i logged out and tryed to log back in now it gives me a warning message ill reboot and get that if you need

what message do you get when you switch to tty1 (ctrl+alt+F1) command prompt and then trying to login from there?

---

### Post by sindrum_murdnis on 2006-11-09
well i was able to login ttyl i get no error messages. i was able to browse through the directories. so i tried /etc/init.d/gdm start and this faild. it said i didnt have enough permissions to login.

---

### Post by professor_chaos on 2006-11-09
> **sindrum_murdnis said:**
> well i was able to login ttyl i get no error messages. i was able to browse through the directories. so i tried /etc/init.d/gdm start and this faild. it said i didnt have enough permissions to login.

did you sudo?

```
sudo /etc/init.d/gdm restart
```

---

### Post by ner0tic on 2006-11-09
> **sindrum_murdnis said:**
> well i was able to login ttyl i get no error messages. i was able to browse through the directories. so i tried /etc/init.d/gdm start and this faild. it said i didnt have enough permissions to login.

are you a member of the gdm group?
> sudo cat /etc/group


---

### Post by aysiu on 2006-11-09
Sounds as if you're not in the *admin* group for whatever reason.

This will help: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by sindrum_murdnis on 2006-11-09
ok im new and did forget to sudo. so i wen tback and did sudo /etc/init.d/gdm start and it says

*starting Gnome Display manager... ok

then loops back to the prompt.im completely lost

---

### Post by ner0tic on 2006-11-09
try this
> sudo /etc/init.d/gdm restart | logout

---

### Post by sindrum_murdnis on 2006-11-09
let me first say thanks for helping me along here. umm now down to business sudo /etc/init.d/gdm restart | exit seems to be the command you wanted me to try. that didnt work though, so im goin to have to tap out here and i hate to say this but im re formating again. 2 in one day not a good score. thanks agin for the help.

---

