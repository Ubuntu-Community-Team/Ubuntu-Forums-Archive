---
title: "printer problems..."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by lost4now on 2007-08-07
When a page is sent to the printer it shows as A4. The driver is set for US Letter. Nothing I do seems to change anything. 

Dell 3110cn laser color
set up as linux network printer

Any suggestions would be appreciated.

---

### Post by Pragmatist on 2007-08-07
Does anything actually print wrong?  Mine says A4 too, but all my printing works perfectly.  When you say "Nothing I do", what have you done so far?  There are several approaches I can suggest, but first tell me what you have already tried.

---

### Post by lost4now on 2007-08-07
The printer just sits there showing the A4 in the window. It never prints. If it was going to print it will say LPD instead of A4

I have reloaded a driver for a M5200

tried converting a RPM driver from dell with alien and installed but it doesn't show up as a driver in printer config so can't use it.

Called Dell and was told if I dont have a service contract they cant or wont help

read till I think my eyes are bleeding.

About one more day and I'll have a new Dell 3100cn for sale - probably pretty cheap. NO MORE DELL CRAP FOR ME....

---

### Post by Pragmatist on 2007-08-07
I just did a small amount of reading so far, but it looks like several other people have gotten your printer to work on Ubuntu--so be hopeful, it should definitely work for you too!  I know how frustrating getting some hardware to work.  Sometimes the best thing, if you can, is just to put it aside for awhile until you can recover from the frustration.  Works for me anyway.

Have you read these?:
[http://ubuntuforums.org/showthread.php?t=181883&highlight=dell+3100cn](http://ubuntuforums.org/showthread.php?t=181883&highlight=dell+3100cn)
[http://ubuntuforums.org/showthread.php?t=283468](http://ubuntuforums.org/showthread.php?t=283468)

The reason I ask, is it is important to know what you have or haven't tried.  Apparently there is more than one driver you can try, and also it is important to pick the right printer when setting it up.

---

### Post by one_roland on 2007-08-15
Did this "A4" paper size problem ever get solved???

Well I installed four printer drivers: dl3100cn.ppd.gz, M5200, S2500, and Lexmark Optra-Color 1200. All were set to standard "letter size", but my 3100cn would say " Load Tray A4". I set my 3100cn to "A4" size and I was able to print. Of course this is not a solution.

I think this a problem with **UBUNTU**. The sofeware sends size "A4" The basic printer driver is flawed.  
:(

---

### Post by one_roland on 2007-08-15
A quick UPDATE as to the Dell 3100cn print driver.  My dl3100cn.ppd.gz driver works fine in the "letter" size in normal printing, but does have the "A4" problem **ONLY** when you "Print Test Page" in the "System>>Administration>>Printing" menu.

---

### Post by freebeer on 2007-08-15
I ran into this problem a while back, and the details are a little foggy.  I went into CUPS (assuming you're using CUPS) and set the paper to "letter" from "A4" in there.  At least that's what I remember doing.  HTH.

---

### Post by Pragmatist on 2007-08-15
> **one_roland said:**
> 
Well I installed four printer drivers: dl3100cn.ppd.gz, M5200, S2500, and Lexmark Optra-Color 1200. All were set to standard "letter size", but [COLOR=Black]my 3100cn would [SIZE=2]say[/SIZE] " Load Tray A4". I set my 3100cn to "A4" size and **I was able to print.**[/COLOR] Of course **this is not a solution**.
I'm sure I don't get it, but if it works, why is it not a solution?  When you say "all were set to..." are you referring to the drivers? You must mean the ppd file.  When you say the "3100cn would say 'load tray A4'", is there a display on the physical printer itself?  Have you tried configuring the printer with CUPS?  What do the settings in Open Office show?

> **one_roland said:**
>  I think this a [COLOR=Black]**problem with ****UBUNTU**.[/COLOR] The sofeware sends size "A4" [COLOR=Black]The basic **printer driver is flawed**.  [/COLOR]
:(

Ubuntu is a distribution of software and some default configurations and settings.  Ubuntu doesn't MAKE any drivers, so if they are flawed, you should file a bug report, and hopefully the writer of the driver will fix it.

---

### Post by one_roland on 2007-08-19
This is a recap of what I am using and have learned about my Dell 3100cn printer. I loaded four drivers:dl3100cn.ppd, M5200, S2500, and Lexmark Optra-Color 1200 into UBUNTU. All the drivers will not work when set up for 8.5" x 11" paper and when you "Print Test Page" in the "System>>Administration>>Printing" menu. The result message on the Dell 3100cn printer is  "Load Tray A4". Outside of "System>>Administration>>Printing" menu all the drivers work except M5200, which has the same "Load Tray A4" message.

A note about using "A4" as a setting with 8.5" x 11" paper: There is a margin problem and the documents are printed with margin errors.  Unacceptable for me.

I am using the dl3100cn.ppd driver which provides me a more complete setup menu.

I do not know who developed the drivers, if all four have the same problem, then they have same core??? 

I will try to forward this to the bug group.

---

