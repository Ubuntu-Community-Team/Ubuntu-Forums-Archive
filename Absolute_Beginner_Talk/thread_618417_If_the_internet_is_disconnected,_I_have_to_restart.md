---
title: "If the internet is disconnected, I have to restart the computer."
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by likegiraffes on 2007-11-20
I'm talking about a wired connection, not wireless, although it does the same thing with wireless.

If, say, my cord pulls out of my computer, or my room mate wants to borrow the ethernet cable for a few minutes, I can't connect to the internet again until I restart the computer.  Even if I plug the cable right back in.

This is the same if I want to switch from wired to wireless or vice versa.  Any time I change the way I'm connecting to the network, I have to restart the computer.  It says that it is connected, but it won't load any pages.

Why?

---

### Post by likegiraffes on 2007-11-20
I'm still using Feisty, by the way.  =)

---

### Post by Inxsible on 2007-11-20
you could try releasing and/or renewing the ip to see if that works rather than rebooting.

---

### Post by likegiraffes on 2007-11-20
...

I didn't think of that.  Duh.  =D  I'll try that next time, it would be a lot less annoying.

But I still would like to know why this is happening, and if there's any way to get it to just /work/.

---

### Post by Inxsible on 2007-11-20
> **likegiraffes said:**
> ...

I didn't think of that.  Duh.  =D  I'll try that next time, it would be a lot less annoying.

But I still would like to know why this is happening, and if there's any way to get it to just /work/.try that out.

But I wouldn't know why it wouldn't work just as is. You are using nm-applet right?

You might wanna try out wicd (pronounced WICKED). They say its good. I have never tried it out since nm-applet does the job for me.

---

### Post by likegiraffes on 2007-11-20
So, it seems that now that I'm home?  The internet works normally, and I don't have this problem.

It probably has something to do with my University's network - it doesn't like Ubuntu connecting to the internet, I've had to mess with stuff before.

Thanks for the help; I'll go whine to the UBLinux developers about what I need to do to get it to work.  =P

---

### Post by Inxsible on 2007-11-20
> **likegiraffes said:**
> So, it seems that now that I'm home?  The internet works normally, and I don't have this problem.

It probably has something to do with my University's network - it doesn't like Ubuntu connecting to the internet, I've had to mess with stuff before.

Thanks for the help; I'll go whine to the UBLinux developers about what I need to do to get it to work.  =P
Well, your university may have a login mechanism to verify if you are authorized to access the University LAN. Maybe that's what is failing the second time on because the univ lan software is not actively looking to authorize someone, if they already have an assigned IP. 

Who knows. The Linux devs in your university might be the best people to ask for help.

---

### Post by Beggar on 2007-11-20
For a while, using feisty I had issues whenever I lost internet, usually because of suspends though. Moral of the story, I could always fix the problem by either right clicking on the nm-applet, disabling networking, then after the icon changes re-enabling it, or otherwise terminating NetworkManager process and restarting it. (make sure you run do "gksudo NetworkManager")

---

### Post by PhoenixBlessings on 2007-12-18
> **Inxsible said:**
> you could try releasing and/or renewing the ip to see if that works rather than rebooting.

How do you release and renew the ip? I'm a total beginner and when my router screws up, I have to restart my computer to get the internet working again even after I reboot my router. It still says my internet is not connected/unable to reach. I was wondering what the code was to restart my internet connection...

---

### Post by bcom on 2007-12-18
Assuming your network card is eth0, try this(that's a zero):

sudo ifconfig eth0 down  

then

sudo ifconfig eth0 up

---

### Post by odiseo77 on 2007-12-18
You could also try:

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

or:

```
sudo /etc/init.d/networking restart
```

These commands never fail for me when, for some reason, my internet connection gets broken and I have to restart my router.

---

### Post by Niniel on 2007-12-18
How about you guys invest in a switch and another network cable? Those things aren't that expensive... Then you wouldn't have to unplug your box for your buddy to use the network.

---

