---
title: "Fonts in Ubuntu"
date: 2009-07-28
forum: Art &amp; Design
---

### Post by Stochastic on 2009-07-28
Hey, just curious if there's an easy way to find fonts in the Ubuntu repositories?  Do they all start with the same ttf string, or is that just a subset of what's available?

---

### Post by Nevon on 2009-07-28
To check the repositories, you could always do a
```
apt-cache search fonts
```

But you can actually install fonts separately, just like you would in Windows or Mac. Just drop them in /usr/share/fonts/Truetype or ~/.fonts and then just log in and out.

---

### Post by Stochastic on 2009-07-28
I'm not actually interested in installing them on my own machine (that's an easy task), I'm looking to create a metapackage of font packages, and I'm just a bit lost as to which formats of fonts are categorized by what strings in the listing that apt-cache spews out.


I'm also actually just looking for font packages, whereas apt-cache search fonts (or font) gives fun little things like ```
tex-guy - miscellaneous utilities using DVIlib
```


Oh, and to be even more troublesome, I'd like to keep everything to the main or universe repositories (that part is the easy part for me, I need direction on how to separate fonts from libraries from programs when reading apt-cache spews mostly).

---

### Post by Hairy_Palms on 2009-07-28
could try doing 
sudo dpkg-query -S .ttf
it will return all packages containing files with .ttf in the filenames

---

### Post by Stochastic on 2009-07-28
Are true type fonts the only decent font format?

---

### Post by Hairy_Palms on 2009-07-28
> Are true type fonts the only decent font format?

i dont know, but for other formats it would just be a case of substituting .ttf for .fontextension

---

### Post by AJB2K3 on 2009-07-28
No ttf is not the only decent type.
ttf is only one of the sets available
[http://en.wikipedia.org/wiki/TrueType]("http://en.wikipedia.org/wiki/TrueType")

---

### Post by Stochastic on 2009-07-28
AJB2K3, Thanks, you've given me half the information I need...  The other half would be which other sets are decent?  I recall that some fonts are bitmaps etc... and want to stay away from those.

---

### Post by wojox on 2009-07-28
[http://tldp.org/HOWTO/Font-HOWTO/](http://tldp.org/HOWTO/Font-HOWTO/)

I like mac fonts:

Download the font package :

$wget [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)

Untar and move it :

$tar zxvf macfonts.tar.gz
$sudo mv macfonts/*.* /usr/share/fonts/

Reload font cache :

$sudo fc-cache -f -v

---

### Post by banago on 2009-07-29
This article might be of help:

[http://www.ubuntuts.com/how-to-install-fonts-in-ubuntu/](http://www.ubuntuts.com/how-to-install-fonts-in-ubuntu/)

---

### Post by AJB2K3 on 2009-07-29
Arg I got foot and mouth.

---

### Post by Newfoundlander on 2009-07-29
> **AJB2K3 said:**
> What an **** they stole my tutorial.

Had he copied your tutorial word-for-word then it would be fair to claim he stole your tutorial but they are simply two blogs on the same subject.  BTW, your link goes to a GIMP tutorial instead of the fonts one.

---

### Post by AlbHeart on 2009-07-29
> **AJB2K3 said:**
> What an **** they stole my tutorial.


As Chief Editor of [http://www.ubuntuts.com](http://www.ubuntuts.com) I would like the readers to judge if the posts, their links are listed below, are the same or better said is the Ubuntuts.com post a plagiarism of AJB2k3's post?


[http://www.ubuntuts.com/how-to-install-fonts-in-ubuntu/](http://www.ubuntuts.com/how-to-install-fonts-in-ubuntu/)

[http://www.s284317130.websitehome.co.uk/tutorials/font.html](http://www.s284317130.websitehome.co.uk/tutorials/font.html)



I would like to advise AJB2k3 to read CAREFULLY before shouting that way. :D

Cheers...

P.S.: I would like to invite AJB2k3 to become an author at Ubuntuts.com and contribute for this community driven website rather than blaming it for plagiarism.

---

### Post by Stochastic on 2009-07-29
> **banago said:**
> This article might be of help:

[http://www.ubuntuts.com/how-to-install-fonts-in-ubuntu/](http://www.ubuntuts.com/how-to-install-fonts-in-ubuntu/)

Actually that article really isn't of any help to the issue at hand (Neither is AJB2K's tutorial on installing fonts) as I'm not interested in installing them, I'm interested in FINDING the good ones in the Main and Universe repositories.

---

### Post by Chemical Imbalance on 2009-07-29
Aller is my favorite.

[http://www.fontsquirrel.com/fonts/Aller](http://www.fontsquirrel.com/fonts/Aller)

It is crisp, clear, and professional.

---

### Post by AJB2K3 on 2009-07-30
**Public apology guys, I'm an ejit.**
**@ AlbHeart** - after this act of stupidity I highly doubt they would accept me.
**@ Stochastic** - I dunno if it will help but there is a program called fontforge that may be able to help out as well as 1001freefont.com

---

### Post by AlbHeart on 2009-07-30
> **AJB2K3 said:**
> **Public apology guys, I'm an ejit.**
**@ AlbHeart** - after this act of stupidity I highly doubt they would accept me.


AJB2K3, I am sure they will accept you. :) 
We are dealing with Ubuntu which is a community based development and we respect its philosophy.
We are looking forward to any tutorial you could post to Ubuntuts.com.
If you have any question, please feel free to ask it: 
[email]info@ubuntuts.com[/email]

Kindly
Mirel
Chief Editor
[http://www.ubuntuts.com](http://www.ubuntuts.com)

---

### Post by AJB2K3 on 2009-07-30
Mods please delete

---

### Post by neobux on 2009-08-01
Will having this many fonts slow down certain applications?

I once included a lot of fonts on Windows, and it slowed down how fast certain applications loaded, because those applications had to load fonts it seemed. Has anyone experienced this in Ubuntu? Is this going to make the Gimp come up slow?

---

### Post by AJB2K3 on 2009-08-01
> **neobux said:**
> Will having this many fonts slow down certain applications?

I once included a lot of fonts on Windows, and it slowed down how fast certain applications loaded, because those applications had to load fonts it seemed. Has anyone experienced this in Ubuntu? Is this going to make the Gimp come up slow?
Yes, OO.org does slow down, Gimp used to but I don't have so many anymore.

---

### Post by Stochastic on 2009-08-05
About how many fonts installed does it take to slow Gimp down on say a single core 1.6Ghz box with 2gig ram?

---

### Post by AJB2K3 on 2009-08-05
> **Stochastic said:**
> About how many fonts installed does it take to slow Gimp down on say a single core 1.6Ghz box with 2gig ram?
Dunno depends on many factors so its impossible to give a figure.
Ive collected 232 in my home/.fonts folder alone.

---

### Post by juancarlospaco on 2009-08-05
I got all DaFont.com in a .DEB, send if you want it PM :)

---

### Post by AJB2K3 on 2009-08-06
> **juancarlospaco said:**
> I got all DaFont.com in a .DEB, send if you want it PM :)

:confused: ALL of Dafont? wow how many fonts is that?

---

### Post by juancarlospaco on 2009-08-07
> **AJB2K3 said:**
> :confused: ALL of Dafont? wow how many fonts is that?

All the entire site of fonts :)
PM if you want link, is only 1 .deb on my host.

---

