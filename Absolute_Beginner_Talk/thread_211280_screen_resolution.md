---
title: "screen resolution"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by kigina on 2006-07-08
the highest ubuntu will let me set my screen resolution to is 1280 x 1024.  my monitors max is 1600 x 1200.  how do i set it higher.

---

### Post by bigken on 2006-07-08
open a console and type sudo dpkg-reconfigure xserver-xorg use the space bar to select your screen sizes ;)

---

### Post by DSn0wMan on 2006-07-08
press CTRL+ALT+F1

Then login

From the terminal try this ```
sudo dpkg-reconfigure xserver-xorg 
```

This will start a wizzard to configure your xserver, including and option to select higher screen resolutions. I am positive that 1600x1200 is in there.

---

### Post by kigina on 2006-07-08
woo hoo! now it boots to a black blank screen.

---

### Post by skull_leader on 2006-07-08
You can try entering the desired settings into [http://www.dkfz.de/spec/linux/modeline/](http://www.dkfz.de/spec/linux/modeline/) 

Then copying and pasting the bottom line in xorg.conf. I'd reccomend doing a search on "modeline" in these forums first, though.

---

### Post by kigina on 2006-07-08
> **skull_leader said:**
> You can try entering the desired settings into [http://www.dkfz.de/spec/linux/modeline/](http://www.dkfz.de/spec/linux/modeline/) 

Then copying and pasting the bottom line in xorg.conf. I'd reccomend doing a search on "modeline" in these forums first, though.

I can even see anything.  I have to boot to windows.
Here is a drawing of what it boots to.

[IMG]http://img86.imageshack.us/img86/5959/newbitmapimage4df.png[/IMG]

---

### Post by kigina on 2006-07-08
I really need help on this on.

---

### Post by kigina on 2006-07-08
bump

---

### Post by kigina on 2006-07-08
help me!

---

### Post by tturrisi on 2006-07-08
> **DSn0wMan said:**
> press CTRL+ALT+F1

Then login

From the terminal try this ```
sudo dpkg-reconfigure xserver-xorg 
```

This will start a wizzard to configure your xserver, including and option to select higher screen resolutions. I am positive that 1600x1200 is in there.
boot to the black screen and repeat the above and select the resolutions to be made available but set the default resolution to a smaller size.  Then when booted into the desktop go to Preferences > Screen Resolution > and make note of the refresh rate.  Then try changing the resolution to the larger size you want and keep the same refresh rate.  If no joy then repeat the reconfigure xorg again and eliminate the large resolution & live w/ it.

---

### Post by jonrkc on 2006-07-08
It's probably a refresh-rate problem.  I had the same thing happen and it mystified me for a long time till I finally found an answer after about five hours of Google searching and mainly useless searching of various Linux forums.  

Your user's manual for the monitor will tell the correct rate.  If you've lost or misplaced the manual, it will be available online somewhere, most likely on the manufacturer's website.  I downloaded the spec sheet on my monitor to keep it handy for reference in the future!

---

### Post by Spleenie on 2006-07-08
I do think the picture of a blank screen was a good touch though.

In /etc/X11/xorg.conf ensure the following are correct

a) Your video card parameters. Has it detected your card correctly.

b) Your monitor has been correctly detected. Even if it has, double check the vertical refresh and horizontal sync values to the manufacturer specs. You may have to google for these, unless you know them

c) check the resolutions available next to your default bitdepth. Try lowering the default depth and adjusting the resolutions next to your default depth using the given format "1600x1200" etc.

Always make a backup of your xorg.conf file whenever you muck with it:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_working
```

or somesuch.

When in console mode, (you are in console mode if you typed ctrl-alt-F1)after checking and adjusting your xorg.conf file, type 

```
startx
```

and make a note of any errors (if any). These will be helpful in assisting you.

Tally ho.

---

### Post by kigina on 2006-07-08
i love you guys.  i am now writing to you from ubuntu.  thanks.

---

### Post by Spleenie on 2006-07-08
And I love you too

Love all around!

---

### Post by kigina on 2006-07-08
when looking for my manual i found about 5 dollars in change

and for some reason im hearing gunshots outside

---

