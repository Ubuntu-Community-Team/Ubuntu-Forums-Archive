---
title: "Add transparency to image in GIMP?"
date: 2008-08-15
forum: Art &amp; Design
---

### Post by Aeph on 2008-08-15
I am trying to take a white background and make it transparent. How can I do this?

---

### Post by adewale on 2008-08-15
Look at your layers panel for something like opacity and move the slider backwards from 100 till you get desired transparency.

---

### Post by Aeph on 2008-08-15
I think that just changes the transparency for the entire layer.

---

### Post by smartboyathome on 2008-08-15
Layer > Transparency > Add Alpha Chanel; or if you want to make a certain color transparent: Layer > Transparency > Color to Alpha.

---

### Post by Aeph on 2008-08-15
I might be doing something wrong, but color to alpha just makes everything alpha and adding an alpha channel doesn't do anything.

---

### Post by smartboyathome on 2008-08-15
What are the colors in your picture? Color to alpha should only make certain shades of the color transparent (ie, if you have a white background and light pastel colors, then the light pastel images will become partially transparent. Click on the color patch to change it to the one you want.

Adding the alpha channel just gives the layer the ability to use alpha, it doesn't do anything right away. With it on, you can erase to transparency, etc. You can use this to use the magic wand tool to delete certain patches of color. Just press the delete key after selecting what you want to delete.

---

### Post by AJB2K3 on 2008-08-15
Make to **select>none** before colour to transparency. That could be the problem

---

### Post by Aeph on 2008-08-17
> **smartboyathome said:**
> Adding the alpha channel just gives the layer the ability to use alpha, it doesn't do anything right away. With it on, you can erase to transparency, etc. You can use this to use the magic wand tool to delete certain patches of color. Just press the delete key after selecting what you want to delete.

That helped. One last thing: there is still a white-ish border around the image from the border pixels that make the image look more smooth. Is there a way to make these also transparent while giving it the same effect or do I just have to go through and delete them all?

---

### Post by smartboyathome on 2008-08-17
If you undo the deletion and then raise the threshold of the magic wand (try 30), then it should get the white pixels for you.

---

### Post by Aeph on 2008-08-17
> **smartboyathome said:**
> If you undo the deletion and then raise the threshold of the magic wand (try 30), then it should get the white pixels for you.

Unfortunately, they're not all white. They are shades that blend the image with the white background for an anti-aliasing effect.

---

### Post by smartboyathome on 2008-08-17
It doesn't matter. The fuzzy select tool will get rid of all colors that blend in to the threshold of the collor you pick.

---

### Post by dodle on 2008-08-17
Ctr+A, then Delete

Unless I am misunderstanding the conversation.

---

### Post by smartboyathome on 2008-08-17
> **dodle said:**
> Ctr+A, then Delete

Unless I am misunderstanding the conversation.

He doesn't want to delete everything, just the white space which is the background of the image.

---

### Post by Fhernd on 2010-08-09
Thanks for your answer **smartboyathome**. Now, the page logo has transparency and shown fine. So long.

---

### Post by the_crayon_king on 2012-01-15
I do a lot of sprite editing and I just use white as my background then : Layer> Transparency> Add Alpha Channel. Then I click the bucket fill/paint tool and for fill type I select BG color fill. Afterwards I just bucket fill the white parts which erases to transparent. I think you have to save as a PNG or GIF to save the transparency.

---

### Post by ofnuts on 2012-01-16
> **the_crayon_king said:**
> I do a lot of sprite editing and I just use white as my background then : Layer> Transparency> Add Alpha Channel. Then I click the bucket fill/paint tool and for fill type I select BG color fill. Afterwards I just bucket fill the white parts which erases to transparent. I think you have to save as a PNG or GIF to save the transparency.And you get really good results that way?

---

### Post by shantiq on 2012-01-22
> **Aeph said:**
> I am trying to take a white background and make it transparent. How can I do this?



if i understand your question  simply

colours/color to alpha/pick white


that is the quickest way i know

---

