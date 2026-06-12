---
title: "Boot process stops at Usplash"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by N8K99 on 2006-06-07
Ti Powerbook with a dual boot, dapper/tiger. The Optical drive recently failed and I have been unable to rescue it. 

During the boot process, I chose Linux and the whole usplash process goes along and then when we get to the point where init is about to take over, the screen flashes, shows the cursur and then returns to the usplash image.

I can sign into linux through a getty and then startx. This does start up kdm however, there are some problems. 

The wireless shows it is connected to the network, however it is not. I am also unable to actually connect using the ethernet. When I go to log out it only allows me the option of signing out of the session.

My problem is pretty straight forward I believe. It was something that I was able to solve by using the rescue option on the installation CD until my optical drive went tits up. So, if anyone knows how I can replicate this from within the system then I'd be really grateful.

---

### Post by BoneKracker on 2006-06-20
If you still need help, you might want to  rephrase your question and create a new post.  I'm not too bright, but I had difficulty understanding your situation and what you are asking for.  Maybe you'll have more luck getting a response.

---

### Post by N8K99 on 2006-06-20
It's ok, I bought a new optical drive and then took the drastic measure of erasing my hard drive, as everything is backed up threeways no worries. Then using the optical drive to re-install OS  X and Kubuntu fresh and clean, I now have a shiny new set of ossen on my machine.

Incidentally, I did figure out why the previous setup was hanging up when it booted. After the boot process was complete and the X-server was starting up, there was problems within /etc/X11/xorg.conf that told the computer that I had hardware that was not connected. This happened even in my new setup. I just commented out those portions of xorg.conf and it runs quite smoothly.

---

