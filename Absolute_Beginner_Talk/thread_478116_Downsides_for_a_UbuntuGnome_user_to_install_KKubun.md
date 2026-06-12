---
title: "Downsides for a Ubuntu/Gnome user to install K*/Kubuntu/KDE programs?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-19
I'm on Ubuntu/gnome. What are the implications in installing Kubuntu/KDE programs? Will that mean that my computer will now run slower, because synaptic/add-remove needed to download and use a lot of KDE "background" files in order to run KDE programs (programs that start with the letter K)? Will more memory (RAM) be used?


If I add/install 2 KDE programs, And I delete both of them, will all the other peripheral "background" files that synaptic/add-remove installed be deleted?

---

### Post by Comzee on 2007-06-19
KDE sucks, don't bother with it.

---

### Post by eentonig on 2007-06-19
KDE doesn't suck. it's just something different. And Allthough I don't like the KDE environment, I do use some KDE apps.

To answer the OP's question. Yes, your system will need to load extra libraries and services to run those kde apps. So more mem will be used and more cpu will be needed. In real life, it doesn't bother me on my 2G RAM, 2.0Ghz cpu.

---

### Post by RomeReactor on 2007-06-19
Hi. I don't think you'll get a noticeable increase in ram and cpu usage (if any); i've installed KDE apps frequently on my Gnome desktop, and all goes perfectly fine. Also, when you uninstall a KDE application, the necessary (KDE related) libraries to run them won't automatically uninstall along with them: you must remove them yourself with this command, I think:
```
sudo apt-get autoremove
```
The downside to installing KDE apps in Gnome?
* Just a little more harddrive space will be used (for the KDE related libraries); and
* The applications will look slightly out of place (or largely out of place, depending on your stance on Desktop integration).

The benefits?
* Access to applications that provide increased functionality like K3B and Ktorrent (which are awesome).

---

### Post by hanzj on 2007-06-19
If I'm not using any KDE program at a given time, will all the KDE libraries be out of memory/RAM? 

In other words, will my computer only be slowed down if a KDE program is currently running?

---

### Post by headcronie on 2007-06-19
> **Comzee said:**
> KDE sucks, don't bother with it.

Wow, that was helpful.  :(

---

### Post by RomeReactor on 2007-06-19
> **hanzj said:**
> If I'm not using any KDE program at a given time, will all the KDE libraries be out of memory/RAM?
Hmmm... I don't know for certain, but I think they shouldn't be running.
> In other words, will my computer only be slowed down if a user program is currently running?
I don't think there's any slowdown--that is, unless you have an old cpu (1 GHz or less) and/or little RAM installed (less than 512 Mb). Otherwise (if your system if reasonably recent), don't worry about it.

---

### Post by hanzj on 2007-06-19
I want to worry about it. 8-)
I have a 1Ghz computer.with 1g ram (I think)

---

### Post by Comzee on 2007-06-19
> **headcronie said:**
> Wow, that was helpful.  :(


LOL, I've just had bad luck with the KDE desktop environment, I.E. Suse uses KDE :( also backtrack 2 uses it, and Kunbutu. And I hate all those OS's.

---

### Post by RomeReactor on 2007-06-19
> **hanzj said:**
> I want to worry about it. 8-)
I have a 1Ghz computer.with 1g ram (I think)

That's a fairly similar setup to the one I have (1.6 GHz Sempron, 1 Gb RAM); no slowdown whatsoever here. Try it yourself; if you see any slowdown, you can always uninstall the applications (but I can almost guarantee you won't) ;)

---

### Post by Comzee on 2007-06-19
> **hanzj said:**
> I want to worry about it. 8-)
I have a 1Ghz computer.with 1g ram (I think)

If you have a 1ghz AMD CPU it won't affect performance but if you have a 1ghz Intel CPU, it will.

---

### Post by hanzj on 2007-06-19
Yes, I have AMD Athlon(tm) 64 Processor 3800+

---

### Post by hanzj on 2007-06-19
My worry in uninstalling is this:

Pretend I install a KDE program. Let's call it kprogram. Let's say i installed it the way I usually do: via "add/remove". Now when I go back to add/remove, and remove kprogram, I don't think it will uninistall all the other files (kde library files) that kprogram needed in order to run. 
That's my concern.

---

### Post by Comzee on 2007-06-19
Dude, don't worry, I have konqueror installed and it hardly takes up any hard drive space and doesn't affect performance in any way.

---

### Post by RomeReactor on 2007-06-19
As I said, use:
```
sudo apt-get autoremove
```
and all those KDE libraries will uninstall (autoremove uninstalls all unneeded libraries; that is, libraries that are not called by any **installed** program). And, as **Comzee** said, those libraries don't take up much space.

---

