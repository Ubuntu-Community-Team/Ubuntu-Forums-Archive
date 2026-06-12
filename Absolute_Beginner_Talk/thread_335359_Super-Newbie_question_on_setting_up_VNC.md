---
title: "Super-Newbie question on setting up VNC"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by navneeth on 2007-01-10
This is embarrassing to ask, but you don't get to know things if you keep quiet. :) 

Question: Does my computer (Ubuntu) need to be turned on if I want to access it from XP from over 350Km away?

---

### Post by mohjlir on 2007-01-10
Try it.

---

### Post by navneeth on 2007-01-10
Try what? Leave my computer on for 4 days on the trot? I don't think so. :D

---

### Post by mohjlir on 2007-01-10
Why not?

---

### Post by navneeth on 2007-01-10
Let's just say that I come from a part of the world where we switch the computer off when we're not using it. :P ;)

---

### Post by mohjlir on 2007-01-10
You don't have servers in your part of the world? I thought you were joking in your post about setting up VNC. Of course, it will not work if it is turned off. And by the way, leaving your computer turned on is _better_ for it than turning it on and off all the time. They don't use that much power either.

---

### Post by kidders on 2007-01-10
Hi there,

If there are other PCs on your network, you could get one of them to wake the XP box up for you on demand. Assuming your XP box's network adapter supports wake-on-LAN, you could SSH into something else on your network, send the magic packet, wait 30 seconds (you would have arranged to have your XP box auto-start its VNC server), and connect.

---

### Post by navneeth on 2007-01-10
> **mohjlir said:**
> You don't have servers in your part of the world? I thought you were joking in your post about setting up VNC. 
Well, I was referring to a simple desktop, and nothing bigger in scale. I told you it was embarrassing to ask such a question. :)

> 
 And by the way, leaving your computer turned on is _better_ for it than turning it on and off all the time. They don't use that much power either.

I've heard arguments for and against that statement. 

> Of course, it will not work if it is turned off.

Thanks.

---

### Post by mohjlir on 2007-01-10
Then the answer to your question depends on how you are connecting to the internet. If you have a adsl modem + router, then you could accomplish what you wish to do. If you have dial up, which is likely if you live in a part of the world without servers, you must leave your PC on. There is nothing wrong with leaving it turned on, don't try to make things too complicated.

---

### Post by navneeth on 2007-01-10
> **mohjlir said:**
> Then the answer to your question depends on how you are connecting to the internet. If you have a adsl modem + router, then you could accomplish what you wish to do. If you have dial up, which is likely if you live in a part of the world without servers, you must leave your PC on. There is nothing wrong with leaving it turned on, don't try to make things too complicated.

I never said we don't have server here.  Regarding internet, I connect throught a (A)DSL modem, but I'm not sure about this router thingie.  It's not a wireless connection.

---

### Post by mohjlir on 2007-01-10
Does an ethernet cable go from the modem to your computer, or is it usb or something else?

---

### Post by navneeth on 2007-01-10
Yes, it's an ethernet cable that goes from comp. to modem.

---

### Post by mohjlir on 2007-01-10
Good. You could probably log into your modem and set up port forwarding to accomplish what you want to do, provided your modem / router can do dynamic dns. Here's what you must do:


1. Find out if your modem / router supports dynamic dns (such as dyndns.org)
2. If it does, make an account on one of the dynamic dns hosts, and put the settings into the modem / router. This will allow you to access your machine over the internet even if you have a dynamically assigned ip (if you have a static one, you can skip these two steps and just remember the ip assigned by your ISP. If you don't know if you have one, ask your isp. Sometimes they can provide one at an additional cost).
3. Find out what port you need for this magic packet you speak of.
4. Configure port forwarding on your modem / router to forward packets with this port as the destination address to your computer (which will have to have a static IP).
5. Configure wake up on lan in your bios.
6. Try it out.

---

### Post by navneeth on 2007-01-10
Ah...so this involves messing with dns and stuff? Thanks for those set of instruction, but I think I'll leave things like ip addresses untouched. (it's a long story :D )

---

### Post by mohjlir on 2007-01-10
That's why I said you should just leave it on.

---

### Post by navneeth on 2007-01-10
Hehe...may be another time. :)

Thanks.

---

### Post by QuicksilverKev on 2007-01-10
I leave mine on 24/7, both the Wintel and Kubuntu boxes.

Im green :)

---

### Post by navneeth on 2007-01-10
I'm greener. :P

---

