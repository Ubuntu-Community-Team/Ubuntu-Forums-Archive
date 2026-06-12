---
title: "Double install by mistake. How to uninstall one."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Karnex420 on 2006-09-30
Oh boy.  I thought I installed wrong my first time.  Just didn't open all the java window from automatix downloads so I reinstalled ubuntu and it worked great but I forgot to uninstall my first ubuntu.  I actually got my second ubuntu to open once but now I can't get past the purple window.
Is there a way I can straighten this out maybe with my burnt ubuntu cd or do I just uninstall?  I would be happy uninstalling my last ubuntu.  I see now my first install may have been good.

I'm just beginning but this all makes sense to me a lot more than windows concepts.  This is fun.
Now I'm triple booted what with windows o.s. and all.
Any suggestions for this one?
I'm not even sure how to uninstall.

---

### Post by BoneKracker on 2006-09-30
Yeah, you got it...
[LIST=1]
[*]Boot from the Ubuntu CD.
[*]System > Administration > Gnome Partition Editor
[*]Delete all the partitions that were created by your previous two Ubuntu installs (be careful not to delete your Windows stuff).
[*]Then reinstall and be a little more careful with automatix.
[/LIST]

---

### Post by Karnex420 on 2006-09-30
I'm on it.

---

### Post by Karnex420 on 2006-09-30
How can you tell what to delete?  I don't know if it is connected to windows or not.

---

### Post by bulldog on 2006-09-30
> **Karnex420 said:**
> How can you tell what to delete?  I don't know if it is connected to windows or not.
 It's not connected to windows for sure :D 

You only have to watch out you delete the windows partition by accident.

Can't you see which your first ubuntu partitions are?
So you just delete the second ubuntu partitions and alter GRUB a little and your done without reinstalling.

Can you put the outcome of ```
 sudo fdisl -l 
```

Maybe we can see what the 'old' ubuntu was.

---

### Post by xpod on 2006-09-30
> I actually got my second ubuntu to open once but now I can't get past the purple window.

PURPLE?????....What happened to the bootifull broon??:mrgreen: 

It should be easy enough to establish what partitions are what.Just dont go deleting the ones you want to keep.
Whatever order you installed in will most likely be the order of your partitions as they show up in Gparted ithink?.....Double check,double check!!!

"sudo fdisk -ls" should list em all

---

### Post by Karnex420 on 2006-10-12
I just read somewhere the new install should erase the old one automatically so maybe I was worrying about the wrong thing.  
If this is not entirely correct I should have backed stuff up and deleted one thing at a time and then looked but I was tired and in a hurry so I did lose stuff.  Oh well starting over is good when you are sure where you are going.
So much good stuff waiting ahead tempts one to skip ahead.
I want this, that, and oh yeah one of those over there too.
Linux rules!

---

