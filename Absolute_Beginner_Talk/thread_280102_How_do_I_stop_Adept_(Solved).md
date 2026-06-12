---
title: "How do I stop Adept? (Solved)"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-10-18
I want to uninstall some packages as they are not updating properly.  During the update installation when it gets to mythtv it says it cannot continue as it may break some packages.  When I then close it and open Adept Manager to remove mythtv it says there is another instance of it running and to close it first.  

How do I close the running instance of Adept?

---

### Post by David_T on 2006-10-19
You can just type in the terminal 
```

sudo killall adept

```
and that should do it.

I don't know what the process name is, but if it's something like adept-manager, you would have to do killall on that instead.

---

### Post by Russty of Oz on 2006-10-19
that didn't work, I tried adept. adept manager, adept_manager but it said "no  process killed"

---

### Post by aysiu on 2006-10-19
```
sudo killall dpkg
``` maybe?

---

### Post by Russty of Oz on 2006-10-19
Nope!  same reply, "no process killed" :-k 

Sigh! :neutral:

---

### Post by po0f on 2006-10-19
Russty of Oz,

Check your home directory for a lock file, maybe something like ~/.adept.lock?  I haven't used Adept, so I really don't know if it sets a lock file or not.

---

### Post by Russty of Oz on 2006-10-19
It said no such file or directory.  I will try a reboot.  I didn't want to do it as last time I couldn't get Ubuntu to boot for 2 days.

I will try it and let you know soon if it works.

---

### Post by Russty of Oz on 2006-10-19
I rebooted but it still says that it is running. :(

---

### Post by po0f on 2006-10-19
Russty of Oz,

Post the output of:
```
$ find ~ -iname "*adept*"
```

---

### Post by Jucato on 2006-10-19
```
sudo dpkg --configure -a
```

---

### Post by Russty of Oz on 2006-10-19
Its OK now, while you were posting that last message I had logged out and logged into gnome to see if that would help.  I tried running synaptic and it said there was a problem and that I should do  **dpkg --reconfigure -a**   So I did that and then it said I need to **dpkg-reconfigure --force mythtv-database** so I then did that and then synaptic worked.  So I was then able to remove mythtv from there and then I logged back into KDE and all is fine.:) 

Thanks for you help, it seems synaptic gives you a clue as to what to do about problems whereas Adept doesn't.  Something to bear in mind.

Russty.

---

### Post by Russty of Oz on 2006-10-19
> **Jucato said:**
> ```
sudo dpkg --configure -a
```

Ah! You had the answer all along!  You posted while I was writing my last post.

---

