---
title: "Is there a software which perform memory cleanup?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-03-10
Hi
Thank you for reading my post.
I have 1.5 GB RAM and after two or 3 days my memory usage shows that I have used 1.1 gig of memory.
It is possible that my maximum memory usage reached that number for after I close applications that I had open it should drop to a normal amount, but it does not.
It also shows that 800 meg of SWAP is in use too, what should I do?
Is there any memory optimizer/ defragmenter/ cleaner for linux?

Thanks.

---

### Post by ansicplusplus on 2008-03-10
Hy,

I have never heard of such software for linux as linux keeps quite good track of ressources and allocates the memory it actually needs.

Let 's have a look which application hogs your memory. Using gnome-system-monitor you can find out very easily. You will see the detailed memory usage on the second tab.
Maybe you discover an application which behaved strangely some time ago. If you are sure you don't need the application running and saved all your work, you can terminate the application with the button in the corner down-right. That should definitely will free the used memory.

Yours, ansicplusplus

---

### Post by forestpixie on 2008-03-10
memory gets used differently here - so things stay put until something else wnats the memory

the only time my memory drops is if I've been editing a doc with loads of images - which all gets put in memory while I'm busy, then once doc is closed - there's a bit of free memory for a while

the opposite of win which on uses memory when it's needed

---

### Post by jan quark on 2008-03-10
also these terminal commands should help to specify the current processes running

```
top
pstree
```

---

### Post by samwyse on 2008-03-10
Log out and restart the X server. Some apps just leak memory.

---

### Post by Arkenzor on 2008-03-10
Also be aware that the longer your session lasts, the more memory will be used as cache. That is, once something has been loaded into memory it's kept there even if it's not needed anymore, and until the space it occupies becomes needed for something else. This way, if you need it again it'll already be there, and if you don't you won't lose anything.

Usually, having a lot of data in memory is rather a good thing as long as your computer stays responsive. It simply means all the programs you loaded once will not need to be loaded again, unless the space they occupy becomes needed for something else.

Then again it's also possible you really have a memory leak somewhere. Try opening a few more memory-heavy programs while monitoring your used memory.

---

### Post by LeAstrale on 2008-03-10
its my general experience that Lunux uses RAM in a different way compared to windows. Where as windows use the pagefile and your ram when needed. Linux actually just keeps the ttuff you've used in the cache so taht when/if you want to start/do the same again it is already in the memory which makes its faster.

but then again.. you haven't bought the RAM not to use have you?

/Astral-1

---

### Post by hyper_ch on 2008-03-10
run

```

free -mem

```

and it'll show you exactely how much memory is used by applications and how much is stil cached by other stuff.

---

### Post by julian67 on 2008-03-10
You might want to read this article, which explains in very clear and easily understandable terms how memory is used/managed in Linux. [FAQ Linux Memory Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

---

### Post by legolas_w on 2008-03-10
Thank you for your help.
I found that 40% of my memory was used by Compiz.real.
Is that program the main compiz fusion or it is an extension?

thanks.

---

### Post by roaldz on 2008-03-10
> **legolas_w said:**
> Thank you for your help.
I found that 40% of my memory was used by Compiz.real.
Is that program the main compiz fusion or it is an extension?

thanks.

40% For Compiz!? I have 2 Gig ram and compiz.real uses 1.8% of my ram. That´s probably a leak there!. Which Ubuntu release do you use? (7.04/7.10/8.04)
Compiz.real is compiz itself.

Roald

---

### Post by ansicplusplus on 2008-03-10
> **legolas_w said:**
> 
Is that program the main compiz fusion or it is an extension?
My guess is it's one of the extensions. I use compiz myself and memory usage is fine here. 
Try disabling half of them an watch your memory. If nothing changes try disabling the other half and so on. That way you will narrow it down with a few rounds. 
After that you are left with the choice between eye candy and memory :)

Yours, ansicplusplus

---

### Post by roaldz on 2008-03-10
> **ansicplusplus said:**
> My guess is it's one of the extensions. I use compiz myself and memory usage is fine here. 
Try disabling half of them an watch your memory. If nothing changes try disabling the other half and so on. That way you will narrow it down with a few rounds. 
After that you are left with the choice between eye candy and memory :)

Yours, ansicplusplus

Compiz.real is not an extention. Its compiz itself.

---

### Post by legolas_w on 2008-03-10
I Installed many add ons to compiz and I think they are playing a nasty game :(
I have Ubuntu 7.10.
I will try to uninstall some plugins to see what will happens.

Thanks

---

### Post by roaldz on 2008-03-10
> **legolas_w said:**
> I Installed many add ons to compiz and I think they are playing a nasty game :(
I have Ubuntu 7.10.
I will try to uninstall some plugins to see what will happens.

Thanks

Try to disable the Blur plugin. Gave me problems too.

---

### Post by marufaberlin on 2008-03-10
You could just install a lowmem kernel...

---

