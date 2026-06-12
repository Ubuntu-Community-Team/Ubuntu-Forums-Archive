---
title: "windows gone from grub"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by MAHER5 on 2007-09-26
when i installed wine my windows xp went missing in my grub loader,all that was left is my ubuntu,how can i get it back??

---

### Post by Jussi Kukkonen on 2007-09-26
I doubt Wine is the culprit, but maybe there was a kernel update at the same time? That could make your Windows-entry vanish, especially if there was a mistake when you edited the entries... 

Can you copy paste the contents of */boot/grub/menu.lst* here? If there is a backup in the same directory (such as */boot/grub/menu.lst**~***), you might want to copy paste that too.

---

### Post by dn_desaku on 2007-09-26
Try a different boot manager of a CD. I would suggest the Smart Boot Manager off of EmergenyBoot CD. [http://www.ebcd.pcministry.com/](http://www.ebcd.pcministry.com/)

---

### Post by lightstream on 2007-09-26
Same has happened to me - indeed there was some update which I applied, and I noticed in the window the message 'Updating menu.lst' or words to that effect.

It seems that it rewrote my menu.lst file and did not make a back up - there is not one in /grub/boot anyway.

Does anyone know if it might have saved my old file in any other location? I had a lot of different options in there, I find it hard to believe it would just wipe it out???

---

### Post by mcduck on 2007-09-26
> **lightstream said:**
> Same has happened to me - indeed there was some update which I applied, and I noticed in the window the message 'Updating menu.lst' or words to that effect.

It seems that it rewrote my menu.lst file and did not make a back up - there is not one in /grub/boot anyway.

Does anyone know if it might have saved my old file in any other location? I had a lot of different options in there, I find it hard to believe it would just wipe it out???

No, it doesn't make a backup. Did you perhaps edit the file yourself at some point? Because updating menu.lst during updates should not erase any of your own entries from the file as long as they are in the correct place inside the file..

---

### Post by lightstream on 2007-09-26
> **mcduck said:**
> No, it doesn't make a backup. Did you perhaps edit the file yourself at some point? Because updating menu.lst during updates should not erase any of your own entries from the file as long as they are in the correct place inside the file..

](*,) Yes I edited it quite a bit - my windows is on the 3rd partition of my main drive, and there were a few special commands I needed to use.

Now I'm worried about how to put them back as I managed to cause Windows to kill itself by having the wrong ones in there before 

I just wanted to play Battlefield before bedtime :cry:

Edit: OK, I see the automagic thingee now. I had put all my options inside there, live and learn eh?

---

### Post by mcduck on 2007-09-26
> **lightstream said:**
> 
Edit: OK, I see the automagic thingee now. I had put all my options inside there, live and learn eh?

Yeah, that's the thing.. You need to add all non-Ubuntu entries either before or after the automagick area. Also, if you do any changes or additions to Ubuntu's boot options be sure to do them also in the default options section (no need to uncomment them, just add your changes).

This way all your own configurations will stay even through kernel updates.

---

### Post by lightstream on 2007-10-02
Thanks for your tips buddy. I was able to restore my previous options without too much difficulty in the end.

---

