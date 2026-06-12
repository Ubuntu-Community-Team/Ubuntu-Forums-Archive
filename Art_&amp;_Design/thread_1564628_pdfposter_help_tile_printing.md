---
title: "pdfposter help: tile printing"
date: 2010-08-30
forum: Art &amp; Design
---

### Post by zms on 2010-08-30
anyone know how to us pdfposter. I keep on getting 


zain@zain-laptop:~$ pdfposter -p10x999a4 test 1.pdf out.pdf
/usr/lib/pymodules/python2.6/pyPdf/pdf.py:52: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
Usage: pdfposterram [options] InputFile OutputFile

pdfposter: error: requires both input and output filename

that was just one of my example. But everything i try keeps getting me the same result. Also if anyone knows an easier way of attempting how to tile print in ubunutu, that would be greatly appreciated. I thank you guys in advance.

---

### Post by Newfoundlander on 2010-08-31
I have not used pdfposter but I have much experience in many other desktop publishing and graphic design apps.  Can you tell me...

 - what you are trying to print
 - how many are tiled per page
 - the dimensions of the tiled section

Cheers,

Stephen

---

### Post by zms on 2010-08-31
Hey, I'm just trying to print out pictures in a tiled version just to make it look different and im also poor, that has something to do with it. just trying to print something, maybe like the chicago skylin for example, that could fill up an empty wall dont really have a dimentions in mind maybe like a tile of 10 long x4down (just throwing that number out there). I was just trying it just to see if i could do it. Sorry i cant be of more help.

---

### Post by jtarin on 2010-09-01
You could look into the Gimp for this. It is often overlooked as is Imagemagik.

---

### Post by zms on 2010-09-02
yea ive been playing around with it but im not experienced with graphic design at all. I did put th picture in excel and seemed to have worked a little, but the margins are all messed up.

---

### Post by jtarin on 2010-09-02
Well if your working in Widow there is always Irfanview.

---

### Post by zms on 2010-09-02
Actully i have purged myself of all thing windows, but ill give it a try. I should be able to find someone with a windows computer

---

### Post by robert shearer on 2010-09-02
OK, tiled printing usually means the same image printed multiple times to get an effect like wall tiles.

From your description (post#3) I think what you are wanting is one image able to be printed over several sheets of paper and used as a giant poster. ???

If this is correct then the program you want is  posterazor.

So open a terminal   Applications >Accesories >Terminal and run this..

```
sudo apt-get install posterazor
```

After it installs find it at Applications >Graphics >PosteRazor.

When it opens click on the **?** icon at its top right for How to Use.

It makes a pdf file that can be printed out and assembled from separate sheets into a large poster.

---

### Post by zms on 2010-09-02
Thank you so much. that is exactly what i was looking for. Thanks alot again.

---

