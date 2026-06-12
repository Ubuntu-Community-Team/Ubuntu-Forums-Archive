---
title: "Problems removing KDE/Xfce with aptitude."
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by r0b0t1 on 2008-07-01
I had installed KDE following this page: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

And Xfce by modifying the commands, but also this page: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)


Sure, those worked. Great! But I ended up wanting a GNOME/Xfce, while removing KDE. I tried to remove it how the page suggests, which did not work. So then I moved on to the 'Pure {enviroment}' help pages, which I followed. I first performed the command to remove KDE via aptitude, which did not work (as in KDE was still there), so I tried removing it via the apt-get command ([http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)). This worked up until it asked me if I wanted to terminate the KDM daemon, which I said yes too. Thus, no GUI, and not even a way for me to enter CLI commands (which I could find). So I hardbooted, and tried to remove KDE again, but which fails (as does the removal of Xfce, or anything else, via aptitude or apt-get) with the message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Then I came to here to ask this question, as the only answer I could come up with would be re-installing, but I probably don't need to do that :p.

Oh, by the way, KDE has hi-jacked my kernel and it now displays the kubuntu logo while booting, and boots into the KDE login screen, which if I log in to without modifying anything, still gets me the GNOME desktop... (Its only my most recent kernel, as I have two of Hardy. This came about when I was making a triple-boot between Mac/Windows/Ubuntu, and the partitions crashed. I then recreated the partitions in the same order I did before, and the data was not erased on the third partition, most likely the others were still intact [it boots also]... So now I have two kernels :KS)

---

### Post by cyberdork33 on 2008-07-01
did you run the command it told you to?

---

### Post by r0b0t1 on 2008-07-01
Yes, I did. I posted this thread because they did not work. When I run them, it prints out the message in [CODE] tags above.


Not trying to say anything bad about you, but that response sounds like you really didn't even read what I posted. If you had read it, you would know I entered what it told me.

---

### Post by cyberdork33 on 2008-07-01
I was talking about what the error message (in the code tags) told you to do... so I could say that you should read the error before posting it ;)
> 
you must manually run 'dpkg --configure -a' to correct the problem

---

### Post by r0b0t1 on 2008-07-01
Yes, I have tried that. It does not know what the program 'dpkq' is. And I can't apt-get it.

---

### Post by cyberdork33 on 2008-07-02
I would guess then that you somehow removed it. It is sounding more like you need to reinstall because you may have done more to your system then you realize.

what does this command tell you:
```
sudo apt-get install -f
```

---

### Post by r0b0t1 on 2008-07-02
I tried to explain that I can no longer apt-get or aptitude or synaptic things. They all display the same error message.

---

### Post by cyberdork33 on 2008-07-02
> **r0b0t1 said:**
> I tried to explain that I can no longer apt-get or aptitude or synaptic things. They all display the same error message.
I understand that. using the -f switch is a method of fixing the database. If it does not work, what have you lost?

If you cannot use apt-get at all, and dpkg is removed for some reason, then the only thing I can suggest is to boot from the LiveCD and chroot into your installed system. From there you can run apt and dpkg (off the cd) and fix your system. I am not going to go into detail about how to do it for various reasons, but there are guides around. Your other choice is to install again.

---

### Post by r0b0t1 on 2008-07-02
Yeah, I said screw it and reinstalled. I actually didn't loose much, it was a pretty new install. I just had to back up some of my .c files.


So, I guess, PEBKAC.

---

