---
title: "remote desktop leopard to Ubuntu"
date: 2008-07-04
forum: Apple Hardware Users
---

### Post by fire_storm on 2008-07-04
Hi

i got a macbook pro with leopard on it, i want to be able to remotely control my Ubuntu desktop can anyone direct me to a tutorial or a program, i want a GUI based one not terminal/command based

Thanks

---

### Post by issih on 2008-07-04
You want to look into using vnc. Hardy has this built in as an option I think, as does leopard, so there should be a minimum of tweaking necessary. I can't actually try it for you right now as I am away from home, but when I get back I will have a look (as I have both hardy and leopard machines too, and see how easy it is too cobble together, I'm pretty sure it'll be very simple, although it might be worth tweaking  a bit so you get a remote desktop sized correctly for your apple machine.

Have a play with the remote desktop feature in ubuntu and set it up to share the desktop, and then look at screen sharing in leopard, I believe both these technologies are really vnc under the skin.

Hope that helps

---

### Post by Wafflesrevenge on 2008-07-04
Also if you want to go a SSH route try setting up [this ]("http://www-personal.umich.edu/~mressl/webshell/")program on your Ubuntu and if you have a dynamic IP address get a dynamicIP to staticIP service like [this]("http://www.dyndns.com/support/clients/"). (so you can get in anytime/where)

My goal is get my server rebuilt and see how this works, I can let you know how it goes if you want. Anyhow, Main bonus of this is SSH from my iPhone into my home network and do things like email files to people, run IRC and whatever else. I would love to do VNC but I can't do that from work so a web SSH is my best option. (what else am I to do all day?)

---

### Post by issih on 2008-07-05
Had a little play last night, if you enable sharing under:

System->Preferences->Remote Desktop

on the ubuntu machine.

Then on the leopard box from the desktop hit command k to opent he connect to server dialog.

in the address bar enter vnc://

and hit connect.

That will pop up a dialog asking for a host...enter the ip address of your ubuntu box and you will be done.

It appeared to be quite slow to me (vnc is slow, but even slower than usual) but that could be my network.

Personally, if I was going to do this regularly, I would set it up somewhat differently. I'd set a command line initiated vncserver to be started at boot. That way I could set the remote screen's resolution to match that of the connecting laptop.

something like:

```
 vncserver -depth 24 -geometry 1280x800
```

ought to do it.

that way I could tweak the vnc server for optimal performance too. One other thing worth noting is that this cn be somewhat insecure, and under no circumstances should you open port 5900 to the outside world. If you want proper remote (as in from the internet) access, look into using ssh port forwarding.

---

### Post by DonnieP on 2008-07-05
> **issih said:**
> Then on the leopard box from the desktop hit command k to opent he connect to server dialog.

in the address bar enter vnc://

and hit connect.
Alternatively, after having set up your Ubuntu box, if you open the Finder in Leopard you'll see the vnc remote desktop listed in the left hand column.  After you click on that you'll see a button in the upper right hand corner to share the desktop.  I had my desktop and laptop set for remote desktop in Ubuntu and didn't even realize that the Ubuntu setup 'just worked' in Leopard, until I had occasion to try it this afternoon.  After clicking the share button you'll have to put in your remote desktop password.

---

### Post by Thievrey Corporation on 2008-09-23
> **issih said:**
> Had a little play last night, if you enable sharing under:

System->Preferences->Remote Desktop

on the ubuntu machine.

Then on the leopard box from the desktop hit command k to opent he connect to server dialog.

in the address bar enter vnc://

and hit connect.

That will pop up a dialog asking for a host...enter the ip address of your ubuntu box and you will be done.

I made exactly as described above, but the MacBook keeps saying: "Connection failed - Make sure that screen sharing is enable on the computer you're attempting to connect".
Screen sharing is enable on my Ubuntu machine (running with Ubuntu 8.04)... Any idea ?

Thanks

---

