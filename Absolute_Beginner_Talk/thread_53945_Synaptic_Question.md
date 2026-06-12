---
title: "Synaptic Question"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-08-02
Is there a way to use synaptic or apt-get to install a previous Nvidia driver package? For instance 66.69?? I want to see if using a different driver will increase performance.

regards...

---

### Post by sapo on 2005-08-02
I dont think so... you can use the nvida installer i think.. but i m not sure about synaptic..

---

### Post by GavinX on 2005-08-02
[QUOTE=grofaz]Is there a way to use synaptic or apt-get to install a previous Nvidia driver package? For instance 66.69?? I want to see if using a different driver will increase performance.

regards...[/QUOTE]
It can be done. You will have to add a repository which has the specific package which you are looking for, then install it using the exact name of the file. However, in my experience with Nvidia drivers the newer ones tend to be better in terms of performance. I would not recommmend going back to an older driver as sometime in the past one of the drivers was broken and an update had to be issued (be careful, it may just happen to be the one you choose to install).

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=grofaz]Is there a way to use synaptic or apt-get to install a previous Nvidia driver package? For instance 66.69?? I want to see if using a different driver will increase performance.

regards...[/QUOTE]

Why are you wanting to use an older one? Performance for all cards (except for TNTs- those drivers get worse) improves with each release. Plus I think the Hoary driver is an older one.

---

### Post by grofaz on 2005-08-02
I have a GeForce FX 5600XT and I'm only getting 912 FPS with glxgears. I don't think that's very good! I would try the newest nvidia driver but I don't know how to correctly install it without buggering up my install and it's not available thru synaptic or apt-get yet.

According to nvidia you should shut down the x server, kill all opengl applications, and set the default run level to boot to a VGA console. I'm not Linux savy enough to operate from the console yet. In fact I haven't a clue! That's in the readme text, however the short instructions simply state download the driver set, run it and follow the installer directions. I already installed a fresh ubuntu 3 times now cause I screwed something somewhere so I'm a little leary. Help would be nice.

regards...

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=grofaz]I have a GeForce FX 5600XT and I'm only getting 912 FPS with glxgears. I don't think that's very good! I would try the newest nvidia driver but I don't know how to correctly install it without buggering up my install and it's not available thru synaptic or apt-get yet.

According to nvidia you should shut down the x server, kill all opengl applications, and set the default run level to boot to a VGA console. I'm not Linux savy enough to operate from the console yet. In fact I haven't a clue! That's in the readme text, however the short instructions simply state download the driver set, run it and follow the installer directions. I already installed a fresh ubuntu 3 times now cause I screwed something somewhere so I'm a little leary. Help would be nice.

regards...[/QUOTE]

Glxgears is a very poor benchmark. My gears score sucks, but my games play fine. Try a game.

---

### Post by grofaz on 2005-08-02
Hmm...well I don't really have any problem other than I have to manually open nvidia settings after booting up the system in order to get it to use my color adjustments. That and the glxgears test which is a steady 912 FPS. Looking at the various forums others are getting  multiple thousands FPS with some cards not as good as mine!

So I question my configuration. I played around with wine and cedega but haven't had any luck getting any game I want to play running so I need something linux native I think to try out.

Oh yeah, I also experience jerky DVD playback. I think it might be time for a newer better video card. :)

Cheers!

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=grofaz] I think it might be time for a newer better video card. :)

Cheers![/QUOTE]

I LOVE my 6600 Gt. Beats any ATI of the same price, and beats the best of Nvidia's last generation.

---

### Post by grofaz on 2005-08-02
Well I took the plunge on a 6800 GT. 'Bout as much as I'm willing to spend, probably better than the rest of my PC now. I think that's the last thing I buy for it till it's time to replace it.

---

### Post by N'Jal on 2005-08-02
Um jerky DVD playback is common, i have heard it's a xine problem and you have to totally remove and reinstall but i havn't tryed it nor found anything supporting this theory.

---

### Post by grofaz on 2005-08-02
OK, thanks for that jerky DVD playback answer. I don't think that's the case in my situation though. It's the same on my Win XP setup too. So I think maybe card related. Maybe not.

Regards...

---

