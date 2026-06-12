---
title: "How practical is this?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by lightsenshi on 2007-08-03
I'm sure this has been asked before.

I'm wanting to use the desktop version as a samba share but I'm having authentication problems with Windows XP (Pro).  I can find the share but I can't log into it.

What simple and obvious thing am I overlooking?

Thanks.  ^_^

---

### Post by guilly on 2007-08-03
do you have the same username and password on both windows and linux machines?

---

### Post by lightsenshi on 2007-08-03
I do not.

You know, I probably need to set up an account that lets me validate with samba.

Hmm....

---

### Post by roaldz on 2007-08-03
> **lightsenshi said:**
> I do not.

You know, I probably need to set up an account that lets me validate with samba.

Hmm....

If you want to connect to your Ubuntu box with your XP box, the easiest way is to open the samba config (sudo gedit /etc/samba/smb.conf) And look for the option "Security". Make it active (remove the ";" character) and set it to "share" (Instead of user).
Doing this, all your share's are visible to everyone.

Now you should be able to connect to your Ubuntu box with your XP box.

---

### Post by guilly on 2007-08-03
humm never knew about that method, maybe that's why i can't see my shares from my ubuntu box?? and only from my xp box??

---

### Post by ugm6hr on 2007-08-03
> **roaldz said:**
> If you want to connect to your Ubuntu box with your XP box, the easiest way is to open the samba config (sudo gedit /etc/samba/smb.conf) And look for the option "Security". Make it active (remove the ";" character) and set it to "share" (Instead of user).
Doing this, all your share's are visible to everyone.

Now you should be able to connect to your Ubuntu box with your XP box.

So you can see exactly where this edit goes: [http://ubuntuforums.org/showpost.php?p=3113048&postcount=2](http://ubuntuforums.org/showpost.php?p=3113048&postcount=2)

---

