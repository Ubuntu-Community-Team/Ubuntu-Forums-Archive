---
title: "Restriced Nvidia driver doesnt work in Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by goodbyewindows on 2007-04-21
I can use the vesa driver with my nvidea GeForce4 500, but it uses 1024x768 resolution, instead of 1600x1200. Even better would be to get the restricted nvidea driver working. I'm using Feisty on a laptop.

---

### Post by sunexplodes on 2007-04-21
There's a great little application called ENVY which will automatically download the newest nVidia (or ATI, for the record) drivers and install them for you. It's an extremely painless process.


Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Deb Package for Feisty: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb)

---

### Post by teknorah on 2007-04-21
> **sunexplodes said:**
> There's a great little application called ENVY which will automatically download the newest nVidia (or ATI, for the record) drivers and install them for you. It's an extremely painless process.


Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Deb Package for Feisty: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb)

WOW!!! This is awesome!  Thank you for this post!  It was so FAST and EASY!

---

### Post by UbieNoobie on 2007-04-21
> **sunexplodes said:**
> There's a great little application called ENVY which will automatically download the newest nVidia (or ATI, for the record) drivers and install them for you. It's an extremely painless process.


Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Deb Package for Feisty: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb)


Oh wow! After a day of trying many different solutions and failing, this worked first time. Thankyou. I recommend anyone having trouble with the Nvidia driver use this.

---

### Post by cumanzor on 2007-04-21
> **UbieNoobie said:**
> Oh wow! After a day of trying many different solutions and failing, this worked first time. Thankyou. I recommend anyone having trouble with the Nvidia driver use this.

Does this work with 7.04?

---

### Post by Mikkel Nielsen on 2007-04-21
I use 7.04 and it doesn't work for me. I get "Error: Dependency is not satisfiable: module-assistant" and I'm not allowed to press the "Install package" button.

What do I do ?

---

### Post by UbieNoobie on 2007-04-21
I'm afraid I don't know. Yes it worked for me in 7.04 since it's my first and only Ubuntu, but I don't know why it's not working for you sorry.

---

### Post by goodbyewindows on 2007-04-22
> **sunexplodes said:**
> There's a great little application called ENVY which will automatically download the newest nVidia (or ATI, for the record) drivers and install them for you. It's an extremely painless process.


Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Deb Package for Feisty: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu2_all.deb)

I'm using lynx to reply to you right now! When I start my computer, I get the X server error message and the server output says it couldn't find the nvidia kernel.

---

### Post by wataboutbob on 2007-04-22
surely, if you're using Feisty, can't you go to System > Admin > Restricted Driver Manager and enable nvidia drivers? thats how I did it...

---

### Post by peebly on 2007-04-22
> **wataboutbob said:**
> surely, if you're using Feisty, can't you go to System > Admin > Restricted Driver Manager and enable nvidia drivers? thats how I did it...

Well you would think so, but for me no.

See the restricted driver manager installs an old nvidia driver and not the new one. The old one will not work with my computer.

Both drivers are in the repositories.

I removed the restricted driver manager as it useless to me.

Envy installs the nvidia control panel too.

---

### Post by wataboutbob on 2007-04-22
A mate of mine wasn't happy installing the restricted drivers too. He said he'd wanted the control panel for power saving features - which I can see that I don't have...

In my case, my laptop still runs relatively cool with normal usage. Battery meter is showing time remaining as almost 2 hrs 40 mins (same as XP) and Beryl runs happy. 

If its not broke, no need to fix it eh? or can you tell if there are other features from the official nvidia drivers that I'm missing?

cheers

---

### Post by goodbyewindows on 2007-04-22
After getting some help on irc, I just resorted to using the nv driver because of some weird stuff going on with the nvidia one. Ah well.

---

### Post by sunexplodes on 2007-04-22
**Wataboutbob:** Even if you're using the restricted drivers, you should be able to access the nvidia controls by typing nvidia-settings in terminal.
[B]
goodbyewindows:[/B] I had a similar problem to what you had. If you install the restricted driver followed by the one Envy installs, they clash. If you go into synaptic, you can remove the following packages and their variables:

linux-restricted-modules*
nvidia-glx
nvidia-kernel-(generic, source, common, all of them)

Once those are removed, CTRL+ALT+F1, and enter "envy -t" in terminal, which would set up your nvidia driver fairly easily and without conflict.

Anyway, that's what worked for me.

---

