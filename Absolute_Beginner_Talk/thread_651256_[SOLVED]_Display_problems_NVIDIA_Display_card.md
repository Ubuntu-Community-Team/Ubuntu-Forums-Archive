---
title: "[SOLVED] Display problems NVIDIA Display card"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by JohnPta on 2007-12-27
I upgraded from version 6 to 7.10. 

I have under restricted drivers a driver for: NVIDIA accelerated graphics driver (latest cards) (enabled)

I created 8 workspaces. I like to have in many workspaces "fire fox" and "open office word processor" or "Open office spreadsheets" open so that I can jump forward and/or backwards. But when I open more that two times fire fox or/and word processor and/or spreadsheet the pulldown menu's stay black although when you click somewhere in the pull down window there is still a link. 
When I open one "fire fox/open office word processor/spreadsheet" more the whole windows stays black. Although the pull down menu still works you see e.g. New file, open file etc on a black window. when you click on that the screen turns back to black again. 
How can I solve that problem?

The system was working OK under that "old" 6 ubuntu version Which I upgraded last night to 7.10

---

### Post by overdrank on 2007-12-27
> **JohnPta said:**
> I upgraded from version 6 to 7.10. 

I have under restricted drivers a driver for: NVIDIA accelerated graphics driver (latest cards) (enabled)

I created 8 workspaces. I like to have in many workspaces "fire fox" and "open office word processor" or "Open office spreadsheets" open so that I can jump forward and/or backwards. But when I open more that two times fire fox or/and word processor and/or spreadsheet the pulldown menu's stay black although when you click somewhere in the pull down window there is still a link. 
When I open one "fire fox/open office word processor/spreadsheet" more the whole windows stays black. Although the pull down menu still works you see e.g. New file, open file etc on a black window. when you click on that the screen turns back to black again. 
How can I solve that problem?

The system was working OK under that "old" 6 ubuntu version Which I upgraded last night to 7.10

Hi and what is the model of the graphics card and are you using compiz?

---

### Post by JohnPta on 2007-12-27
It is a Epox motherboard EP-MGF6100-M/g According to the manual the display is a NVIDIA GeForce 6100. Under this block I see an other block with NVIDIA nForce 430/nForce 410. I have that information from the System block Diagram in the manual. I hope this will help.

---

### Post by kregg on 2007-12-27
Have you tried going to System>Preferences>Appearance, and then going to the "Visual Effects" tab and selecting either "Normal" or "None"?

And, as last resort, have you tried installing drivers using [Envy](http://albertomilone.com/nvidia_scripts1.html)?

---

### Post by overdrank on 2007-12-27
> **JohnPta said:**
> It is a Epox motherboard EP-MGF6100-M/g According to the manual the display is a NVIDIA GeForce 6100. Under this block I see an other block with NVIDIA nForce 430/nForce 410. I have that information from the System block Diagram in the manual. I hope this will help.

Ok so it is onboard graphics, have you checked how much memory is being shared or dedicated to the graphics? Also how much memory does the system have?

---

### Post by JohnPta on 2007-12-27
Yes I tried to find the amount of memory used for the display on the motherboard in the CMOS but I did not see anything. But I will look again. I also had a gut feel that that could be a solution. I have 1 (one) Gb RAM in the box I will put one Gb more in the machine because the Swap memory on the HD is sometimes used for 50 to 60%. In the meantime I have put the display "Visual effects" back to normal and that works. Thanks.

---

### Post by JohnPta on 2007-12-27
I did increase the display memory to 128M and now everything works OK. I have also put the visual effect from NONE back to NORMAL  and opened 7*(fire fox) and the word processor + the spreadsheet and everything is visual. 
Thanks for the help

---

### Post by overdrank on 2007-12-27
> **JohnPta said:**
> I did increase the display memory to 128M and now everything works OK. I have also put the visual effect from NONE back to NORMAL  and opened 7*(fire fox) and the word processor + the spreadsheet and everything is visual. 
Thanks for the help

Great and can you mark the thread as solved by using the thread tools. Good luck!

---

