---
title: "Should I upgrade Xubuntu 6.06 to 6.10 on an iMac G3?"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by crios on 2008-06-09
I recently installed Xubuntu 6.06.1 on a G3 iMac, 333MHz, 64MB RAM. It's actually working suprisingly well. A little slow but all in all it will be a fine email and internet machine. I ran the update manager and got a message saying that 6.10 is available to install. Should I do it? The machine is working fine as is. Is there anything that I really need in the 6.10 upgrade?

One other question. When I boot everything says "OK" except for dev/null. That says "failed." Should I be worried. I have a rough idea that dev/null is like a black hole (things go in, nothing comes out). If dev/null failed does that mean that the hard drive is filling up?

---

### Post by stream303 on 2008-06-10
Unless there is something you absolutely need in 6.10, I'd probably be happy for the time being with a working Dapper 6.06x, especially with only 64mb ram.

Being an LTS, Dapper is still delivering security updates, whereas 6.10 is not.  So at this point, if it is still working well for you, I don't see a need to upgrade.

If you run

```
df -H
```

you can get an idea on the status of how much hard disk space you have left.  I don't know about the dev/null problem, although that is a "virtual" bit-bucket as they say. :)

If you are running out of space, you may want to run a general cleanup of all those old packages that got updated and are no longer in use just hanging out in your cache:

```
sudo apt-get autoclean
```

If you feel like tweaking, you may want to try using the "noatime" parameter in /etc/fstab to speed things up a bit. I went into a little detail here, and you may have to scroll to see the entry in the code example:

[http://ubuntuforums.org/showthread.php?t=692318](http://ubuntuforums.org/showthread.php?t=692318)

Might boost your speed a bit, and also save some hard drive life.

Basically, unless you put more ram into that box, I think you're done!

(btw, just in case you feel like putting in more ram to do a major upgrade, I'd copy or write down your existing /etc/X11/xorg.conf and also your /etc/yaboot.conf - it might come in very handy down the road.) :)

---

### Post by crios on 2008-06-10
So how do I keep 6.06.1 up to date? It looks like when I run the update manager the system jumps right to 6.10. Is there a setting somewhere that will just install security updates?

Chris

---

### Post by stream303 on 2008-06-10
Just don't click on the 6.10 update icon.

They system should not upgrade all by itself to 6.10 unless you tell it to do so.

You can go into System > Administration > Synaptic Package Manager and double check your settings.  I'm coming from hardy, so this might be a little different - the key point is to make sure your channel is set to just "Ubuntu 6.06 LTS"

Perhaps this might get rid of the pesky updates for 6.10...

---

### Post by oswaldkelso on 2008-06-10
Stream was dead right, stick with what works. Unless of course there is a pressing need to upgrade.

If there is a pressing need to upgrade and only if. With only 64mb of ram the only real way to up upgrade is more ram or..... loose xfce and goto a "box" blackbox, fluxbox, or openbox followed by a lighter file manager.

I would recommended more ram first (buy secondhand as the ram may cost more than the machine is worth). Setting up a "box" can be very very confusing to a new user. That said there are lots of tutorials around. But once setup will result in a faster and very enjoyable machine.

I have blackbox - rox-filer setup on an imac 333 with 256mb on Debian lenny/testing. Runs very well. Its mostly web and email and watching streaming dvds, though will run anything just slower :)  I don't know if I could have learned to set it up with out another machine connected to the internet though.

Options, choices, choices, options ah the joys of Linux.

---

### Post by crios on 2008-06-10
Could you post some links for "box" setups? I might want to play around with some of those. They sound interesting.
Thanks

---

### Post by stream303 on 2008-06-10
Well, you can always install fluxbox via synaptic or apt-get, and then when you reboot, change your session in the lower-left corner of the gdm boot screen to fluxbox.  You could also install any of the other *box window managers and try them out like this.

On really low memory machines, some opt to build up from a simple server install (although not usually installing the additional server apps when prompted), and manually layering a lightweight X gui on top:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

The thing to remember is that even though your desktop might be faster, you won't see any speed increase if the apps themselves, such as Firefox, Gimp, OpenOffice, etc are eating a lot of ram. So you look for lighter-weight alternatives, even learn to love the commandline - but it's not mandatory.

---

### Post by oswaldkelso on 2008-06-11
> **crios said:**
> Could you post some links for "box" setups? I might want to play around with some of those. They sound interesting.
Thanks

Guide to Window Maker
[http://ubuntuforums.org/showthread.php?t=85363](http://ubuntuforums.org/showthread.php?t=85363)

[http://en.wikipedia.org/wiki/Window_Maker](http://en.wikipedia.org/wiki/Window_Maker)

good links on this page.

I have this on a setup. It's fast, easy and ugly! 20 min's to setup. 2 hours to make look good :) It also has some nice features  non of the boxes have.

fluxbox

[http://fluxbox-wiki.org/index.php/Howtos](http://fluxbox-wiki.org/index.php/Howtos)

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

Always been a bit flaky for me but looks good and many people love it.

openbox

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

No idea. Meant to be fast?

blackbox

Rock solid, once setup as you like it, it just works. Not as many features as some of the other boxes.

[http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)

My stuff
My basic blackbox setup in my bottom signature link, but you'd need to dig through other stuff to get to it. 
More tweeking [http://www.my2bits.org/?cat=6](http://www.my2bits.org/?cat=6)
What it looks like
[http://img516.imageshack.us/my.php?image=redg5zr9.png](http://img516.imageshack.us/my.php?image=redg5zr9.png)



Stream was right about keeping xfce. Nice to have a safe place to return to if and when things screw up.

---

### Post by VitaLiNux on 2008-06-23
Hi, crios!
Hi, guys!
I've run into this thread and I have to tell you I have bought an old imac g3 333mhz too w/96mb of ram.
I wonder how you installed (x)ubuntu on your machine, crios. I've just downloaded 
ubuntu dapper to give it a try. Would you please give me any advise. I'm lost!
Thank you!

---

### Post by VitaLiNux on 2008-06-23
I forgot to tell that this machine has MacOS 8.6 installed in it. I'd appreciate any help. Thanks in advance!

---

