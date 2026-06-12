---
title: "Using windows fonts in ubuntu"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-21
Hi, I am currently running the new version of Ubuntu: 7.04. I want to use the fonts from my windows partition with Ubuntu. I tried the tutorial at this page: [http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html](http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html)

using method 3 to install the fonts system wide. However, when I got to the step to execute the command: mkfontdir, nothing happened!

Can someone tell me how to fix this and carry on to the next step?

---

### Post by peebly on 2007-04-21
search for msttcorefonts in synaptic.

---

### Post by the8thstar on 2007-04-21
Assuming that you can access your Windows partition while running Ubuntu, all your need to do is go to your c:\Windows\Fonts folder and select the fonts you like (CTRL+C) and then go back to your Ubuntu partition and into the Fonts folder, and paste the fonts (CTRL+V) within.

That's how I did it and it worked flawlessly.

---

### Post by noorez on 2007-04-21
ohh....It works.....I forgot to check if the fonts were already working.
Thanks for the help!

---

### Post by the8thstar on 2007-04-21
I'm glad we could help. :)

---

### Post by p3_Arme on 2007-04-22
Sorry to push in, but it's a similar question. I have a FONTS cd which I'd like to put onto my Linux, (just a few not all of them) any idea on how I can do this. They are .ttf fonts.

I'm running Xubuntu 6.10.

Thanks

---

### Post by noorez on 2007-04-22
Try doing what I did... You just need to find the location of the .ttf font files and copy the fonts from your cd into there. Then logout and login again and you should be able to use the fonts. I've never used Xubuntu but I would think they would work in a similar manner?

---

### Post by p3_Arme on 2007-04-23
okay thanks I'll try that and get back to you :)

---

