---
title: "X Server"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Finto on 2007-11-01
`Hi Guys,

I am tryin to run an apllication GUI interface remotely using ssh.  THis is what i have done:

1 : INstalled exceed on my local Xp pc
2: ssh to linux box as local user
3 : ran my program command

I get error like   opendispaly : unable to open dispaly 0.0

Can anyone tell me what im doing wrong?  Thanks

Fint

---

### Post by Pumalite on 2007-11-01
For Windows->Linux is better Samba.

---

### Post by Hospadar on 2007-11-01
What ssh client are you using?  you probably need to turn on X tunneling (or maybe it's called forewarding, not sure) in your ssh client.  Also there may be some configuration with exceed that needs to be done (exceed needs to be running when you try to open an app, it probably won't open itself)

I'm not familiar with exceed, I've only used xming and xwin32 in the past.  If you are getting that message though, it's because the server isn't able to make contact with your windows x-server.

My bet would be that tunneling in the ssh client needs to get turned on.

---

