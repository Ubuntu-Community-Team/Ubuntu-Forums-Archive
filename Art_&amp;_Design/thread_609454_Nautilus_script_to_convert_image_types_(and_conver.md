---
title: "Nautilus script to convert image types (and convert question)?"
date: 2007-11-11
forum: Art &amp; Design
---

### Post by smartboyathome on 2007-11-11
I was wondering if there was a nautilus script for converting image types. This would be a great help for me. Also, if not, is there a way to use the convert tool on imagemagick to convert several images to PNG while keeping their origional filename (the part be for the .* part). Thanks for the help!

---

### Post by geirha on 2007-11-11
It's not too hard to make such a script. Here's an example script 
```
#!/bin/bash

scriptname=`basename $0`
# Determine image type to convert to based on the name of the script
newext=`echo $scriptname | sed 's/convert.to.\(.\+\)/.\1/'`
logfile=`mktemp -t $script_name.XXXXXX`

tail -f $logfile | zenity --text-info --title="Converting images to $newext" &
for image in "$@"; do
    # Determine target image name
    target=$(echo $image|sed 's/\(.*\)\..\+/\1/')$newext
    echo "$image -> $target" >> $logfile
    convert "$image" "$target"
done

echo done >> $logfile
rm -f $logfile

```

If you save this script as ~/.gnome2/nautilus-scripts/convert_to_png you will be able to select several images in nautilus, and convert them to png. foo.jpg will be converted to foo.png (was this what you meant by keeping the original filename?)

The script decides what filetype to convert to based on the script's name, so making symlinks for other image types will let you use the same script. i.e. 
```
cd ~/.gnome2/nautilus-scripts/
ln -s convert_to_png convert_to_jpg
ln -s convert_to_png convert_to_gif

```
With the above symlinks, you can convert to jpg and gif as well.

---

### Post by smartboyathome on 2007-11-11
> **geirha said:**
> It's not too hard to make such a script. Here's an example script 
```
#!/bin/bash

scriptname=`basename $0`
# Determine image type to convert to based on the name of the script
newext=`echo $scriptname | sed 's/convert.to.\(.\+\)/.\1/'`
logfile=`mktemp -t $script_name.XXXXXX`

tail -f $logfile | zenity --text-info --title="Converting images to $newext" &
for image in "$@"; do
    # Determine target image name
    target=$(echo $image|sed 's/\(.*\)\..\+/\1/')$newext
    echo "$image -> $target" >> $logfile
    convert "$image" "$target"
done

echo done >> $logfile
rm -f $logfile

```

If you save this script as ~/.gnome2/nautilus-scripts/convert_to_png you will be able to select several images in nautilus, and convert them to png. foo.jpg will be converted to foo.png (was this what you meant by keeping the original filename?)

The script decides what filetype to convert to based on the script's name, so making symlinks for other image types will let you use the same script. i.e. 
```
cd ~/.gnome2/nautilus-scripts/
ln -s convert_to_png convert_to_jpg
ln -s convert_to_png convert_to_gif

```
With the above symlinks, you can convert to jpg and gif as well.

That is what I meant by keeping the origional filename, and thanks for the script, I will try it out!

---

### Post by geirha on 2007-11-11
Note that it if you convert foo.jpg to foo.png, and foo.png allready exist, it will overwrite it without asking. If you know a little bash scripting, it's easy to add a little check for that though.

---

### Post by smartboyathome on 2007-11-11
Unfortunately, I know very little bash scripting, but this script works great! I just converted a whole bunch of windows icons to png.

---

