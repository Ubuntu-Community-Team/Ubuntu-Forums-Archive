---
title: "looking for a way to split image into 3x3 sections"
date: 2009-12-24
forum: Art &amp; Design
---

### Post by rebeltaz on 2009-12-24
Let me start by saying that I have a very unique hobby - I collect gift cards. You know, the cards that you put money on to give as gifts, ensuring the recipient cannot use your money just anywhere? Well, I found years ago that I liked the designs on them and I now have well over a hundred from all different stores. I would like to scan then into the computer and put the images on my web site - thereby eliciting the help of others in finding these cards throughout the US and possibly even the world. 

Having said that, my collection is kept in dozens of baseball card sleeves that go into three-ring binders. If I were to scan these sheets in in one pass (each sheet is 8 1/2 x 11 inches), is there a program that I can use that would take that image and then cut it into 3 sections wide x 3 sections tall? That would make it so much easier to scan these than either having to scan each card individually or having to manually cut each sheet in gimp. 

Thank you in advance for your help and Merry Christmas to you all... :)

---

### Post by Exodist on 2009-12-24
Short question: > looking for a way to split image into 3x3 sections
Short answer: Use GIMPs cut/splice tool.

---

### Post by rebeltaz on 2009-12-25
> **Exodist said:**
> Short question: 
Short answer: Use GIMPs cut/splice tool.

umm... don't suppose you could give a slightly longer answer? :confused:

I looked through the gimp menus, ran 'gimp --help' and 'man gimp' and found absolutely no reference to a cut/splice tool, which I am guessing/hoping would be a command-line function?

---

### Post by Exodist on 2009-12-25
> **rebeltaz said:**
> umm... don't suppose you could give a slightly longer answer? :confused:

I looked through the gimp menus, ran 'gimp --help' and 'man gimp' and found absolutely no reference to a cut/splice tool, which I am guessing/hoping would be a command-line function?
My bad, you can use the Rectangle Selection tool. I had something else on my mind before.
In addition there is also the Crop Tool. I use the rectangle selction tool the most. Just copy and paste the selection into a new file the size of the selection you copied, then save each individual piece. Again sorry about the confusion.

---

### Post by SecretCode on 2009-12-25
Reading your question I felt like there must be a way to do this. Since every sheet will have the same crop positions you shouldn't need to do it manually.

If it's not possible in the Gimp (I suspect it is possible but I haven't found anything), it looks like it might be possible using [**imagemagick**]("http://www.imagemagick.org/script/index.php") - see for example these suggestions: [http://www.imagemagick.org/Usage/crop/#crop_tile](http://www.imagemagick.org/Usage/crop/#crop_tile); [http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=15079](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=15079)

---

### Post by jpbardiau on 2009-12-25
Hi,

[PostRazor](http://posterazor.sourceforge.net/)

---

### Post by rebeltaz on 2009-12-26
> **Exodist said:**
> My bad, you can use the Rectangle Selection tool. I had something else on my mind before.
In addition there is also the Crop Tool. I use the rectangle selction tool the most. Just copy and paste the selection into a new file the size of the selection you copied, then save each individual piece. Again sorry about the confusion.

No problem at all... I really wanted to avoid having to do this manually as I do have quite a few to do...

> **SecretCode said:**
> Reading your question I felt like there must be a way to do this. Since every sheet will have the same crop positions you shouldn't need to do it manually.

If it's not possible in the Gimp (I suspect it is possible but I haven't found anything), it looks like it might be possible using [**imagemagick**]("http://www.imagemagick.org/script/index.php") - see for example these suggestions: [http://www.imagemagick.org/Usage/crop/#crop_tile](http://www.imagemagick.org/Usage/crop/#crop_tile); [http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=15079](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=15079)

That was what I figured as well. As a matter of fact, I already have imagemagick installed. I installed it a while back to use to convert multiple JPG files into a single PDF document - works great for that! I had forgotten I had installed that program. After looking at the link you supplied, I think that that just might do the trick. Thank you!

> **jpbardiau said:**
> Hi,

[PostRazor](http://posterazor.sourceforge.net/)

That program looks great, except that it's output is a multipage PDF, which would require further processing steps. I do appreciate the suggestion, though.

I believe I am going to give SecretCode's suggestion a go. As always, the answer was right there all along, staring me in the face. It just took someone else to point it out! Thanks again to all of you.

---

### Post by PC_load_letter on 2009-12-29
> **SecretCode said:**
> Reading your question I felt like there must be a way to do this. Since every sheet will have the same crop positions you shouldn't need to do it manually.

If it's not possible in the Gimp (I suspect it is possible but I haven't found anything), it looks like it might be possible using [**imagemagick**]("http://www.imagemagick.org/script/index.php") - see for example these suggestions: [http://www.imagemagick.org/Usage/crop/#crop_tile](http://www.imagemagick.org/Usage/crop/#crop_tile); [http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=15079](http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=15079)

+1 for Imagemagick if you have to slice many image files exactly the same way. Just one command from the terminal will do the same thing to all the files in the directory. The online documentation is not bad at all.

---

