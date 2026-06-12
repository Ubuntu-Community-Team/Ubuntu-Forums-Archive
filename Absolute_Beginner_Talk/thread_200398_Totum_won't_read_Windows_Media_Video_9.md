---
title: "Totum won't read Windows Media Video 9"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by PhilOSparta on 2006-06-20
I occasionally receive .wmv files via email.  When I click on them, Totum opens and issues an error message that it can't play Windows Media Video 9 files and may need additional codecs.

What codecs do I need, and where would I find them?

Thanks for your help.

---

### Post by %hMa@?b&lt;C on 2006-06-20
you need the win32 codecs. use automatix to install them

---

### Post by ctgray on 2006-06-20
I dont think you can play encrypted WMV's or MOV's. Not entirely sure though.

---

### Post by FredB on 2006-06-20
[QUOTE=ctgray]I dont think you can play encrypted WMV's or MOV's. Not entirely sure though.[/QUOTE]

DRM *crippled... I mean protected* file won't be played.

---

### Post by mjm115 on 2006-06-20
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

According to this, all codecs work except for .wmv.  I have gotten .movs to work with xine by installing libxine-extracodecs from the repository.  For some reason, I cannot get gstreamer to work the way is't "supposed" to work.

---

### Post by FredB on 2006-06-20
For WMV file - besides of DRM crippled ones - I installed by hand (**shame on me**) the full win32codecs package I found on Mplayer site.

And WMV files are played.

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=FredB]For WMV file - besides of DRM crippled ones - I installed by hand (**shame on me**) the full win32codecs package I found on Mplayer site.

And WMV files are played.[/QUOTE]

Would I be correct in saying that the win32codecs won't work with a 64bit Ubuntu install?

---

### Post by FredB on 2006-06-20
[QUOTE=Torquemada28]Would I be correct in saying that the win32codecs won't work with a 64bit Ubuntu install?[/QUOTE]

I'm afraid you will be awfully right...

---

### Post by Torquemada28 on 2006-06-20
[QUOTE=FredB]I'm afraid you will be awfully right...[/QUOTE]

win32 codecs
Wine
Skype

I'm getting annoyed now.

---

### Post by catty0320 on 2006-06-20
windows medi 9 is what we call a proprietary codecand is a closed source thing.  this means that open source software cant support it without intrusive licencse agreements if at all. use divx, mpeg, AVI,

---

### Post by FredB on 2006-06-20
[QUOTE=catty0320]windows medi 9 is what we call a proprietary codecand is a closed source thing.  this means that open source software cant support it without intrusive licencse agreements if at all. use divx, mpeg, AVI,[/QUOTE]

If you receive a wmv file, you'll have to tell the sender to send you another format. Long, isn't it ?

---

