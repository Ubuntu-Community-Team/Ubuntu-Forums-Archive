---
title: "Is it now safe to update?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by stig on 2007-02-12
Regarding the "Announcement: WARNING : potential problem with new kernel update" banner at the top of this forum.

I did not do the update when it arrived. Is it now safe to do so? I've looked at the long thread (357 messages!) and the last, closing announcement sent by Vorian but I don't understand what that announcement means and whether or not it refers to me. Do I just run the update now - or do I have to do a system upgrade or what?

Thanks!

---

### Post by frodon on 2007-02-12
Yes it is safe ;)

Obviously if you have installed nvidia drivers or other specific drivers outside the official repositories then you will have to install them again like for any kernel update.

---

### Post by Anicka on 2007-02-12
I think it means: update shouldn't be too much of a problem...

I updated (I'm using 6.10) with synaptic without problems. Aptitude on the other hand complained about some dependency problems with apt-watch, imagemanick and blt-demo. It suggested to remove some of the linux components (pretty much go back to the old kernel) to solve the dependecies. After removing and re-installing the apt-watch & co. the dependecies were resolved (without touching linux) and all is good.

Just one thing, I'm using Ubuntu as a guest in VMWare so I don't have to worry about drivers for graphics and so on. That seems otherwise to be the biggest headache for many users.

Good luck!

---

### Post by stig on 2007-02-12
> **frodon said:**
> Yes it is safe ;)
Obviously if you have installed nvidia drivers or other specific drivers outside the official repositories then you will have to install them again like for any kernel update.

Thanks! that's the simple, concise advice that I needed but couldn't find (but perhaps I hadn't looked far enough due to being too busy). I stick to the repos because I like an easy life. :) 

I'll wait until later when I've finshed my most important piece of work on the machine, then give it a try.

And thanks to Anicka too for your input and support.

---

