---
title: "im getting tired, please help"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-10
Alrite

My Goal: transparent windows
My Set Up: Dell Inspiron 6000 laptop, Ubuntu 6.06 Dapper Drake

I have tried to set up XGL/Compiz, and it did not work so well, made everything really laggy.

Can anyone please help me?????

---

### Post by daWabbit on 2006-07-10
You almost certainly lack the video capability this use demands. There may be a few high-end notebooks which can handle this use, but i can't think of one, off hand. 

My wife ran what you are trying to run on her desktop. She has a very high-end NVidia graphics adapter with 512 MB of memory and it's own graphics processor. It worked there, but even so it was evident the system was really working pretty hard. 

Jack

---

### Post by michael1977 on 2006-07-10
You may want to post more specs.  Needed to know, what is your graphics card, where did you download and install xgl compiz, from repository on synaptic or self build, what type of processor, how much ram.  That should be a good start.  I ask because I have an Nvidia card and may be able to help if you have an Nvidia graphics card.  Also most people don't realize what is in that particular laptop, and are not going to take the time to look it up.  So give us a bit more info. and we can see what comes from it.  :D

---

### Post by nalmeth on 2006-07-10
If all you're looking for is transparent windows, you should try kubuntu, I know you can have transperancy for inactive windows, and moving windows, stuff like that. It hasn't worked for me yet (intel video), but it might be due to limitiations in my card. I'm sure it will be less exhaustive for you than xgl was, if you can get it to work,

Attached is a screenshot of where you enable the stuff in desktop settings.

Might be worth a try
sudo aptitude install kubuntu-desktop

---

### Post by IrishGangsta on 2006-07-10
I Believe these are my notebook specs, If not then something close.

# Intel Pentium M Processor 760 (2.0GHz/2MB Cache/533MHz FSB) 
# 15.4 inch UltraSharp WSXGA+ (1680x1050)
# 1GB, DDR2, 533MHz
# 128MB DDR ATI's MOBILITY RADEON X300 PCI Express x16 Graphics 
# 80GB 7200rpm Hard Drive (Hitachi 7k60 HTS726060M9AT00)
# 8x CD/DVD burner (DVD+/-RW) with double-layer (SONY)
# Intel PRO/Wireless 2200 (802.11b/g) Internal Wireless 

And this is the forum i had previously followed but did not work:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by adam.tropics on 2006-07-10
go to [compiz.net]("http://www.compiz.net/viewtopic.php?id=389"). Their howto is excellent. As far as I can tell you have plenty good enough machine for xgl. Runs fine for me on 1.5 celeron M with 128mb shared video memory, 512mb DDR2 ram on ATI card, so you should be able to do it fine.

---

### Post by Crosbie on 2006-07-10
Have you got the right (proprietary) drivers for your video card?  What's the output of typing fxglrxinfo into a terminal?

Took me a couple of goes to get my ATI graphics card running correctly.

---

### Post by IrishGangsta on 2006-07-12
when i type fxglxinfo it comes back as :command not found.

And i think it turns out i have an Intel graphics card

---

