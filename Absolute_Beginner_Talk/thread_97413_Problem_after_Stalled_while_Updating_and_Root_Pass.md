---
title: "Problem after Stalled while Updating and Root Pass?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by JFREY on 2005-11-30
Hey everybody,

First the easy one, i think....  what the heck is the default login and pass for the root user?  After I just finished a clean install of Ubuntu i tried to install new nforce drivers but couldn't log into root.  During install, a time during which I could set the root didn't show up, should it?

Secondly,  after finishing the install the update manager popped up like a good update manager will and i started the update download (update update update) it stalled half way for some unknown reason, and now when I try to load the update manager to get a closer look it say "unable to get exclusive lock".  So I figure it must still be stuck thinking it's downloading... know how I can fix that?

Thanks!

Jon

---

### Post by amohanty on 2005-12-01
> First the easy one, i think.... what the heck is the default login and pass for the root user? After I just finished a clean install of Ubuntu i tried to install new nforce drivers but couldn't log into root. During install, a time during which I could set the root didn't show up, should it?

Search the forums for root password. There are about oh-1000 posts just asking that ques :)

> 
Secondly, after finishing the install the update manager popped up like a good update manager will and i started the update download (update update update) it stalled half way for some unknown reason, and now when I try to load the update manager to get a closer look it say "unable to get exclusive lock". So I figure it must still be stuck thinking it's downloading... know how I can fix that?

In the terminal

sudo killall update-manager

Then try again.

HTH
AM

---

### Post by aysiu on 2005-12-01
[QUOTE=JFREY]
First the easy one, i think....  what the heck is the default login and pass for the root user?  After I just finished a clean install of Ubuntu i tried to install new nforce drivers but couldn't log into root.  During install, a time during which I could set the root didn't show up, should it?[/quote] [I just posted on this today](http://www.ubuntuforums.org/showpost.php?p=534324&postcount=2)

> 
Secondly,  after finishing the install the update manager popped up like a good update manager will and i started the update download (update update update) it stalled half way for some unknown reason, and now when I try to load the update manager to get a closer look it say "unable to get exclusive lock".  So I figure it must still be stuck thinking it's downloading... know how I can fix that? I hate the update manager. It's better to use Synaptic Package Manager or the terminal to do updates. That said, try, in the Run dialogue (Alt-F2), the command ```
sudo killall update-manager
``` **Edit**: I'm too slow in answering... beaten to it.

---

