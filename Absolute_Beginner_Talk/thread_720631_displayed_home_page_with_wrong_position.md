---
title: "displayed home page with wrong position"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Garavan on 2008-03-10
More precisely I only see the bottom part of the first screen, which is the standard, not modified ubuntu GG home page.

I increased the resolution of my display - Asus MW221U.
It should operate at 1680 x 1050 resolution by 60 Hy VESA. The display type is WSXGA+.
My MoBo came with a built-in graphic card, a  nVIDIA®GeForce 6100/nForce 430.

I tried to change the OSD settings, reset and position settings. None of them solved the positioning issue.
I find out, that I could access the system via Function key, so there I changed the Screen Resolution under Preferences to the above mentioned values. I also tried to fix the issue by going to Screens and Graphics, where
ASUS is not listed under the Manufacturer tab, so I selected Generic
and under Choose Screen LCD Panel 1680 x 1050 and I also checked the Widescreen monitor option and clicked OK.

Under Graphic Cards I selected nVIDIA with Geforce 6 series.

However, none of the following solved the problem. What a waste of time. Anyone has an idea what to do?

---

### Post by dokdoom on 2008-03-10
I am very jealous, NVIDIA support rocks. First make sure you are using the driver fromt he restricted drivers manager. After that I think there is a GUI for everything else. with that driver installed on the command line type nvidia- then hit the Tab key twice. I believe you want nvidia-config but there might be another optin you'll have to look.

---

### Post by Garavan on 2008-03-11
dokdoom, thanks for your reply.

I figured out, what you mean under restricted drivers, run nvidia from there. Then I get to the terminal window and entered nvidia- tab tab

it wrote back: 
nvidia-bug-report.sh
nvidia-settings
nvidia-glx-config
nvidia-xconfig

I then tried nvidia-settings, but it had not changed the display. 
I've no idea what to do next. Anyway, I went out and bought a book about ubuntu to learn the basics at least. Although, it would be nice to see the whole screen again with the places and all other info on the menu bar. Can you or someone help me to set at least the Display up?

I'll restart the system, maybe that would bring up the whole screen. However, I do post this first.

---

