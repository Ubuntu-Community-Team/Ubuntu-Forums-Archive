---
title: "gimp questions...."
date: 2008-11-28
forum: Art &amp; Design
---

### Post by hockey97 on 2008-11-28
hi, ok I have a friend that wants me to like take out a background of a image of her and  send her the image.

in otherwords I want to make the background transparent but only showing the image part of where she is.

I want to save it and send it to her so she can just cut and past herself into another image without having to delete the background.

I already took out the background... but now when I send it to her the background appears again.. even though I saved it as png format. Which on my computers shows a checkerboarded background well when look at with a pic view or in the os it shows no background or anything.

The problem I have is sending the pic and having her able to open the photo with the checkboarded background indicating no background.so she can easily just cope and paste herself in another photo without needing to delete the background which currently she claims the background is still there.

any idea?

---

### Post by smartboyathome on 2008-11-28
Could she actually be opening the old file instead of the one you made? Since it is PNG, it doesn't save any non-essential info with the picture, so it wouldn't know that it had a background there before.

---

### Post by whiteraven on 2008-11-28
One way to do this is, using PNG as your output image type, you would need at least two layers in your XCF file, topmost would be the cutout, and the other the default Background layer. Right click the Background layer and select "Add Alpha Channel". With the Background layer still active, Select All and press delete. Save the file as yourfilename.png and it should be transparent if you've done the procedure correctly.

There are numerous tutorials about creating transparent backgrounds using GIMP:

[[COLOR="Blue"]_Transparent Background GIMP_[/COLOR]]("http://www.google.com/search?hl=en&q=transparent+background+gimp&aq=7&oq=%22transparent+back")

---

### Post by hockey97 on 2008-11-28
thanks. I will take a look.

She is bugging me lol haha it is getting annoying.

Thanks for the replies I will take a look at that tutorial.. thanks soo much!!!.

---

### Post by Northsider on 2008-11-29
Correct, you need to make an alpha channel:  

Layer > Transparency > Add Alpha Channel

Select/delete what you want transparent and then save.  I usually save as .gif but png can do transparencies as well.

---

### Post by Northsider on 2008-11-29
Oops, double post.

---

