---
title: "Install on totally different physical hard drive."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Stan_1936 on 2007-08-27
Hello all,

I would like to install Ubuntu on a old hard drive of mine.  The drive is currently not being used and I would like to remove my current drive (disconnect it from the cable) and connect the cable to the other drive onto which I want to install Ubuntu.  I'm hoping that this way the data on the one I'm using now(Windows) will stay intact so that if something goes wrong with the install, since the old hard drive is a Maxtor 10.0 GB drive that is years past its warranty period, I will still have access to my files.  

My question is can I do this and still go back to the old 10.0 GB drive if I want by disconnecting the 10.0 GB drive or will the system not recognize the current drive (the Windows HD) the same way and cause some some detection problems?  Will the OS (Windows) on the current drive run smooth if I remove it and then have to reconnect it?

I'm planning to test out Ubuntu on the old HD for a month and then if all goes well, I will replace it with my current HD and partition it to dual boot Windows/Ubuntu.  This is why I am really hoping that disconnecting and then reconnecting would not cause problems because if it does, I will have to spend a day doing nothing but getting everything up and running in the dual boot format.

EDIT:  Also, how can I check if my disk has problems like bad sectors, etc..can I do it with GParted?

---

### Post by jimbob on 2007-08-27
You shouldn't have any problem physically swapping out one hard drive for another.  With the good HD sitting on the bench completely disconnected nothing will happen to it and it will be fine when you change it back again.

Gparted has a check function that you can use on a partition although I don't know how thorough it is.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by fallencyi on 2007-08-27
My first word of advise would be to back up anything important before you start  any of this, just to be on the safe side.

Once you have that, what you are describing as far as swapping harddrives will work fine. If you run into problems , just put the old drive back & it will boot like it was never removed.

 Other than the risks of you making connection errors, or general data loss issues from misshandling,  you will not affect your windows install at all, if you do as you suggest, & completely swap the windows harddrive for the other one.

 Once you are ready to make the switch completely, Setting up a dual boot on the 2nd hard drive is supprisingly easy.  The automated installer takes care of most situations very well. 

Why not just set up your PC with 2 harddrives & install linux on the 2nd one?


 As far as your question about checking a harddisk in linux  the command is "fsck".

---

### Post by tahitiwibble on 2007-08-27
> **Stan_1936 said:**
> Hello all,

I would like to install Ubuntu on a old hard drive of mine.  The drive is currently not being used and I would like to remove my current drive (disconnect it from the cable) and connect the cable to the other drive onto which I want to install Ubuntu.  I'm hoping that this way the data on the one I'm using now(Windows) will stay intact so that if something goes wrong with the install, since the old hard drive is a Maxtor 10.0 GB drive that is years past its warranty period, I will still have access to my files.  

My question is can I do this and still go back to the old 10.0 GB drive if I want by disconnecting the 10.0 GB drive or will the system not recognize the current drive (the Windows HD) the same way and cause some some detection problems?  Will the OS (Windows) on the current drive run smooth if I remove it and then have to reconnect it?

I'm planning to test out Ubuntu on the old HD for a month and then if all goes well, I will replace it with my current HD and partition it to dual boot Windows/Ubuntu.  This is why I am really hoping that disconnecting and then reconnecting would not cause problems because if it does, I will have to spend a day doing nothing but getting everything up and running in the dual boot format.

EDIT:  Also, how can I check if my disk has problems like bad sectors, etc..can I do it with GParted?

I did exactly what you describe and had no problems whatever.

The Windows HD will remain indefinitely in the same state it was in the second you unplugged it, until you re-connect in a month or so. Just don't make any modifications to your bios while using Ubuntu if it can be avoided.

---

### Post by MemoK on 2007-08-27
> **fallencyi said:**
> 

 Once you are ready to make the switch completely, Setting up a dual boot on the 2nd hard drive is supprisingly easy.  The automated installer takes care of most situations very well. 

Why not just set up your PC with 2 harddrives & install linux on the 2nd one?
I did this and it's working without any problem.

---

### Post by Stan_1936 on 2007-08-27
> **fallencyi said:**
> ...Why not just set up your PC with 2 harddrives & install linux on the 2nd one?...

I'd really like to do this but after sifting through these forums, I realized that I understand very little about all things grub.  I still search for grub tutorials everyday through google hoping to turn up something specific to my situation.  I realized that I require step by step instructions, preferably screenshots but these are not essential.  For example, in a Fluxbox install thread, I read "change directory to the newly created one after tar ..... .tar.gz"  I would have no clue how to change directory to the specific directory...all I know is cd /home or cd /home/username which I think is the quivalent of Places>Home although I'm not sure.

I'm very comfortable with the GParted menus.  I don't know what it will be like when I actually use it, but it seems easy enough.  Thus, from what I've got so far, right now this swapping alternative is what I could think of.

---

### Post by MemoK on 2007-08-27
Ubuntu does it automagically. During the installation it asked me where I wanted to install it and I selected my secondary (and bigger) hard drive.

---

### Post by fallencyi on 2007-08-27
98% of the time you won't even need to mess with GRUB. The Ubuntu install CD will handle what goes in your grub menu for you.

For the Other 2% check out google for "Supergrub CD". 

 I am not promising anything, but I can say that for me just installing ubuntu from the Live CD & pointing it at my 2nd harddrive 
just worked.


Later I tried reinstalling windows & had to mess with grub (windows loves to eat your MBR),  but didnt find it that difficult & there was plenty of help on these  forums to get it straightened out.

Good luck with whichever way you decide to go.

---

### Post by laidback on 2007-08-27
This will work fine. I have a caddy system with which I regularly swap the hdd to try other Linux flavours or other configurations. In my view it is a great way to protect your data/system just as you describe. I've even moved an Ubuntu system onto a new pc using the same hdd, it worked!! quite fantastic. My only complaint about the caddy system is that it's a bit noisy, I'm into peace and quiet at the moment.

I suggest that you make sure the BIOS recognises the new hdd, go into the bios just to check it. On my older machine it needs a prompt in the Bios to make this happen reliably, I think newer versions are more automated, but, better be sure than sorry.

---

### Post by Stan_1936 on 2007-08-31
I've installed it on the 2nd hd...will using "swapping " for now until Gutsy.

Thanks for the help.

---

### Post by wolfen69 on 2007-08-31
here's how i do it. [http://ubuntuforums.org/showthread.php?t=539736](http://ubuntuforums.org/showthread.php?t=539736)

---

### Post by Stan_1936 on 2007-08-31
But that is only good for 1 OS.

---

