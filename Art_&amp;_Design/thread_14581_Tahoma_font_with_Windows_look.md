---
title: "Tahoma font with Windows look"
date: 2005-02-08
forum: Art &amp; Design
---

### Post by mirtux on 2005-02-08
Hi,
 sorry if this question has been already posted in a different way, in another thread but i've lost the way. I'm trying to get the same appereance in Ubuntu as i have in a windows machine, in particular regarding system fonts. I didn't find a way to reach this point.
 I've seen just a screenshot representing, in linux, the thing i would like to have, but i don't know how to arrive to the same point.
        Look here  [http://www.kdevelop.org/graphics/pic_corner/kdevelop-3.0_IDEAl_KDE_plastic.png]("http://www.kdevelop.org/graphics/pic_corner/kdevelop-3.0_IDEAl_KDE_plastic.png"). This is what i would like to have! 
     
     
        Some help [img]http://www.ubuntuforums.org/images/smilies/icon_sad.gif[/img]?
       
        Regards,
        MC

---

### Post by macewan on 2005-02-08
non smooth fonts?

Computer > Desktop Preferences > Font

---

### Post by Jad on 2005-02-08
here ya go
[http://ubuntuforums.org/showthread.php?t=4456&highlight=smooth+fonts](http://ubuntuforums.org/showthread.php?t=4456&highlight=smooth+fonts)

---

### Post by macewan on 2005-02-08
[QUOTE=Jad]here ya go
[http://ubuntuforums.org/showthread.php?t=4456&highlight=smooth+fonts](http://ubuntuforums.org/showthread.php?t=4456&highlight=smooth+fonts)[/QUOTE]
 think he's looking to have jagged edges instead of smooth

---

### Post by mirtux on 2005-02-09
Yes you've the point. Very simple: like this
 
 MC

---

### Post by mirtux on 2005-02-09
It must be possible in linux since the first link is taken from the Kdevelop site! ](*,)
 
 MC

---

### Post by oddabe19 on 2005-02-09
[QUOTE=mirtux]It must be possible in linux since the first link is taken from the Kdevelop site! ](*,)
 
 MC[/QUOTE]
 turn off AA fonts in Preferences -> Fonts

and

sudo apt-get install msttcorefonts (with universal repo enabled)

then

Goto preferences -> fonts and select Tahoma under all the options.

that SHOULD do it

i didn't try it... i don't feel like changing the fonts on my computers sorry :-P

---

### Post by mirtux on 2005-02-10
Thanks, i've tried your suggestion but unfortunately this is what i get.... light years far from what i would like.
 
 Regards
 MC

---

### Post by ubuntu_fan on 2005-02-10
[QUOTE=mirtux]Thanks, i've tried your suggestion but unfortunately this is what i get.... light years far from what i would like.
 
 Regards
 MC[/QUOTE]
 I believe that MS uses 8 point for the system fonts.

The screenshot looks about 10. Maybe making the font size 8 migh help.

a.

---

### Post by mirtux on 2005-02-10
Some sort of better..... but still not the same! However thanks, it's improving :|. 
 
 Regards,
 MC

---

### Post by Nuak on 2005-02-10
Try **Trebuchet MS 8**, i thinks is even better than Tahoma

---

### Post by ubuntu_fan on 2005-02-10
[QUOTE=mirtux]Some sort of better..... but still not the same! However thanks, it's improving :|. 
 
 Regards,
 MC[/QUOTE]

Which part still needs improving?

Can we see it?

a.

---

### Post by jinacio on 2005-02-10
there's more to it than just this... 

antialiasing has to be disabled, for the fonts to look really crisp and sharp, and other settings have to be enabled for them not to look "jagged".

i have 96dpi and 8pt fonts; desktop fonts look nice (with aa), but my major problem is firefox web pages and thunderbird ... (specially those bold fonts, they look really horrid!)

look here for more information: [http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1)

(pics here: [http://mysite.verizon.net/vze8992v/](http://mysite.verizon.net/vze8992v/))


Cheers,
Joao Inacio

---

### Post by mirtux on 2005-02-11
> **jinacio]there's more to it than just this... 
   
 antialiasing has to be disabled, for the fonts to look really crisp and sharp, and other settings have to be enabled for them not to look "jagged".
   
 i have 96dpi and 8pt fonts said:**
> http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1[/url]
   
   (pics here: [http://mysite.verizon.net/vze8992v/]("http://mysite.verizon.net/vze8992v/"))
   
   
   Cheers,
   Joao Inacio
   Ok this is the screenshot i was searching for ([http://mysite.verizon.net/vze8992v/screenshot0.html]("http://mysite.verizon.net/vze8992v/screenshot0.html")). I would like to have the **same font you have for the desktop** icons. Is it necessary to have kde, or is possible to have with gnome?

---

### Post by jinacio on 2005-02-11
[QUOTE=mirtux]Ok this is the screenshot i was searching for ([http://mysite.verizon.net/vze8992v/screenshot0.html]("http://mysite.verizon.net/vze8992v/screenshot0.html")). I would like to have the **same font you have for the desktop** icons. Is it necessary to have kde, or is possible to have with gnome?[/QUOTE]

heh, these are not my screenshots...

I'm trying to get my fonts to look like that, but still no luck :'(
still need to figure out what's missing...

---

### Post by mirtux on 2005-02-11
If you catch it... ;) please advise me....
 Have you asked the creator of these shots?
 
 Regards,
 MC

---

### Post by macewan on 2005-02-11
it says at the top what the font is

under Computer > whatever > Font

select the desktop font and change it - also go to the details section and change hinting to none

---

### Post by mirtux on 2005-02-12
Well, it was't possible for me to gain a good look under gnome, but now i've installed KDE 3.3.2 and with Tahoma fonts i've reached a good balance. And for me it's faster than gnome.
 
 Regards,
 MC

---

### Post by piedamaro on 2005-02-12
Maybe you want to disable aa for font saze smaller than 11 for ex. this is done in /etc/fonts.conf
As a personal note: aliased fonts are ugly!

---

### Post by forcotton on 2005-02-14
[QUOTE=mirtux]Some sort of better..... but still not the same! However thanks, it's improving :|. 
 
 Regards,
 MC[/QUOTE]
 add the following lines in your /etc/fonts/local.conf
        <match target="font">
                <test qual="any" name="family">
                        <string>Tahoma</string>
                </test>
                <test name="pixelsize" compare="more_eq">
                        <int>9</int>
                </test>
                <test name="pixelsize" compare="less_eq">
                        <int>16</int>
                </test>
                <test name="weight" compare="less_eq">
                        <const>medium</const>
                </test>
                <edit name="antialias" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>

---

### Post by tousavelo on 2005-02-17
Hello,

I'm always amazed to see that stock Linux font display is OK for most people. For me it's absolutely unacceptable.

See hypelinks bellow for detailed information. Basically, if you think that your linux display is not as expected, try the following:

Turn off anti-aliasing. Don't hesitate to switch it off in the KDE panel (for QT apps), the Gnome panel (for GTK apps) and in the local.conf XFT configuration file.

***Recompile FREETYPE with the TT_CONFIG_OPTION_BYTECODE_INTERPRETER option ON.***

Notice that the latter might not be legal in your area.

See those resources
General:
[http://avi.alkalay.net/linux/docs/font-howto/Font.html](http://avi.alkalay.net/linux/docs/font-howto/Font.html)

General + Mandrake:
[http://convexhull.com/mandrake_fonts.html](http://convexhull.com/mandrake_fonts.html)

General + SUSE:
[http://ed.asisaid.com/freetypefix.html](http://ed.asisaid.com/freetypefix.html)
Notice that the 9.1+ part did not apply to my 9.2 Suse.

To know where FREETYPE was installed in your distro:
[http://www.theregister.co.uk/2002/10/25/fabulous_fonts_in_linux/](http://www.theregister.co.uk/2002/10/25/fabulous_fonts_in_linux/)

To know more about Xft:
[http://www.keithp.com/~keithp/render/Xft.tutorial](http://www.keithp.com/~keithp/render/Xft.tutorial)
[http://www.xfree86.org/current/fontconfig.3.html](http://www.xfree86.org/current/fontconfig.3.html)
It confirms that you should update local.conf and not fonts.conf. fonts.conf might be replaced when you reinstall XFT.

---

### Post by NeoChaosX on 2005-02-17
Um, I just downloaded msttcorefonts, but there's no Tahoma selectable. Am I doing something wrong?  :|

---

### Post by kassetra on 2005-02-17
Ok, you installed the msttcorefonts, and you don't see Tahoma where?  In your fonts list?
 
 I'm not sure if Ubuntu comes standard with this feature or not, but you can try:
 1. Open a nautilus window (Computer->Home)
 2. Type this in the location window
  ```
fonts:///
``` 
 and press enter.  
 
 You should see a list of fonts installed and available on your system.  If you don't see Tahoma in that list, PM me.

---

### Post by mirtux on 2005-02-17
[QUOTE=NeoChaosX]Um, I just downloaded msttcorefonts, but there's no Tahoma selectable. Am I doing something wrong?  :|[/QUOTE]
 Hi,
   unfortunately there is no tahoma font in that package.... There is some sort of M$ protection with it. If you want it i think you have to take it from Windows...
 
 Regards,
 MC

---

### Post by sayash on 2005-02-27
um... how do you take tahoma from windows?

Sayash

---

### Post by bvc on 2005-02-27
drag and drop to your .fonts dir in your Home dir (in you don't have it, create it >mkdir -p .fonts) and restart X, or log out and in , or start the gnome-font-properties, or ....about 3 other ways of doing the same.

---

### Post by mirtux on 2005-02-28
Hi,
  i used a VERY dirty way of doing that.... but it works... i just copied the two files **tahoma.ttf **and **tahomabd.ttf** in 

[i]/usr/share/fonts/truetype/ttf-bitstream-vera/

[/i]For sure there are better choices...

Regards,
MC

---

### Post by finity on 2005-03-02
The default font used in MS Applications is MS Sans Serif.  Try that font instead of Tahoma.

*EDIT*:  You can find this font in this attachment (hopefully) or goto:
 %WINDIR%/Fonts/MICROSS.ttf

---

### Post by mirtux on 2005-03-02
Well,
   in my Windows XP i have only, by default, Tahoma and Trebuchet....

Regards,
MC

---

### Post by Zootropo on 2005-03-05
[QUOTE=finity]The default font used in MS Applications is MS Sans Serif.  Try that font instead of Tahoma.

*EDIT*:  You can find this font in this attachment (hopefully) or goto:
 %WINDIR%/Fonts/MICROSS.ttf[/QUOTE]
 is that attachment legal? you know, being copyrighted by microsoft....

---

### Post by J. S. Jackson on 2005-03-07
[QUOTE=finity]The default font used in MS Applications is MS Sans Serif.  Try that font instead of Tahoma.

*EDIT*:  You can find this font in this attachment (hopefully) or goto:
 %WINDIR%/Fonts/MICROSS.ttf[/QUOTE]

I think you are mistaken.  MS Sans Serif hasn't been used since win98?  XP uses Tahoma for nearly everything.  Window title bars are Trebuchet.

Everyone has their opinion of what looks good in regards to fonts.  I personally prefer Verdana and use it in every place where I need a small sans serif font.  It's very good at small sizes.  In fact it was designed for that purpose.

Anti-aliasing looks OK on fonts at low res, to me, but at higher resolutions like 1600x1200 the smaller sizes look quite blurry.

---

### Post by deelerious on 2005-03-19
[QUOTE=mirtux]Hi,
 sorry if this question has been already posted in a different way, in another thread but i've lost the way. I'm trying to get the same appereance in Ubuntu as i have in a windows machine, in particular regarding system fonts. I didn't find a way to reach this point.
 I've seen just a screenshot representing, in linux, the thing i would like to have, but i don't know how to arrive to the same point.
        Look here  [http://www.kdevelop.org/graphics/pic_corner/kdevelop-3.0_IDEAl_KDE_plastic.png]("http://www.kdevelop.org/graphics/pic_corner/kdevelop-3.0_IDEAl_KDE_plastic.png"). This is what i would like to have! 
     
     
        Some help [img]http://www.ubuntuforums.org/images/smilies/icon_sad.gif[/img]?
[/QUOTE]

See my end note [here](http://www.ubuntuforums.org/showthread.php?t=20976)

---

