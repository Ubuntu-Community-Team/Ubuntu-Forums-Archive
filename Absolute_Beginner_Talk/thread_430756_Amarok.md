---
title: "Amarok"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by OscarL on 2007-05-02
Amarok finds about a 10th of all my music files. How do I get it to find the rest and put it in the collection?

---

### Post by starcraft.man on 2007-05-02
Do you have all the codecs installed to play the restricted audio and video formats? If you didn't install those its likely amarok wouldn't see your MP3s. 

Two ways to install depending on your preference.

Make sure you have all the extra repos, I think w32 and a few others are in medibuntu. Guide to adding repos [here.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") If your using edgy or dapper, use the links in my sig and check for the same section titled "Add Extra Repositories". Make sure to add your versions repos.

Synaptic Package Manger: (If you like Gui)

1) Go System > Administration Synaptic Package Manger.

2) Search for gstreamer, search button is on the right of the main bar.

3) Tick off all of the "gstreamer0.10" packages, EXCEPT those that end in -dev -dbg or -doc (with or without the hyphen)

4) Push apply.

Terminal: (Text Install)

1) Open terminal via Applications > Accesories > Terminal

2) Type in this to terminal:

```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

If you do have those installed, then it might be a specific problem with the program that might be faulty. Try rhythmbox and see if it detects your library.

---

### Post by Ianman on 2007-05-02
You probably don't have all the right codecs installed. In my case I used Automatix2 to install codecs and after that Amarok found all my music!

Hope this helps.

---

### Post by OscarL on 2007-05-03
Tried bot to copy those lines into terminal and install the codecs from Automatix2... sure, it found a couple of more songs but still not all of them...

---

