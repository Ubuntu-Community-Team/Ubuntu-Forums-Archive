---
title: "JPEG Quality Restore (PNG)"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2008-01-27
I am looking for a free program that will convert .jpg files into .png files- restoring the original file quality. It can be for linux or XP, but I really need that program. I found one, but it's $100!
[http://www.unjpg.com/](http://www.unjpg.com/)

Does anybody know of a program that can do this? Or if the results are actually worth it?

---

### Post by mortsahl on 2008-01-27
JPEG is a lossy format ... once the original file (.raw, or whatever) is saved as a jpeg, unless the compression was set to 0, the resulting jpeg file has thrown away a lot of the information found in the original ... there is no way of getting it back short of giong back to the original (non-jpegged) image.

---

### Post by thelatinist on 2008-01-27
You can't do that, any more than you can recover CD-quality sound from an .mp3 file.  You can convert the jpg/mp3 to a lossless format, but it will have exactly the same quality as the source file.

That said, I have had some limited success applying filters to jpgs in the GIMP or PhotoShop to remove some jpg artifacts, making them look slightly better on the screen.  But that doesn't add any of your lost imformation back in, it just smooths the image out a bit.

---

### Post by Ian505 on 2008-01-27
So unjpeg is bologna?

EDIT- Sorry, it is really [http://unjpeg.com/](http://unjpeg.com/) not unjpg.com

---

### Post by rich.bradshaw on 2008-01-27
Try using imagemagick for simple conversions etc.

Read: [http://www.ibm.com/developerworks/linux/library/l-graf/](http://www.ibm.com/developerworks/linux/library/l-graf/)

```
 convert input.jpg output.png
```

Will change input.jpg into output.png, this works at the command line obviously.

---

### Post by TheForkOfJustice on 2008-01-27
> **Ian505 said:**
> So unjpeg is bologna?

EDIT- Sorry, it is really [http://unjpeg.com/](http://unjpeg.com/) not unjpg.com

Sounds like it.  Unless there is some way to 'guess' what the missing data is from the data that is there and then add it back to the image.  I have no idea if that kind of data extrapolation is possible though.  The most it would do is make the picture look 'smoother' and less pixellated.  Any details that you would wish make clearer would probably come out looking smudged and blurry.

Maybe you should hunt for a review of unjpeg.  It sounds like $100 snakeoil.

---

### Post by Steveway on 2008-01-27
In the demonstration on that page it looks as if they only add blur to the image.
Not really impressive and never worth 100$!
Also listen to the other posters, your best bet would be to try to revert the things that jpeg did with gimp.

---

### Post by thelatinist on 2008-01-27
> **Steveway said:**
> In the demonstration on that page it looks as if they only add blur to the image. Not really impressive and never worth 100$!  Also listen to the other posters, your best bet would be to try to revert the things that jpeg did with gimp.

Yeah, even an amateur can do better than that by playing around with GIMP.

---

