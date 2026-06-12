---
title: "[SOLVED] Need Help Making Application Work"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by chperry on 2008-04-07
I am completely new to Linux.  I am running x64 Gutsy.  I want to make the Slide Rule emulator from the following site work.
[http://www.finseth.com/realbasic/index-sliderule.php](http://www.finseth.com/realbasic/index-sliderule.php)

I know, slide rules are old.  Any ideas on how I make this work in Gutsy?

Thanks

Charles

---

### Post by spiderbatdad on 2008-04-07
Lets say you download the linux.zip to your desktop. Right click on the package and select extract here.
Open a terminal:

```
sudo apt-get install libstdc++5
cd Desktop/linux-sliderule
./SlideRule.L &
```
You may get an error dialogue. If you close it, the slide should open anyway.
Increase the size from the drop down arrow "picket 6" small"

---

### Post by Therion on 2008-04-08
I can get it to work... Sort of.  You're going to be disappointed, but here's what you need to do.  You have the .zip file, right?  

Copy or move it to your desktop, right-click on the file and then click on "Extract Here".  

You'll wind up with a new folder on your desktop: Linux-Sliderule.  

Open that folder, and double click on the "SlideRule.L" file.  

If you get an error message, just click on "Okay". 

The application will start.  

Enjoy.  

Further instructions, comments, etc. in the .html file if you care to read them.

---

### Post by chperry on 2008-04-08
I had already tried what you suggested with no luck.  I ended up having to create a separate directory under Slide_Rule called images-bmp.  I then copied all of the bmp files and the rulelist bmp.txt file to this new folder.  I still get the opening error but selecting OK causes the app to open.  Now it works, although the graphics are pretty bad.

Thanks for answering.

---

