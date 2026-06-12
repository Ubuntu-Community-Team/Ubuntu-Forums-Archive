---
title: "Booting from external HDD."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Cyann0923 on 2007-07-10
So I grabbed me up a free HP Pavilion notebook without a hard drive in it. I am lazy and broke and don't want to search for one while I live in Germany, so i decided to use an external hard drive instead.

Now when I get back to the states,  i plan on getting me an internal hdd,  and when i do I want to move all of my data over to it.  Anyone have an idea of how to do this?

And also,  after about 30 minutes i begin to experience problems.  namely,  I lose root privelages. 
i can't open up anything and the computer is basically dead.  just recently I can't even boot up.  it tells me the hard drive is write protected.  It also says that apt-get is not installed and to use apt-get install apt to install it.  A paradox of sorts.  Is this just from using the external?  or is there a way to work around this?

I have Kubuntu 7.04 on my desktop and ubuntu 7.04 on my ps3 and have not experienced any problems like this with them. I know my desktop has an ntfs drive in it, but no problems have occured there. 

Should I just give up and wait?  or is this something more?

---

### Post by logos34 on 2007-07-10
> **Cyann0923 said:**
> So I grabbed me up a free HP Pavilion notebook without a hard drive in it. I am lazy and broke and don't want to search for one while I live in Germany, so i decided to use an external hard drive instead.

Now when I get back to the states,  i plan on getting me an internal hdd,  and when i do I want to move all of my data over to it.  Anyone have an idea of how to do this?

And also,  after about 30 minutes i begin to experience problems.  namely,  I lose root privelages...

If you can get the computer to cooperate long enough you could use gparted from within (k)ubuntu to set up mirror partition(s) on the new internal drive (i.e. same size), then use Partimage from a CD (on SystemRescueCd, Gparted live cd, etc) to ghost your root partition (and any others like /home) over to the new drive (they have to be unmounted).

---

