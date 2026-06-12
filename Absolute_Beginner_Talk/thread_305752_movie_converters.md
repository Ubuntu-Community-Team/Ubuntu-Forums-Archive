---
title: "movie converters"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-11-23
first off to all the americans, happy thanksgiving.

now for the question. i have a bunch of WMVs that im not able to play right now. ive installed mplayer and all of the codecs i can think of. i was just wondering if there was a movie converter that can change it to say .avi.

---

### Post by benuski on 2006-11-23
Are you sure you installed the w32codecs package?  Its in a different section on the RestrictedFormats pages, so you might have missed it.

But if you still want to convert, the one that I can think of is VLC.  Its both the media player and has a converter function.  Actually, come to think of it, VLC will probably be able to play your WMVs, its great at playing anything and everything.  Go to file, wizard, and then to transcode, and choose your container formats, and then it should save as whatever you want.  

Hope it works for you!

---

### Post by erwinquita on 2006-11-23
no need to convert .wmv format to .avi just install needed codecs [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs"). ;)

---

### Post by Hranj on 2006-11-23
erwinquita: so i just put all of that code into the terminal and it did everything but at the end it said 0 changed 0 installed 0 unmodified or w/e so i had them the whole time. 

i cant think of anything. but i feel left in the dust cause half the videos on the net are WMVs

---

### Post by benuski on 2006-11-23
Just to make sure, did you install the [w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5")?
They're different from the rest of the media codecs, because they can't be distrubtued directly with Ubuntu or in Ubuntu repositories.

---

### Post by DrMilo on 2006-12-03
Ah the fix I needed, thanks!

---

