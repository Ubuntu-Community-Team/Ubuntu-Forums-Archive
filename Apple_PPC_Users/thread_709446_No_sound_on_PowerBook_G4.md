---
title: "No sound on PowerBook G4"
date: 2008-02-27
forum: Apple PPC Users
---

### Post by Gunglefoob on 2008-02-27
Hello,

I've read a lot of threads on this subject but they either don't help or I don't understand them, being new to this world.
I've successfully installed Feisty on my PowerBook G4 Alu and it works fine except that I have no sound at all and the wireless connection does not work. The sound issue is more important.
In a terminal there is no powermac or dev/snd if that means anything.
I tried installing alsa base and gstreamer. The manager says they are installed but I can't be sure. Sorry if this not too clear, but I'm in a ungle here - adventure and all that...
I'd appeciate hearing something on my Ubuntu OS, if anyone can help.

Thanks,

Pat

---

### Post by stream303 on 2008-02-28
I remember seeing many problems with ti-books, but maybe this tip will help with your au-book:  (among other things)

[https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e](https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e)

Let us know if you get sound working!

---

### Post by superprash2003 on 2008-02-28
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Gunglefoob on 2008-03-05
Thanks all for the replies. I've been out of action for a few days but will try these solutions and report back...

---

### Post by Gunglefoob on 2008-03-06
Well, I am new to terminal but I did find out that snd-powermac works by  using
 sudo modprobe snd-powermac
However when I try to install it I end up with this window and what then? If I just reboot it does not work.

---

### Post by stream303 on 2008-03-06
Just hit return to write it out.

You did preface it with sudo

```
sudo nano -w /etc/modules
```

Usually a ctrl-o should write it then...

Another alternative is to use a gui editor, but you have to start it from the commandline for temporary root priveleges:

```
gksudo gedit /etc/modules
```

Then save

---

### Post by Gunglefoob on 2008-03-06
ça y est! I'm finally listening to Bruce Cockburn on Ubuntu!
It's the first time I hear the drums on boot that some spoke of, thanks to your help.
Now, if I could get the Airport Extreme connection going...

Thanks again,

Pat

---

