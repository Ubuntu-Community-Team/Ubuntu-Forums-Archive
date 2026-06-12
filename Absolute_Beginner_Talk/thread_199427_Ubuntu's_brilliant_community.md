---
title: "Ubuntu's brilliant community"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by johnwiseman.ca on 2006-06-18
As you can see this is my first time posting on these forums. I just wanted to send out a quick **thank you** to everyone that contributes here. I recently switched my home pc from windows to linux (ubuntu 6.06) and I absolutely love it. These forums, the wiki, and users how-to's helped me get everything up and running in no time flat. It took me only a few hours to get all my devices and programs setup and about an hour to get XGL running (which is beautiful).

I will be passing out live cds to all my friends this week. Hopefully they love the OS as much as I do.

I posted more on my switch from windows-linux on my blog. Hopefully it helps others.

[http://www.johnwiseman.ca/blogging/]("http://www.johnwiseman.ca/blogging/")

Thanks Again

---

### Post by evilghost on 2006-06-18
Exactly my experience as well when I started running Hoary Hedgehog.  These forums are an excellent resource and it was very nice going from a 'learning' role to a 'helping' one.  Ubuntu is a great community and an excellent desktop/server solution.  I've transitioned my entire house from Microsoft to Ubuntu and actually influenced my father to do the same; he loves Ubuntu.  He's proclaiming the greatness that is Ubuntu like I was to him the first time I installed it.

Welcome to the forum :D

---

### Post by johnwiseman.ca on 2006-06-18
Thanks. I'm looking forward to posting here.

My dad is actually buying his first pc next week. I'm thinking of starting him off fresh with Ubuntu. Hopefully I can figure out how to setup some type of VPN so I can fix problems that he runs into since we don't live in the same province.

---

### Post by evilghost on 2006-06-18
I had my father installed openssh-server and modify /etc/ssh/sshd_config and change the listen port to something >50000 TCP to avoid the brute-force SSH style probes/attacks.  I'll also VNC into his machine from time to time (TCP 5900) but don't leave TCP 5900 open all the time.

See "System -> Preferences -> Remote Desktop"

---

### Post by nalmeth on 2006-06-18
:)
Cheers to that!
           :)

EDIT: Like your blog of your Ubuntu experience.

Have you got a skydome setup for XGL yet?

---

### Post by johnwiseman.ca on 2006-06-18
What exactly is skydome? Is it a patch that allows you to add a graphic to the background when rotating the desktop..?

---

### Post by nalmeth on 2006-06-19
exactly. I use AIGLX and have the Gsetcompiz thing running in my system tray, so I just use that to add the skydome.

It needs to be certain resolution to work, like 2x1 --> 2048x1024

Panoramic images work best, so you don't get the ugly line in your skydome.

[http://ubuntuforums.org/showthread.php?t=149436](http://ubuntuforums.org/showthread.php?t=149436)

---

### Post by uzi09 on 2006-06-19
[QUOTE=nalmeth]exactly. I use AIGLX and have the Gsetcompiz thing running in my system tray, so I just use that to add the skydome.

It needs to be certain resolution to work, like 2x1 --> 2048x1024

Panoramic images work best, so you don't get the ugly line in your skydome.

[http://ubuntuforums.org/showthread.php?t=149436](http://ubuntuforums.org/showthread.php?t=149436)[/QUOTE]

:eek: :eek: :eek: :eek: :eek: :eek: 
wow! that's beautiful! *sheds tear* ;)

---

### Post by u.b.u.n.t.u on 2006-06-19
nalmeth I like the "Fly A UFO".

:D

---

### Post by nalmeth on 2006-06-19
hehe

If you have a decent, 3D-accelerated vid card, then install FlightGear
```
sudo apt-get install fgfs
```
To launch with UFO the command is:
```
fgfs --aircraft=ufo
```

---

