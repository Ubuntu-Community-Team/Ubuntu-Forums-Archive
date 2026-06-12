---
title: "playing dvds"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by daf1 on 2007-03-15
Hi everyone,
have installed ubuntu 6.10 on my spare computer at home, most things seem to be working ok have just got onto web and e-mail, having a problem playing DVD's
have TOTEM and have just installed GEXINE and am getting this error

No URI handler implemented for dvd

same message for totem and gexine can any one tell what it is and how to fix
daf1

---

### Post by arochester on 2007-03-15
Have you installed libdvdcss2? Look at "RestrictedFormats" at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by lamalex on 2007-03-15
do you have libdvdcss2 installed?

medibuntu.sos-sts.com/

will allow you get it, just FYI its illegal in us so use it at your own risk. .. I doubt the legality has stopped too many people though.

---

### Post by John.Michael.Kane on 2007-03-15
Frist make sure all the repos enabled.You can uncomment the lines running the command listed.
```
gksudo gedit /etc/apt/sources.list 
``` you should see a few lines with # next to it remove that symbol.

save the file,and run 

```
gksudo aptitude update
```


Next up installing the files you want.

Run the command listed:
```
gksudo aptitude install acidrip brasero libdvdread3 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui 

```

After that.

Run this:
```
gksudo /usr/share/doc/libdvdread3/install-css.sh
```

Hope this helps.

---

### Post by daf1 on 2007-03-15
hi SD,
Tried that,
 totem gives same error
gexine played a slide show dvd that I made
tried to play THE CROW and it hung up
tried another DVD got the intro telling me it was for sale and not for rent (legit)
and that was it
daf1

---

### Post by John.Michael.Kane on 2007-03-15
The gstreamer version of totem maybe giving you issue.

Try installing totem-xine. 
```
gksudo aptitude install totem-xine
```

---

### Post by daf1 on 2007-03-15
hi sd 
tried same results only THE CROW does not hang the machine 
totem starts as default and reports "do not have appropriate plugins"
daf1

---

### Post by John.Michael.Kane on 2007-03-15
Thats odd. are these dvd's Org/backup's or are these rips that are on your harddrive?

If totem wont play them theres two more programs I can think of which *may* play your movies.
```
gksudo aptitude install mplayer vlc
```

---

### Post by lamalex on 2007-03-15
i have never gotten totem to work, vlc has always done a better job for me.

---

### Post by panch0 on 2007-03-15
Install MPlayer, then run from the command line:

mplayer dvd://

If it doesn't work, post the output you get.

---

### Post by daf1 on 2007-03-16
thanks for the tips and suggestions will give them a try will let you know asap
daf1

---

### Post by daf1 on 2007-03-16
hi SD
just tried

gksudo aptitude install mplayer vlc

got whole screen of text that ended with:

0 packages upgraded, 24 newly installed, 0 to remove and 141 not upgraded.
Need to get 20.2MB of archives. After unpacking 45.5MB will be used.
Do you want to continue? [Y/n/?] y

answered Y
and nothing happened it just sat there (still sitting there now as I write) did vlc install if it did where is it

AROCHESTER I also looked at the site for libdvdcss2 but did not know how to install it
DAF1

---

### Post by daf1 on 2007-03-19
can anyone give me some info on this 
DAF1

---

### Post by meborc on 2007-03-19
you didn't install vlc yet... you probably need to do```
sudo apt-get update
```and then```
sudo apt-get install vlc
```try vlc... it's my choice of player for movies and dvd's :p

---

### Post by GSF1200S on 2007-04-08
Only on Linux would I have a damn problem playing DVDs... Im getting burned out on finding new problems everyday.

Ok, so VLC is installed, and it does no good. Hell, I dont even know if Im launching it right. It opens a window and then just closes and says nothing. I think im going to have to boot windows just to watch a movie.

Pathetic..

---

### Post by masterch on 2007-04-08
Why dont use XINE Movie Player instead?? Works greate for me...

Regards

---

### Post by GSF1200S on 2007-04-08
> **masterch said:**
> Why dont use XINE Movie Player instead?? Works greate for me...

Regards

Oh hey.. dont take this the wrong way. It just makes me mad... you have to have an illegal decryptor to watch movies on Linux? That doesnt make sense... Just more corporate domination that crawls under my skin.. Xine didnt work by the way..

---

### Post by r00tintheb0x on 2007-04-08
No software to decrypt DVDs is free.

---

### Post by GSF1200S on 2007-04-08
> **r00tintheb0x said:**
> No software to decrypt DVDs is free.

Awesome... its not enough for them to get money for the DVD... and I cant legally make a free DVD player without paying a fee for the decoders. I hate the world, and its greedy people..

---

### Post by Nythain on 2007-04-08
not sure if libdvdcss2 is in the main repos, i got mine from seveas... but libdvdread3 is in either the universe or multiverse and it should possibly do the trick

---

### Post by GSF1200S on 2007-04-08
> **Nythain said:**
> not sure if libdvdcss2 is in the main repos, i got mine from seveas... but libdvdread3 is in either the universe or multiverse and it should possibly do the trick

Well, this allowed me to view the previews, but it would never take me to the movie menu.. it just acted like the DVD was over... I wonder why?

---

### Post by johnnylong on 2007-05-08
Pancho,
  Thanks. MPlayer works like a charm. Do you know anyting about the Xine Movie Player.
  Holla Back...  Hack the Planet!!

---

### Post by johnnylong on 2007-05-11
Just wanted everyone to know that I was able to get not only the MPlayer, but also the Xine Movie Player and Totem working. Thanks for all the help!

Hack the Planet!!

---

### Post by gohanssjn on 2007-05-11
Ok, here's an idea for you.

Tell your computer to play the DVD upon load.

If I tell totem to load the DVD, I get errors, plugins not available errors.  but if I instead tell it to play cdrom0, it plays fine.

Hope that helps!

---

### Post by rggavubt on 2007-05-14
I can't play DVD's since I upgraded to Feisty.  I have mplayer and ran the command and got this :

Playing dvd://.
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://.

---

### Post by heather on 2007-05-14
hi

Ubuntu 6.06

i have tried almost everyting from this page and can not get dvd to play at all on vlc


Can anyome help me

Thank You

---

