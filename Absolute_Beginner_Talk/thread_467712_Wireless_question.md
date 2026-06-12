---
title: "Wireless question"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by sw1995 on 2007-06-08
Hello!

A quick question:

I have a linksys wireless card (laptop) that has been recognized by Ubuntu (out of the box) and works well (it is set to connect via automatic DHCP--roaming IS NOT enabled), however I notice that when I restart my laptop often the system will have a hard time reconnecting to the network. Sometimes it works, sometimes it doesn't--sometimes it will connect an hour or two later if I leave it be. In any event, I cannot guarantee that I will have the internet when I turn my computer on and that is difficult to deal with and overall I fell as though I have very little control over the situation.

Is this simply the nature of the beast? It is rather frustrating as I use my computer to work from home, however I have to fix it because I refuse to give up my Gnome/Ubuntu desktop!

Cheers!
-S

---

### Post by scrooge_74 on 2007-06-08
have you tried to set it to roaming and then use the network manager? Some cards have better support than others.

You should look for your specific model in the forums you may get lucky and find the solution

---

### Post by sw1995 on 2007-06-08
Howdy!

I have set it to roaming mode using the network manager and  it will recognize the network but has never connected (I have never had a connection when the connection strength bars are in my control panel--it shows I am connected but no dice; alas, when the network manager icon (the two little computers) is present the internet will work...sometimes). Currently it is working as such (via network manager):

Wireless connection is enabled; address=dhcp
Wired connection=roaming mode enabled

Anybody have any clue what I am rambling about? I suspect this has something to do with the other (Windows based) machines in the house fighting for an ip address but I am dizzy from reading so much about networking--I have absolutely loved my experience with Gnome/Ubuntu, however I am wondering if maybe I would have more luck in another distro as it is imperative I have a highly functional internet connection.

-S

---

### Post by luca.mg on 2007-06-10
try a static address instead of dhcp,good luck

---

### Post by carusoswi on 2007-06-10
> **sw1995 said:**
> Hello!

A quick question:

I have a linksys wireless card (laptop) that has been recognized by Ubuntu (out of the box) and works well (it is set to connect via automatic DHCP--roaming IS NOT enabled), however I notice that when I restart my laptop often the system will have a hard time reconnecting to the network. Sometimes it works, sometimes it doesn't--sometimes it will connect an hour or two later if I leave it be. In any event, I cannot guarantee that I will have the internet when I turn my computer on and that is difficult to deal with and overall I fell as though I have very little control over the situation.

Is this simply the nature of the beast? It is rather frustrating as I use my computer to work from home, however I have to fix it because I refuse to give up my Gnome/Ubuntu desktop!

Cheers!
-S

Have you tried the command 

iwconfig

from the terminal??

If you do, it should report the name of your router.  If it shows you none or any, then, your wirless adapter is not properly associated with the router.  I use a Belkin N1 adapter, and, when it is working, works very well.  However, it can and does drop its association with my router.  I cannot explain this, so, I have just learned the command to work around the problem when it occurs - from the terminal type:

sudo iwconfig wlan0 ESSID name_of_your_router

When you hit enter, you will be prompted for your system password.

If you have typed the command correctly and, if the command is successful, you will notice your wireless adapter respond (the light on mine blinks).

From your terminal, run the command 

iwconfig

again.  This time, you should see the name of your router in the first line of the response.  

Now, you should be able to connect to the 'net.

Hope this helps.

I wish I could figure out why my router tends to drop its association with the router.

If I walk away from my computer while it is connected to the 'net, many times I will return to find Firefox unable to find any server.  I don't know why this is, but the above command works for me.

Caruso

---

### Post by sw1995 on 2007-06-11
Thank you for this information--I'll certainly give it a go:)

---

