---
title: "recursive file renaming?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-12-30
What would be the easiest way to recursivly go through my music directory and rename all images to either cover.png or cover.jpg depending on what the file extension is?

Also how would I recursivly go through and remove all files that end in .mood?

---

### Post by aktiwers on 2007-12-30
[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by unabatedshagie on 2007-12-30
Thanks for that but how would I get it to recursively go through all the directories?

If I'm reading the man page right it doesn't have a recursive option so I would have to go into every directory manually and run the command.

---

### Post by vanadium on 2007-12-30
The find command can search all files, and using the -exec option you can act on each file found. What you exactly want to do is unclar, though. If you "rename all images to either cover.png or cover.jpg" you will delete images if there is more than one. Suppose, however, you would like to rename all "folder.jpg" images to "cover.jpg" then an easy way would be to issue, from within the top directory:

find . -iname folder.jpg -execdir mv {} cover.jpg \;

---

### Post by aktiwers on 2007-12-30
Yes thats what I found too.
Like here:
[http://ubuntuforums.org/showthread.php?t=557359](http://ubuntuforums.org/showthread.php?t=557359)

But this is to rename the extentions..  now if all your "cover" pictures has deferent names a GUI method would be better.

Install Krename:
```
sudo apt-get install krename
```
Run Krename
```
krename
```

Click on "Please add some files.."

In the Location field type in the path to the folder containing all other folders with the jpg and png's in.

In the filter type: ```
*.jpg
```

And mark the "Add subdirectories recursively"

and click "open".

Then do the same again, only this time type ```
*.png
``` in the Filter place.

Finally go to the Filename tab and in the "Template" Field, delete the $ and type in "Cover".

This should rename them all.

---

### Post by nick_h on 2007-12-30
> But this is to rename the extentions.. now if all your "cover" pictures has deferent names a GUI method would be better.

The find method also works, just use:
```
find . -name "*.jpg" -execdir mv '{}' cover.jpg \;
```

---

### Post by unabatedshagie on 2007-12-30
Woh, thanks for the info.

Basically what I have is album covers inside album folders. They are either .jpg or .png files but they are all different names. Some are in the form {artist}_{album}.ext, some are folder.ext etc.

I'm just wanting some way to change all the image names to cover.ext, I don't have to worry about overwriting images because there will only be one image inside each folder.

I'll have a look at krename but I don't really want to install a kde app if I can avoid it.

---

### Post by Fixman on 2007-12-30
Maybe this will be faster and more useful

```

cd [[directory]]
ls -1R | grep .jpg | xargs -f cover.jpg
ls -1R | grep .png | xargs -f cover.png

```

There will be far faster.

---

### Post by nick_h on 2007-12-30
Please note that you need to use -execdir not -exec because you want the command executed in the directory that the file is in.

If you ran my original command you would just keep overwriting a single file each time.

---

### Post by MrFSL on 2007-12-30
note also that you will probably want to run these commands ignoring case.

In the example of find you can use:```
find ./ -iname "*.jpg" -execdir mv '{}' cover.jpg \;
```

In the case of grep you can use:
```
ls -1R | grep -i .jpg | xargs -f cover.jpg
```

Just my two cents. ;)

---

### Post by unabatedshagie on 2007-12-31
Thanks for all the help, I tried the grep command but the terminal said that **-f** was an invalid option.

---

### Post by ghostdog74 on 2007-12-31
> **MrFSL said:**
> 

In the case of grep you can use:
```
ls -1R | grep -i .jpg | xargs -f cover.jpg
```



no need for grep. Use shell expansion
```

ls -1R *.[jJ][pP[gG] | blah..........

```

---

### Post by ghostdog74 on 2007-12-31
> **unabatedshagie said:**
> What would be the easiest way to recursivly go through my music directory and rename all images to either cover.png or cover.jpg depending on what the file extension is?

Also how would I recursivly go through and remove all files that end in .mood?

change all .png to .jpg using rename, if you have it
```

# rename .png .jpg *.png

```
using find
```

find /fullpath -type f -name "*.[pP][nN][gG]"   | while read filefound
do
    mv "$filefound" "${filefound%.???}.jpg"
done

```

---

### Post by vanadium on 2007-12-31
This shows that in the shell, there are sometimes different ways to accomplish things, one simpler than the other.

---

### Post by nick_h on 2007-12-31
> Thanks for all the help, I tried the grep command but the terminal said that -f was an invalid option.
That suggestion doesn't work. The intention was to generate a list of files using *ls* and then build up a move command using *xargs*.  The -f option is invalid for *xargs* and there is no command specified.

---

