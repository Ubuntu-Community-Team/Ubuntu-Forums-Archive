---
title: "My log in lasts less than 10 seconds."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-19
Details of ~/.Xsession-errors file

/etc/gdm/PreSession/Default:  Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default:  running:  /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u                                /var/run/utmp -x "/var/lib/gdm/ :0.Xservers"  -h "" -l ":0" "dace"  <continuation of above line
/etc/gdm/Xsession:  Beginning session setup...
mkdtemp:  private socket dir:  No space left on device

I think ubuntu has a strange sense of humor.

How do I deal with this?

---

### Post by Rui Pais on 2007-06-19
> **ICUR2Ys said:**
>   No space left on device

what sense of humor? seems that you run out of space :(

check with:
```
df -h
```

---

### Post by ICUR2Ys on 2007-06-19
I just installed a dual boot on my laptop yesterday.  I have plenty of room on the hd.  But I can't log in.  I am on another computer for this.  

Nice talking to you again. :)

---

### Post by Rui Pais on 2007-06-19
Hi, 
I recognized your avatar (ffffff, say the cat on my avatar) but need to do a search to associate to a specific thread (i'm posting to much...) 

You are the user who's post about use sudo instead of gksudo... 
You can verify your .ICEauthority file (ls -l) Should belong to you, not root. 

Have you run already df -h? Sometimes there are bugs with logs not being deleted and all space goes for them...

Check those 2 first.

and nice to talk to you too, sorry you have problems.

---

### Post by ICUR2Ys on 2007-06-19
Yes it says that my root size is 2.5 G and is 100%.  I have to load the live cd and check the partitions.  I am certain that I made the root 10G yesterday.  Maybe I screwed up again.  I do that a lot lately.   Thanks .

---

### Post by Znupi on 2007-06-19
Wow. 2.5Gb is the exact size a fresh install of Ubuntu takes up. So if you made the partition of 2.5Gb, it's clear that you have runned out of space, lol. Maybe you wanted that partition to be the swap? :popcorn:

---

### Post by Yes on 2007-06-19
It used to do that for me.  When that happened, I would go into the failsafe terminal, and enter ```
sudo apt-get clean
```and I could log in again.  Although I would still look into it, becasue I'm sure there's a better way to fix it (So you don't have to do that nearly everytime you log in).  If you do find a more permanant fix, please post it here, as I would loke to hear about it!

---

### Post by Rui Pais on 2007-06-19
yep 2,5 G is too small for practical uses. It will filled up in no time...

You can make separated partitions at least for /home and /var if you want to keep things with that size.

---

### Post by Rui Pais on 2007-06-19
> **Yes said:**
> It used to do that for me.  When that happened, I would go into the failsafe terminal, and enter ```
sudo apt-get clean
```and I could log in again.  Although I would still look into it, becasue I'm sure there's a better way to fix it (So you don't have to do that nearly everytime you log in).  If you do find a more permanant fix, please post it here, as I would loke to hear about it!

well, you can use synaptic for that:
On main menu: Settings -> Files. Choose 'Delete downloaded packages after installation'

or add 
```
apt-get clean
``` to your /etc/rc.local (before exit 0 line)

---

### Post by ICUR2Ys on 2007-06-19
I was certain that I made a 10G root yesterday.  But my mind plays tricks on me every now and then.  My permanent fix is to make the partition size 10G  like I thought I did yesterday.  I have already deleted all of the partitions and resized them.  The system is being installed now.  When I started the thread I was certain that I had 10G and the system was only 2.5G.  That is why I made the comment about ubuntu's sense of humor.

---

### Post by Znupi on 2007-06-19
Well, good luck this time around :)

---

### Post by holdinout on 2007-07-19
Same problem... Different error log:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "administrator"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Desktop:/tmp/.ICE-unix/6126
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension
Starting gdesklets-daemon...

Connecting to daemon [###          ]
(update-notifier:6209): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.


I tried going into "Sessions" to disable gDesklets, but it just won't come up. How else can I remove this from start-up?

---

