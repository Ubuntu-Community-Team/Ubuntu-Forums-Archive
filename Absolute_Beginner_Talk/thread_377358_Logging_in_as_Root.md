---
title: "Logging in as Root"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by sven_henson on 2007-03-06
Is there a way i can log in as root, not just inside the terminal but as a whole from the initial log in screen on ubuntu edgy eft? Can anyone help with this

Sven

---

### Post by 23meg on 2007-03-06
It's not recommended, and there's no use case requiring you to do it.

If you do want to enable it, check the "Allow local system administrator login" checkbox in System / Administration / Login Window / Security.

---

### Post by rsambuca on 2007-03-06
This feature is disabled by default in ubuntu for good reasons.  It can be done, but for what reason?  If you need to, you can open a root terminal by entering the command ```
sudo -i
```

---

### Post by aysiu on 2007-03-06
It's completely unnecessary and potentially dangerous.

This will help you get as graphical-root as you need to be:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by sven_henson on 2007-03-08
Thanks guys, I really have no pressing need, i used to use fedora and u could on there so i was just wondering

Thanks again
Sven

---

### Post by andrewlinn957 on 2007-03-08
i can think of a reason in that when i try to have my firewall open on startup automatically it wont because 'i dont have sufficant priviladges' which gets kinda annoying

---

### Post by pe1800 on 2007-03-10
I did just set that switch. But how do I now sign in as root? I want to look at the contents of a floppy and Gnome will not let me. It says I have no permission. By the way, it is my computer, I installed the Ubuntu software, and Ubuntu has no right to in any way restrict what I want to see or do!

---

