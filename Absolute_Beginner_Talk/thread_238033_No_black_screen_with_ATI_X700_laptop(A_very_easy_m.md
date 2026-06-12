---
title: "No black screen with ATI X700 laptop(A very easy method)"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by kejinlu on 2006-08-17
First,I don't know was it the right place where I post!


Many guys may encounter this situation:
When you start getting into Gnome(or other WM)
It just becomes black sceen,and if you click your mouse,the hard disk has a reflection of your action!
Some people suggest to use a second Monitor to solve the problem!
But I found someone has another method,just enter ctrl+alt+f1 get into text mode
then:

> sudo nano /etc/X11/xorg.conf 

Find the "Device"
just add 

> Option "MonitorLayout" "LVDS, AUTO"
 
after the line which contains the "ati" word!
then save changes!

Now you should

> 
sudo killall gdm
sudo gdm


and the problem will be solved!

I myself also have the doubt about the method!
What does > Option "MonitorLayout" "LVDS, AUTO"mean!
And why it can solve the problem?

Thanks in advance!

---

