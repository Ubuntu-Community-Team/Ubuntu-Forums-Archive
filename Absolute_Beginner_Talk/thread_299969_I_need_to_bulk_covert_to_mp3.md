---
title: "I need to bulk covert to mp3"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by CameronCalver on 2006-11-15
Hello i have about 1000 songs all in ogg format but i need mp3 format for what i use for i have found some converters but is there anyway i can convert a whole folder from ogg to mp3 gui or cli does not matter

---

### Post by DarkN00b on 2006-11-15
This assumes you have ffmpeg installed, if not you can get it from the repos. You can use ffmpeg to convert many types of media. I'm not sure how Ubuntu handles wildcards, but something like:

```

ffmpeg -i *.ogg *.mp3

```

should work. Try typing ```
man ffmpeg
``` into a terminal window for more info (there's a lot). You can set many options: bitrate, etc...

---

### Post by CameronCalver on 2006-11-15
yes but is there a way like i used to do on windows to just do a whole folder?

---

### Post by Jose Catre-Vandis on 2006-11-15
Cameron

darkN00b's suggestion should do a whole folder if you run the command from the folder containing the ogg files.

Another way is to install Sound Converter from Synaptic (soundconverter), this will give you a GUI to do the same thing, but you will need to ensure you have all the codecs installed and I found I needed to install lame 0.8 gstreamer to get mp3 conversion

---

### Post by DarkN00b on 2006-11-15
> **Jose Catre-Vandis said:**
> Cameron

darkN00b's suggestion should do a whole folder if you run the command from the folder containing the ogg files.*snip*

I suppose I should have mentioned that... :redface:

---

### Post by Jose Catre-Vandis on 2006-11-15
> **DarkN00b said:**
> I suppose I should have mentioned that... :redface:

I knew what you meant ;)

---

### Post by Decade on 2006-11-15
> **DarkN00b said:**
> 
```

ffmpeg -i *.ogg *.mp3

```

Are you sure that would work? I would have thought that the wildcard *.wav would expand in unexpected ways. At least ffmpeg seems to check for file collision. That was most unpleasant when I tried something like that with lame.

I would've tried something like
```

for i in *.ogg; do [[ ! -a "${i%ogg}mp3" ]] && oggdec "$i" -o - | lame --preset standard - "${i%ogg}mp3" ; done

```
with "in */*.ogg" or whatever depending on your directory structure, and different presets or other settings depending on what you like. Note, if you have a .ogg and a .mp3 of the same base name, this command would not overwrite the mp3. I hear that LAME is one of the best MP3 encoders available. However, this technique would not preserve the ID3 tags, and I'm not sure how to approach that subject yet.

The "[[ -a file ]]" portion tests whether the file exists, the "!" inverts the test, and the "&&" somehow makes the next command conditional. You could leave out the test, "do oggdec ..." if you do want to overwrite the old mp3.

---

### Post by Marsolin on 2006-11-15
[Perl Audio Converter]("http://linuxappfinder.com/package/pacpl") is an easy way to convert a folder or individual files. It can be run from the command line, as a plug-in to [Amarok]("http://linuxappfinder.com/package/amarok"), or by right clicking on a folder using [Konqueror]("http://linuxappfinder.com/package/konqueror").

---

### Post by CameronCalver on 2006-11-15
Jose and everyone for your help i used the soundconverter idea and it was great im in the process of converting to wav but where can i get me mp3 plugin

---

### Post by DarkN00b on 2006-11-16
> **Decade said:**
> Are you sure that would work? I would have thought that the wildcard *.wav would expand in unexpected ways. At least ffmpeg seems to check for file collision. That was most unpleasant when I tried something like that with lame.
*snip*


You're probably right. I'm not really sure how Ubuntu handles wildcards. I was just throwing this out as a possibility. I actually have more experience using ffmpeg on single video files, specifically to convert .flv->.mpg or .flv->.wmv. The only way to describe it is *fast*. On WinXP I use Riva FLV encoder to convert and a 20Mb file takes about 5 minutes. With ffmpeg it takes no more than 20 seconds for the same file.

---

### Post by CatKiller on 2006-11-16
> **CameronCalver said:**
> Jose and everyone for your help i used the soundconverter idea and it was great im in the process of converting to wav but where can i get me mp3 plugin


[Ubuntu Wiki]("https://help.ubuntu.com/community/RestrictedFormats")
[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs")

I think. I could play mp3s long before I installed Sound Converter, so I don't know for sure which it was.

---

### Post by Jose Catre-Vandis on 2006-11-16
> **CameronCalver said:**
> Jose and everyone for your help i used the soundconverter idea and it was great im in the process of converting to wav but where can i get me mp3 plugin

As I said, what worked for me was to install 

gstreamer0.8-lame 

from the repositories. This got me working. You may need to enable universe or multiverse to get it or you can find it at [http://lame.sourceforge.net/](http://lame.sourceforge.net/)

---

### Post by MiniJames on 2006-11-19
Google was my friend -- works like a charm:

Edgy (6.10):

Add multiverse sources.
Install package gstreamer0.10-plugins-ugly-multiverse.
Others:

Install package gstreamer0.8-lame.
Or easier: install multimedia codecs with EasyUbuntu or Automatix.

Reference:
[http://soundconverter.berlios.de/gstreamer_mp3_encoding_howto.php](http://soundconverter.berlios.de/gstreamer_mp3_encoding_howto.php)

Thanks!

---

### Post by Nattie on 2006-11-20
What kind of quality loss are you going to experience?  Seems to me if you convert from one lossy format to another, you are asking for a crappy sounding song.

---

### Post by strfryed on 2006-12-20
for x in *.ogg; do ffmpeg -i "$x" -ab 128 "`basename "$x" .ogg`.mp3"; done

This does an entire dir at once.  You must be inside the dir you want to convert.  It's also doable with gstreamer but the expression is a bit more complicated because you have to setup the conversion pipeline yourself.  Substitute whatever you want your target bitrate to be up there where 128 is.

As far as quality loss: it's not too bad if you're like me and you just have a few crappy proprietary devices that won't play ogg this is acceptable.  Just don't go converting to some other lossy format from these mp3s.

BTW - the reason just doing ffmpeg -i *.ogg *.mp3 doesn't work is because the shell expands the *s before it runs ffmpeg, therefore this is actually ffmpeg -i followed by a list of all the ogg files in the dir and a list of all the mp3 files in the dir.  You need just one ogg and one mp3 file at a time.

---

### Post by valke on 2007-02-16
thanks this answered my question too!

---

