---
title: "live cd"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by wolfs4475 on 2006-03-04
when i run live cd it is ok on every thing. then screen goes black with - in corner. and my pc locks up. it wont do any thing. i have to shut it off. what can i do.

---

### Post by Mustard on 2006-03-04
One thing I would be curious about is if you hit ctrl + alt + f1 when you get the blackscreen, does it to take you to a command line login prompt, or a command line of any kind?

I can't recall exactly how the liveCD works, but does it ask you what type of graphics driver you want to use at the start?  

I'm thinking at the moment you might have an ATI graphics card is that right?  

If not, then what type of graphics card do you have and what are your other system specs?

---

### Post by KenzoIX on 2006-03-04
(Excuse me, my English is poor)
This is a little off-topic, but I don't want to start a new thread for this simple question....:)
I have a mobo based on xpress 200 chipset, and as you know, I have to use vesa driver instead of ati. AFAIK, the only way I can do it is boot in the expert mode. But I'm sick of pressing Enter a thousand times. So I'm looking for an alternative way. I guess I can boot in normal mode, use the command prompt and change the driver section in xorg.conf file from "ati" to "vesa" and restart the X. Will it work? I've tried but when I open xorg.conf in vi I get the message "Readonly file" or somthing like that, and the vi also make me confused. Is there any tutorial for basic editing in vi and how can I change the file attribute?
Sorry for asking such a stupid question, I know that's very simple but I'm very new to linux (just got the Ubuntu CD yesterday)

---

### Post by Mustard on 2006-03-04
[QUOTE=KenzoIX](Excuse me, my English is poor)
This is a little off-topic, but I don't want to start a new thread for this simple question....:)
I have a mobo based on xpress 200 chipset, and as you know, I have to use vesa driver instead of ati. AFAIK, the only way I can do it is boot in the expert mode. But I'm sick of pressing Enter a thousand times. So I'm looking for an alternative way. I guess I can boot in normal mode, use the command prompt and change the driver section in xorg.conf file from "ati" to "vesa" and restart the X. Will it work? I've tried but when I open xorg.conf in vi I get the message "Readonly file" or somthing like that, and the vi also make me confused. Is there any tutorial for basic editing in vi and how can I change the file attribute?
Sorry for asking such a stupid question, I know that's very simple but I'm very new to linux (just got the Ubuntu CD yesterday)[/QUOTE]

Open vi as a 'superuser' using the **sudo** command..

```
sudo vi path_to_filename
```

This should allow you to access the file with read and write ability.

If vi confuses you, try nano.

```
sudo nano /etc/X11/xorg.conf
```

---

