---
title: "Apple LED Cinema Display"
date: 2009-01-12
forum: Apple Hardware Users
---

### Post by carrick on 2009-01-12
I have an Apple 24 LED Cinema Display that I am trying to get working on my macbook 5.1.  This is the new one with the mini display port.  Whenever I connect it and enable it via nvidia-settings the display is just garbled/static.  I have tried the nvidia-177 and 180 drivers from intrepid and jaunty as well as the latest (non-beta) 180 driver directly from nvidia without any success.  

I've also tried disabling compiz, glx and everything else I could find.  It looks like it could be a refresh rate problem, but those look ok.  Or maybe this is some sort of DRM problem?  Has anyone else had any luck with this display in gnu/linux?  Thanks.

Carrick

---

### Post by carrick on 2009-01-13
Just a few more details.  This problem occurs with both the 32 and 64 bit versions of Intrepid.  I have 4G of ram, but it also exhibits the same behavior with 2G.

---

### Post by anjanesh on 2009-01-13
Out of curiosity, are Apple monitors compatible with Linux/Debian/Ubuntu ?

---

### Post by Profiler on 2009-01-14
I to have a MBP 5.1 with a external monitor > Samsung syncMaster 2223nw. connected through the mini display port.

And yes its all static :(

---

### Post by carrick on 2009-01-14
Does the samsung monitor have a display port connector or is it a vga or dvi connector?  Does the monitor work under OS X?  It looks like the nvidia driver isn't really up to snuff.

The 24in apple cinema display is only listed as working with particular Apples with mini display ports, but I would expect it would work under linux as well, unless it is some sort of DRM problem.

I have submitted a help request with nvidia, I'll update the thread if anything comes from it.

Carrick

---

### Post by Profiler on 2009-01-15
> **carrick said:**
> Does the samsung monitor have a display port connector or is it a vga or dvi connector?  Does the monitor work under OS X?  It looks like the nvidia driver isn't really up to snuff.

Carrick


Carrick,

I use a MDP to VGA adaptor and yes it works under OSX and MS Vista.

This is a real downside and the main reason why i still use OSX.

I am using the 180.11 btw, because i cant find the newer 180 driver in the synaptic manager, but the same problem occurs with 177.x installed :(

thx

---

### Post by carrick on 2009-03-02
Just a follow up, I was not able to get the apple lcd cinema display to work.  I ended up returning it and getting a 24in acer display with the same resolution.  This display works great with the normal dvi adapter.  I spent a lot of time trying to get the apple display to work, but by no means did I exhaust all options.

---

### Post by tigrux on 2009-11-24
Guys, just to let you know that the Apple Led Cinema Display works ok with the driver 195.xx of nvidia (currently in beta status).

This is with Ubuntu Karmic 64 bit + MacbookPro 5,5 + Led Display 24".

---

### Post by ts230 on 2009-12-08
I have a ViewSonic 22 inch that has a high resolution under OSX(1600x1200 or something), but on Ubuntu it has a lower resolution. It is connected using a VGA->MiniDisplay Port. I have a Macbook 1,1

---

### Post by fabrixx on 2009-12-22
Try new [B]190.53 drivers:

[Release note]("http://forums.opensuse.org/tech-news/428966-nvidia-driver-190-53-released-2009-12-16-a.html")

[/B]*Fixed a problem that caused resolution limitations or corruption on certain DisplayPort devices such as the Apple 24" Cinema display or some DisplayPort to VGA adapters.*

---

### Post by Alisdead1 on 2010-01-29
I use a MDP to VGA adaptor.

---

### Post by Alisdead1 on 2010-01-29
I use a MDP to VGA adaptor and yes it works under OSX and MS Vista.

This is a real downside and the main reason why i still use OSX.

---

### Post by Pinguinusa on 2010-03-21
I have self-made PC with Asus mAtx HDMI Motherboard. I have installed Aplle optional grafic card Nvidia G120 with built in mini port female. I tryed to start Ubuntu in safe mode and it works with 1280x720 resolution. But I could not get 1920x1200 native resolution. So I have installed ALTLinux I86 5.0 and start in safe mode with generic LCD monitor 1980x1200 and generic grafics driver 1920x1080, and IT WORKS!!!!! In native resolution!!!!. Meanwhile Nvidia proprietary driver does nor work at all. ALTLinux is local Russian linux distributive of KDE. I think Kubuntu will work as well.

---

### Post by StepanRibin603 on 2010-10-19
ìíå ðàçðàáîòàëè [crm ñèñòåìó](http://clientbase.ru) ñ ó÷åòîì ìîèõ ïîæåëàíèé è îñîáåííîñòåé áèçíåñà.

---

