---
title: "Accessing game server within Virtual machine"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by yarri on 2007-07-01
Hi!

    I am looking for help with the following problem: I am running Windows XP within Virtual box - everything runs just great. Recently I have came to an idea that I could run an RPG game with [Screenmonke]("http://www.nbos.com/products/screenmonkey/screenmonkey.htm") software - which should act as a game server. Problem is that when I start game the address is [http://10.2.0.15:10015](http://10.2.0.15:10015)
which is quite different from my real ip. Of course this means that players are unable to connect to my game. 
Now I do not know much about networking but how can I route the connection  to the server running in virtual machine?
Thanks in advance.
                                      Yarri

---

### Post by cogadh on 2007-07-01
I know this isn't an answer to your question, but trying to run games through a virtual machine is generally not recommended. The virtual machine does not have the necessary access to your hardware (specifically the video card) to properly run the game.

If you are just running the game server, then I don't see why it couldn't work, unfortunately I don't know enough about VM to help with that.

---

### Post by bloodniece on 2007-07-01
I have never done this, but you may want to look at changing the virtual machine's IP to a static IP in your subnet. E.G. IP 192.168.1.200  netmask 255.255.255.0

Use NAT from your firewall to forward any service/port to that IP.

---

### Post by Eggnog on 2007-07-01
Are virtual machines ever going to be able to access your vid card directly, for 3D capability, or is that something that is just not doable?

---

### Post by cogadh on 2007-07-01
No, 3D gaming on a VM is not possible.

---

### Post by bodhi.zazen on 2007-07-01
Actually this is something that is in development ...

[http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)

And here [http://www.novadevelopment.com/parallels/upgrade_3/default.aspx](http://www.novadevelopment.com/parallels/upgrade_3/default.aspx)

> 50+ NEW AND IMPROVED FEATURES INCLUDING:

    * OpenGL 1.5 / DirectX Support - Run games and 3D applications at native speed in Windows. Click here for a partial list of games. 

This is in development with qemu and I assume VMWaer and Virtualbox as well.

---

