---
title: "SAMBA Question"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by guilly on 2007-08-03
Alright i got Samba up and running but why is it i can only see my file shares from windows and not from ubuntu? I have ubuntu dual booting with Vista and yet i can only see the shares from vista and not ubuntu??

thanks

---

### Post by GMachine_24 on 2007-08-03
you have to give more information. such as, the contents of your smb.conf file .... how are your computers connected....?? wirelessly, via a lan, etc. do you have firestarter or other firewall software enabled and do you have firewire software on your windows box?

give us something to work with.

---

### Post by guilly on 2007-08-03
Server ( linux) = wired
Desktop (linux/Vista) = wired
Desktop (girlfriends running XP) = wireless

both connected wired, thru a linksys router.

when i boot into vista i have no problem accessing my shares on my server. When i boot into ubuntu i can not see my shares on my server only shares that are located on my girlfriends p.c.

I can not give you my smb.conf since i'm at work but let me know if you need it and i can post it later on when i get home.

p.s I do have firestarter enabled but when i was testing i made sure to disable it just for testing purposes until i can get full connectivity then i will re enable and play with rules. And also I do have the proper ports opened on my linksys.

---

### Post by GMachine_24 on 2007-08-03
Let's start with something simple:

When you click on places>network servers

what is the output? Do you see your network listed there? I'm assuming you do bc you can see locations on your girlfriend's computer - but let me know what comes up when you do places>network servers

---

### Post by guilly on 2007-08-06
when i go to network all that i see is windows network then inside of that i have two workgroups of mshome and workgroup

but i do not see my linux server

---

