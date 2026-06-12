---
title: "Renaming RAW images a la jhead"
date: 2009-08-01
forum: Art &amp; Design
---

### Post by SpacyRicochet on 2009-08-01
I recently went on vacation and took a lot of photos with a Nikon digital camera. I set it to save the photos as both jpeg and RAW images (.NEF) Now I have some different folders (by date in which I imported them) where all the photo's are named Bla 01.jpg, Bla 01.nef, Bla 02.jpg, Bla 02.nef, etc. Sometimes Windows makes my life harder than it needs to be.

I want to put all the images in one folder and rename both the jpegs and the RAWs to the time that they were taken. I know that for jpegs I can use jhead for this. Is there an equivalent program to rename RAW images? If not, does anyone know of a good script to accomplish the same?

---

### Post by _sAm_ on 2009-08-01
First I tried pyRenamer; it could do what you wanted but only for JPG(it cant see the exif data for my NEF files). 

Then I tried Thunar and the rename plugin
(sudo aptitude install thunar thunar-media-tags-plugin)
If you select the files within Thunar and right click>rename you can add the date in front of the filename;
DSC_5323.NEF turns into 2009_08_01_DSC_5323.NEF

Then we have exiv2(learned about it from this thread: [http://ubuntuforums.org/showthread.php?p=7665035](http://ubuntuforums.org/showthread.php?p=7665035)). In the terminal go to the folder with *.jpg and *.NEF files, and run: exiv2 -F rename -r "%Y-%m-%d" *.NEF *.JPG
DSC_5323.NEF
DSC_5323.JPG
turns into:
2009-07-24_1.JPG
2009-07-24_1.NEF

And the next file: 
2009-07-24_2.JPG
2009-07-24_2.NEF
And so on. 

Be sure to have backup before you do stuff like this.

---

### Post by SpacyRicochet on 2009-08-01
Thanks for the reply!

In the end I found out that exiftool for windows is also capable of this. But I'll keep your reply in mind when I'm back at my own pc.

---

### Post by _sAm_ on 2009-08-01
> **SpacyRicochet said:**
> Thanks for the reply!

In the end I found out that exiftool for windows is also capable of this. But I'll keep your reply in mind when I'm back at my own pc.
You can install exiftool via Synaptic if you are using Ubuntu Jaunty.

---

### Post by AJB2K3 on 2009-08-02
Um nef and jpg are two different file formats.
.NEF is an uncompressed raw data.
.jpg is an altered compressed image format.
.nefs have to be compressed and saved to jpgs and not just renamed.
Unless you need the raw format and understand its purpose don't use it.

---

### Post by SpacyRicochet on 2009-08-20
Well, I used both so I could keep the jpegs for easy photo's. Then I could use the nefs to mess around with. I know their purpose, but haven't worked with them yet, so I was curious.

Thanks for the replies you both :)

---

### Post by AJB2K3 on 2009-08-20
> **SpacyRicochet said:**
> Well, I used both so I could keep the jpegs for easy photo's. Then I could use the nefs to mess around with. I know their purpose, but haven't worked with them yet, so I was curious.

Thanks for the replies you both :)

No worry's, just do me the favour of joining [http://photography4allforum.co.uk]("http://photography4allforum.co.uk") and showing off you photos. :popcorn::popcorn:

---

