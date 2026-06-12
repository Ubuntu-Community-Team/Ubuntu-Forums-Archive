---
title: "Help for coping at 800x600?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ZorMonkey on 2007-06-07
So, I decided to try out Ubuntu on my crummier computer. Problem is, my monitor is so crummy that it only works up to 800x600. Using XP, 800x600 has been fine, since I only really use the computer for surfing the net and reading emails. But so far in Ubuntu it's nearly unusable...

- I tried both Evolution and Thunderbird for email. I use Thunderbird in XP, and it's fine. In Ubuntu, I was only able to see maybe 5 lines of email in the preview window for both programs. I could have made it show more, but at the expense of showing less of the email list.

- Many windows dont quite fit into 800x600, so I have to manually move them around to see everything. It's crazy how many configuration windows I've seen that cannot be resized, and have "Ok" button just off the bottom of the screen. One easy example - the installer. I have to hide the top and bottom toolbars to be able to see part of the bottom buttons. Evolution's minimum width is about 810, so it was freaking out when I tried to maximize it.

- Not quite related, but the startup and shutdwn screens are convinced that my monitor can do higher resolution, like maybe 1024x768. That's pretty annoying, but who cares.

So, what can I do to make Ubuntu more bearable? One thing I noticed is that the fonts are BIG. They didnt really seem so big while in Ubuntu, but once I switched back to XP it was apparent that the font size doesnt help at all. But, I couldnt find anywhere to change the overall font size.

---

### Post by kerry_s on 2007-06-07
try changing your dpi to make all the fonts smaller, that should then help the applications display right. if that works then you should be able to resize the windows smaller then click on the maximize button to adjust them to the 800x600 size, they should then open to that size max.

gedit ~/.Xdefaults

Xft.dpi: 75

you'll most likely need to go lower than that.

---

### Post by w4ett on 2007-06-08
When you select System>Preferences>Screen Resolution is 800x600 the only resolution available on the list?

---

### Post by ZorMonkey on 2007-06-08
kerry_s: Thanks, that did the trick, mostly. I dont have an .Xdefaults file in my home directory, but I was able to set the dpi using the font system preferences tool. Now I just need to convince Firefox to use that setting...

w4ett: No, I also have 1024x768 and 640x480 also. But, 1024x768 doesnt work on my monitor. I could maybe get it to work by playing with refresh rates, but I'd rather not kill my monitor. So, I've actually edited xorg.conf to remove all traces of 1024x768.

---

### Post by w4ett on 2007-06-08
You can edit xorg.conf to list your required resoultions and refresh rates to better suit your monitor.   On the Screen Resolution tab under preferences you can also select your default resolution, after you add your desired resolutions in your edit.

you can edit by:   sudo gedit /etc/X11/xorg.conf        
  in the terminal

or you can select your resolution rates if you:  sudo dpkg-reconfigure x-server-xorg

leave the video  driver references as they are, just select your desired resolutions from the menu

---

### Post by w4ett on 2007-06-08
> **w4ett said:**
> You can edit xorg.conf to list your required resoultions and refresh rates to better suit your monitor.   On the Screen Resolution tab under preferences you can also select your default resolution, after you add your desired resolutions in your edit.

you can edit by:   sudo gedit /etc/X11/xorg.conf        
  in the terminal

or you can select your resolution rates if you:  sudo dpkg-reconfigure x-server-xorg

leave the video  driver references as they are, just select your desired resolutions from the menu

One thing I forgot to add.....BEFORE you change your resolutions and refresh rates...check your monitor  and video card documentation for the available settings....or get these off the manufacturers website.  We don't want to smoke a good monitor!  At the best, an unsupported res/refresh setting will give you an out of range alarm on your monitor and crash X...at worst...blue smoke can appear.

---

### Post by kerry_s on 2007-06-08
> **ZorMonkey said:**
> kerry_s: Thanks, that did the trick, mostly. I dont have an .Xdefaults file in my home directory, but I was able to set the dpi using the font system preferences tool. Now I just need to convince Firefox to use that setting...

w4ett: No, I also have 1024x768 and 640x480 also. But, 1024x768 doesnt work on my monitor. I could maybe get it to work by playing with refresh rates, but I'd rather not kill my monitor. So, I've actually edited xorg.conf to remove all traces of 1024x768.


You create the .Xdefaults file, it should take care of the firefox problem to, that is suppose to cover all X applications.

Are you sure your monitor doesn't do 1024x768, it might just need to have a lower default than 24. For instance on this laptop the highest is 16, but it will work with 800x600x24, to get the higher i have to use 1024x768x16 to make it work other wise i just get a funny screen of colors.

Can you provide your monitor and video card info, so we can look up the settings and better help you. thanks.

---

### Post by stchman on 2007-06-08
> **ZorMonkey said:**
> So, I decided to try out Ubuntu on my crummier computer. Problem is, my monitor is so crummy that it only works up to 800x600. Using XP, 800x600 has been fine, since I only really use the computer for surfing the net and reading emails. But so far in Ubuntu it's nearly unusable...

- I tried both Evolution and Thunderbird for email. I use Thunderbird in XP, and it's fine. In Ubuntu, I was only able to see maybe 5 lines of email in the preview window for both programs. I could have made it show more, but at the expense of showing less of the email list.

- Many windows dont quite fit into 800x600, so I have to manually move them around to see everything. It's crazy how many configuration windows I've seen that cannot be resized, and have "Ok" button just off the bottom of the screen. One easy example - the installer. I have to hide the top and bottom toolbars to be able to see part of the bottom buttons. Evolution's minimum width is about 810, so it was freaking out when I tried to maximize it.

- Not quite related, but the startup and shutdwn screens are convinced that my monitor can do higher resolution, like maybe 1024x768. That's pretty annoying, but who cares.

So, what can I do to make Ubuntu more bearable? One thing I noticed is that the fonts are BIG. They didnt really seem so big while in Ubuntu, but once I switched back to XP it was apparent that the font size doesnt help at all. But, I couldnt find anywhere to change the overall font size.

That must be one old @$$ monitor.  Even el-cheapos support 1280x1024.  19" CRT monitors are pretty cheap these days, maybe you can invest in one.  You could probably get a used 19" for arouns $40 at a computer store.

---

### Post by ZorMonkey on 2007-06-10
Yes,it is pretty old. It probably is supposed to support 1024x768, but it doesnt. It will display something, but split into vertical bands. So, I could probably mess with refresh rates and coax it into displaying 1024x768 properly, but I've used it for years at 800x600, so I dont feel the need to mess with it. Even if I got it to display 1024x768, it'd probably be smushed to one side or something - the knobs that adjust that sort of thing arent totally effective anymore. It has lived through a flooded basement (it was on the floor), so I'm just happy it works. :)

I'm not completely insane. My "good" computer has an LCD monitor with a decent resolution. 

Anyways, my Firefox problems are mostly fixed. From digging around on the net, I've found that Firefox is riddled with dpi bugs in Linux. Some people were saying that dpi issues went away when they managed to enable "Pango", but I had no such luck. I ended up changing the default font size in Firefox from 16 to 13, which helped a lot - even though the site I was testing with doesnt use the default font. I was mostly testing with Slashdot.org, and once I got that mostly everything looked fine. But, after surfing around for a day or so, I clicked [this link]("http://www.extremetech.com/article2/0,1697,2142647,00.asp") on Slashdot, and found that the article text was microscopic. That was the only site, so I ignored it - until I went to fark.com, and all of the text was microscopic. The problem was that while I was testing Firefox I changed it's "layout.css.dpi" setting to various values, and the last value I set was something crazy: 7. That setting was only affecting a very small number of fonts, while it should have been affecting everything. Once I set it to something reasonable (0, to use the system's dpi) the microscopic fonts were fixed.

So in a nutshell, Firefox doesnt use your system's dpi for everything, but that's because it's buggy. Setting the default font size helps though. I tried Epiphany for a bit, and it rendered things fine.

---

