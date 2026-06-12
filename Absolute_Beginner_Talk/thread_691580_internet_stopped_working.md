---
title: "internet stopped working"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jimmyjosh on 2008-02-08
Hi, I just installed Ubuntu 7.10 on my machine this morning. Everything was working great, when it asked me to update to install some security things. I did and after restarting my internet wouldn't work. I have no clue what to do, help!!

---

### Post by nynoah on 2008-02-08
laptop wireless or plug and play internet?

---

### Post by jimmyjosh on 2008-02-08
> **nynoah said:**
> laptop wireless or plug and play internet?

desktop, plug and play ethernet

---

### Post by sumguy231 on 2008-02-08
Are you using a static or dynamic IP address?
Re-verify that your network settings are correct, and see what happens if you do this in a terminal:
```
sudo /etc/init.d/networking restart
```

---

### Post by jimmyjosh on 2008-02-08
> **sumguy231 said:**
> Are you using a static or dynamic IP address?
Re-verify that your network settings are correct, and see what happens if you do this in a terminal:
```
sudo /etc/init.d/networking restart
```

dynamic. i'm in xp right now, so i'm going to have to restart. what should i be looking for when i put that in the terminal?

---

### Post by nynoah on 2008-02-08
That command he gave you will just shut down and restart your connection.   That might just solve it.

---

### Post by jimmyjosh on 2008-02-08
That worked, thanks!!

---

### Post by nynoah on 2008-02-08
I think you can also restart them by just Right clicking on the icon for your internet and enabling or disabling.   Also,,,,,,,,sometimes a simple Ctrl-Alt-backspace will be enough to reset it.  Warning this will kick out out to the login screen so have all things saved, saved (just encase)  But most of the time you will not loose a thing.  It will just reset everything.

---

