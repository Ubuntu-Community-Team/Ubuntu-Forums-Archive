---
title: "Application for Displaying EXIF data alongisde Thumbnails"
date: 2007-03-30
forum: Art &amp; Design
---

### Post by Ted_Smith on 2007-03-30
Hi

I need an application that shows thumbnails of my digital photos taken with my digital camera but what I need is the option to have all of the EXIF data displayed alongside the thumbnails so that I can compare how the settings of one photograph differ from the ffects captured in another photograph.

I have tried DigiKam and Picass for Linux but neither do what I need as stated above. Any others? 

Thanks

Ted

---

### Post by SuSUntu on 2007-03-30
My hands are quivering as I type this because I am about to commit Linux heresy. But, you sound pretty serious about your photography, so here goes.

Give Canto Cumulus a try:

[http://www.canto.com/](http://www.canto.com/)

It's not free and it's not necessarily cheap, but they do have a  Linux version (good for them) that you can try before you buy. 

I use Cumulus on Windows, and it is powerful and will require some effort to get it set-up properly. Expect to be frustrated before you get the hang of it (but we also use Linux, so we're used to that :) ). I have never used the Linux version, so I can't vouch for it. I have my doubts that it is anything more than a pale comparison of its Windows and Mac brethren, but why not give it a shot and see. 

As far as its capabilities fitting your desires, you could build catalogs from criteria such as which images were shot with flash, which images were shot with shutter speed at 1/250 s, which images were shot using autoexposure, which images were shot at f8, which images were shot using your L70-200 lens, or combinations of various criteria. You can also specify which data appears with the thumbs.

If you were working in Mac or Windows, I would also recommend you try Extensis Portfolio, as it's a top competitor, but they don't cater to Linux users (I'm surprised Canto does).

Anyway, I don't know of any better digital asset managers for Win, Mac or Linux, and I've looked (and tried them) myself. Maybe someone will surprise us, at least perhaps with an application that does (sort of) what you specifically ask. Otherwise, I'm pretty sure there is nothing that compares with Cumulus or Portfolio overall.

Good luck.

---

### Post by bpmorris on 2007-03-30
The best one I found was [http://www.bibblelabs.com/](http://www.bibblelabs.com/). It isn't free but it isn't that expensive and I don't mind supporting good Linux projects with a few dollars. I am sure Linux Dev's need to eat too... haha.  I use it to do all the basic post processing for my Canon 400D....

Good Luck

Ben

---

### Post by SuSUntu on 2007-03-31
> **bpmorris said:**
> The best one I found was [http://www.bibblelabs.com/](http://www.bibblelabs.com/). It isn't free but it isn't that expensive and I don't mind supporting good Linux projects with a few dollars. I am sure Linux Dev's need to eat too... haha.  I use it to do all the basic post processing for my Canon 400D....

Good Luck

Ben

Hello, Ben. 

Bibble is very nice RAW processing software. The [Noise Ninja]("http://www.picturecode.com/") is very nice indeed (which is included with Bibble).

However, I wasn't aware that Bibble had the kind of features that Ted Smith is looking for.

---

### Post by SuSUntu on 2007-03-31
Attached is a screenshot of my Cumulus 6.x (I haven't upgraded to 7.x yet). The screenshot shows various EXIF data that I have added to my Cumulus Thumbnails View (some of the info that I didn't want posted has been blurred out ... if you have the skill, you can probably reconstruct the data :) ). The camera in this case was an inexpensive Canon digital that I used to make some quick "test" shots prior to shooting with a medium format film camera. The camera model could also be displayed in the Cumulus Thumbnail View (as well as a lot of other info) but I did not add that particular field to the View. 

**Other Viable Possibilities**

_Roll your own_

With some command-line tools liike [ExifTool]("http://www.sno.phy.queensu.ca/~phil/exiftool/"), cthumb and imagemagick, you could generate highly customized html "contact sheets" of thumbnails and extracted EXIF information of your choice. The output could be viewed in a browser.

_Pre-built contact sheet or gallery scripts_

These range from quite simple to quite complex, and there are a lot of them. You'd have to check which ones allow for EXIF data placement along with the thumbs.

_Image Editor / Viewer html export_*

A lot of image editors / viewers allow selected thumbnails to be used for creation of a web gallery or contact sheet (I think Gimp even has some plugins but I'm not sure about whether any have EXIF output along with the thumbs). One that I know works with EXIF is gThumb Viewer. For example, it has the capability of creating an html page / contact sheet with the following EXIF data placed as a caption to the thumbnail:

-- Date and time
-- Exposure time
-- Exposure mode
-- Flash info
-- Shutter speed
-- Aperture value
-- Focal Length
-- Camera model

**The EXIF data is quite limited compared to what is actually available in the images, but it may be enough (it does have basic exposure data) compared to having to write a custom script or having to pay for a full-blown asset management application like Cumulus.**

---

### Post by Ted_Smith on 2007-04-02
Thanks for all the info. 

I will look into it all, although I feel a new Python project coming on ;-) . 

Ted

---

### Post by stani on 2008-01-23
Phatch can do that for you:
[http://photobatch.stani.be](http://photobatch.stani.be)

Start Phatch and choose Tools>Image inspector. You will see something like this:

[IMG]http://photobatch.wikidot.com/local--files/image-inspector/image_inspector_exif.png[/IMG]

You can open it simultaneously for any amount of pictures you want.

To have better exif & iptc support, you can also download the package python-pyexiv2 (hardy, but also works on gutsy):
[http://packages.ubuntu.com/hardy/python/python-pyexiv2](http://packages.ubuntu.com/hardy/python/python-pyexiv2)

Good luck,

Stani

---

### Post by Martin-Herrmann on 2008-01-31
Hi,

Mapivi ([http://mapivi.de.vu]("http://mapivi.de.vu")) will show you the thumbnails, EXIF date and if you want also the embedded JPEG comments and the IPTC data of your pictures.

See screeenshot: [Thumbs, IPTC and EXIF]("http://mapivi.sourceforge.net/081-DirThumbs.jpg").

Mapivi is available as Perl skript,  Debian package and for Ubuntu there is a description available in this forum: [Mapivi Ubunutu Installation]("http://ubuntuforums.org/showthread.php?t=130912&highlight=mapivi").

Regards
        Martin

---

