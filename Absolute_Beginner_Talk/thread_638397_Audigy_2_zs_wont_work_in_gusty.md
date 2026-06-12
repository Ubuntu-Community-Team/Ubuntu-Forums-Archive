---
title: "Audigy 2 zs wont work in gusty"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by All.Bets.Are.Off on 2007-12-12
I just upgraded to ghusty and my audigy 2 zs wont work. 

avalible devices in the Volume control are:

0: Intel ICH6
1: Audigy 2 zs
2: Sigmatel STAC9750.51

I have selected the audigy, and tried changing the optical out on/off (i use optical out so it should probably stay on. 

It should be noted that this swtich will not stay off though, once i close the volume control it goes back to being on. 

In aslamixer the Audigy 2 zs is the default card. 

I get sound out of my onboard card through my laptop speakers. 

I get this:

> ryan@Ryans-Bitch:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_emu10k1


and added
 > options snd-snd_emu10k1 index=0
options snd-snd_intel8x0 index=1

to /etc/modprobe.d/alsa-base


still no dice. any help appreciated

---

### Post by MetalMusicAddict on 2007-12-12
Crazy. Im friends with Ubuntu's old ALSA maintainer and on his word I bought this exact card off of Ebay because of the chipset.

It *should* work great OTB. Ill be doing a clean install soon and Ill let you know how it goes.

Sorry I can help now.

---

### Post by All.Bets.Are.Off on 2007-12-12
i also have a new issue, if i use the onboard sound ports, the main volume control does nothing, only the volume control in whatever program im using.

---

### Post by MetalMusicAddict on 2007-12-12
> **All.Bets.Are.Off said:**
> i also have a new issue, if i use the onboard sound ports, the main volume control does nothing, only the volume control in whatever program im using.

Try disabling the onboard card in the BIOS and just using the PCI card. That very well could be the issue.

---

### Post by All.Bets.Are.Off on 2007-12-12
i cant figure out how to disable in in dells bios for my latitude d610, it doesnt seem to be an option. ug.

---

### Post by kpkeerthi on 2007-12-12
> **All.Bets.Are.Off said:**
> i cant figure out how to disable in in dells bios for my latitude d610, it doesnt seem to be an option. ug.

You can't disable onboard sound device in the bios for dell laptops.

---

### Post by MetalMusicAddict on 2007-12-12
> **All.Bets.Are.Off said:**
> i cant figure out how to disable in in dells bios for my latitude d610, it doesnt seem to be an option. ug.

So wait, you're using the USB version?

---

### Post by All.Bets.Are.Off on 2007-12-12
No the Audigy is the mini pci version.

Dell Bios sucks. Theres pretty much no optioins for changing anything in it.

---

### Post by MetalMusicAddict on 2007-12-12
> **All.Bets.Are.Off said:**
> No the Audigy is the mini pci version.

Not commonly but there is a version. Im just correcting you for the benefit of other readers.

[http://images.google.com/images?q=Audigy+2+zs&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&sa=N&tab=wi](http://images.google.com/images?q=Audigy+2+zs&ie=UTF-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&sa=N&tab=wi)

---

### Post by All.Bets.Are.Off on 2007-12-12
im using the Creative PCMCIA Sound Blaster Audigy 2 ZS Notebook

---

### Post by All.Bets.Are.Off on 2007-12-12
i blacklisted the drivers for the internal soundcard and now it works. But i dont get any audio from firefox, i get sound everywhere else but non in firefox.

---

### Post by kpkeerthi on 2007-12-13
[http://planet-geek.com/archives/003048.html](http://planet-geek.com/archives/003048.html)

---

### Post by anachreon_ on 2007-12-21
I, too, have been having problems with my Audigy 2 ZS Notebook ever since I upgraded to Kubuntu Gutsy.  Things worked fine in Feisty, but I suspect Gutsy overwrote some of the config files I edited to get it working in the first place under Feisty.  Now, whenever I plug in the Audigy I get no sound, my computer won't shut itself down (it hangs at a black screen after unloading most of the system), Amarok hangs, etc.  Also, artsd seems to be causing all sorts of problems - hanging on startup, etc.  I'm no expert on linux audio, but it seems like arts is no longer developed and I should get rid of it, or turn it off, anyway.

I'm on a Dell Inspiron 9300.

---

