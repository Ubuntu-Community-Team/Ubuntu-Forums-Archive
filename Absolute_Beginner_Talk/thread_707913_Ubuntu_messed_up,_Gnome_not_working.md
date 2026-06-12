---
title: "Ubuntu messed up, Gnome not working"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by ispy on 2008-02-25
Ok, so i was trying to get my network to function properly (works fine in my dad's winblow$ laptop, but not in Ubuntu), and i think my network card died on me or something... so i connected to the internet via an ethernet cable, and booted into my 4gb Xubuntu partition (for emergencies only), which also can't connect. it can see it, just can't connect wirelessly. so here i am, and i'm wondering why Gnome failed on me (both Gnome panels and AWN), and the network won't connect. i havn't done anything different... just tried to connect to the internet...

but i did notice something i never did... when i start up, so does conky, which showed Tor as one of the top CPU % takers... what does that mean and why does it happen now...?

thanks for the help... I really love the spirit of community i find here...

---

### Post by spiderbatdad on 2008-02-25
TOR uses anon-proxy, I believe. You may need to add the proxy settings to your /etc/bash.bashrc file...you certainly would  need to to use apt-get. I would try to purge TOR and anon-proxy...it can be difficult to get rid of anon-proxy if something in sbin is trying to use it.
```
sudo apt-get remove --purge anon-proxy
```

```
sudo dpkg -r TOR
```

---

### Post by macogw on 2008-02-25
can you try running ```
sudo dhclient
``` while using the wired network?

---

### Post by ispy on 2008-02-25
certainly, after dinner... meanwhile, if anyone else has any ideas, keep em coming...

---

### Post by ispy on 2008-02-25
Ok, so after reboot, i can't even get into my Ubuntu partition... i can access the files and everything from my Xubuntu backup partition, but that's it... no gnome... i might just install gnome on my Xubuntu partition and them move my files from my Ubuntu partition to my Xubuntu one, make that my primary...

how can i install just gnome, not the apps that come with Ubuntu by default? i just want the desktop manager... if that's the right term...

but before that, i'd rather learn how to fix my issue rather than run away from it...

---

### Post by ispy on 2008-02-26
bump... i really need some help here, i can't even boot into my Ubuntu partition, now not just gnome is messed up...

---

### Post by JoshuaRL on 2008-02-26
Do you have any more information?  Can you boot into Recovery Mode?  Does startx send any errors?

---

### Post by ispy on 2008-02-26
ok, so i got into my ubuntu, and AWN started, so i have Firefox, but no gnome panel... and startx gives me

```
troy@troy-laptop:~$ startx
xauth:  creating new authority file /home/troy/.serverauth.6515

X: user not authorized to run the X server, aborting.
Couldnt get a file descriptor referring to the console

```

so i don't know what that means, but i'm gonna assume it's bad because it gives me an error...

HELP!!!!1!!!

---

### Post by MasterAlone on 2008-02-26
I'm new at this also but I have a question.  Did you use SUDO before the execution part of the code?

Just a thought.

---

### Post by oedha on 2008-02-26
mmm......
can you turn of the gdm with sudo /etc/init.d/gdm stop
then reset the graphic configuration :==> sudo dpkg-reconfigure -phigh xserver-xorg
then sudo /etc/init.d/gdm start

---

### Post by JoshuaRL on 2008-02-26
> **MasterAlone said:**
> I'm new at this also but I have a question.  Did you use SUDO before the execution part of the code?

Just a thought.

No, its not needed.  The "startx" command just starts the Xorg app.  It has it's own ability to verify root priviledges if and when needed.

:)

---

### Post by ispy on 2008-02-26
> **oedha said:**
> mmm......
can you turn of the gdm with sudo /etc/init.d/gdm stop
then reset the graphic configuration :==> sudo dpkg-reconfigure -phigh xserver-xorg
then sudo /etc/init.d/gdm start

ok, i'll try that...

EDIT: after trying twice in normal Ubuntu, and getting a black screen after the first command, i don't think it's working... so i booted into recovery mode, tried the first command, and it worked! second command, however, did not... and i can't for the life of me remember exactly what it said... something to the effect of "dpkg-reconfigure is not installed", so i tried just skipping it and got back into my regular Ubuntu... without my gnome panels... but AWN works, which is how i'm writing this...

---

### Post by ispy on 2008-02-26
bump

---

### Post by ispy on 2008-02-26
bump again

---

### Post by JoshuaRL on 2008-02-26
First of all, try not to bump so often.  At most, once a day three times total.

Second, if you're going to try it in Recovery Mode, drop the sudo:
```

dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by ispy on 2008-02-26
thanks JoshuaRL, i appreciate it.

wow, i can't believe i didn't try that...

thanks...

and sorry about the bumping, i was worried i'd get lost in the sea of other cries for help...

---

### Post by ispy on 2008-02-26
ok, so after a reboot and trying the commands, dropping the sudo (recovery mode again), it still tells me that "dpkg-reconfigure" is not installed...

this only happened after my network went down, but now it's back up and i don't get it...

i'm gonna try one last-ditch resort, i havn't updated in a few days... so i'll tell you if it works...

---

### Post by ispy on 2008-02-26
negatory, an update did not fix it. i'll be back in an hour, so if anyone has any ideas, lemme have em

---

### Post by JoshuaRL on 2008-02-26
Okay, it sounds like dpkg is messed up.

Try this:
```

sudo apt-get install -f

```
And if you're trying from Recovery, drop the sudo.

You can also try going into Synaptic and reinstalling anything in the Broken filter.

And lastly, you could always try:
```

sudo apt-get install --reinstall dpkg

```
But I haven't ever tried that myself, so not sure how it would work.

---

### Post by 32County on 2008-05-18
> **spiderbatdad said:**
> TOR uses anon-proxy, I believe. You may need to add the proxy settings to your /etc/bash.bashrc file...you certainly would  need to to use apt-get. I would try to purge TOR and anon-proxy...it can be difficult to get rid of anon-proxy if something in sbin is trying to use it.
```
sudo apt-get remove --purge anon-proxy
```

```
sudo dpkg -r TOR
```



     SpiderbatDad, the commands above just prevented me from pulling my hair out!  ](*,) anon=proxy and TOR are no more!! \\:D/ All is well with updating and/or installing thanks to you!! :biggrin:

---

