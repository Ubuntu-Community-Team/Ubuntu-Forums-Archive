---
title: "photos auto lighting gimp"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-09-25
all i would like to do is auto adjust light on some pictures ive taken. is there a simple fast way to do this? shot with Nikon D80 Raw NEF files. I have gimp setup but when i adjust the light it gets grainy

---

### Post by bubbalouie on 2007-09-25
try:

Filters -> Enhance -> Despeckle

Also, whilst it has nothing to do with lighting, checkout the following Gimp plugin:

[http://ubuntuforums.org/showthread.php?t=547560](http://ubuntuforums.org/showthread.php?t=547560)

Gimp takes a lot of patience to get the hang of, but t is worthwhile.

Good Luck :)

Ryan

---

### Post by javierfh on 2007-09-25
Hi,

im not sure if this helps but it is worth to take a look. [http://photobatch.stani.be/](http://photobatch.stani.be/)

I have Nikon D70 and i like sometimes also to modify levels or some contrast. 

Im not sure if phatch can handle RAW but well, it is usefull application, for quick editing lots of pictures.


Javi

---

### Post by trucker33377 on 2007-09-25
Wow i looked at the video on that link. So cool . is the plugin an easy install i dont want to mess this up

---

### Post by anaconda on 2007-09-25
Depends in what you need.

if you just want to light all pictures in a folder then imagemagick:s convert command from the command line would be easiest. (once you figure out the exact command you want to give.) Then you wouldn't need to open each file in a GUI program like gimp.

here is one link:
[http://www.imagemagick.org/Usage/photos/#brightening](http://www.imagemagick.org/Usage/photos/#brightening)

---

### Post by bubbalouie on 2007-09-25
I am using gutsy, so you might ant to get the one that best suits your release, but yes, it was very easy to install if you get the deb file. For me it was double click install. Then play.

Feisty Version:

[http://web.tiscali.it/carlobaldassi/GimpLqrPlugin/gimp-lqr-plugin_0.2.0_UbuntuFeisty-i386.deb](http://web.tiscali.it/carlobaldassi/GimpLqrPlugin/gimp-lqr-plugin_0.2.0_UbuntuFeisty-i386.deb)

Gutsy Version:

[http://stuporglue.org/downloads/lqr/gimp-lqr-plugin_0.2.0_i386.deb](http://stuporglue.org/downloads/lqr/gimp-lqr-plugin_0.2.0_i386.deb)

As an aside I use digikam for managing photos (until i need something more powerful), it is no picasa, but still very nice.

---

### Post by trucker33377 on 2007-09-25
ive installed it but i dont see the plugin anywhere, also would you know how i change a NEF or save a NEF as a jpeg file

---

### Post by bubbalouie on 2007-09-26
1) In my case Image->Liquid Rescale

However, apparently the newest Feisty installer goes under the layer menu now.

2)To decode NEF files try DeNEF

**sudo apt-get install denef**

Fore more info look at [http://www.cheeseplant.org/~daniel/pages/denef.html](http://www.cheeseplant.org/~daniel/pages/denef.html) not owning a DSLR I have never needed it so I can't offer much more help than that.

Apparently this [http://www.kde-apps.org/content/show.php/Qtpfsgui?content=54820](http://www.kde-apps.org/content/show.php/Qtpfsgui?content=54820) can work with NEF's too.

---

