---
title: "Compro Videomate DVB-T200"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Goodson1974 on 2007-03-02
Hi
 
I'm very new to Ubuntu and GNU/Linux in general and was wondering if anyone has been able to get a **Compro Videomate DVB-T200** tv card working in Edgy?
 
I've found out that it's an **saa7134** if that helps?!
 
It's the last major hurdle i need to get over so that i can ditch XP for good!
 
Any help will be greatly appreciated, but please keep it simple (if possible) as i get easily confused :confused: !!!!

---

### Post by Goodson1974 on 2007-03-21
I've still not had any luck with this TV card.
 
Has anyone got any ideas?!!

---

### Post by Goodson1974 on 2007-04-26
I've installed Feisty and have still not had any luck with this DVB card.
 
Does anyone know if it is possible to get this working?
 
I'm thinking of ditching it and getting another card.  
 
Can anyone reccommend a PCI DVB card that works 'out of the box' for Feisty, or a link to somewhere that lists compatible digital tv cards?
 
Any help will be greatly appreciated :)

---

### Post by raver31 on 2007-05-20
You are of course using the proper firmware for the card ?
you need to copy is to /lib/firmware
then
sudo modprobe saa7134_dvb

---

### Post by Goodson1974 on 2007-05-20
raver31 you are a :KS

I did the modprobe thang, started up Kaffeine, scanned for channels and it worked :D

Thanks a lot mate, much appreciated :)

---

### Post by Mad_Max_1412 on 2008-03-12
Guys,

I need help.  I also have a DVB-T300 card. I installed it and then when I booted up, I installed Kaffeine.  I selected "au-Newcastle" as the location and basically kept all other prompts as the default.  When I started Kaffeine, I chose "TV" from the options available.  I then went to scan for channels and it would show varying signal strengths, but the "Stop Scan" would change back to "Start Scan" and there would be no channels listed.

I then found this thread.  I read raver31's entry and admittedly didn't know what he meant by 
> you need to copy is to /lib/firmware
but I did open a terminal and enter
> sudo modprobe saa7134_dvb

Now when I start Kaffeine, I don't have the TV option, only options to play audio, VCD and DVD's.

Could someone please assist?  As you can tell, I'm a newbie.

Thanks

Max

---

