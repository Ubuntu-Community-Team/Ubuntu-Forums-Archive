---
title: "wireless, wine, and other problems"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by alSuhail on 2007-04-20
I'm an absolute newbie to linux. I've installed feisty on my C2D  and now I'm trying to get the wireless to work. I'm following the instructions here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I'm getting tripped up at the section immediately under the "Common" heading. It's telling me to use Wine along with the driver cd from bootcamp to get the Windows driver to put into ndiswrapper. I've installed Wine successfully but I get an error message ( could not load L"c:\\windows\\system32\\program.exe": Module not found)  when I try to run it using the "program" command. I can't find Wine on my hard disk  using the GUI. Where is it and how do I get it to run properly?

This whole process seems like it could probably be done more easily. Is there another way to get a Windows wireless driver that will work?  If so, how do I bypass Wine? Oh, and again, I'm totally new; so if you could be as detailed as possible, it would really help me out. Thanks!

---

### Post by ronocdh on 2007-04-20
> **alSuhail said:**
> I'm an absolute newbie to linux. I've installed feisty on my C2D  and now I'm trying to get the wireless to work. I'm following the instructions here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I'm getting tripped up at the section immediately under the "Common" heading. It's telling me to use Wine along with the driver cd from bootcamp to get the Windows driver to put into ndiswrapper. I've installed Wine successfully but I get an error message ( could not load L"c:\\windows\\system32\\program.exe": Module not found)  when I try to run it using the "program" command. I can't find Wine on my hard disk  using the GUI. Where is it and how do I get it to run properly?

This whole process seems like it could probably be done more easily. Is there another way to get a Windows wireless driver that will work?  If so, how do I bypass Wine? Oh, and again, I'm totally new; so if you could be as detailed as possible, it would really help me out. Thanks!
I personally triple boot, and so the ```
sudo mount /dev/sda4 /mnt
``` section worked flawlessly for me; I definitely recommend that as a rather painless process, but if you don't want XP on your system, hm, I don't know. I've very limited experience with WINE, and I've certainly never used it with ndiswrapper.

Isn't it a possibility that someone compile the drivers and then host them somewhere for community use? It would make much more sense than this whole WINE/XP ordeal....

---

### Post by muchmusic on 2007-04-21
Yeah... skip the WINE/XP driver thing... save yourself the trouble.

Get online in Ubuntu with a wired connection (or on another computer/OS wireless)

Download the driver for your wireless card from another PC maker (lenovo, etc) for windows XP and use that. Need help figuring out which driver? I went to the ndiswrapper website but if you ask I can probably explain it here (or someone else may beat me to it)

---

### Post by ronocdh on 2007-04-21
> **muchmusic said:**
> Yeah... skip the WINE/XP driver thing... save yourself the trouble.

Get online in Ubuntu with a wired connection (or on another computer/OS wireless)

Download the driver for your wireless card from another PC maker (lenovo, etc) for windows XP and use that. Need help figuring out which driver? I went to the ndiswrapper website but if you ask I can probably explain it here (or someone else may beat me to it)
Actually, I'd love to take you up on that! I have a C2D MBP 15", I think it's an Atheros chipset--so I've read, anyway.

As I posted above, in Edgy I used ndiswrapper on the Apple-provided XP drivers, but if on Feisty I can install from a freely available driver, I'd love to try! I'll dawdle around a bit on a wired connection until I hear back from you. =)

---

### Post by alSuhail on 2007-04-21
> **muchmusic said:**
>  I went to the ndiswrapper website but if you ask I can probably explain it here (or someone else may beat me to it)

Are you referring to the wiki with the long list of drivers? I think I'll try that out and see if it works. If not, which website are you referring to?

---

### Post by muchmusic on 2007-04-21
Yeah, I am referring to that wiki... I am looking for the page I followed... will post back when I find.

---

### Post by muchmusic on 2007-04-21
Ok...

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I used the section on Windows driver installation to find the device ID for my wireless card using lspci -n

I then went to the list at

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

The device I found had a link to driver downloads...

I used cabextract (installed with synaptic) to extract files... then installed continuing with the instructions from the ndiswrapper windows section.

Once I saw that it was installed properly, I DID have to reboot to access wireless networks.

I hope this is clear... Let me know what I need to clarify or add.

---

