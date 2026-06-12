---
title: "Software/commands to move &amp; rename photos based on EXIF data or tags?"
date: 2010-10-23
forum: Art &amp; Design
---

### Post by Mander on 2010-10-23
I have a huge folder of old images that I would like to re-organize.  Most of them have been dumped into folders that are vaguely descriptive, but there are lots of duplicates, cruddy images that don't really need to be saved, etc.

I have been working on establishing some file naming conventions and a set of tags that I can use to describe all of the images consistently.  It would be nice if I could then use those tags (which, depending on the software you use, can be written to the file itself) to automatically move the files into subdirectories.

Does this make any sense?  I envision it working something like the windows program MP3tag, which you can use to assign properties like artist/album to a group of files, then automatically move those files from their existing subdirectories into a single folder by album, and/or rename the files to something like "artist - track name", depending on which fields you tell it to use.  I know that software like Windows Photo Gallery or DigiKam can assign similar info to the files based on the tags you add, but I don't think that they can rename or move them using this information.

Does anyone know of such a program?  It can be either Linux or Windows, I use both on my computer.

---

### Post by lykeion on 2010-10-23
I don't know how much command-line experience you have, but I can outline how you could do this using commands and bash script.
In this example I'm using command-line tools **jhead** and **imagemagick** to add and read comments to a photo file

1. Install command-line tools:
```
sudo apt-get install jhead imagemagick
```
2. Add/edit comment to a jpeg photo using jhead:
```
jhead -ce <filename>.jpg
```
This command will open up the text editor defined in the EDITOR variable to let you add/edit a comment to the photo.
You can set f.e. gedit as your text editor with this command:
```
export EDITOR=gedit
```
You could also use imagemagick convert to add a comment directly like this
```
convert -comment "tag" <filename>.jpg <new_filename>.jpg
```
3. Read comment line stored in the photo using imagemagick identify command:
```
identify -format "%c" <filename>.jpg
```
To remove newlines add a little sed:
```
identify -format "%c" <filename>.jpg |sed '/^.*$/N;s/\n//g' 
```

This is a start, you can continue with creating a nautilus script to let you add comment to photos from nautilus, and create a script where you read the tag stored in comment and move the photo to a directory with the name of the tag.

[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)
[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

---

### Post by Mander on 2010-10-25
Wow, that is awesome! Thanks!  I'm relatively new to Linux so I often forget to look for command line solutions.

WRT your suggestions: can I add multiple tags all in one line, or do I need to run separate commands for that?  I presume that running the "comment" command a second time will overwrite whatever I put in the first time.

---

### Post by lykeion on 2010-10-25
Multiple tags...ok, let's see. The comment of the image is text, so you could have as many tags as you'd like, 
heck you could even write a little short-story there if you'd like :)

[FONT="Courier New"]jhead -ce[/FONT] will edit the comment if exists otherwise create new
[FONT="Courier New"]convert -comment[/FONT] will overwrite (I think)

To parse the tags with a script and automatically create/move to dirs, you'd need tag them systematically. 
By that I mean you need to use a special character to separate tags, and also define what the order of the tags mean. 
Hope you've followed me so far.

An example, say you want to tag a couple of images like this:
image1.jpg - photos,vacation
image2.jpg - photos,portrait
image3.jpg - archive

And you'd like to automatically create/move to dirs like this:
photos/vacation/image1.jpg
photos/portrait/image2.jpg
archive/image3.jpg

The system is comma as tag separator and the order is: dir,subdir,sub-subdir (etc)

That way it'd be easy to create a script that parsed the tags with [FONT="Courier New"]identify -format "%c"[/FONT]
Learning to write bash scripts is extremely useful in a Linux environment, so I'll let you do the scripting yourself. 
The links in my previous post are useful, and if you need any help just post your question and I'll try to answer. 
Good luck :P

---

