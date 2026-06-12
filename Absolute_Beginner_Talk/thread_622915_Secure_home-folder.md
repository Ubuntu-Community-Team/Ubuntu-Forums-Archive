---
title: "Secure home-folder"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Martje_001 on 2007-11-25
HI all,
How do I secure my homefolder? Now it is readable (writeable?) for everyone, I don't want that.

Thank you,
Martin

---

### Post by brennydoogles on 2007-11-25
> **Martje_001 said:**
> HI all,
How do I secure my homefolder? Now it is readable (writeable?) for everyone, I don't want that.

Thank you,
Martin

hmmm... is it really writeable for everyone?? Let me poke around and see if I can find a good answer. I will post back.

---

### Post by KhaaL on 2007-11-25
brennydoogles, should he set the permissions in his home folder to 600 (read/write for the owner, no acess to the others)?

Sorry, I'm not too familiar with how this command should be executed :p

Edit: ok i think the command should be:

sudo chmod -Rv 600 ~/


NO NOT USE THIS YET! let someone else in the forum see and approve the command first as i'm not sure wether it can mess up some config files or something else...

---

### Post by brennydoogles on 2007-11-25
> **KhaaL said:**
> brennydoogles, should he set the permissions in his home folder to 600 (read/write for the owner, no acess to the others)?

Sorry, I'm not too familiar with how this command should be executed :p

Edit: ok i think the command should be:

sudo chmod -Rv 600 ~/


NO NOT USE THIS YET! let someone else in the forum see and approve the command first as i'm not sure wether it can mess up some config files or something else...

I'm trying to find out as well. I seem to remember from somewhere that Home folder permissions have to be 644, but I am trying to find out for sure now. To the OP, would encryption be a useful option for you?

::EDIT::

Accordint to [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=287043") it apperas that you will be unable to log in if your home folder has permissions other than 644 (which means if you can log in now, we can't change the permissions to lock anyone else out.) We could however look at some encryption options if you want.

---

### Post by Martje_001 on 2007-11-25
I'm using easycrypt.. works fine ;). Can I make another group (because it's readable by the group)? What should I call it?

---

