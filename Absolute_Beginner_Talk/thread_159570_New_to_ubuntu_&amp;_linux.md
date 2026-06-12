---
title: "New to ubuntu &amp; linux"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Qwest on 2006-04-13
Hey people.

I was given a PC the other week with a failed hard drive.  The owner didn't want it anymore so just gave it to me which was awfully nice of them!..

after sticking a new Hard drive in there, i realised i didn't have an operating system to stick on it (lol), so decided to see what i could find in the way of Linux.  A friend of mine told me he had seen screen shots of ubuntu and said it looked nice, so decided to give it a whirl!

So now im running ubuntu 5.10 on tis box and i am enjoying it!  It looks nice, it's quick, and hopefully, it'll be good for what i want it for.

Basically, the box is quite small.  It stands about 10 inches tall, and would fit nicely in with my TV setup!  So i was thinking i could link it up to the TV and use it to show video's, play old games, show pictures etc etc.

I've now come accross a problem.  The box doesn't have a TV out, and because of it's compact size and manufacturer (Dell), it doesn't have any card ports at the back, so i cant put in a graphics card.  ([here's an image of the box]("http://www.ixbt.com/short/2k2-10/dell-opti260.jpg")).

So first off, does anyone know how i can get this box running on a TV. Can i fit a TV out socket somewhere?

Also, my box isn't connected to the internet. so i cant really use the repositories.  Is there any programs that people would advise on using on my ubuntu box?

---

### Post by encompass on 2006-04-13
As for repositories... I recommend getting the box working with the internet connected... once you have ti the way you want... disable the autointernet at boot to speed things up a bit and then disconnect it.
As for a tv out if you don't ahve even a pci there is only one option to get it to your tv screen...
[try froogle.]("http://froogle.google.com/froogle?q=pc+to+tv+converter&hl=en&btnG=Search+Froogle")
They have lots to pick from.  and are not software based so dead on easy to install.8)

---

### Post by Qwest on 2006-04-13
Thanks encompass.

the way my internet is set up (through my cable TV), it goes to my windows box via USB, and then goes through the installed software for the user & pass. I dont think the software will work on linux, but i shall have a look, see what i can sort out.

---

### Post by encompass on 2006-04-13
there are a few options there too... you could setup your computer to share internet... or check to see if there is a ethernet jack in the back of your computer...
looks kinda like this... [http://en.wikipedia.org/wiki/RJ45]("http://en.wikipedia.org/wiki/RJ45")
If so try plugging in one of thos cable to your linux box.  It may just work.:D

---

### Post by Qwest on 2006-04-13
encompass, you'd think so wouldn't you!

2 weeks back, my friend was round and was doing some work on his laptop. So we tried connecting his laptop to my PC so he could share the connection (using a network cable obviously), but as soon as the laptop & Pc were connected, the internet failed to work on the PC.  Once the network cable was unplugged, the internet worked again!   So not too sure what's going on there.

What i might do is plug the USB internet plug into the linux box and see if that works. if not, i'll run an network cable from my TV box (my net comes via that) straight into the linux box and see if that'll work.  If not, i'll have to try other things.

Just outta interest, can i buy a wireless USB thing and connect it to the linux box and then connect to the internet via a router? Or is that a pain in a** to get working?

---

### Post by Sef on 2006-04-13
> Just outta interest, can i buy a wireless USB thing and connect it to the linux box and then connect to the internet via a router? Or is that a pain in a** to get working?

Do research, buy a compatible one, and it will be easy to set up.

---

### Post by johnnymac on 2006-04-13
That problem is usually because cable providers use your MAC address to base who can connect from your feed and who can't.  I haven't the foggiest idea why they do this 'cause there are tons of ways around it.  So here's my suggestion:

1.  Get a Router (Linksys is a good one)
2.  Connect your modem to the rounter (via cable they provided to connect to your PC)
3.  Connect your computer to your router via RJ45 cable

There's a setting in your router to duplication the MAC address of your computer (the manual covers how to do it).  Once you get that set-up you can just connect computers to the router and have many, many hours of networked computing fun :)

Also...this provides added security because routers are a great NAT firewall.

GL

---

### Post by Qwest on 2006-04-13
Johnny, thank's for that buddy.

I wasn't too sure whether windows & linux could both network together via a router.  I do actually have a wireless router, it's totally rubbish and i cannot get it to work at all!.. but i will be investin in a good'un soon as my girlfriend want's to use her laptop for the internet.

---

### Post by encompass on 2006-04-15
That is great... don't for get to look into the hardware compatibility list.  [http://doc.gwos.org/index.php/HCL]("http://doc.gwos.org/index.php/HCL")
Hope this helps... last of all don't be affraid to ask for linux compatible software.  Tell them and spread the word.

---

### Post by encompass on 2006-04-16
and if you want it in your tv for cheap you can make an ir reciever for it and take signals to turn off the computer or play mp3's or play movies... many things... it si a blast to learn... I am going to make a howto once I have perfected it.

---

