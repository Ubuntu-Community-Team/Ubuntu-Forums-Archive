---
title: "Please please help"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2007-11-19
I convinced someone to try Ubuntu, just to see if he liked the live cd. I was telling him this over the internet, and the next thing I knew, he had installed it because he's mad- he only wanted to try it so he could tag his songs right. Anyway, ever since he installed it, he has had nothing but problems. I'm not much of a techie and I've been trying to help him. It's driving me nuts :P. 

His latest problem is screen resolution. He wants to change it but it won't save, when he leaves the menu it resets back to the old resolution. He has been asking me to help for a while now so pleeeease help so he can shush. 

I don't know why he isn't asking you himself, he's a bit lazy. :P

---

### Post by Joakim Stokland on 2007-11-19
Did he install Feisty Fawn or Gutsy Gibbon? The very few problems I had with Feisty were solved when I installed Gutsy.
Also, you should tell us what hardware he's got. That'll make it all much easier. :)
For a starter, what make and model is his graphics card? Then we will know how to solve the resolution problem.

If he starts console and types "sudo lshw", all installed hardware will be displayed. Tell him to post the output here, or send it to you, and you post it here.

Joakim

---

### Post by Ionamay on 2007-11-19
he says:

pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress norm

oh and he is running gutsy

---

### Post by aqchat300 on 2007-11-19
not to be rude uhh but can u put that in a human being format

processor:

graphics card:

and from there on u should know what to do :P

also 

OS::popcorn:

---

### Post by Ionamay on 2007-11-19
processor- AMD athlon 64 Processor 3000+
Graphics card- nVidia
OS- gutsy

---

### Post by Joakim Stokland on 2007-11-19
As far as I can understand, that would be his sound card. Is his sound working properly?
Please post the entire output?

---

### Post by Ionamay on 2007-11-19
it's confusing me, there is loooads of it and it repeats itself a lot

---

### Post by coolguy2006delhi on 2007-11-19
Install **envy** to solve all the nVidia and ATI drivers problem .

Here is the download link for envy.

**[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)**

I used envy before installing Compiz-Fusion

---

### Post by maniac_X on 2007-11-19
why not give him the URL to the forums and let him post? it seems rather silly to try and try to help him via thrid party?

---

### Post by Ionamay on 2007-11-19
He's given up and wants to uninstall Ubuntu without damaging his windows partition, can someone tell me how to do that? :) sorry for the trouble.

---

### Post by Ionamay on 2007-11-19
He's too lazy

---

### Post by Duck2006 on 2007-11-19
This should do that.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Joakim Stokland on 2007-11-19
If he has given up Ubuntu, and don't want to try at all, than that's probably the best solution. You can't start using a new OS without being willing to learn it first.

> **Ionamay said:**
> it's confusing me, there is loooads of it and it repeats itself a lot
It actually doesn't. Many of the listings seem like the same, but that's just because they include Linux' way of addressing them - referring to them. In between there are descriptions of what hardware we're dealing with. That's why I asked you to post it. If you look through the entire list, you will see sections like "Display", "Multimedia", and stuff like that. And where it says "*-display:0", you'll see what graphics card he's got. If it's some nVidia card (which is most likely since he's got nVidia sound card), follow coolguy2006delhi's link.
If not, please copy and paste the entire section, from *-display:0" to "*-display:1", or any other similar line. And we'll take it from there.

Good luck!
Joakim

---

### Post by Ionamay on 2007-11-19
He has decided to go back to windows for now but he says he will go into ubuntu every so often to see if he can get used to it or fix the maaaany problems he had. So everything is okay for now.

---

### Post by Joakim Stokland on 2007-11-19
Okay. Has he considered dual-booting then? That is by far the best solution for someone wanting to try other OS's while being used to Windows. I dual booted for several months before changing completely. I kept Windows just in case. That way you always have a familiar OS to return to if everything fails.

Again, good luck!
Joakim

---

