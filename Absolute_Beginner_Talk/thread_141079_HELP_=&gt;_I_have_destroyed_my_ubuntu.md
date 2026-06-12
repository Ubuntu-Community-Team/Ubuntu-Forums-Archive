---
title: "HELP =&gt; I have destroyed my ubuntu"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by hellboy on 2006-03-07
Hi,

Hope anyone can help, I'm quite new to linux, had installed ubuntu 5.10, and already did quit some things with it. I've installed the K8-SMP kernel ( I have an x2 4400) , Quake4 , mPlayer , ....  So I really would hate needing to reinstall it.

My actual problem is this:

My last good boot I noticed that mp3 play performance was pretty poor (it worked, but sounded like a 10$ radio) , so I tried installing nvidia audio drivers,  which then caused my Quake4 to no longer have audio. Now, I had taken backup files of my alsa ..... (the files where you map your snd card modules or something), so I've put them back , and restarted (oh yes that same boot I also unsuccesfully tried to install wine, compile failed ), next reboot, boot looks fine, all status messages say 'OK', but it finishes with a " user name:" terminal screen. So somehow my desktop fails to boot, but I dont know what to do now, don't even know where to start.

Other usefull info is that before that reboot running alsamixer gave me a "no such directory" exception and running sudo gedit worked, but gave an alsa like warning

Please help, I'm having a housewarming this friday, and wanted to show everyone what a great platform Ubuntu K8 SMP was, running it as an mp3 thing ..... I hope I won't be showing them the qualities of XP ...

---

### Post by christhemonkey on 2006-03-07
Try logging into the terminal and typing
```
sudo startx
```
It will probably spew out a few random errors (or start the nice GUI an sort everything out..!)

---

### Post by Brunellus on 2006-03-07
[QUOTE=hellboy]Hi,

Hope anyone can help, I'm quite new to linux, had installed ubuntu 5.10, and already did quit some things with it. I've installed the K8-SMP kernel ( I have an x2 4400) , Quake4 , mPlayer , ....  So I really would hate needing to reinstall it.

My actual problem is this:

My last good boot I noticed that mp3 play performance was pretty poor (it worked, but sounded like a 10$ radio) , so I tried installing nvidia audio drivers,  which then caused my Quake4 to no longer have audio. Now, I had taken backup files of my alsa ..... (the files where you map your snd card modules or something), so I've put them back , and restarted (oh yes that same boot I also unsuccesfully tried to install wine, compile failed ), next reboot, boot looks fine, all status messages say 'OK', but it finishes with a " user name:" terminal screen. So somehow my desktop fails to boot, but I dont know what to do now, don't even know where to start.

Other usefull info is that before that reboot running alsamixer gave me a "no such directory" exception and running sudo gedit worked, but gave an alsa like warning

Please help, I'm having a housewarming this friday, and wanted to show everyone what a great platform Ubuntu K8 SMP was, running it as an mp3 thing ..... I hope I won't be showing them the qualities of XP ...[/QUOTE]
oh relax.  it booted, you just don't have X (that'll be the Xwindows system, which deals with your graphics).

log into the textmode terminal and try 

```
sudo dpkg-reconfigure xserver-xorg
```

follow the prompts, then reboot and see what happens.

---

### Post by hellboy on 2006-03-07
Ok I have done what you guys said. running the sudo startx does get me into gnome (how it looks stock), so thx. But, rebooting still gives me the same result

update : this is the last message in my Xorg log : AUDIT: Tue Mar  7 21:14:46 2006: 9641 X: client 5 rejected from local host

---

### Post by hellboy on 2006-03-07
Again a step further .. 

I noticed that I can also run startx as a normal user, resulting in a 100% normal desktop. Why doesnt it work while booting then ?

---

### Post by hellboy on 2006-03-07
my .Xauthority file is 0bytes, does that give anyone more info ?

---

### Post by hellboy on 2006-03-07
ok found solution , apparently reinstalling and reconfiguring gdm MAY have worked

but I needed to do a chmod on .Xauthority , dont know why, bat that works, now back to sound ...

---

