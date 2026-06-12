---
title: "Kubuntu on 2.4 GHz MacBook Pro"
date: 2007-07-02
forum: Apple Intel Users
---

### Post by violinmandan on 2007-07-02
I just have a quick couple questions about installing Kubuntu on my new shiny MacBook Pro. :D

I read the guide at help.ubuntu.com/community/MacBook and it says to set lpj=8000000 on the 2 GHz model to avoid kernel panic. Is this value different for the 2.4 GHz model?

Also, how much swap space is advisable (I have 2 GB of RAM)?

In case it's useful, here's my system specs (copied from system profiler hardware tab:
  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro3,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.4 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	4 MB
  Memory:	2 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	MBP31.0070.B02
  SMC Version:	1.16f8
  
Thanks!

---

### Post by cyberdork33 on 2007-07-02
I am not sure that the kernel panic problem is even an issue anymore. I have a C2D 2.16GHz and have never used the kernel parameter without ever getting a kernel panic. If it works without then don't worry about it. You can always add it later is need be.

---

### Post by violinmandan on 2007-07-02
Thanks for the advice, but I'm now having another problem.
When it boots the live CD, it gives me this:

```

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

Any advice?

---

### Post by cyberdork33 on 2007-07-02
did you verify the cd? Sounds like a corrupted file to me.

---

### Post by violinmandan on 2007-07-02
I verified the CD on another machine. (When I try to verify it on the MacBook, it just gives me the aforementioned screen.)

Should I try the alternate install CD?

---

### Post by chem on 2007-07-02
Lots of info about how to install and expected problems for your type of MBP in this thread:  [http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by cyberdork33 on 2007-07-02
Ah that's why... Santa Rosa machine.

---

### Post by ronocdh on 2007-07-02
Don't have a SR MBP, but I recommend you use the application **Burn**. Get it [here]("http://www.opensourcemac.org"). Automatically verifies the burn after disc creation. Very reliable.

---

### Post by violinmandan on 2007-07-02
OK, I successfully installed Kubuntu using the amd64 alternate install CD, but I've run into another problem...

It won't boot.

It will load GRUB and say the kernel is alive, but then I just get a black screen.
When I was installing, I accidentally set the resolution of X too low, but I don't think that would cause this... would it?

I used three partitions for Linux (/, /home, and swap), in case it matters.

Please help! I feel that I'm really close now...

---

### Post by alephsmith on 2007-07-03
Follow the instructions in this post: [http://ubuntuforums.org/showpost.php?p=2892053&postcount=10](http://ubuntuforums.org/showpost.php?p=2892053&postcount=10)

The nvidia drivers don't work so you have to change the default display driver to 'vesa'

---

### Post by Baladahn on 2007-07-03
> **violinmandan said:**
> OK, I successfully installed Kubuntu using the amd64 alternate install CD, but I've run into another problem...

It won't boot.

It will load GRUB and say the kernel is alive, but then I just get a black screen.
When I was installing, I accidentally set the resolution of X too low, but I don't think that would cause this... would it?

I used three partitions for Linux (/, /home, and swap), in case it matters.

Please help! I feel that I'm really close now...

Edit the boot command in GRUB by removing "Splash" from the command.  The splash screen makes things freeze up during boot.

---

### Post by violinmandan on 2007-07-03
> **alephsmith said:**
> Follow the instructions in this post: [http://ubuntuforums.org/showpost.php?p=2892053&postcount=10](http://ubuntuforums.org/showpost.php?p=2892053&postcount=10)

The nvidia drivers don't work so you have to change the default display driver to 'vesa'

I got rid of the GRUB splash screen and made X use the vesa drivers, but it still doesn't work.
It tries to run kdm, but it fails.
Could this be a KDE-specific issue?

---

### Post by cyberdork33 on 2007-07-03
login on the terminal and run 'startx' and see if that works.

---

### Post by violinmandan on 2007-07-03
I finally managed to get this working! Something was apparently wrong with my X configuration (still don't know what), but now it's working... mostly.
I'm trying to install the build-essential stuff, but when it asks for the installation CD, it won't recognize it. 
I need this to get wi-fi working. Until then, I'm stuck plugging in an ethernet cable.

---

### Post by cyberdork33 on 2007-07-03
comment out the cd-rom line in your sources.list

---

### Post by violinmandan on 2007-07-03
> **cyberdork33 said:**
> comment out the cd-rom line in your sources.list

It works! Thanks for all the help.

Now I just have to get the video card and sound working, but it seems like those problems are facing all SR MBP users...

---

### Post by chem on 2007-07-03
> **violinmandan said:**
> It works! Thanks for all the help.

Now I just have to get the video card and sound working, but it seems like those problems are facing all SR MBP users...

If you go back to the thread I linked on the first page, there is a partial fix for sound (speakers, yes.  headphones, no.)   Just today, nvidia stated their binary drivers would be fixed in the next release (yay).  Anyway, to consolidate discussion, maybe better to take all the comments to that other thread.

[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by Aerugo on 2007-07-04
> **chem said:**
> If you go back to the thread I linked on the first page, there is a partial fix for sound (speakers, yes.  headphones, no.)   Just today, nvidia stated their binary drivers would be fixed in the next release (yay).  Anyway, to consolidate discussion, maybe better to take all the comments to that other thread.

[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)
Fantastic about the new nvidia driver! The vesa resolution is killing my eyes *_*

---

