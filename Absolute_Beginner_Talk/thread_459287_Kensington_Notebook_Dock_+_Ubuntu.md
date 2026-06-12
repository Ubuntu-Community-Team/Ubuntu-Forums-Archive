---
title: "Kensington Notebook Dock + Ubuntu"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by koxx1100 on 2007-05-30
My dad heard I bought a new computer so he purchased me a Kensington notebook dock.  

(This product)
[http://www.dell.kensington.com/html/6461.html](http://www.dell.kensington.com/html/6461.html)

Can I make this thing work with Ubuntu?  I have done a n00b-worthy search for Ubuntu drivers, but came up with nothing.

I am a complete n00b.

Thanks.

---

### Post by Inxsible on 2007-05-30
> **koxx1100 said:**
> My dad heard I bought a new computer so he purchased me a Kensington notebook dock. 
 
(This product)
[http://www.dell.kensington.com/html/6461.html](http://www.dell.kensington.com/html/6461.html)
 
Can I make this thing work with Ubuntu? I have done a n00b-worthy search for Ubuntu drivers, but came up with nothing.
 
I am a complete n00b.
 
Thanks.
I dont see a reason why the ports on the dock would not work if they work on your laptop. I could be wrong though !!

---

### Post by koxx1100 on 2007-05-30
The dock is some gizmo that sends the computer power, has three USB ports, a printer hookup, a monitor hookup, and maybe some other stuff, and it commuicates all of this with the computer by just a single USB port.  The device came with a CD with windows drivers.  

I tried hooking it up to my computer (with just the power, and then with a USB drive stuck in the dock) and my computer didn't recognize anything.  So I think I need to get drivers or else this thing goes on craigslist.

---

### Post by Inxsible on 2007-05-30
> **koxx1100 said:**
> The dock is some gizmo that sends the computer power, has three USB ports, a printer hookup, a monitor hookup, and maybe some other stuff, and it commuicates all of this with the computer by just a single USB port. The device came with a CD with windows drivers. 
 
I tried hooking it up to my computer (with just the power, and then with a USB drive stuck in the dock) and my computer didn't recognize anything. So I think I need to get drivers or [COLOR=red]else this thing goes on craigslist[/COLOR].
 
Your dad wouldnt be too happy about that !! LOL :D ;)

---

### Post by hillbilly on 2007-05-30
Why don't you try checking on the Dell site. Maybe they have some drivers for this on their site (well chances are slim!)

---

### Post by moiety_tx on 2007-06-01
I have one of these.  Dell definitely doesn't have drivers for it; there are barely even drivers listed for windows on Kensington's site, much less Dell's. Fro me, the nic worked as soon as I plugged it in, and audio seems to work too. I havn't tried plugging in USB devices yet as I seem not to have any here.:redface:

koxx1100, what laptop do you have?

---

### Post by Papar_Man on 2007-06-06
The only thing i cant get to work is the video. Everything else is working fine for. As someone said earlier, the NIC was working as soon as i put the wire in it. For the sound you need to change your sound preferences to output it to USB Audio.

If anyone can get the video to work, i would like to know how you did it :)

---

### Post by homergreg on 2007-06-06
OK, so it sounds like this dock is a string of several discrete usb devices, not so proprietary that they won't work in linux, since you are getting all the other ports to work.  Instead of looking for "Notebook Dock" drivers, it would probably be a matter of looking for the proper USB video driver.  There is probably a USB video chipset on there just waiting for proper drivers and configuration.  Does the video chipset make itself known in the device manager when the dock is active in windows?  If it does, it might give you a direction to look.  I don't even have a clue if there are any Linux USB video device drivers, but who knows?

---

### Post by Papar_Man on 2007-06-07
Yeah it's like a little "hub" that you plug in a USB port. Right now in device manager i have the USB port, the USB sound and the USB Ethernet. Ubuntu doest recognize the USB video. It's there but need drivers to work. I've tried to search (not a big search) for it but nothing. I'm still looking for some USB video drivers. All i find is webcam drivers. But i need a driver going the other "way". I don't want to send images to my computer hehe. 

I've found [http://linux-uvc.berlios.de/#download](http://linux-uvc.berlios.de/#download)

If you read it all they will say that video output will be integrated later.

But i cannot find anything else. Anyone found something ?

---

