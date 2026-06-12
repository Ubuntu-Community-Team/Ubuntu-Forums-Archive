---
title: "Adobe RGB"
date: 2008-07-11
forum: Art &amp; Design
---

### Post by DanielReidal on 2008-07-11
Hi! I am looking for a simple image viewer that can handle Adobe RGB. I know that gimp accept aRGB but does gimp has an image viewer as well?

Cheers Daniel

---

### Post by deanjm1963 on 2008-07-11
Is there any reason in particular that you need to have Adobe RGB accuracy for just viewing images?

icc profiles such as Adobe RGB etc., are for providing consistent colour between monitor/scan/application/print. 

Some more info might help.

---

### Post by DanielReidal on 2008-07-11
If you have an image with with the embedded color profile adobe RGB and the application use the sRGB color space, the colors might look dull and different. I have all of my pictures in adobe RGB and I don't wan't to assign them to sRGB just to view them on my linux computer.

Cheers Daniel

---

### Post by deanjm1963 on 2008-07-11
Have you installed the icc profiles available for ubuntu?

The image viewers available, gthumb, gwenview etc, do not support icc profiles yet.

Certain applications such as Gimp, Inkscape and Scribus support icc profiles, but as I said previously, the intent of icc profiles, such as sRGB, AdobeRGB, etc are to produce "what you see on your monitor is what will (or should be) printed".

Opening an AdobeRGB image will shift in colour when your application is not set for AdobeRGB.

Until linux supports icc profiles at the operating system level, e.g. set a system wide profile for both rgb and cmyk that all applications can use to display and print "what you see is what you get", different applications will produce different display colors.

We're not up to mac colour yet, perhaps in another year or so.

---

### Post by DanielReidal on 2008-07-11
Ok, then it is problem. I'm a photographer and can not accept color loss when I display my images. Even if most of the LCD TV:s and monitors are not able to display the full adobe color space, the conversion generates strange colors.

I'm used to the "windows world" where a lot image viewers support different color spaces.

I'm setting up a media PC and was hopeful to use mythbuntu, but maybee that is not an option then... Of course I could convert the images to sRGB, I usually do that when I publish them to the web. But then it not possible to just browse my "working directories" where I edit my pictures...

Thanks Daniel

---

### Post by nick_edwards on 2008-07-11
from my understanding Adobe RGB in only a workspace and no matter what you view it on it's not going to show any more colour than sRGB because no monitor exists which can show the full colour space. If you want to accurately display colors you need a monitor calibration profile (from a calibrator like Huey, Spider etc) and this can be loaded system wide with xcalib.
The colour shift from converting Adobe RGB from sRGB probably comes from how it is converted ie whether the adobe profile is clipped or scaled to convert to the smaller sRGB.
In terms of the Gimp File - Preferences - Color Management -- RGB profile can be set to AdobeRGB, Monitor can be set to your calibration profile and the Display Rendering intent setting adjusts how the computer fits the very large workspace profile into the very small monitor profile (whatever suits you the best).
Until you have a profile for your monitor, you're wasting your time caring about anything else.
please correct me if I'm wrong anywhere here, this is just my understanding and I'm learning too

---

### Post by nick_edwards on 2008-07-14
I now see what you mean, processing a picture in Adobe and opening in the image viewer the image comes out flat, even with Xcalib calibration which should calibrate both images the same so it must be related to the Adobe to sRGB coversion in the images viewer

---

### Post by DanielReidal on 2008-08-03
The adobe colorspace is "bigger" than sRGB. Then its easy to understand that if you use a viewer, lets say firefox, that asumes that the image is in sRGB there could be a mis match in colors. 

This is normally no problem, most of the people use srgb in the cameras. But some photo nerds like me use other color spaces ;-)


One more thing, I have to find out if my monitor calibration tool has linux drivers...

Cheers! Daniel

---

### Post by rubinstein on 2008-08-04
For monitor calibration, look at [http://www.argyllcms.com/](http://www.argyllcms.com/) if your hardware calibration meter is supported. I have an Xrite DTP94 and it works flawlessly.

---

### Post by rubinstein on 2008-08-04
Oh, and Firefox 3 now has integrated color management. It is not enabled by default, but you can enable it when you follow the instructions at [http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478](http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478) :

# Type about:config in Firefox 3's address bar and press Return. The configuration settings will appear.
# In the Filter field, type gfx. The list of settings will shorten to show just those related to graphics, ie gfx.
# If the Value for gfx.color_management.enabled is False, double-click anywhere on that line to toggle the setting to True.
# Quit and relaunch Firefox 3 and you're in business.

This might also help: [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)

---

### Post by ImpressMe on 2008-08-05
I had to compile GQview 2.1.5 to support LittleCMS (I think it is called) and now my GQview supports monitor profiles as well as colour profiles. The monitor profile generated by my hardware for calibrating screens I had to make on Windows. Colour profile support for Linux sucks. 

People, trust us. We need Adobe RGB from time to time. These colour spaces was not invented by retarded ignorants and they are not used by retarded ignorants. This user perfectly well understands when to use Adobe RGB and when not to. I do as well. 

Your point must be that what Linux does not fully support, users do not need. You are wrong.

As a photographer I do not like to be limitied by Linux. Paying for Windows software is not all joy but at least now I don't have to struggle with software limitations. Actually, photography is an expensive habit, equiment is so expensive so that software licenses is a drop in the ocean in comparison. 

Linux is just not the number one (or two) choice for photographers.

---

### Post by oldsoundguy on 2008-08-05
I have to echo somewhat the post of impressme.

Linux is not ready for prime time as far as photographers and as far as color management.  Argyle is a step in the right direction, but still a very convoluted way to get your colorimeter to work.  And the inability to be able to plug in a printer profile easily is the second basic issue.

GIMP is a fine program .. to a point  .. that point being it does not have the total image management capabilities of CS2 and beyond (namely Adobe Bridge)

And use of a pad is still hit and miss for some.  I managed to get my Wacom Intuos 3 running, and it is OK, but not there yet in comparison to it's usability in Windows. (but in this case Wacom is co-operating)

Hence, most hard core amateurs and the professional photographers are still going to use a Windows box. (I have a Windows box that contains just photographic programs, Adobe programs and media items (awaiting Mediabuntu on those!) in the main .. very little else is done on that machine!)

What has to happen is that pressure has to be put on to Adobe to write for Linux in a serious manner.  They do for Windows and for Apple .. and I would be willing to PAY for programming in Linux just to be able to FINALLY dump Windows altogether.  Either that, 
or some serious effort has to be expended by the code writers for Linux to get that aspect of the system up to snuff.
(there are a lot of purchasers of Photoshop out there .. that means a lot of users that could be brought into Linux that are still out in the cold!)

And there are still other programs that don't even have an attempt to cover.  IE: Picture Perfect,  Programs for Nikon, Image Rescue for that occasional "oops, didn't mean to delete that from the disk" situation.

As much as I love and use Linux (on three computers in my place), I do agree that a lot of progress has to be made to attract the photographer and the graphic artist.  They will NOT move if programming their efforts takes an inordinate amount of time and energy. 

Not everyone wants to be a computer programmer.  Most just want to USE the thing and forget about it.

---

### Post by miegiel on 2009-02-27
I'm leaving the "You shouldn't use ubuntu for photography" discussion for what it is. Even though this is an old thread, the title is so to the point that I can't resist posting what I found in bits and pieces across this forum and the rest of the web.

For those who want to try working with abobeRGB I came across the following programs:[LIST]
[*]UFRaw : for converting raw images to adobeRGB
[*]F-Spot : for managing and (pre)viewing) images in adobeRGB (since ver 0.50, intrepid repo's and later I believe)
[*]GIMP : for editing images in adobeRGB
[/LIST]Obviously you'll need a monitor that displays adobeRGB with reasonable accuracy, else setting up these programs to use adobeRGB is pointless. These monitors do exist nowadays. Check out "wide gamut" monitors, most of these can be calibrated for adobeRGB.

Finally, working in adobeRGB isn't pointless even though you are going to convert to sRGB or what ever in the end. After all when I edit and mix audio I do that in something losless even though I'm going to convert it to mp3.

---

### Post by kayosiii on 2009-02-27
I don't know if anybody mentioned it but Digikam supports Colour management and is not a bad image management tool...

---

