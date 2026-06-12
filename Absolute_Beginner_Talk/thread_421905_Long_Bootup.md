---
title: "Long Bootup"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Yourdogsdead on 2007-04-24
Is it normal for Ubuntu 7.04 to take a while to boot. If it is i would like to know how to increase it so i don't have to stare at a blank screen for 8 minutes. I am kinda new to this Linux thing but plan on becoming very familiar with it.

---

### Post by Happy_Man on 2007-04-24
If you are booting from a LiveCD, then yes it is, since it takes longer for a computer to read information off a disc than to read a hard drive. If you had installed it, then it really shouldn't take so long.

---

### Post by Yourdogsdead on 2007-04-24
Thats the problem i am booting from my HDD not the disk. I have no idea why it takes so long. my comp is a 2.6 GHZ celeron with 1 gig of RAM.

---

### Post by Yourdogsdead on 2007-04-24
Is it possible that grub is taking too long to find Ubuntu?

---

### Post by meney on 2007-04-24
Is it stalling on the actual loading of Ubuntu, or before you even see the GRUB screen?

Edit: Also, are you dual booting?

---

### Post by Yourdogsdead on 2007-04-24
While loading ubuntu, no i have only one OS on this computer.

---

### Post by alexlex on 2007-04-24
check the services you have set up to run when the computer starts. Try to reduce it if at all possible.. celerons (no offence) are one of the worst processors you can have and it can not handle much.

---

### Post by meney on 2007-04-24
If you install the program bootchart in synaptic. Then upload the chart here, it might give us some indication of whats going on. ;)

---

### Post by Yourdogsdead on 2007-04-24
I know celerons are crappy processors, i am installing it now, get back to you with the results. How do i use the program? ( i am new)

---

### Post by meney on 2007-04-24
Once you install it, just do a restart. Bootchart will create a chart for you in the directory /var/log/bootchart. It's a useful tool for debugging problems such as yours :D

---

### Post by Yourdogsdead on 2007-04-24
[http://i43.photobucket.com/albums/e356/Yourdogsdead/feisty-20070424-1.png](http://i43.photobucket.com/albums/e356/Yourdogsdead/feisty-20070424-1.png)



Here it is. Please Advise.

---

### Post by Happy_Man on 2007-04-24
I can't see the text, could you post a bigger picture please?

---

### Post by freakavoid on 2007-04-24
There is a filed bug in feisty. For some people the boot process hangs at "Configuring network interfaces". You might want to check that out by removing the options "quite splash" in grub. If that's the case [this]("https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675") might help.

---

### Post by Yourdogsdead on 2007-04-24
i can't make it any bigger, can you open it in gimp or something and zoom? i will give your link a try. thanks

---

### Post by Yourdogsdead on 2007-04-24
That may not be the problem as it doesn't display anything during this process. Just a blank screen, then it proceeds. I can't make it any bigger because i am a noob, sorry.(the pic i mean)

---

### Post by Happy_Man on 2007-04-24
All right, then just take a screenshot of the desktop with that up, and post it as an attachment on here instead of photobucket. We really need to see those words! ;)

---

### Post by Yourdogsdead on 2007-04-24
[IMG]http://i43.photobucket.com/albums/e356/Yourdogsdead/feisty-20070424-1.png[/IMG]

---

### Post by Yourdogsdead on 2007-04-24
I can't really make it any bigger, if i try to change the resolution then it is either too big or too small. I have an Intel 845GL which i heard has an issue with linux. I had to edit something to get it too work(Long boot was there before anyway)

---

### Post by mac.ryan on 2007-04-24
> **Yourdogsdead said:**
> Thats the problem i am booting from my HDD not the disk. I have no idea why it takes so long. my comp is a 2.6 GHZ celeron with 1 gig of RAM.

I am running on a much more powerful system but Feisty64 takes about twice the time Edgy32 was taking... :(

You can however optimize the boot sequence with some tricks, like optimizing the boot partition (from the liveCD, with it being unmounted you have to issue the command:

```
e2fsck -fD <yourbootpartition>
```

and adding the option "profile" to the boot parameters the first time you reboot (you need to install "readahead" for that before)

---

