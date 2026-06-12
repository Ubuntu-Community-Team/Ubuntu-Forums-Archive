---
title: "Decompose???"
date: 2008-06-07
forum: Art &amp; Design
---

### Post by shelbyvision on 2008-06-07
I would really like to be Windows-free eventually, and occasionally I need to produce a jpg image in CMYK color. I've read that this can't be done in GIMP, or any other linux program, but then I read stuff like this:

***********************

 CMYK(and other modes) support in GIMP
Posted by: Greg Folkert on May 06, 2006 09:54 PM
What in the BLAZES are you talking about?

Open a Pic, goto Image--> Mode--> Decompose

There are a ton of options there.

    * RGB
    * RGBA
    * HSV
    * CMY
    * CMYK
    * Alpha
    * LAB
    * YCbCr_ITU_R470
    * YCbCr_ITU_R709
    * YCbCr_ITU_R470_256
    * YCbCr_ITU_R709_256



AND you can Decompose to Layers or Not.



IOW, if you haven't actually looked for CMYK support in GIMP for sometime... You should probably do so again.

******************************

(Taken from this web page: [http://www.linux.com/feature/53951](http://www.linux.com/feature/53951))

I tried this on my version of GIMP (2.4.0-rc3), and "decompose" is not there. So I looked it up in the GIMP manual, where it has this:

************************

 You can find this filter through Filters &#8594; Colors &#8594; Decompose

This filter separates an image into its different components (RGB, HSV...).

************************
 
My version of GIMP does not have "colors" in the filter menu. Is there something I need to download and install? Have any of you out there had any experience with this?
Thanks,
Steve

---

### Post by oedipuss on 2008-06-07
I vaguely remember looking for this too, and it being in a very different location than the one it was supposed to.
I have 'Decompose' in menu 'Colors/Components/Decompose', in gimp 2.4.5 (the hardy default), hope that helps.

I suspect your image will need to be in RGB mode first though, indexed or grayscale will not work.

---

### Post by shelbyvision on 2008-06-07
Yep, that's where it is.
THANK YOU.
I thought I had seen it before, but I couldn't find it.
Now I just have to figure out how to use it ;).
Steve

---

### Post by digitalis_vulgaris on 2008-06-08
You can use Phatch to convert RGB images to CMYK.

---

### Post by shelbyvision on 2008-06-09
> **digitalis_vulgaris said:**
> You can use Phatch to convert RGB images to CMYK.

Thanks for the tip. Have you done it? If so could you explain how?
Steve

---

### Post by digitalis_vulgaris on 2008-06-09
Phatch is photo batch processor. Whan you open Phatch you add desired actions. On the end you add "save" action and set variables. After this drag and drop into Phatch desired image.

To convert RGB to CMYK use Convert Mode action.

---

### Post by shelbyvision on 2008-06-09
> **digitalis_vulgaris said:**
> Phatch is photo batch processor. Whan you open Phatch you add desired actions. On the end you add "save" action and set variables. After this drag and drop into Phatch desired image.

To convert RGB to CMYK use Convert Mode action.
Thanks for the instructions. I tried it, and it seemed to work, but there doesn't seem to be any way to tell if the image produced is actually cmyk. How can I tell?
Steve

---

### Post by digitalis_vulgaris on 2008-06-10
Hahahahaaha... this is a right question! :) I don't have an answer. Try to open it in GIMP! If refused than it's not a RGB anymore :) hahahahaha!

---

### Post by shelbyvision on 2008-06-10
[QUOTE=digitalis_vulgaris;5154294 Try to open it in GIMP! If refused than it's not a RGB anymore :) hahahahaha![/QUOTE]

Well, that test doesn't work. I tried an older image from my files that I know is CMYK, and GIMP opens it, but in RGB mode, and no acknowledgment that it was ever anything other than RGB, although the colors on the screen don't look right. 
Steve

---

### Post by digitalis_vulgaris on 2008-06-10
Try to make some test with Krita. Krita should have CMYK support.

---

### Post by shelbyvision on 2008-06-10
> **digitalis_vulgaris said:**
> Try to make some test with Krita. Krita should have CMYK support.

Thanks again for the suggestion. I didn't know about Krita. Looks like a great program. I looked it up and at first I thought I'd have to get the whole KOffice suite, but I searched "Krita" with Synaptic, and found that I could get it as a stand-alone program. It does indeed identify the color mode  of an image, and the one I converted with Phatch was identified as CMYK. Actually, I could bypass Phatch and GIMP altogether, and just use Krita, since it will make the conversion from RGB to CMYK, along with any other image editing I might need to do. I'm getting closer than ever to being Windows-free!
Steve

---

### Post by digitalis_vulgaris on 2008-06-11
I'm glad that you manage to solve your problem. I'm in contact with Krita developers. They announce truly useful version of Krita for this year. I'm hoping that new Krita will be answer for CMYK raster images... Anyway, Krita team are really nice people, and they going in good direction. If some programmers have a time to join Krita project, it would be nice... :KS

---

