---
title: "No Sound in headphones"
date: 2009-11-07
forum: Apple Hardware Users
---

### Post by ricky0319 on 2009-11-07
I am using Karmiv on my Macbook 2,1. The external speakers work fine, however when I put headphones in the sound does not work. I have tried different sound settings and it still does not work (The headphones work, I tested them in Mac OSX)Any help would be greatly appreciated.

---

### Post by Glucklich on 2009-11-08
I don't have a definitive solution for this problem but I think I may have a quick fix.

In the sound mixer, when you click on "Select controls" (not sure if that's the same name for it since I'm using it on my native language and a derivative), you'll see two options. One named "Front" and another named "Surround". Select them both and close. Now, these two will appear on the main window. Unmute the "Surround" and put it on max (this one, will be controlling the headphones but... since when you unplug the phones it won't be giving any sound, you don't need to control it). The "Front" one just put it on max, it will be controlling your computer speakers (that, on the other hand, you'll have to mute when you don't want any sound coming out from them). 
For the sound level coming out from both, just use the main channel which should be controllable from your shortcuts or visible from your desktop and leveled with a simple mouse movement.

---

### Post by Deverell on 2009-11-08
> **Glucklich said:**
> 
In the sound mixer

I remember this solution working for me when I had the Karmic Beta, then I switched to Jaunty and now I'm back at Karmic. 

My problem is I can't find the sound mixer only sound preferences where I have no option to unmute the surround.

---

### Post by Glucklich on 2009-11-08
> **Deverell said:**
> I remember this solution working for me when I had the Karmic Beta, then I switched to Jaunty and now I'm back at Karmic. 

My problem is I can't find the sound mixer only sound preferences where I have no option to unmute the surround.

Unfortunately, I'm on a production machine so I haven't updated to Karmic yet. So, I'm sorry to not be able to help you on that subject. Hope somebody takes a minute to check it and let you know where you can find it. But that's very strange indeed.

Maybe, if it comes to that point, look for a mixer in the repositories that might fit your needs?

---

### Post by adityavpratap on 2009-11-09
Thanks guys!

You made my day. I was struggling with this problem since eternity. Now I can listen to my favorite music without disturbing others.:D

---

### Post by yoyo007 on 2009-11-10
I have a macbook 2,1 my headphones didn't work but I ran alsamixer from the terminal and found a speaker was muted. I unmuted it in alsamixer and now my headphones work perfectly. :D

---

### Post by Glucklich on 2009-11-10
Glad to know this solution has worked for all of you ;)

---

### Post by linuxopjemac on 2009-11-13
it also worked for me, so great !! (MacBook 2,1)

I added a pic of how the settings should be to have it working...

[IMG]http://mac.linux.be/Ubuntu/alsamixer[/IMG]

---

