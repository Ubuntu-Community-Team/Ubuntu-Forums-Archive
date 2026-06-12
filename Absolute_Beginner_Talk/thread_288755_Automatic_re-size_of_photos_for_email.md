---
title: "Automatic re-size of photos for email"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2006-10-30
Hi,

I'm looking for photo album type software that will automatically re-size photos down to a reasonable amount for email.  In Windows, I run Finepix (came with my Fuji camera)  I select a photo/s click "send to email" and it automatically opens up my email client with the photo re-sized and attached, ready to add text.  

Mrs. Phosphoric uses this facility a lot and I won't convert her to Ubuntu if I can't find a similar feature.  

Needless to say, terminal work is out of the question.

I'm currently using gthumb and evolution.

Thanks. :)

---

### Post by Bartender on 2006-10-30
Until someone smarter comes along, I'll tell you what I figured out in GIMP a coupla days ago.  It's not as automatic as you describe.

Open GIMP.  Click on "File>Open".  Find the picture you want to compress and bring it up.  Go to "File>Save as Copy".  Rename the file by adding a "1" or something really simple.  Click "save", new window pops up, drag slider to left to increase compression.  Save to Desktop or some other handy place.

I'm sure there are easier ways but there's something to get you started anyway.  

I haven't tried this, but "Official Ubuntu Book" recommends F-Spot for working with images.  Find it in Synaptic and let Synaptic handle the install.  Maybe that application has a simple method.

---

### Post by Phosphoric on 2006-10-30
Thanks Bartender,  I'm sure what you've suggested will work but I don't think I can sell the idea to Mrs. Phosphoric, she's used to one click and go. :(

---

### Post by Marsolin on 2006-10-30
[F-Spot]("http://linuxappfinder.com/package/f-spot") has an email menu entry that gives you choices for the size image to send. It's under the File menu.

[Digikam]("http://linuxappfinder.com/package/digikam") can to the same thing. It's Email Images entry is under the Image menu.

If you use [Konqueror]("http://linuxappfinder.com/package/konqueror") you can install the konq-kim package that creates a menu that allows you to resize images by right-clicking on them and selecting a size.

---

### Post by Phosphoric on 2006-10-30
I've installed F-Spot but I don't seem to have the option to re-size the images to email.  It just sends the full size image. :( 

I think I've tried all the options but I can't find one for re-sizing.  Am I doing something wrong?

Thanks.

---

### Post by Phosphoric on 2006-10-30
Oh Boy, I must be really stupid.

I've installed DigiKam now and can't find the option to change the image size there either.

What am I missing?

Thanks

---

### Post by Marsolin on 2006-10-30
Try installing [kipi-plugins]("http://linuxappfinder.com/package/kipi-plugins") and [imagemagick]("http://linuxappfinder.com/package/imagemagick"). It could be that those are required.

---

### Post by wadeall on 2006-10-30
I use Picasa which does this well

---

### Post by Phosphoric on 2006-10-30
Thanks for the further suggestions folks.

Kipi plugins gave me the email sizing options but it won't work with my Evolution email client, it seems to be geared up for kmail or something.

I've been playing with Picasa most of the evening and thought I was getting somewhere, but it only seems to load one picture at a time.  You can't have two or more picture attachments in the same email.

This just about sums up my luck with Ubuntu, everything I try to do is a real struggle.

I'm going to bed, try again tomorrow.

Thanks for the help so far.:)

---

### Post by Phosphoric on 2006-10-31
I've has a go at all the suggestions and have plumped for Digikam with all the plugins.  That seems to give me what I'm after, just need to get familiar with the software.

Thanks folks!

---

### Post by R Smit on 2006-12-15
> **wadeall said:**
> I use Picasa which does this well
Picasa just creates a new email with the NAME of the file, but not the file itsself...very annoying.

---

