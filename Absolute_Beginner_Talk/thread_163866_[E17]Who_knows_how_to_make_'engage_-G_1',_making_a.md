---
title: "[E17]Who knows how to make 'engage -G 1', making a thumbnail ??"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-04-21
Who knows how to make engage -G 1, making a thumbnail ??
with fvwm ??

I can get only the icon in the engage bar ... 
No thumnbnail ..

Thx 

Patrick

---

### Post by Paulus on 2006-04-21
I wasn't aware engage was capable of doing thumbnails, is this a cvs update?

---

### Post by patrick295767 on 2006-04-21
[QUOTE=Paulus]I wasn't aware engage was capable of doing thumbnails, is this a cvs update?[/QUOTE]
  
This is possible via fvwm (E17 installed).. .
Look there :[http://www.guistyles.com/wp-gallery/Fvwm-OSX_Milky-02.jpg](http://www.guistyles.com/wp-gallery/Fvwm-OSX_Milky-02.jpg)

Greetings !!

---

### Post by ThomasAdam on 2006-04-21
[QUOTE=patrick295767]This is possible via fvwm (E17 installed).. .
Look there :[http://www.guistyles.com/wp-gallery/Fvwm-OSX_Milky-02.jpg](http://www.guistyles.com/wp-gallery/Fvwm-OSX_Milky-02.jpg)

Greetings !![/QUOTE]

What is it you're asking?   How to generate the thumbnails, or how to have them appear in this 'engage' thingy?  (Of which FvwmButtons within FVWM is superior to it anyway).

-- Thomas Adam

---

### Post by patrick295767 on 2006-04-22
[QUOTE=ThomasAdam]What is it you're asking?   How to generate the thumbnails, or how to have them appear in this 'engage' thingy?  (Of which FvwmButtons within FVWM is superior to it anyway).

-- Thomas Adam[/QUOTE]
  
This screenshot : [http://www.guistyles.com/wp-gallery/Fvwm-OSX_Milky-02.jpg](http://www.guistyles.com/wp-gallery/Fvwm-OSX_Milky-02.jpg)
has some thumbnails in the docker bar ....

Looks very nice target ! 

Greetz

---

### Post by patrick295767 on 2006-04-23
I have found these code from milky fvwm theme (mac os x):
  
```
###################################################################
### Thumbnail in Engage (E17 part)
### BY KarnEvil,cptmorgan and Gulivert
### http://forums.gentoo.org/viewtopic.php?t=292447
### http://forums.gentoo.org/viewtopic.php?p=2084007#2084007
###################################################################

DestroyFunc Thumbnail
AddToFunc Thumbnail
+ I Raise
+ I PipeRead "$[fvwm_scripts_path]/minimize/build.sh $[w.id] \"$[w.name]\""
+ I Iconify

DestroyFunc DeThumbnail
AddToFunc DeThumbnail
+ I Iconify
+ I MoveToDesk 0 $[desk.n]
+ I Exec sleep 1.5 && rm -f $[HOME]/.e/apps/engage/launcher/$[w.id].eapp

###################################################################

```
   
```
#!/bin/sh
###################################################################
### Thumbnail in Engage (E17 part)
### By KarnEvil and cptmorgan
### http://forums.gentoo.org/viewtopic.php?t=292447
### http://forums.gentoo.org/viewtopic.php?p=2084007#2084007
###################################################################


cd ~/theme-fvwm/scripts/minimize

xwd -silent -id $1 > .temp.xwd

resolution=`identify .temp.xwd | cut -d" " -f 3`
width=`echo $resolution | cut -dx -f1`
height=`echo $resolution | cut -dx -f2`
if [[ $height -lt $width ]]; then
        convert -resize 194x -frame 1x1 -mattecolor black -quality 0 xwd:.temp.xwd png:.temp.png
        composite -geometry +0+$(((196-($height*196/$width))/2)) .temp.png transparent.png icon.png
else
        convert -resize 196 -frame 1x1 -mattecolor black -quality 0 xwd:.temp.xwd png:icon.png
fi

edje_cc -id . -fd . icon.edc icon.eapp

enlightenment_eapp \
icon.eapp \
-set-name "$2" \
-set-generic "$1" \
-set-comment "$1" \
-set-exe "FvwmCommand \"WindowId $1 DeThumbnail\"" \
-set-win-name "$1" \
-set-win-class "$1" \
-set-wait-exit "1" \

cp -f icon.eapp ~/.e/apps/engage/launcher/$1.eapp

```
  
[http://fvwm.lair.be/viewtopic.php?t=203](http://fvwm.lair.be/viewtopic.php?t=203)

---

### Post by patrick295767 on 2006-04-23
Nice screenshot : [http://chronomancy.free.fr/fvwm/screenshot_050211_0717.jpg](http://chronomancy.free.fr/fvwm/screenshot_050211_0717.jpg)

:-)

---

