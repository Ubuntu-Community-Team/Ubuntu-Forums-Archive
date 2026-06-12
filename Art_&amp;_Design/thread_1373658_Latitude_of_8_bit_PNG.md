---
title: "Latitude of 8 bit PNG"
date: 2010-01-06
forum: Art &amp; Design
---

### Post by rmccutchan on 2010-01-06
It seems like when I work with 8 bit PNG's in GIMP, there is a huge latitude to work with.  When working with 8 bit jpegs or tiff's in Photoshop, I did not have much to work with.  The 8 bit PNG's appear to have as much latitude at working with 16 bit TIFF's in Photoshop.

I don't know much about the technical side of how GIMP works, but maybe somebody could explain the difference.

I am using Rawtherapee to convert raw Canon files to 8 bit PNG's, then put the finishing touches on them in GIMP.  I do extensive dodging and burning on my photographs, and the results are much better than I expected.  I still have a wide latitude for light/darken when adjusting in GIMP.

Also, the files seem to be quite large when opened in GIMP.  Could this have something to do with the overall latitude of the photograph?

---

### Post by Exodist on 2010-01-06
define latitude?

---

### Post by mcduck on 2010-01-06
> **rmccutchan said:**
> 
Also, the files seem to be quite large when opened in GIMP.  Could this have something to do with the overall latitude of the photograph?

If by "latitude" you mean lag, the file size of course has huge effect on how much resources it takes to edit the image.

If the file *seems* larger than the files you edited with Photoshop, they they probably *ar*e larger and that's all you need to explain why editing them tasks your computer more. :)

---

### Post by rmccutchan on 2010-01-06
Actually, what I mean by latitude is the range of light to dark.  ie: Some color negative films have a 4 stop latitude, while some black and white films have a 6 stop latitude.  In other words, with GIMP I am able to lighten or darken a photograph while in 8 bit mode more than I could in other image editors. I have more "room" for adjustment.

If one has a narrow latitude and tries to lighten a photograph too much, the highlights will lose detail, or "block up".  The same applies the shadows if you darken too much.  So the narrower the latitude, the sooner it will "block up"

As far as size, when I would edit a photograph in photoshop, I considered it a large file if it reached 30-40 Mb while I was editing.  In Gimp, it says the file is sometimes 200-300 Mb (I'm speaking of the info bar at the bottom of the image window in both ps and gimp)  When I save the file, it goes back to a smaller size (10 Mb+-)

So it sounds like GIMP is, so to speak, "opening up" some room to work with in an image.

Maybe I am just perceiving things incorrectly, but after 7 years of editing in photoshop, I seem to have a lot more to work with in GIMP.  You might even say I have more freedom ;)

---

### Post by mcduck on 2010-01-06
ah, so you are talking about the dynamic range. (having spent quite some time at sea the only meaning I can think for "latitude" is the angular measure for distance from equator :D)

I must say I haven't noticed any difference, but try doing the same editing with the same image in both programs to see if there's any difference in that case. Because doing it with different types of files might not be a very good way to compare, PNG uses lossless compression, JPEG is a lossy compression and TIFF is a whole mess off it's own with way too many compressions types to even try to figure out what's going on. Files with lossless compression or no compression at all of course have more room for editing since they have more information about the image, while JPEG files already have lost quite alot of the data.

Of course there really can be some distance in the way Gimp and Photoshop implement different tools. Actually it would be quite a surprise if they behaved exactly the same way. :)

I think I'll have to test this myself as well..

---

### Post by rmccutchan on 2010-01-06
Ah yes...dynamic range.  That's the words I should have used.  It would have been simpler if I had said that in the first place.  I still think in terms of film.  Sorry.

I would like to do a test on the two different programs, but since I fell in love with Ubuntu, I dumped all my windows stuff and don't have any place to do it. :(

If you get a chance to do a test, it would be interesting to know what the results are.

Whatever the case, I am VERY pleased since I made the switch this past summer.

---

### Post by Exodist on 2010-01-06
> **mcduck said:**
> ah, so you are talking about the dynamic range. (having spent quite some time at sea the only meaning I can think for "latitude" is the angular measure for distance from equator :D)
LOL same with me mate. I am a naval vet so I was looking at what he posted with a lot of confusion..

> I must say I haven't noticed any difference, but try doing the same editing with the same image in both programs to see if there's any difference in that case. Because doing it with different types of files might not be a very good way to compare, PNG uses lossless compression, JPEG is a lossy compression and TIFF is a whole mess off it's own with way too many compressions types to even try to figure out what's going on. Files with lossless compression or no compression at all of course have more room for editing since they have more information about the image, while JPEG files already have lost quite alot of the data.

Of course there really can be some distance in the way Gimp and Photoshop implement different tools. Actually it would be quite a surprise if they behaved exactly the same way. :)

I think I'll have to test this myself as well..
Only thing I have noticed between GIMP and Photoshop is that GIMP has a hard time with images over 120megapixle or how ever many MPs a image is at 15,000px X 8,000px. But how often does anyone work at the resolution. :)

---

### Post by mcduck on 2010-01-07
I just tested this with Gimp on Ubuntu and Photoshop CS3 on a Mac, and indeed Gimp allows for more aggressive  brightness adjustments without burning any part of the image. On the other hand, Phostoshop maintains contrast in the image better (at least if it's not set to use legacy mode), so the image doesn't get washed out as easily. The legacy mode (which I believe works like in versions before CS3) wishes out the image like Gimp does, but also burns light/dark areas way sooner than Gimp does.

Quite an interesting finding, I must say. :)

By the way, what comes to the size reported in the status bar, I beleive Photoshop reports the size of the image as if it was saved to disk in the format the image currently is. Gimp on the other hand reports the size the image takes in RAM while open for editing. (while editing a image file it of course is handled as uncompressed bitmap data, and can be compressed only when saved to a file).

What comes to extremely large resolution images (and also 16-bit depths, at least until next Gimp release) you might want to try Cinepaint. It's image processing application based on Gimp and specifically developed to handle extreme resolutions and bit depths, and is widely used by movie studios and professional photographers when high bit depths and large resolutions are needed (Photoshop really only gained support for this kind of things quite recently, and still lacks support for man all image formats used in movie industry, so it never was a viable choice for that kind of professional use). Although I must warn you that Cinepaint is based on Gimp 1, not Gimp 2 so it might appear a bit less user friendly..

---

### Post by rmccutchan on 2010-01-07
Cool!  Thanks for taking the time to do all of that!  I love doing things like that, but I don't have the stuff to do it with.

I would really like to use cine paint, but I don't know how to use it in Ubuntu.  There isn't a Debian version for it, so I guess you have to compile it yourself, which is above my Linux skill level at this time (I just became a convert in August)

I guess Krita is another good program for editing in 16 bit, but I haven't tried it out yet.  I'm still learning GIMP.

By the way, I'm glad to see you have the answer in your sig! :)

---

### Post by mcduck on 2010-01-07
I found a PPA repository for Cinepaint, seems like experimental testing packages but still probably better than compiling it from source..

[https://launchpad.net/~cinepaint/+archive/experimental]("https://launchpad.net/~cinepaint/+archive/experimental")

The Cinepaint page also has link to experimental GTK2 version packages for Debian, with a bit of luck they might work on Ubuntu as well.

(what comes to the answer, might not really be the answer for life, universe and everything but I thought it would make sense to at least give *some* answer.. :))

---

### Post by hessiess on 2010-01-09
Be careful with how you interpret terms like `8 bit' an 8 bit image is normally a pelleted format which can have at maximum 256 unique colours. A `8 bit' image as far as photoshops image creation dialogue is concerned is actually a 32 bit image, with 8 bits for each of the R,G,B,and A channels(8 bit per channel), which can support up to 16 million unique colours.

The PNG file format supports both.

---

### Post by Exodist on 2010-01-10
> **hessiess said:**
> Be careful with how you interpret terms like `8 bit' an 8 bit image is normally a pelleted format which can have at maximum 256 unique colours. A `8 bit' image as far as photoshops image creation dialogue is concerned is actually a 32 bit image, with 8 bits for each of the R,G,B,and A channels(8 bit per channel), which can support up to 16 million unique colours.

The PNG file format supports both.
Very true.

---

### Post by durand on 2010-02-11
> **Exodist said:**
> LOL same with me mate. I am a naval vet so I was looking at what he posted with a lot of confusion..


Only thing I have noticed between GIMP and Photoshop is that GIMP has a hard time with images over 120megapixle or how ever many MPs a image is at 15,000px X 8,000px. But how often does anyone work at the resolution. :)

Ouch, I had that problem recently. GIMP went totally beserk with some 180MP(!) mosaic image I made. What was even more annoying was that imagemagick did an even worse job than the GIMP...

---

### Post by mcduck on 2010-02-12
> **durand said:**
> Ouch, I had that problem recently. GIMP went totally beserk with some 180MP(!) mosaic image I made. What was even more annoying was that imagemagick did an even worse job than the GIMP...

Try Cinepaint. It's *made* to handle ridiculous resolutions, color depths and strange image formats used in movie industry, and is commonly used by professional photographers when they need to work with extremely large files.

---

### Post by durand on 2010-02-12
Well, I only really needed it to resize that image down to more useful sizes for the web.

---

