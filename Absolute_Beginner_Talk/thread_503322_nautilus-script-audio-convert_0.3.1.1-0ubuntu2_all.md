---
title: "nautilus-script-audio-convert_0.3.1.1-0ubuntu2_all help"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-17
i have install it but when i right the music file and the script thing i can't find the audio convert script

---

### Post by raja on 2007-07-17
Where is the script file? It has to be in ~/.nautilus/scripts or ~/.gnome/nautilus-scripts.

---

### Post by zerobinary on 2007-07-17
it wasn't in there

---

### Post by raja on 2007-07-17
I dont know what this particular script is that you are installing. But for any script, all you have to do is to have it in the specified folder. This is one of the above depending on the version of nautilus that you have. You can also instead use the script as a nautilus action, which I think is a more elegant solution since you have control over the file types for which the option will appear in the right-click menu.

---

### Post by zerobinary on 2007-07-18
then is there audio convert script for that available  u know and recommand

---

### Post by raja on 2007-07-19
What script are you trying to use ? Can you give a link for the place where you got it ?

---

### Post by zerobinary on 2007-07-19
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fa%2Faudio-convert%2Fnautilus-script-audio-convert_0.3.1.1-0ubuntu2_all.deb&md5sum=a543c965c6c0a1ac5e715aab5f847aa0&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fa%2Faudio-convert%2Fnautilus-script-audio-convert_0.3.1.1-0ubuntu2_all.deb&md5sum=a543c965c6c0a1ac5e715aab5f847aa0&arch=all&type=main)
then i update using update manager
now when i click on this i got this image 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-5.png[/IMG]

---

### Post by raja on 2007-07-19
Looks like you have to enable the script first - if you have not already done this, try```
nautilus-script-manager enable ConvertAudioFile
```

---

### Post by zerobinary on 2007-07-22
```
zerobinary@zerobinary-desktop:~$ nautilus-script-manager enable ConvertAudioFilePlease restart nautilus to get an updated menu.

```
```
 you don't have the right codec to decode the selected file. missin' codec: flac
```

---

### Post by zerobinary on 2007-07-23
plz help i need ur help

---

### Post by raja on 2007-07-23
```
sudo aptitude install flac
```
And then try the command again.

---

### Post by zerobinary on 2007-07-23
i can convert now but the problem is where is the output file
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-3-3.png[/IMG]

---

### Post by bodhi.zazen on 2007-07-23
Ah, I see what you are asking now ...

Well, lets search for it ...

Start with that music directory on your desktop ...

Otherwise look in your home directory ...

---

### Post by zerobinary on 2007-07-23
i did not there
it never ask me for the directory

---

### Post by raja on 2007-07-24
Sorry, I have never had to use this script.
But I downloaded the source and looked through it.
In the conversion section there is this code ...
```
out_file=`echo "$in_file" | sed 's/\.\w*$/'.$formatout'/'`
```
To me, this means that the outfile will have the same name as the in file with just the new extension.
So, if your file is '/home/XXX/test.wav' and you convert it to mp3, it should be '/home/XXX/test.mp3'.
What exactly are you using this script for?

---

### Post by zerobinary on 2007-07-24
convert flac to aac

---

### Post by raja on 2007-07-24
Like I said, you should find the converted file in the same folder. If not, try to use other methods like the one suggested [here]("https://help.ubuntu.com/community/CDRipping#head-61f3b32e3a56a998568cad44e305d1557e7ffee0").

---

