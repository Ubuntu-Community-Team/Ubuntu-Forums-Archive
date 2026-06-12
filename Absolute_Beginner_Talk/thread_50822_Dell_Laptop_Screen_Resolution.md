---
title: "Dell Laptop Screen Resolution"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by tamoore on 2005-07-21
Dell Latitude CPi 266mhz, 128mb ram.
NeoMagic

Under System->Preferences->Screen Resolution
Itlists only options for 800x600 or 600x480

I need to set to 1024x768

Under System->Administration->Device Manager
It shows:  Neomagic NM2160

Can someone guide me please in beginners terms how to correct the problem so I can have 1024x768?

Thank you

---

### Post by Mircoza on 2005-07-21
i dont think the cpi can get 1024*768

---

### Post by Saru san on 2005-07-21
Nope, I have that same laptop. Maximum resolution is 800x600. With the windows driver you can set it to 1024x768 but it just makes a virtual screen and pans when you hit the edge.
As a side note. 16 bit color will give you much better performance with this old chipset.
And look into adding```
Option "OverlayMem" "829440"
```In your xorg.conf.
See [http://www.xfree86.org/4.3.0/neomagic.4.html](http://www.xfree86.org/4.3.0/neomagic.4.html)

---

### Post by tamoore on 2005-07-21
[QUOTE=Saru san]Nope, I have that same laptop. Maximum resolution is 800x600. With the windows driver you can set it to 1024x768 but it just makes a virtual screen and pans when you hit the edge.
As a side note. 16 bit color will give you much better performance with this old chipset.
And look into adding```
Option "OverlayMem" "829440"
```In your xorg.conf.
See [http://www.xfree86.org/4.3.0/neomagic.4.html](http://www.xfree86.org/4.3.0/neomagic.4.html)[/QUOTE]
 I have 1024x768 in Mandrake Linux, just not in Ubuntu, and in Windows without scrolling.

---

### Post by Jussi Kukkonen on 2005-07-21
You could try running 
```
sudo dpkg-reconfigure xserver-xorg
```
and answering the questions... Helped me in a similar situation.

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=tamoore]I have 1024x768 in Mandrake Linux, just not in Ubuntu, and in Windows without scrolling.[/QUOTE]


Then copy your xorg.conf file from Mandrake and put it in Ubuntu. Best of both worlds.

---

