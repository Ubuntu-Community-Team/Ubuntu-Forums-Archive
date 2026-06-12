---
title: "scroll wheel on bluetooth mouse"
date: 2005-03-27
forum: Apple PPC Users
---

### Post by dherren on 2005-03-27
Running warty on an original Tibook with the D-Link bluetooth adapter and a Kensington bluetooth mouse. The left and right mouse buttons work fine, but so far I haven't been able to find anywhere to get the scroll wheel working.

On an intel box running SuSE 9.1/9.2 the config was easy to find. Can't find anything similar on ubuntu...

Suggestions?

---

### Post by blchalifax on 2005-03-30
Hi I was running into the same problem... I have a powerbook TI 1GHZ 15in running hoary and I'm using an mx900 bluetooth mouse. When I first installed ubuntu I thought everything was installed and working right... except my scroll wheel wouldn't work (an obvious pain). Turns out that bluetooth is not really installed right out of the box like I thought (though it is thankfully in the kernel). What I did to get the scroll wheel to work was to install bluez with synaptic or apt-get.. then look in the /etc/default/bluez-utils file... you need to change HIDD_ENABLED to 1. After I did that my mouse worked like a charm. 

Hope that helps... It's quite possible I'm wrong since I'm a newbie myself.

blchalifax

btw... when first installing bluez your mouse will likely stop working altogether so dont freek out like I did a few times... and you may or may not need to reboot... I did have to but like I said I'm no expert... good luck

---

### Post by dherren on 2005-03-31
[QUOTE=blchalifax]What I did to get the scroll wheel to work was to install bluez with synaptic or apt-get.. then look in the /etc/default/bluez-utils file... you need to change HIDD_ENABLED to 1. After I did that my mouse worked like a charm. 
[/QUOTE]

That sounds reasonable. I just tried an apt-get install bluez, but obviously bluez is not in my possible sources. Where did you find the bluez package?

---

### Post by dherren on 2005-03-31
[QUOTE=blchalifax]btw... when first installing bluez your mouse will likely stop working altogether so dont freek out like I did a few times... and you may or may not need to reboot... I did have to but like I said I'm no expert... good luck[/QUOTE]

OK, so I found and installed the bluez utils:

apt-get install bluez-*

and I made the changes to the /etc/default/bluez-utils file.

And, like you, my mouse doesn't work at all, even after a couple of reboots...

It worked ok before, just not the scroll wheel....

After you "freeked out", what did you do to get the mouse back again? I restarted in OSX and the mouse works there.  I put in fresh batteries and paired again, and then rebooted into ubuntu--still no joy...

---

