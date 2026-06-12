---
title: "batch image conversion"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by seepage87 on 2008-04-01
I really don't know much about CLI scripting, but I want to make a bmp copy of all my jpg album art in my music folder.  Basically I have:

/music/artist 1/album 1/cover.jpg
/music/artist 1/album 2/cover.jpg
/music/artist 2/album 1/cover.jpg
/music/artist 2/album 2/cover.jpg
etc.

and I want a bmp copy of each of the cover.jpgs.  Doing this manually isn't an option, obviously, since there's a lot of artists and even more albums.  Ideally I'd want the conversion to be as unlossy as possible.  Any suggestions?

---

### Post by aeiah on 2008-04-01
have a look here: [http://ubuntuforums.org/showthread.php?t=736931](http://ubuntuforums.org/showthread.php?t=736931)

word on the street seems to be either phatch or image magick

---

### Post by seepage87 on 2008-04-02
Phatch looks promising

> can duplicate (sub)folder hierarchies

Looks easy too, though I wouldn't mind having used this as an excuse to pick up some CLI scripting skills... Girls only like guys of have good skills :(

---

### Post by ezzieyguywuf on 2008-04-05
Is it me or is the save function in phatch broken? Anytime I try to save in <folder> and i drop a folder in with subdirectories, it goes into the first subdirectory and then saves the image in the parent folder. see illustration.

ls /music/Artist
  Album1  Album2   Album3


Now, if I drop the Artist directory into a phatch session, with the only action bein- Save, filename:cover, as: jpeg, in:<folder> - it will go into album1, do the conversion (the files are bmp right now) then save it in Artist and stop. Can anyone verify this/help me fix it? I really want to convert all my files for my shiny new Cowon D2 :-D

---

### Post by PointyWombat on 2008-04-05
Hi seepage87,

I enjoy these little scripting one-liner challenges.

The following will find all your jpg images, descending from the directory you run it in and convert the jpg images it finds to bmp images. The original image is untouched. This is with the ImageMagick **convert** command.

```

for img in `find . -type f -name "*.jpg"`; do convert "$img" "${img/.jpg}".bmp; done

```

Example:

I'm in a directory which has a couple subdirectoryies with jpg images in it:

```

$ **find .**
.
./crap
./crap/image2.jpg
./crap/images.jpg
./crap/fooo
./crap/fooo/abcd.jpg
./crap/fooo/xyz.jpg
./junk
./junk/crap.jpg
./junk/foo.jpg
$ 
**$ for img in `find . -type f -name "*.jpg"`; do convert "$img" "${img/.jpg}".bmp; done**
$
**$ find .**
.
./crap
./crap/image2.jpg
./crap/image2.bmp
./crap/images.jpg
./crap/images.bmp
./crap/fooo
./crap/fooo/xyz.jpg
./crap/fooo/xyz.bmp
./crap/fooo/abcd.jpg
./crap/fooo/abcd.bmp
./junk
./junk/crap.jpg
./junk/crap.bmp
./junk/foo.jpg
./junk/foo.bmp
$

```

Keep in mind that converting from jpg to bmp can increase the file size 10 fold. Make sure you have enough space.

Hope this helps!

---

### Post by stani on 2008-04-05
> **ezzieyguywuf said:**
> Is it me or is the save function in phatch broken? Anytime I try to save in <folder> and i drop a folder in with subdirectories, it goes into the first subdirectory and then saves the image in the parent folder. see illustration.

ls /music/Artist
  Album1  Album2   Album3


Now, if I drop the Artist directory into a phatch session, with the only action bein- Save, filename:cover, as: jpeg, in:<folder> - it will go into album1, do the conversion (the files are bmp right now) then save it in Artist and stop. Can anyone verify this/help me fix it? I really want to convert all my files for my shiny new Cowon D2 :-D
Hi, I am the author of Phatch. You can help improve the Phatch documentation as it is a wiki:
[http://photobatch.wikidot.com/action-save](http://photobatch.wikidot.com/action-save)

You need to study:
[http://photobatch.wikidot.com/variables](http://photobatch.wikidot.com/variables)

If I guess your problem right, you forgot to add the <subfolder>:
<folder>/<subfolder>
or if you want to copy the folders:
<folder>_copy/<subfolder>

---

### Post by ezzieyguywuf on 2008-04-05
Thanks stani that did solve my problem. I had taken a look at the variables page, but I guess I did not understand it completely :-D thanks for your help man and great program!

---

### Post by happyisland on 2008-05-11
Hey stani,
I just wanted to write to thank you for a great application. I just discovered phatch today and I am very pleased with how well it works. Great job!

---

