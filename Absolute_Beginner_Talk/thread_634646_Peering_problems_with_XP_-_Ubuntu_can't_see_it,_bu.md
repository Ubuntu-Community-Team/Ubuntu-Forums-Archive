---
title: "Peering problems with XP - Ubuntu can't see it, but Win box sees Ubuntu"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by linuxaddict on 2007-12-07
It seems like everyone has problems setting up samba and getting their windows boxes to recognize their Linux, and my problem is exactly the opposite. 
My window box can see the Ubuntu laptop, but the laptop can only see "windows network" under the 'Places => Network' tab. It can't go any further into the network to actually identify my window's name.
It worked last night (the first time I got the wireless card running). I rebooted this morning, and after I "re-fixed" my wireless card (it works this time after multiple reboots), I can no longer see my windows machine. I didn't do anything else to this network. I can ping from ubuntu over, and every network troubleshooting thing I can think of says it should work. I rechecked my sharing policy on my folders, and they're all good. I even tried taking off my firewall completely from my windows box just to see if that happened to block it overnight.

I'm not absolutely a beginner, but I'm new to the forums, so I thought I'd try this as my first place to post. If this needs to be moved into a diff forum, please do so, but is there anyone out there there that can help? I'm sure it's some user error thing, but for the life of me I can't figure out why, and I'm not good enough at linux to troubleshoot it myself from the laptop, which would probably be the best place to do it from..

I've also tried it from a wired connection, just in case something had happened with my wireless, and still the same story.

I've had pretty indepth training on both windows and multiple flavors of UNIX/Linux, and understand networking fairly well, so feel free to assume you can use some level of tech talk when you respond...

Thanks!

---

### Post by Ketahazure on 2007-12-07
im kinda new to linux/ubuntu myself but as far as my knowledge goes i believe you have to mount those network shares each time you need to access them. you can script it to auto mount im sure i just dont know how yet. hope someone here helps you man, my first post no one helped me so i gotta at least post my little knowledge. hope it maybe helps. good luck!

---

### Post by mouseboyx on 2007-12-07
in the file manager (nautilus)
type smb://ip address of the computer

the ip is usualy 192.168.2.X or 192.168.1.X

so you would type
smb://192.168.2.X

and it should connect or smb://192.168.1.X

just replace x with numbers 2-255 untill it works.

if it doesn't work i don't know how to help

mine stopped showing devices in the windows network one day so i have to do this now

---

### Post by linuxaddict on 2007-12-08
yeah, typing in the IP worked. I wonder why  it can't browse through...

Here's a little windows fun- open a cmd.exe (windows key +r, type cmd) type ipconfig /all at the command line and you can see your windows IP so you don't have to guess through 254 assignable IPs :}.

Mounting a folder across the network is something I just didn't feel like doing, I might do it for my wife in the future, especially if that will maintain the mount and this problem keeps coming up.

Thanks for all the help!


:guitar:

---

