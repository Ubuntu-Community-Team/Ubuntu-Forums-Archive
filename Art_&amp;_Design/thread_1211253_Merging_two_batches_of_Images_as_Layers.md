---
title: "Merging two batches of Images as Layers"
date: 2009-07-12
forum: Art &amp; Design
---

### Post by Arador Aristata on 2009-07-12
Hi everyone

I have been playing around with stopmotion animation recently and I have stubled into a little problem.

Because of the complexity and rendering time I have rendered my main character into Transparent PNG images.

Then I have the animated background on another batch of PNG images.

Now what I need to do is to paste the Character Images into the background Images as a New Layer, then merge and save (to new file or current background image file)

This is simple enough to do by hand in GIMP and takes about 10 seconds per picture. Problem is I have 2 batches each with 1020 images in them.

Is there a program I can use to automate this? Or a script that will basically go:

Open Background00001.png
Open Character00001.png
Copy Character00001.png
Paste into Background00001.png
Save Background00001.png
Close Both

Open Background00002.png
Open Character00002.png
Copy Character00002.png
Paste into Background00002.png
Save Background00002.png
Close Both

.....and so on till the end of the folder or till a set number.

Any help would be highly appreciated!

Thank You!

---

### Post by oedipuss on 2009-07-13
I believe imagemagick can do what you want.. It requires a bit of reading, but it's an excellent command line tool, and you can install it from the repos :

[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

In fact, I'm almost sure it can, I just don't know the exact command line options.

---

### Post by Arador Aristata on 2009-07-18
> **oedipuss said:**
> I believe imagemagick can do what you want.. It requires a bit of reading, but it's an excellent command line tool, and you can install it from the repos :

[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

In fact, I'm almost sure it can, I just don't know the exact command line options.

Thank you so much!

I managed to easily track down the correct syntax needed to do the work and then wrote a small .sh script to loop it for me.

```

for ((f=1;f<=9;f++))
do
  convert Background000$f.png Actor000$f.png -layers merge ./Output/Shot$f.png
done

for ((f=10;f<=99;f++))
do
  convert Background00$f.png Actor00$f.png -layers merge ./Output/Shot$f.png
done

for ((f=100;f<=540;f++))
do
  convert Background0$f.png Actor0$f.png -layers merge ./Output/Shot$f.png
done

echo OEDIPUSS ROCKS!!

```

:D

---

