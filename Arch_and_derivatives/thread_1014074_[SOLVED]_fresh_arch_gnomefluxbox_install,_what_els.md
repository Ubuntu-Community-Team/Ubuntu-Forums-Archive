---
title: "[SOLVED] fresh arch gnome/fluxbox install, what else do i need?"
date: 2008-12-17
forum: Arch and derivatives
---

### Post by tjwoosta on 2008-12-17
i have installed arch with gnome/fluxbox

i have even themed it all up and everything is looking great

but there are some concerns i have considering that i have never done a base install of any distros before

1. what should i do for a firewall, if anything?

i mean what do i need to do to make my arch install as secure as a fresh ubuntu install (or better)

2. how do i get my sound to work like ubuntu does? 
(or better yet can i make it work like elive does, because elive works perfectly for games where ubuntu doesnt)

right now when i try to open the volume manager it says "no gstreamer volume control plugins and/or devices found"

obviousl, i have no clue what i am doing when it comes to sound

3. is there anything else that i need to do that i might be forgetting?



up untill now i have been following the arch wikki (and its awesome) but now i have no idea where to look because i have no idea what i am looking for

---

### Post by sisco311 on 2008-12-17
> **tjwoosta said:**
> 

2. how do i get my sound to work like ubuntu does? 
(or better yet can i make it work like elive does, because elive works perfectly for games where ubuntu doesnt)

right now when i try to open the volume manager it says "no gstreamer volume control plugins and/or devices found"

obviousl, i have no clue what i am doing when it comes to sound



did you add your user to the *audio* group?
list the groups:
```
id
```


add your user to the group, as root:
```
usermod -aG audio *username*
```
(log out and log back in for the changes to take effect)

---

### Post by tjwoosta on 2008-12-17
wow, ok i feel stupid now

i had like every group except audio

but thank you it worked perfectly



how about the firewall?

---

### Post by smartboyathome on 2008-12-17
I'd say that you don't really need a firewall if you are behind a router. Are you? Also, I think the built in ip-tables kernel based firewall is configured already.

---

### Post by tjwoosta on 2008-12-17
i am behind a my router right now when im home, but i am usually not on my home network

this is a laptop


i also thought that iptables was part of the kernel untill i found these two wiki pages

[http://wiki.archlinux.org/index.php/Firewalls]("http://wiki.archlinux.org/index.php/Firewalls")

[http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO]("http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO")

i searched pacman and found that iptabes is actually not installed yet

so now i see that iptables is not installed or configured by default

do you guys think this "simple stateful firewall" setup will be comparable to the defualt ubuntu iptables config?

does anybody know of any better way to configure iptables for laptop use?

---

### Post by crimesaucer on 2008-12-17
```
pacman -Sy firestarter
```

[http://www.archlinux.org/packages/?q=firestarter](http://www.archlinux.org/packages/?q=firestarter)


Firewall wiki: [http://wiki.archlinux.org/index.php/Firewalls](http://wiki.archlinux.org/index.php/Firewalls)

Alsa Wiki: [http://wiki.archlinux.org/index.php/ALSA](http://wiki.archlinux.org/index.php/ALSA)

---

### Post by will1911a1 on 2008-12-17
To my knowledge, Ubuntu iptables isn't configured at all by default.

As crimesaucer has pointed out, install Firestarter and you'll be well on your way.

---

### Post by crimesaucer on 2008-12-17
> **will1911a1 said:**
> To my knowledge, Ubuntu iptables isn't configured at all by default.

As crimesaucer has pointed out, install Firestarter and you'll be well on your way.

To get the iptables to work you would have to follow this part of the Firewall wiki for iptables: [http://wiki.archlinux.org/index.php/Firewalls#iptables](http://wiki.archlinux.org/index.php/Firewalls#iptables)

Firestarter is much easier to configure and use.

---

### Post by tjwoosta on 2008-12-17
ok i ended up just going for it and im glad i did


i followed this guide word for word  (it is much clearer and more in depth then the other posted firewall wikis)
[http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO]("http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO")

it works beautifully

and i feel so much more secure now...


> To my knowledge, Ubuntu iptables isn't configured at all by default.

As crimesaucer has pointed out, install Firestarter and you'll be well on your way. 

what!   really?

back when i had ubuntu installed i was told that it was already configured and i didnt need to worry about it

those bastards...

anyway i have now learned the art of iptables, thanks to the arch wiki, and i dont think i will have to ever worry about it again


thanks all for your help

---

### Post by Barrucadu on 2008-12-18
> **tjwoosta said:**
> what!   really?

back when i had ubuntu installed i was told that it was already configured and i didnt need to worry about it
Yes, really. That's because there are no listening services by default on Ubuntu, so a firewall is useless anyway - same on Arch. So, the firewall will happily sit around and do nothing unless you install some form of server.

---

### Post by tjwoosta on 2008-12-18
ahh, i see


well it cant hurt to use it anyway

---

### Post by will1911a1 on 2008-12-19
Won't hurt at all unless you misconfigure it like I did. I don't recall what I did exactly, but  at one point I could not get online at all until I removed iptables.

Anyway, good luck. :) I hope you're enjoying Arch!

---

### Post by tjwoosta on 2008-12-19
thanks

i am definatly enjoying my arch!

check out my screenshots here
[http://ubuntuforums.org/showthread.php?p=6400039&posted=1#post6400039]("http://ubuntuforums.org/showthread.php?p=6400039&posted=1#post6400039")

---

### Post by will1911a1 on 2008-12-19
Looks good.  I'm a big fan of fluxbox actually. :)

---

### Post by Xiong Chiamiov on 2008-12-22
> **tjwoosta said:**
> thanks

i am definatly enjoying my arch!

check out my screenshots here
[http://ubuntuforums.org/showthread.php?p=6400039&posted=1#post6400039]("http://ubuntuforums.org/showthread.php?p=6400039&posted=1#post6400039")
Your screens look really nice.  Sometime, though, when you're feeling adventurous, try out [awesome]("http://awesome.naquadah.org/"), or another tiling window manager.  They're not for everyone, but you might find that it works well for you.

---

### Post by tjwoosta on 2008-12-22
> Your screens look really nice. Sometime, though, when you're feeling adventurous, try out awesome, or another tiling window manager. They're not for everyone, but you might find that it works well for you. 


its funny that you mention that because i was thinking about stepping it up and trying out awesome

---

### Post by Xiong Chiamiov on 2008-12-22
One thing that will save you a lot of trouble: read the man page for awesomerc.  It lists the default bindings for things, which is helpful, as the official documentation has a lot of holes and is in the process of moving from awesome2 to awesome3.

Also, you might find it easier to hit the mod4+# keycombo for switching desktops if you remap caps lock to another mod4 (windows key).  You can do that by putting this in your ~/.xinitrc:
```

# remap caps lock to windows key
xmodmap -e 'add Mod4 = Caps_Lock'

```

---

### Post by tjwoosta on 2008-12-22
thanks, ill keep that in mind

---

### Post by tjwoosta on 2008-12-23
well...    i did it

i installed awesome

and i have to say, it's awesome!!

at first it was a bit confusing because i didn't understand the keys, and the layout options but after reading the manual, and a bit of the wiki, it all came fairly easily

only about 10 mins playing around and i feel right at home with it

i just can't believe i didn't try it sooner

tiling windows definatly makes so much more sense then floating windows

---

