---
title: "Screen Resolution Issues on PowerBook G4"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by akrodha on 2005-04-10
I've spent some time on IRC trying to get this fixed, and some progress has been made.

My screen has a native resolution of 1152x768. I can change my resolution to a million different settings, except for 1152x768. The only ones that come close are:

1024x768 (entire screen visible, but distorted)
1280x768 (not distorted, but screen truncates to leave out the 128 columns on the right)

I've got a PowerBook G4 Titanium, and the graphics card is an ATI Radeon 9000 (I believe). Any suggestions would be greatly appreciated.

---

### Post by erkki70 on 2005-04-11
Hi,
Have you tried to reconfigure your X server?
```
sudo dpkg-reconfigure xserver-xorg
```
Hope this helps,
Cheers,
Erkki

---

### Post by akrodha on 2005-04-11
Whee! It's finally fixed, and your idea helped.

I had to choose the 55 kHz option, and after I reconfigured X like you suggested, I needed to add a few lines in xorg.conf

Thanks!

---

### Post by babasofa on 2006-11-27
Very helpful thread. Put Edgy on my old 667 G4 T-Book and was only getting 800x600.

Ran: the dpkg=reconfig and life & my screen are happy!:mrgreen:

1152x768 is a beautiful thing after a week of 800x600...](*,)


Many many thanks, --baba

---

### Post by esswords on 2007-01-05
I am very new to Linux, so please excuse me if this question is ridiculously basic.

I am trying to install Ubuntu on my tiBook 400mhz (ATI Rage Mobility 128 graphics) and I have this same 800x600 problem. I would like to try the fix described in this thread, but I really need more detailed instructions as to how to do it. How do you reconfigure the X Server? What is dpkg=reconfig? Is there a (beginner-friendly) resource out there that will tell me what these things are and how to work with them?

If someone could post more detailed instructions or point me in the right direction I would really appreciate it.

Thanks.

---

### Post by esswords on 2007-01-06
nevermind. I figured it out. For those who are in the same spot as me:

1. Open a terminal window

2. type "sudo dpkg-reconfigure xserver-xorg" without the quotation marks

3. go through each option just pressing OK until you get to the monitor resolution list. When you get there select the space next to the resolution you need and press space bar to put a little star in it. 

4. Finish going through the options until the end

5. Restart.

It seems silly that the hardest part was figuring out I had to press space bar to select the resolution. :)

---

