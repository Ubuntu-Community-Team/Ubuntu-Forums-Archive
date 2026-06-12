---
title: "first attempt error"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by s_i_leigh on 2006-07-07
This is the first time i've ever done anything with linux, and i can't even boot it up.

I'm using the live cd to run ubuntu. It gets me to the first menu of run/install ubuntu, check cd etc. After i select the run/install option i come to a dos-style window with a border of random characters. It says that there was a failure in opening X. It lets me see some stats about my ubuntu then brings me to a dos prompt.

i did a little research and tried setting my X up with the command "sudo dpkg-reconfigure xserver-xorg", went through the menus, then used "sudo dpkg-reconfigure gdm" to start it up again, but it just does the smae thing.

It gives me a warning message that says:
"Fatal server error
no screens found
X10 fatal IO error 104(connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining"

If you've experienced this or a similar problem (or just know what to do) could you help me out?

---

### Post by richbarna on 2006-07-07
Could you tell us what graphics card you have, then we can tell you what driver to select when you do "sudo dpkg-reconfigure xserver-xorg".

---

### Post by s_i_leigh on 2006-07-07
i have a pci-express ATI radion x700 pro, i selected ati in the driver menu, i assumed that was the one

---

### Post by richbarna on 2006-07-07
> **s_i_leigh said:**
> i have a pci-express ATI radion x700 pro, i selected ati in the driver menu, i assumed that was the one

Try giving "vesa" a go, some people do this to get started and then once up and running, install the latest ati drivers. I have heard that "easy ubuntu" does it quite well.

---

### Post by s_i_leigh on 2006-07-08
I tried vesa, but then when i tried using "sudo dpkg-reconfigure gdm" it gave me a warning that said "warning find:" then it said that it could not locate a file. I tried using "startx" and my minitor just went black and eventually atomaticly turned off (which means it wasn't reciving a signal)

---

### Post by s_i_leigh on 2006-07-08
oh, should i try to update my driver through windows? (i haven't because i figured that that would only work with windows)

---

### Post by richbarna on 2006-07-08
> **s_i_leigh said:**
> oh, should i try to update my driver through windows? (i haven't because i figured that that would only work with windows)

You are right, that won't make a difference to the linux distro.
Do the sudo "depkg-reconfigure xserver-xorg" choose vesa, reboot, and see what happens without doing ""sudo dpkg-reconfigure gdm".

Another option is to do a "server" install only. with no desktop. Once it is installed you can then "sudo aptitude install ubuntu-desktop".
I had to do this a couple of times when installing to a laptop with an ATI graphics card, and it worked.

---

### Post by s_i_leigh on 2006-07-09
I tried using vesa, but after i finished it just brought me back to that same old command promp. I tried using startx but some of the warnings from before would pop up and the output would just shutoff again (I'm thinking that's because vesa won't work with my card}

I tried doing all this and just rebooting after the xserver-xorg thing (by using the sudo reboot command and just shuting down) and it just went back to the origanel config files because it's only a live cd.

now, if i do the server install, how would i get x working from there? (I'm assuming that x would be needed in order to run desktop ubuntu}

any idea's or instructions on what to do?

---

### Post by siccness on 2006-07-09
> **s_i_leigh said:**
> 

any idea's or instructions on what to do?

(I hope i'm not murdered for posting this link that a wonderful member of the Ubuntu Community has created)
[http://www.psychocats.net/ubuntu/nox.php](http://www.psychocats.net/ubuntu/nox.php)

---

### Post by s_i_leigh on 2006-07-09
well, i think that that almost got it working, but when i get to typeing "sudo /ect/init.d/gdm start" it says that it's starting the GNOME display manager, but the thing on the right says it failed [fail]. i hit ctrl-alt-f7 and it just brought me to a blinking uderscore that wouldn't let me do anything.

So i geuss the question is how do i getr GNOME working (just reading around i geuss this is like a directX of ubuntu, and is therefore likely the cause of this entrie problem)

---

### Post by jimrz on 2006-07-09
> **siccness said:**
> ([COLOR="Red"]I hope i'm not murdered for posting this link that a wonderful member of the Ubuntu Community has created[/COLOR])
[http://www.psychocats.net/ubuntu/nox.php](http://www.psychocats.net/ubuntu/nox.php)

why in the world would that even be a possibility???

---

