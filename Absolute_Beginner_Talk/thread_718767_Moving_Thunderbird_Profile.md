---
title: "Moving Thunderbird Profile"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2008-03-08
How do I tell Thunderbird in my Xubuntu to point to my Thunderbird folders I created in Thunderbird under XP which is located in /home/eMail/Thunderbird?

---

### Post by markharding557 on 2008-03-08
> **mikeypc2006 said:**
> How do I tell Thunderbird in my Xubuntu to point to my Thunderbird folders I created in Thunderbird under XP which is located in /home/eMail/Thunderbird?

you can copy your profile from xp to the one in ubuntu

---

### Post by mikeypc2006 on 2008-03-08
> **markharding557 said:**
> you can copy your profile from xp to the one in ubuntu

Ok, so how do I point Thunderbird to a different location for the file storage from the default location?

---

### Post by ugm6hr on 2008-03-08
Your Thunderbird emails are located at:
Edit-> Account Settings...
Local Folders
In the box below "Message Storage"

I think you can just browse to where the profile is.

I actually did it the other way round (created a default setting in Ubuntu, and then access that from Windows), but I assume it works similarly both ways.

---

### Post by mikeypc2006 on 2008-03-08
> **ugm6hr said:**
> Your Thunderbird emails are located at:
Edit-> Account Settings...
Local Folders
In the box below "Message Storage"

I think you can just browse to where the profile is.

I actually did it the other way round (created a default setting in Ubuntu, and then access that from Windows), but I assume it works similarly both ways.

I've played with the profile.ini file and now when I try and open Thunderbird, it comes up with the message saying 'Thunderbird is already running and may have crashed, try restarting'.

What have I done wrong?

---

### Post by mikeypc2006 on 2008-03-08
Found the command I needed to open the profile manager in Xubunutu :)

```
sudo thunderbird -profilemanager
```

---

