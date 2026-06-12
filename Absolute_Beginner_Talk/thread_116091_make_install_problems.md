---
title: "make install problems"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-01-11
hi all,
   I am having a little trouble with my sound card (soundblaster live, platinum).  From what I have read thus far, I need to use emuk10 so that sound on my system functions properly. It seems that I do have emuk10 on my system, but things are not functioning as they should - That is to say that out of the four speakers, only two speakers are functioning. 

What i have decided to do is download and install the alsa driver (which seems to be the best option that i have come accross). 
inorder for the driver to be installed it seems that I need to make and make install. Unfortunately, I am getting a command not found. Is there anything that I need to install, inorder to use the make command?

thanks

---

### Post by 23meg on 2006-01-11
I haven't done this myself so I may be missing something but did you try inserting "emu10k" to your /etc/modules file so that it will be loaded on startup?

To see if it's already loaded, type ```
lsmod |grep emu10k
```If there's no output, it's not loaded.

You already have ALSA installed; I don't think recompiling it will help anything (do a forum search to find out). But if you must compile something and you're missing make and other tools, install the build-essential package.

---

### Post by mwanafunzi on 2006-01-11
thanks for that. 
I typed in lsmod |grep emu10k
and i got some output. I unfortunately still have the same problem. 
I would like to copy and paste the output. But I am not sure how to do this.

---

### Post by 23meg on 2006-01-12
Just select the output in the terminal, and hit your middle mouse button here in the text entry box (or both mouse buttons if you don't have a middle one). 

Also, do a forum search; your card is a very common one and I'm just about sure this problem has been had and solved many times before.

---

### Post by paulmilliken on 2006-01-12
[QUOTE=mwanafunzi]hi all,
   I am having a little trouble with my sound card (soundblaster live, platinum).  From what I have read thus far, I need to use emuk10 so that sound on my system functions properly. It seems that I do have emuk10 on my system, but things are not functioning as they should - That is to say that out of the four speakers, only two speakers are functioning. 

What i have decided to do is download and install the alsa driver (which seems to be the best option that i have come accross). 
inorder for the driver to be installed it seems that I need to make and make install. Unfortunately, I am getting a command not found. Is there anything that I need to install, inorder to use the make command?

thanks[/QUOTE]

Have you run "alsamixer" to check if some channels are muted?

---

