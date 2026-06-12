---
title: "what ports should I use for Deluge?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-12-01
No matter which series of ports I choose, it seems to say it is closed when I click on Test.
What ports should it be set at? I dont really understand the concept of ports.

---

### Post by lightstream on 2007-12-01
Ports are a lot less complex than they sound! They are really just an identifying number which allows your OS (ie Linux) to send incoming requests to the correct program. Such a program is said to be 'listening on port XXX'.

I suspect that your problem is probably caused by accessing the net via a router or wireless box. If this is the case, you will need to go to your router configuration (usually by going to 192.168.0.1, 192.168.2.1 or similiar in your web browser) and 'open the ports' which Deluge is listening on.

Where you find this option will depend on your make of router/wireless. My Linksys router has the options in 'Advanced > Port Forwarding', while my dad's Belkin has it somewhere else (can't remember offhand where).

Once you find the option, enter the range of ports that Deluge is listening on, and also enter your PC's local IP - which you can find by right-clicking on the Network icon to the left of the PC clock. Choose Connection Information, and you will see your IP there - it will be something like 192.168.XXX.XXX

---

### Post by KevNice on 2007-12-01
cool, thanks for this post.. I tried to get into the router but it is password protected, and Im assuming that my ISP set the password so I will have to call them to get in. Then I will try your instructions

thanks!

---

### Post by lightstream on 2007-12-01
Try a blank password - that's often the default

Edited to add: also be aware that your router will most likely give you a different local IP every day or so, depending on what other machines the router is already connected to. This means you will need to keep changing the IP in the router settings to match - or give your PC a static IP if possible. Alternatively, if no other machines are connected to the router, you will always get the same IP so it won't be an issue.

Are you sure your ISP supplied your router? That's pretty unusual in the UK at least!

---

### Post by KevNice on 2007-12-01
> **lightstream said:**
> Try a blank password - that's often the default

Edited to add: also be aware that your router will most likely give you a different local IP every day or so, depending on what other machines the router is already connected to. This means you will need to keep changing the IP in the router settings to match - or give your PC a static IP if possible. Alternatively, if no other machines are connected to the router, you will always get the same IP so it won't be an issue.

Are you sure your ISP supplied your router? That's pretty unusual in the UK at least!

It also asks for a username when I log in, and Ive no idea what that is. In either case, blank username/pass didnt get me in.

Yeah the ISP gave it to me when they installed Internet here, I live in Taiwan so its a bit different I guess.

I will call them in a day or two and hopefully I can get into this thing! The Internet works fine but Im trying to find these ports and also install a wireless hub

---

