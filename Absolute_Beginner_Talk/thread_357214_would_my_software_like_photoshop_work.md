---
title: "would my software like photoshop work?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by fmdamcat on 2007-02-09
Ok, I am thinking about switching to Ubuntu, but I need to know if my expensive programs like photshop/illustrator/pagemaker etc will actually be usable...along with all my other things like games etc. Any help will be very appreciated.:)

---

### Post by 23meg on 2007-02-09
You can run some of them via WINE / Crossover. Start by going to [http://www.winehq.com](http://www.winehq.com) and checking their compatibility status. 

Most versions of Photoshop work.

---

### Post by Shay Stephens on 2007-02-09
Photoshop 7 works if ran via wine, and it runs better if ran under crossover linux.  However, Photoshop CS and later do not work yet.  I was using PS CS2 but downgraded to PS7 when I switched to linux.

An option might be to run vmware and install windows onto that, and PS CS2 there, or dual boot, but dual booting is a real drag.

---

### Post by miseljt on 2007-02-09
In addition to that, there are often times Linux alternatives Photoshop -> Gimp, Office -> Open Office, stuff like that. For things there isn't a Linux alternative, you can use Wine (free)/Cedega (not-free), or install VMServer or VirtualBox to install a guest OS.

---

### Post by -Ghost9- on 2007-02-09
do not plan on them working. they won't work like you want them to if at all. I'm dual booting myself because I use the adobe creative suite and it only works on my windows.

You have the choice of dual booting, using free alternatives, trying to use wine(but it won't really work for you), going to a mac, or sticking with what you have.

I'm dual booting cause i like the linux mentality, but the software i need for my professional work is only available for mac or windows. Linux is more of a toy for me right now than my primary OS, but maybe some time down the line when I learn how to use the alternative programs I may make a full switch. Right now ubuntu does not have *all *of the necessary tools for a graphic designer; atleast in comparison to what is on the other platforms.

---

### Post by m4xr8d on 2007-02-09
Photoshop CS2 will run under wine. While it does take a little longer to load than in Windows it still runs. Once up and running you shouldn't notice much difference.

Nice tutorial

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

---

### Post by Shay Stephens on 2007-02-09
> **m4xr8d said:**
> Photoshop CS2 will run under wine. While it does take a little longer to load than in Windows it still runs. Once up and running you shouldn't notice much difference.

Nice tutorial

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

Are you saying that based on experience?  Do you have PS CS2 running in wine on your computer?

---

### Post by Brunellus on 2007-02-09
the short answer is:  probably not.

There are ways of making Windows software work.  They are not perfect.  They often don't work as well as advertised.  Do not rely on assurances that WINE will solve all your problems.  It will not. 

There are, however, excellent programs available in Linux.  Some you might already be using in Windows--Firefox, Thunderbird, Doom 3, Quake 4.  Others are alternative programs:  Evolution for Outlook, OpenOffice for MS Office, Gimp for Photoshop.  Some are clearly superior to their Windows equivalents.  

Bottom line:  it's a different OS.  Software is more likely NOT to run than to run properly.  Identify the programs you cannot live without, and then ask specific questions about whether you can migrate to new programs or run your old programs via a compatibility layer (WINE) or virtual machine (VMware) or, as a last resort, dual-booting.

---

### Post by m4xr8d on 2007-02-09
technically i do not have CS2 running on an ubuntu install, but i do have it running on a Zenwalk install. 

i used the above link as a guide. the guide did not work on CS but it worked for the most part on CS2. the only part that i didn't need to do was *recode ucs-2..ascii adobe.reg* and i use the generated menu item(after wineboot) to start CS2. wine version is 9.22

the place that i worked at used CS2. at home i use Gimp, but it is nice to have the option to use CS2 at home

---

