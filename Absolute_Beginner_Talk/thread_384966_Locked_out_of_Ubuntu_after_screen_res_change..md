---
title: "Locked out of Ubuntu after screen res change."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by rogersausages on 2007-03-15
Upon my very first install of Ubuntu Dapper Drake.......

After fooling with my desktop resolution, in an unsuccessful effort to get it to 1920x1200 for my dell 24" widescreen, I decided to change the resolution to 1024 by 768.  As soon as I did I got an error message saying the monitor could not display this (why I am unsure).  

Since I was stuck with the error message, I did a hard reboot with the button on my pc.  Now whenever it boots up I just get a flashing prompt for login.  After I do, I get a very generic looking error screen with something about an xserver error with only  YES or NO as an option to view.  If I hit Yes It asks me if I want to look at more Xserverfile stuff and then I get taken back to a (dos-like) prompt.  

Any thoughts on how I can rectify this situation and get back to my original desktop.  

Sorry if this is not very specific.  If you need more info let me know and I will go through the setup and write down specifically what I see and then report it.  

Thanks,
RogerSausages

---

### Post by arochester on 2007-03-15
Go to the (dos-like) prompt. Input > sudo dpkg-reconfigure xserver-xorgThis will open a text-based wizard which will let you reconfigure the xserver. Answer the questions you can. If there any you can't answer then go with the default suggestion. If at first it doesn't succeed then try again. If nothing seems to work then choose VESA as the most basic option. This should bring back graphics. If you had a specific graphics card installed you will probably have to install it again.

---

### Post by rogersausages on 2007-03-16
Thanks arochester, it took some doing but it worked like a charm!

---

