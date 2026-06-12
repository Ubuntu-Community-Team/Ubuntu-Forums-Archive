---
title: "undoing an update..."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Hranj on 2007-11-19
is there a way that i can undo an update to my computer? the most recent update i did updated Mplayer and now it wont play .avi files. thanks.

---

### Post by tprzepiorka on 2007-11-19
As far as I know there is no way of undoing an update. I'm sure there is a fix for the Mplayer problem though.

---

### Post by Myrgen on 2007-11-20
Same problem here. AVI files work just fine in Totem or Xine, but Mplayer refuses to play them. Anyone has a fix yet? Thanks in advance :)

---

### Post by zvacet on 2007-11-20
if you have both versions in var/cache/apt/archives you can downgrade by installing lower version with command

```
sudo dpkg -i packagename
```

when you are finish go to synaptic and find** mplayer>mark it>packages>lock version**

Better solution will be to find fix for that problem.

---

### Post by coolguy2006delhi on 2007-11-20
There may be some codec problem. You should try reinstalling the properitary codecs. I hope you have all the codecs list . These are the codecs 

gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 

gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

Check if anyone of them is not installed !

---

### Post by Myrgen on 2007-11-20
Indeed, I was missing all the gstreamer0.10-plugin-ugly* suite. Now, most AVI files play correctly, thank you so much. Just a few remain impossible to open with MPlayer. However, I cannot find the libxine-extracodecs.. Where could I get them?

---

### Post by zvacet on 2007-11-20
There is no **libxine-extracodecs** for Gutsy.I think it is replaced with other codec,bit I don´t know with wich one.Try 

```
sudo aptitude install libxine-extracodecs
```

and maybe you will get that information.

---

### Post by Myrgen on 2007-11-20
Thank you for the tip. I had already tried that, with the result as follows:

> myriam@aurora:~$ sudo aptitude install libxine-extracodecs
[sudo] password for myriam:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for libxine-extracodecs
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
myriam@aurora:~$ 


Any further idea? :)

---

### Post by Myrgen on 2007-11-21
I've applied the suggestion in this thread: 

[http://ubuntuforums.org/showthread.php?t=618703]("http://ubuntuforums.org/showthread.php?t=618703")

and it now works fine, after the downgrade of the MPlayer package. :)

---

### Post by nocturn on 2007-11-21
> **Hranj said:**
> is there a way that i can undo an update to my computer? the most recent update i did updated Mplayer and now it wont play .avi files. thanks.

Go in synaptic, select the package and then you should look for an option to show versions.  That allows you to select a different version from the list.  
After that, lock the package (in synaptic) to prevent further upgrades.

---

