---
title: "Humanity icon theme has some bitmap files with wrong extension names?"
date: 2010-10-07
forum: Art &amp; Design
---

### Post by t.rei on 2010-10-07
Hi,

as I am trying to create a universal "gnome theme to kde theme" kind of script - at least for the humanity theme I ran into something that puzzled me at first:

```

inkscape PNG/24x24/apps/gnome-eterm.svg --export-png=gnome-eterm.png
PNG/24x24/apps/gnome-eterm.svg:1: parser error : Start tag expected, '<' not found
&#65533;PNG
** (inkscape:28081): WARNING **: Specified document PNG/24x24/apps/gnome-eterm.svg cannot be opened (does not exist or not a valid SVG file)

```I kindof skipped the important information: "[COLOR=DarkRed]not a valid SVG file[/COLOR]"

Now, I am not even going to ask why this Bitmapfile has .svg as a suffix (that has got to be a bad joke? It wouldn't even HURT if it was called .png the theme would WORK!)

What I would like to know is a good way to determine the filetype in a shellscript.

right now I am running something like this:
```
mkdir -p $outdir
cp $inputdir/*.* $outdir/
cd $outdir
for i in *; do inkscape $i --export-png=`echo $i | sed -e 's/svg$/png/'`; done
rm *.svg
```don't be surprised I used the cp way to resolve all the links to proper files on my quest to find the error. It's going to change back to not copying anything. For now, thats not the problem I'm having.


Shot sumup of the question:
How can I find out if a file a.svg is not actually a.png just with a 'wrong' suffix?

Thanks.


-----------
*edit*

I am just accepting some error messages now. My script looks like this:
```

#!/bin/bash
indir="/home/myname/Humanity"
outdir="/home/myname/Humanity-PNG"
#===============================================================================

for cate in actions animations apps categories devices emblems mimes places status stock
do 
    for size in 16 22 24 32 48 64 128
    do
        #-------------------------------------------------------------------------------
        iapp=$indir/$cate/$size
        oapp=$outdir/$size'x'$size/$cate
        echo "========================================================================="
        echo "converting: $cate at size: $size"
        mkdir -p $oapp
        cp $iapp/*.* $oapp/
        cd $oapp
        for i in * 
        do
            t=$( file --mime-type "$i" )
            if [ "$t" = "$i: image/png" ]
            then
                mv $i `echo $i | sed -e 's/svg$/png/'`
                mv $i `echo $i | sed -e 's/xpm$/png/'`
            else
                inkscape $i --export-png=`echo $i | sed -e 's/svg$/png/'`
            fi
        done
        rm *.svg
    done
done

```seems to work fine so far. :)

---

