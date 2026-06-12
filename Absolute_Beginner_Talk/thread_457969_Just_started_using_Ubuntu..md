---
title: "Just started using Ubuntu."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Keego on 2007-05-29
I just started using Ubuntu yesterday and it seems good. 
I have no idea how to use it though.

I want to set up my wireless card but the CD i got with it wont work on Ubuntu. 
I know it's not working 'cause none of the lights are on.
How do i set this up? 

Also, i'd like to know how to install my graphics card. Can anyone direct me to some posts where these are explained? Thanks. 

;)

[COLOR="Red"]**EDIT**[/COLOR]
[B]My graphics card is a GeForce 7300LE
My wireless card is Sitecom WL-171. [/B]

So...help please?

---

### Post by mikewhatever on 2007-05-29
First, you'll need to identify the exact models of both the wireless and the graphics cards. Go to Application>Accessories>Terminal and post here the output of the following
> sudo lshw

---

### Post by Outrunner on 2007-05-29
> **Keego said:**
> Can anyone direct me to some posts where these are explained?

Well, not really, we can't do that. You see we need more information first. As in, what video card are you trying to install drivers for? An ATI card(which?) or Nvidia(which one?) And we also need the model of the wifi card to help you set it up.

---

### Post by Bachstelze on 2007-05-29
What's the model of the cards ?

---

### Post by Keego on 2007-05-29
Yeah, i'll get you them. I'm at a friends on his laptop so i don't know them right now. 

I'll get back to yous thanks for the help. :)

---

### Post by Keego on 2007-05-29
Alright my graphics card is a GeForce 7300LE 
and my wireless card is Sitecom WL-171. 

So yeah. Any help? xD

---

### Post by Keego on 2007-05-29
Anyone?

This is turning into a lost cause.

---

### Post by Kuoi on 2007-05-29
I can't help you for the wireless , but for the videocard I recommend you to install [Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu6_all.deb").
First uninstall your driver using the tool , and then install it .

If you can't boot after it , just boot in "recovery console" , and type there > dpkg-reconfigure xserver-xorg , but normally , using  Envy should work well.

Kuoi

---

### Post by Keego on 2007-05-29
Bump :popcorn:

---

### Post by Dougie187 on 2007-05-29
You could look into the Ndiswrapper for your wireless. Not sure if it will help you out all that much. But its worth a shot.

---

### Post by morghi76 on 2007-05-29
yep, google for ndiswrapper and you will find how easy can be to fix you wireless card. At least I managed to fix it just using a combination of this software and the XP driver for my card.
Check this link [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by Dougie187 on 2007-05-29
If im not mistaken, you will have to get the windows driver from the cd that you have with your wireless card. Then you will use the ndiswrapper to use that driver for your wireless card. Please correct me if im wrong, as I have never used ndiswrapper, i only have an ipw2200. It shouldn't be too hard for your wireless card though. Let us know if you have any more problems.

---

