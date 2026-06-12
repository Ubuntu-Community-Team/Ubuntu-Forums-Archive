---
title: "i have 1 gb of ram but ubuntu is only reading 503"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by pympnplaya on 2008-02-20
I have a sony vaio pcg-grz630 and i recently switched from xp to ubuntu.  i have been fooling around with ubuntu for a while now and i love it.  but i was checking out my system monitor and i noticed that it was only reading 503.2 mb of ram, but i have 1 gb of ram installed in the form of two 512 sticks.  any help on this issue would be appreciated.  thank you.

also i was running xubuntu and thought that it might have a limit on the ram it can use so i switched to ubuntu but it still reads only 503 instead of 1 gb. is there a limit on xubuntu for ram? because it runs better than ubuntu. thanks

---

### Post by stchman on 2008-02-20
> **pympnplaya said:**
> I have a sony vaio pcg-grz630 and i recently switched from xp to ubuntu.  i have been fooling around with ubuntu for a while now and i love it.  but i was checking out my system monitor and i noticed that it was only reading 503.2 mb of ram, but i have 1 gb of ram installed in the form of two 512 sticks.  any help on this issue would be appreciated.  thank you.

also i was running xubuntu and thought that it might have a limit on the ram it can use so i switched to ubuntu but it still reads only 503 instead of 1 gb. is there a limit on xubuntu for ram? because it runs better than ubuntu. thanks

Does the video card use system RAM?  On my laptop I have 1GB, but my system only reads about ~870MB as the video card uses 128MB.

---

### Post by agim on 2008-02-20
No, there is no limit to ram for xubuntu. It runs faster because it is a lighter system. It was made to run quickly on lesser resources. As far as your ram usage goes, I had some trouble once with a system-monitor on kde. Type 'free -m' into a terminal (without the quotes of course) and read the output. It will give you your memory total. It probably won't be different, but as I said, I had a similar problem once, and it was the gui frontend, not the actual system.
Either way, good luck!

---

### Post by TuxImpersonator on 2008-02-20
Did your xp recognise the 1 Gb? If your not sure then as the computer boots up there should be an option that flashes up to enter the system BOIS (normally by pressing F2 or Enter) If you go into that you RAM should be listed somewhere like:

RAM Slot A: 512Mb 
RAM Slot B: 512Mb 

If your BIOS only see's one then you might have a dodgy RAM stick. Also unless you know what your doing **NEVER** change your BIOS settings and always choose the Exit without saving option when you leave it. (it could do things like tell your computer it's a toaster... well not quite but you get the idea)

If you post the results of your findings back in this post.

---

### Post by hyper_ch on 2008-02-20
post the output of

```

free -m

```

and use [noparse]```

```[/noparse] tags around it.

---

### Post by jordanmthomas on 2008-02-20
> **agim said:**
> No, there is no limit to ram for xubuntu.
There certainly is for 32-bit.  For 64-bit the limit is basically infinity to us now, but there's still a limit there too.
32-bit Operating Systems can only address 4GB of memory (and in practice you only get like 3.5 GB).

Not that it's really relevant to this person's problem or anything but I'm a semantics guy.  :)

And...to make this post useful at least, does Xubuntu come with lshw?
```
sudo lshw -short -class memory
```
Will tell you what memory it detects on your system.  You should probably have two 512 MB sticks.  Perhaps one of yours has come loose and that's why you're only getting half the memory you expect?

---

### Post by pympnplaya on 2008-02-20
when i type free m i get this as an output:

             total       used       free     shared    buffers     cached
Mem:           503        328        175          0         10        154
-/+ buffers/cache:        163        340
Swap:         1474         33       1440

---

### Post by timbounceback on 2008-02-20
> **pympnplaya said:**
> when i type free m i get this as an output:

             total       used       free     shared    buffers     cached
Mem:           503        328        175          0         10        154
-/+ buffers/cache:        163        340
Swap:         1474         33       1440

Weird... have you checked the bios?

---

### Post by hyper_ch on 2008-02-20
you got 1 GB....

503 MB used
328 MB free
175 MB shred (probably video card)

---

### Post by pympnplaya on 2008-02-21
the 503 is under the total column, the 328 is under the used and the 175 is under the free column so it is only reading the one memory card, i will check the bios when i get home and see what it says, any other tips/suggestions thanks.

---

### Post by pympnplaya on 2008-02-21
well i took both my memory cards out and switched them and tested each seperatly in different slots and they both worked and then i put them in together and it only read 512 so i took them out and put them back in and now it is reading 1024 so i guess the actually memory slots are messed up but it is working now.  i should have known it was not xubuntu or ubuntu causing the trouble because they are awesome.  thanks for all the help!

---

### Post by hyper_ch on 2008-02-21
oh, yeah... I did appoint the values to the wrong slot ;) but mine added up nicely to 1gb ^^

---

