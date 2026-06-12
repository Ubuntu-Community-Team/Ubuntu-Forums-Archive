---
title: "open soundjuicer when putting in cd"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Circus-Killer on 2008-03-31
currently, in the hardy beta, when you put a cd in the drive, it automatically opens up rhythmbox instead of soundjuicer. how do i change it back so that when i insert a cd it opens up soundjuicer?

---

### Post by Circus-Killer on 2008-03-31
*bump*

anybody?

---

### Post by Achtung on 2008-03-31
Not sure about Hardy, but in gutsy, click System/Preferences/Removable drives and media/multimedia, tick "Play audio CDs when inserted" and use the command:```
sound-juicer -d %d
```

---

### Post by alexforcefive on 2008-03-31
System > Preferences > Removable Drives and Media > Multimedia

*edit* must type faster >.<

---

### Post by stchman on 2008-03-31
Try System--->Preferences--->Removable Drives and Media.  I believe you look under the Multimedia tab and there is a category for what to do when a CD is inserted.

I believe if you use:

```
sound-juicer -d %d
```

That will cause sound juicer to fire up automatically.

---

### Post by Circus-Killer on 2008-03-31
no such luck :(
(see attachment)

---

### Post by plucky on 2008-03-31
Try **System > Preferences > Preferred Applications > Multimedia**

Good Luck

---

### Post by shanepardue on 2008-03-31
I haven't been able to accomplish this either. It's not the same procedure as Gutsy and 
plucky's recommendation is for media files, not cd's.

---

### Post by Circus-Killer on 2008-04-02
> **shanepardue said:**
> I haven't been able to accomplish this either. It's not the same procedure as Gutsy and 
plucky's recommendation is for media files, not cd's.

yeh, thats what i was getting at with the screenshot i posted in the above post.

---

