---
title: "Ati Radeon Mobility Drivers"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by dwessell on 2005-11-25
Hey all..

I have a Compaq Presario 2100 laptop, with a Radeon Mobility graphics card.. Do I need to install the standard ATI drivers using the instructions in the guides? Or would the Mobility take it's own set of drivers?

Thanks
David

---

### Post by KingBahamut on 2005-11-25
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

Im not sure if those instructions vary in any way referencing the Mobility drivers.

---

### Post by dwessell on 2005-11-27
Hey all..

Well unfortunately that crashed X..  And me being me, I didn't get the error message before trying to fix things.. 

How can I go back to the original drivers Ubuntu is using, after installing the new drivers? So I can get the error message, then revert back to workable drivers?

Thanks
David


[QUOTE=KingBahamut][http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

Im not sure if those instructions vary in any way referencing the Mobility drivers.[/QUOTE]

---

### Post by Darrin on 2005-11-27
Heres how I installed mine
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver)

Had no issues at all. Im using an ATI Radeon 9800 pro.

---

### Post by 23meg on 2005-11-27
[quote=dwessell]Hey all..

I have a Compaq Presario 2100 laptop, with a Radeon Mobility graphics card.. Do I need to install the standard ATI drivers using the instructions in the guides? Or would the Mobility take it's own set of drivers?

Thanks
David[/quote]You need to specify the exact model of your Radeon Mobility chip, since the fglrx drivers don't support some older models.

To back to the old driver, replace the word "radeon" with "ati" in the Device section of your xorg.conf file.

---

### Post by dwessell on 2005-11-27
Hey 23 Meg..

It is a Radeon Mobility U1...

Thanks 
David


[QUOTE=23meg]You need to specify the exact model of your Radeon Mobility chip, since the fglrx drivers don't support some older models.

To back to the old driver, replace the word "radeon" with "ati" in the Device section of your xorg.conf file.[/QUOTE]

---

### Post by 23meg on 2005-11-28
This is from the ATI website:

> **Q2: **[B]Which ATI graphics cards can use this driver? 
                        [/B]                                                                   **A2:**                                                  The ATI Proprietary Linux driver currently supports                           Radeon 8500 and later AGP or PCI Express graphics products,                           as well as FireGL 8700 and later products.  We do not                           currently plan to include support for any products                           earlier than this. Drivers for earlier                           products should already be available from the [DRI                           Project]("http://dri.sf.net/") or [Utah-GLX                         project]("http://utah-glx.sf.net/").

**[FONT=Verdana][COLOR=#000066][/COLOR][/FONT]**

> **[FONT=Verdana][COLOR=#000066]ATI Mobility&#8482; Product Support [/COLOR][/FONT] **

      [FONT=verdana][SIZE=2]The ATI Proprietary Linux driver is designed to support the following [FONT=verdana][SIZE=2]ATI[/SIZE][/FONT] Mobility&#8482; products:[/SIZE][/FONT] 
  [LIST]
[*] [FONT=verdana][SIZE=2]Mobility&#8482; Radeon&#174; X700[/SIZE][/FONT]
[*] [FONT=verdana][SIZE=2]Mobility&#8482; Radeon&#174; 9800[/SIZE][/FONT]
[*] [FONT=verdana][SIZE=2]Mobility&#8482; Radeon&#174; 9600[/SIZE][/FONT]
[*] [FONT=verdana][SIZE=2]Mobility&#8482; Radeon&#174; 9550[/SIZE][/FONT]
[*] [FONT=verdana][SIZE=2]Mobility&#8482; Radeon&#174; 9000[/SIZE][/FONT]
[*] [FONT=verdana][SIZE=2]Mobility&#8482; Radeon&#174; 9200[/SIZE][/FONT]
[*] [FONT=verdana][SIZE=2]Radeon&#174; Xpress 200M series[/SIZE][/FONT][/LIST]  **    **



**    **

---

