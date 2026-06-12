---
title: "gimp cmyk"
date: 2007-11-22
forum: Art &amp; Design
---

### Post by Chymera on 2007-11-22
where can i get the cmyk plugin for gimp in for my 64bit machine?

---

### Post by inksmithy on 2007-11-22
I'm not sure there is such a thing. Be worth having a good look around google for it though.

---

### Post by Chymera on 2007-11-23
splendid reply.... you know so much!!!! 
by "no such thing" you mean no cmyk plugin or no cmyk plugin for 64bit

---

### Post by jlenain on 2007-11-23
Hello,

I am also looking for a cmyk plug-in for Gimp.
Unfortunately, it does not seem to exist yet for Ubuntu... but it does for instance for SUSE:

[http://www.linuxcdmall.com/suse-9.3-i386-disk2.html]("http://www.linuxcdmall.com/suse-9.3-i386-disk2.html") (for instance)

I read some stuff on the net and saw that one has to create a cmyk profile by its own in order to convert a RGB picture in CMYK. Does anyobody knows how to do it ?

Thanks a lot

---

### Post by Chymera on 2007-11-24
this is just hell.... can it be so hard to make a proper plugin that will help the gimp have a chance to become at least remotely comparable to photoshop?

---

### Post by johannes on 2007-11-25
[http://www.blackfiveservices.co.uk/separate.shtml]("http://www.blackfiveservices.co.uk/separate.shtml")
or
[http://cue.yellowmagic.info/softwares/separate.html]("http://cue.yellowmagic.info/softwares/separate.html")

I have only tried the first one. I don't think there are any ubuntu packages. With 64-bit you need to recompile it before installing, e.g.
wget [http://www.blackfiveservices.co.uk/linux_resources/separate-gimp2-0.3_linux.tar.gz](http://www.blackfiveservices.co.uk/linux_resources/separate-gimp2-0.3_linux.tar.gz)
tar zxvf separate-gimp2-0.3_linux.tar.gz
cd separate-0.3_linux/
rm separate separate.o tiff.o util.o
make
sudo install -D -m755 separate /usr/lib/gimp/2.0/plug-ins/
sudo install -D -m644 sRGB/*.icm /usr/share/color/icc/

Or a similar process.
Then add some ICC Profiles (e.g. adobe's) to /usr/share/color/icc/
from here:
[http://download.adobe.com/pub/adobe/iccprofiles/win/AdobeICCProfiles.zip](http://download.adobe.com/pub/adobe/iccprofiles/win/AdobeICCProfiles.zip)

Oh, and you'll need pkgconfig, gcc, lcms, libtiff and of course gtk2 and gimp to compile.

---

### Post by Chymera on 2007-11-25
pretty straightforward ....

---

### Post by AJB2K3 on 2007-11-25
Is it so hard to look in the preferances? 2.4 has in in the rc version in the repo's

---

### Post by Chymera on 2007-11-25
strangely enough it's one of the first places i looked.... you get a cmyk menu somewhere under pref which then asks you to select an icc profile for cmyk.... or smth like that... and that's when i started looking for one, and slowly got redirected to the "separate" plugin...

---

### Post by ImpressMe on 2007-12-02
If you need CMYK or LAB mode then GIMP is just the wrong program. My advice is to do what I did: get some professional software, and get the job done!

---

### Post by digitalis_vulgaris on 2007-12-03
Maybe to save an RGB file and than convert it to a CMYK with some other application?

---

### Post by digitalis_vulgaris on 2007-12-03
I just make some test on this topic. Gimp mess up black channel, becouse it's using RGB mode. Still it's possible convert RGB TIF in valid CMYK tif using Phatch.

---

### Post by ImpressMe on 2007-12-03
You can waste years with workarounds and buggy tools. My advice: get some professional software, and get the job done!

---

### Post by jlenain on 2007-12-04
Hello everybody,

johannes, thank you so much for your link to the ICC profiles from Adobe !! It was what I was searching for...

Thanks

---

### Post by jlenain on 2007-12-04
> **ImpressMe said:**
> My advice: get some professional software, and get the job done!

ImpressMe, unfortunately we are talking about FREE solutions, and usually the 'professional' softwares are NOT free and (very) expensive...
With the risk to seem nit-picking, I was searching for a free, easy-to-use stuff.

---

### Post by Chymera on 2007-12-04
> **ImpressMe said:**
> You can waste years with workarounds and buggy tools. My advice: get some professional software, and get the job done!

I know that gimp is a toy in comparison with photoshop, and i would be more than willing to work with ps, regardless if it's free or not.... however i havn't had any luck in making it work on linux (tried both wine and running it over a virtual machine), and even though for me gutsy has proven to be a lot slower than vista, i'd still rather stick to linux....

---

### Post by ImpressMe on 2007-12-05
Yeah, I know what you mean, but Linux really just is an operating system. No OS is stronger than the software available for it.

---

### Post by diggity626 on 2008-11-11
The gimp-plugin-registry, available through synaptic package manager contains a CMYK plugin.  I used these instructions:
[http://angpilipinogimp.wordpress.com/2008/11/01/update-your-gimp-plug-ins-on-ubuntu-810/](http://angpilipinogimp.wordpress.com/2008/11/01/update-your-gimp-plug-ins-on-ubuntu-810/)

---

### Post by sambody on 2008-11-24
A plugin that might be useful to you:
separate+, for a DEB package see [this article]("http://my.opera.com/area42/blog/gimp-cmyk") by [Eckhard M. Jäger]("http://my.opera.com/area42") (more related articles in that same blog)

---

### Post by leandromartinez98 on 2009-07-28
If anyone is interested in this still:

1 - Install the "gimp-plugin-registry" package.

2 - Download the CMYK colorspace from Adobe:

[http://www.adobe.com/support/downloads/iccprofiles/icc_eula_win_end.html](http://www.adobe.com/support/downloads/iccprofiles/icc_eula_win_end.html)

3 - Unzip the zip file wherever you want.

4 - Open the Gimp and go to Edit -> Preferences -> Color Management

    Choose a RGB profile from the RGB folder created above, and
    a CMYK profile from the CMYK folder. There are several of them,
    if you are profesional probably you know what is the difference
    between them. I don't.

5 - Open you image. Go to: Image -> Separate -> Separate
 
    This will create an image with a bizar color.

6 - In this image with bizar color, go to:

    Image -> Separate -> Save

And save your image in CMYK colorspace 
(saving from the standard saving menu of Gimp does not work).

---

### Post by Sockerdrickan on 2009-07-29
Lol Chymera had some issues for sure xD

---

### Post by frogotronic on 2010-07-15
> **leandromartinez98 said:**
> If anyone is interested in this still:

1 - Install the "gimp-plugin-registry" package.

2 - Download the CMYK colorspace from Adobe:

[http://www.adobe.com/support/downloads/iccprofiles/icc_eula_win_end.html](http://www.adobe.com/support/downloads/iccprofiles/icc_eula_win_end.html)

3 - Unzip the zip file wherever you want.

4 - Open the Gimp and go to Edit -> Preferences -> Color Management

    Choose a RGB profile from the RGB folder created above, and
    a CMYK profile from the CMYK folder. There are several of them,
    if you are profesional probably you know what is the difference
    between them. I don't.

5 - Open you image. Go to: Image -> Separate -> Separate
 
    This will create an image with a bizar color.

6 - In this image with bizar color, go to:

    Image -> Separate -> Save

And save your image in CMYK colorspace 
(saving from the standard saving menu of Gimp does not work).

Thanks for the post - works very well.

-CH

---

### Post by Alung C.L. Pan on 2011-03-18
I got it,
thanks a lots
l love it.
from Taiwan New Country. Illa-Formosa island . 
Not Chinese, Not China, Not speaking Manderin, I'm speaking in mother tongue is Taiwanese , 95% Taiwaner peoples easy to speaking and hearing in Mother Tongue Taiwanese.
and speaking Japanese.
Welcome to Taiwan.
YouTek Design.:popcorn:):P

---

