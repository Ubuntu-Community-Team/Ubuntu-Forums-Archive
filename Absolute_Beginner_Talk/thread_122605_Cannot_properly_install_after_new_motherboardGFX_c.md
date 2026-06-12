---
title: "Cannot properly install after new motherboard/GFX card..."
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by xelink on 2006-01-28
!FIXED!


I had been using ubuntu fine for a while with no important issues whatsoever. I however decided I wanted a better graphics card(I went from a radeon 9250 to a Geforce7800GT) and I swapped it and the motherboard to install it. my PSU is fine, and I can run windows XP pro fine no issues, playing everygame I run accross at maxed out settings. unfortunately, ubuntu simply does not want to start. I get "2d artifacting"
[http://img7.imageshack.us/img7/7985/wtf6ii.jpg](http://img7.imageshack.us/img7/7985/wtf6ii.jpg) (please note that the dark spot on the screen is only visable to a camera it is clear to the eye)

I tried installing multiple times and I even tried using my boards onboard video to install ubuntu(had an issue with xserver) but to no avail.

here is my basic hardware setup

s754 Athlon 64 3000+
512mb DDr Ram(soon to be swapped to 2GB)
7800GT [http://www.newegg.com/Product/Product.asp?Item=N82E16814130256](http://www.newegg.com/Product/Product.asp?Item=N82E16814130256)
MSI motherboard
[http://www.newegg.com/Product/Product.asp?Item=N82E16813130534](http://www.newegg.com/Product/Product.asp?Item=N82E16813130534)

---

### Post by bscbrit on 2006-01-28
Don't worry about the dark line. Both your display and the camera's CCD are using a scan pattern.  At any specific time some of your display pixels are switched off and when you take a picture the camera scans the scene in rows.  What you can see is simply where the camera is scanning the pixels that are not illuminated.  Your eye does all the corrections necessary but your camera can only record the light that it sees at any given instant.

This can be explained in a more scientifically correct way, but I hope this simple explanation helps.  The black line is not linked to your fault in any way.

I'm sorry that I cannot help on the main problem with installing your graphics card.

---

### Post by xelink on 2006-01-28
yeah I knew that... I should have explained it more clearly... the darkline as you said is just because the screen is constantly refreshing and I didn't se the camera exposure long enough.

but my problem is that whenever I try to do much of anything i more or less get a I said 2d artifacting and the system locks up.

---

### Post by bscbrit on 2006-01-28
From the information that you have provided, it looks like you are using incorrect drivers.  When you upgraded the graphics card, I'll bet you used the nice new CD to update windows so that it could make the most of the card.  But you have gone from an ATI card to NVIDIA (which, of course, you already know).  Have you changed the Ubuntu drivers for your card and, if so, what to?  Did the install go as you expected without error messages?

---

### Post by xelink on 2006-01-28
I did a fresh install of both OS-es though, so driver incompatability would not be an issue. Swapping a motherboard(especially if you are changing chipsets as I did) warants a fresh install about 90% of the time.

---

### Post by xelink on 2006-01-28
well, I am officially lost... seriously any advice, anything I can eliminate?

---

### Post by bscbrit on 2006-01-28
Well, if everything apart from the display is working fine, then I would suggest you revisit your drivers.  Or am I misunderstanding the problem?  You have complained about 2d artifacts or are you suggesting that you cannot even get past the log-in screen?

And I cannot even guess what you mean by > and I even tried using my boards onboard video to install ubuntu.

Can you explain what the problem is that you are experiencing - just for those dimwits such as myself who do not understand...:D

---

### Post by xelink on 2006-01-28
well, I simply cannot get ubuntu to go past the point where you are asked to log in. I can enter my username and password and then it more orless freezes up and looks artifacted. the same happens if I don't login but try to right click one of the little things on the bottom. it just freezes.

---

### Post by codejunkie on 2006-01-28
you haven't installed the official nvidia driver yet, just a guess try dropping to a console  by pressing ctrl+alt+F1 and edit the /etc/X11/xorg.conf file by running ```
sudo dpkg-reconfigure xserver-xorg
``` and change the driver to "vesa" you can just press enter to the rest of the questions to accept the default values on the rest of the configuration then restart the xserver with 
sudo /etc/init.d/gdm/restart this shoud make the gui usable enough to install the nvidia driver from [www.nvidia.com](www.nvidia.com) here's a good guide on that
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) hope this helps and let me know how this works.

---

### Post by xelink on 2006-01-28
I will try that, hopefully it shall work. WHy didn't I have to do this with my ATi card in the past though? I mean I did to get FGLX gears working but that was about it.

also, for future reference, how do you start up in terminal? recovery mode?

EDIT: apparently setting it to vesa fixed it. I thank you very much.

---

### Post by codejunkie on 2006-01-29
[QUOTE=xelink]I will try that, hopefully it shall work. WHy didn't I have to do this with my ATi card in the past though? I mean I did to get FGLX gears working but that was about it.

also, for future reference, how do you start up in terminal? recovery mode?

EDIT: apparently setting it to vesa fixed it. I thank you very much.[/QUOTE]
just a guess but the reason you didn't have to do this with your ati card is it's older hardware so the native support under linux is better also the default ubuntu install sets nvidia cards to use the nv drivers and the nv driver doesn't fully support the newer 7800 cards.

to start up in recovery mode at the grub menu choose the option that has (recovery mode) beside it. if you only have ubuntu installed you won't see the grub menu you'll see a little counter in the top left hand corner of the screen just press ESC before it gets to zero and then the grub menu will show up hope this helps.

---

### Post by xelink on 2006-02-04
thanks for the advise code junkie. I got the graphics working fine through doing exactly what you said, though I did it before you posted. Wouldn't have had thought about the driver aspect with the 7800GT being too new, thought it ran offf the same drivers as the 6 series and what not.

---

