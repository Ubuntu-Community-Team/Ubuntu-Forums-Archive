---
title: "A windows 98 icon theme for gnome?"
date: 2009-02-23
forum: Art &amp; Design
---

### Post by Bramkaandorp on 2009-02-23
This may seem like a step backwards, but hey, so be it.

Is there any icon theme out there in the Windows 98 style? The gnome default theme comes close... but not close enough.

I started computing on windows 3.1(it was outdated already), but really learned most things on windows 98. So it is mostly the nostalgia. Being able to go back to those years without having to install windows 98 itself.

I am not skilled enough to create the theme myself, so that is out.

Thanks on beforehand.

Cheers,

Bram

---

### Post by kidux on 2009-02-23
You could look on gnome-look.org or deviantart.com.

---

### Post by Bramkaandorp on 2009-02-23
Sadly, gnome-look only offers gnome-xp, and deviantart only offers some desktop icons.

And googling doesn't really help either.

So, If anyone know anything, now is the moment to tell.

Cheers,

Bram

---

### Post by Devport on 2009-02-23
You could create your own theme. The icons are either in apps ( *.exe ) or libs ( *.dll ) - most icons are in two libs, afaik system*.dll and shell*.dll - its been a while so I cant tell for sure which ones. There are tools to extract those icons ( e.g. [http://www.angusj.com/resourcehacker/](http://www.angusj.com/resourcehacker/) ). Then you need to convert those icons to e.g. png and create your own theme by e.g. taking the xp theme you mentioned as a starting point and fill it up with the new icons.

---

### Post by Bramkaandorp on 2009-02-23
Sadly, I don't have windows 98. it was on a computer we had at least 6 years ago

If I had, I would try to create the theme, but I have never done it, so I am afraid I will screw up.

Anyway, If anyone still has windows 98, and can send me the file, I could try. Or am I swimming in dangerous waters now?

---

### Post by Flimm on 2009-02-23
I believe the "Redmond" gtk theme is supposed to look like windows 98.

---

### Post by brandon88tube on 2009-02-23
> **Flimm said:**
> I believe the "Redmond" gtk theme is supposed to look like windows 98.

I think he is right

---

### Post by Bramkaandorp on 2009-02-23
He is right. But that was not the issue. I am looking for an icon theme.

I want the whole '98 experience. Without bsod of course, but you get the idea.

---

### Post by Bramkaandorp on 2009-02-25
I know it isn't that long ago, but doesn't anyone have a clue?

I am seriously considering to make the theme myself, if only I would have the files.

---

### Post by villalcalde84 on 2009-03-03
I'm looking for an icon theme similar to that of Windows 98 too, googling for an answer I found this post. Doing another search I found a package with the icons in this forum ([http://ubuntuforums.org/showthread.php?t=870290]("http://ubuntuforums.org/showthread.php?t=870290"))

The author, Sugi, posted the icons; I ordered them acording to their size but they are in .xpm format, so i assume they have to be converted to .png.

Besides, I think he made a theme but for Kde because of the name of some icons, and also because of the preview image in it.

I hope that someone can make an icon theme for Gnome, or Ubuntu specifically, with this package, it is very complete.

Thanks

---

### Post by Bramkaandorp on 2009-03-03
I can not view the icons at the moment, but I can see by the screen shot that it looks very similar.

Cheers,

Bram

---

### Post by tviuff on 2010-09-04
Hello there

I know it's a long time since the last reply but here goes.

I am also a nostalgic type and want to make my ubuntu 10.04 look like win 95/98 but like so many others I couldn't find a theme. Therefore I was wondering if you succeeded in making the theme or not? If you did could you guide me in how to get it on my laptop?

If not, is there anyone who knows a place to get something that looks like win 95/98?

Cheers

---

### Post by 23dornot23d on 2010-09-04
I have never created themes before but if you want to .... use this to convert from xpm to png

I just tried it on one and it works ok ...... needs to be made into a batch command though.
and done using the icons in the file already posted.

convert ark.xpm -matte -transparent white -type palette image.png


or a small batch script .... put this small script into the directory with the icons

gedit xpmpng.sh
         (cut and paste the text from below into it and save it ..... then to make it executable do the following)

chmod u+x xpmpng.sh

         *(put it in the directory with the icons then do the following)

./xpmpng.sh

```

echo "Script Starting.."

echo "start For loop"
for pic in *.xpm
do
        echo "converting $pic"
        convert $pic -matte -transparent white -type palette  $(basename $pic .xpm).png
done
# This will make a separate directory for them called png
mkdir png
# This will copy the png files to it ....
mv *.png png

echo "finished"


```


Interesting read ..... [how to make effective icons for Gnome ]("http://library.gnome.org/devel/hig-book/stable/icons-design.html.en")


I like the idea of merging [two things together]("http://www.axialis.com/docs/iw/Batch_merge_images.htm") to enhance its appearance too ..... not sure how to do this ......

Like to merge a nice reflective or shiny button ..... to the existing icons ...... is it possible using Gimp or Imagemagick

---

### Post by kriukov on 2011-01-29
I managed to theme Ubuntu pretty close to Win98. [Here]("http://auburn.edu/~nzk0001/sci/workshop.htm#2011-01-29") I described how to do that and posted a screenshot.

---

### Post by Bramkaandorp on 2011-02-02
A really cool theme.

There is a small issue though, called the gtkrc file. After putting it into my home folder and reloading Gnome, everything on the desktop went haywire, including maximised programs.

Otherwise a great theme.

Cheers

---

### Post by kriukov on 2011-02-07
You should not put the gtkrc file into your home folder. It should be in 

/usr/share/themes/Redmond/gtk-2.0/

---

### Post by Bramkaandorp on 2011-02-13
Your file really made the difference. Thanks a lot!

Cheers

---

