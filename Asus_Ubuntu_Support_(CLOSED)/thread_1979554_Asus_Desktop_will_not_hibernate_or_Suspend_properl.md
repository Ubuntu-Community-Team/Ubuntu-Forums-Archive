---
title: "Asus Desktop will not hibernate or Suspend properly"
date: 2012-05-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by wgregori on 2012-05-13
I recently upgraded from 11.10 to 12.04 and now my system will not successfully hibernate or suspend.  When i try to either hibernate or suspend the system goes through the processes and shuts down momentarily and  then immediately restarts and as if it has come out of a successful suspend or hibernate event.  

I've read most of the threads but nothing seems to help my problem.

thanks for any help.  Love Ubuntu!

Wayne

---

### Post by Mr.Plex on 2012-05-14
How big is your swap partition? have you tried this URL's solution's? 

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

### Post by wgregori on 2012-05-18
Thanks for the note Mr. Plex but none of those solutions worked.  I increased my swap drive rom 3 to 10 gigs... added the suggested script but it still wakes up immediately after a suspend or hibernate.... very frustrating.

---

### Post by dinutu on 2012-05-31
> **wgregori said:**
> Thanks for the note Mr. Plex but none of those solutions worked.  I increased my swap drive rom 3 to 10 gigs... added the suggested script but it still wakes up immediately after a suspend or hibernate.... very frustrating.

Strange, that script worked perfectly for my AsusUX31e, i am sure you have checked what are the actions for closing the lid? check it once again, just in case you have missed it. I had one similar issue on my old Fujitsu laptop and it came out that it was a physical issue, when i was closing the lid, the button that it was pressing to suspend it was not working properly and it was being activating and inactivating very often, that was causing errors on wake-ups. Maybe it worth forcing the lid a bit when closing it? This is all what comes out for now.

---

### Post by MauVar on 2012-06-14
I have the same suspend problem with ASUS U6V and Ubuntu 12.04. 
I tried to use some scripts relate to the suspend bug. However these did not resolve. 
With the 11.10 release I was using Nvidia drivers and suspend/resume functionality were working,  however I needed to reconfigure the display every time I worked with one or two monitors.

The details of my problem are the following

Notebook: ASUS U6V
Cpu: Intel Core 2 Duo Processor P8600, 2.40 GHz 
Display: 12.1" WXGA Resolution 1280x800, LED backlight
Video Graphics & Memory: NVIDIA GeForce 9400M GS
External monitor (1680x1050) connected to HDMI interface

Ubuntu 12.04, 64, kernel 3.2.0-25
graphic drivers: Gallium 0.4 on NV98
display configuration: dual view
power management configuration: lid closed => suspend

At startup the two display are correctly managed and all is working OK.

-pressing "Fn+Space Bar"
   external monitor backlight goes off (black screen)
   lcd display becomes dark grey (backlight is on)
   pressing again "Fn+Space Bar" all monitors go on, all OK.

-Fn+F7 (LCD Icon) correctly toggles the display panel ON and OFF. However external monitor
          resolution is changed when lcd off and dual view configuration is changed 
          when lcd "on" (external on the right instead the original external on the top)

- Fn+F8 (LCD/Monitor Icon) should toggle between the Notebook PC’s LCD display and an
external monitor in the sequence: Notebook PC LCD -> External Monitor -> Both. 
However it toggles beetwen dual view and mirror view and every time dual view configuration is changed (external monitor on the right)

- closing the lid
    external monitor goes off
    lcd becomes dark grey
    no suspend action is performed (hard disk is working)
    - opening the lid
      external monitor remains off
      lcd dislpsy remains dark grey
      the system hangs, every action does not restore the desktop,
      It needs to hold the power button over 4 seconds and reboot.

- Fn+F1 (suspend to RAM) correctly  suspend the system. 
    However pressing a key, to resume, only LCD display goes on, 
    The external monitor backlight remains off. 
    The lcd display is white however blind digiting my password desktop appears.
    The system correcly see the external monitor but any action I perform
    does not activate the external monitor.


Thanks for any suggestions

---

