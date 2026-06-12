---
title: "Ubuntu Splash hangs after login"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by g1gabyt3 on 2007-01-08
This might be an easy fix that I just can't figure out, but when I log into Gnome with Beryl, the little splash scrren that Ubuntu puts up hangs for about 2 mins until it finally dissapears.  All Applications run as soon as I log in, just the rectangular window stays.  It's a mild annoyance, but annoying all the same.  If I log into Gnome without beryl booting with it, everything loads fine and the splash screen goes away within a few seconds.

Thanks in advance.

---

### Post by Waappu on 2007-01-08
Hi
Could you post guides you followed to install Beryl and what video card you have?

---

### Post by g1gabyt3 on 2007-01-09
sure can, I followed the instructions from the Beryl Wiki found at 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

and as for my video card, it's an ATI Radeon IGP 345M.  I'm on a laptop, not a desktop.  If you need the model number of my laptop, it a HP model ze5731us.

Thanks again.

---

### Post by sardion on 2007-01-09
> **g1gabyt3 said:**
> sure can, I followed the instructions from the Beryl Wiki found at 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

and as for my video card, it's an ATI Radeon IGP 345M.  I'm on a laptop, not a desktop.  If you need the model number of my laptop, it a HP model ze5731us.

Thanks again.


That site says: 
"Please note: ATI Cards : Depending on your card you may find that you can use the ati/radeon driver with AIGLX. If you experience problems then you may need to use Xgl with the fglrx Driver."

I have always found that ATI cards are much happier using XGL that AIGLX.  Try installing XGL (there are guides everywhere on how to).

---

### Post by Waappu on 2007-01-09
> **sardion said:**
> I have always found that ATI cards are much happier using XGL that AIGLX.  Try installing XGL (there are guides everywhere on how to).
I don't want to start arguing but my opinion is oposite =) Personaly I didn't get XGL workin and AiGLX worked perfect right away.
Here is link howto setup open source ati/radeon driver for AiGLX. Try it and in case no luck then XGL might be good option. I used same guide that you already have for Beryl and this for ATI drivers.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Waappu on 2007-01-09
Hi

Did you created separated session for Beryl as guide say? That isn't needed necessary. You can login gnome and type in terminal ```
beryl-manager
``` if it works ok then you can add beryl to start up applications

---

### Post by rfdeshon on 2007-01-19
I have this same problem. I don't want beryl to run automatically. I had it set like that for a while but I don't always want to use beryl since I am on a laptop and I like running things as simple as possible when I am not plugged in. I also do not want to have to launch it myself every time. Setting it up as a session works and seems like it would be the logical way to set beryl up, it's just one little problem that should really be fixed. PS - I'm running it on an Intel 915GM so it is not an ATI problem.

---

### Post by mcduck on 2007-01-19
I remember that the problem with splash image was caused by having 'splash' included in some plugin, probably 'fade'. Try removing 'splash' from all animations and effect plugins..

---

### Post by rfdeshon on 2007-01-22
Hate to sound like a noob but it's late and my mind is not functioning well... How do your remove splash from the plugins?

---

### Post by RobertoIsRad on 2007-02-03
If you haven't figured it out yet there's a good step by step guide for this at [http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl#Gnome_splash_hangs_when_using_Beryl](http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl#Gnome_splash_hangs_when_using_Beryl)
Just make sure to follow all of the directions and not just skip to the terminal command like I did... This works for me

---

