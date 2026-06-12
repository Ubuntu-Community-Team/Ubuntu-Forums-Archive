---
title: "How to add MP3 and WMA pluguin to Nero Linux 3"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-12-20
I need to add the MP3 support to Nero Linux 3 in order to create Audio CD's from MP3 or WMA.

Somebody can tell me how to do it?

Thank you

---

### Post by Buffalo Soldier on 2007-12-20
I have no experience with Nero. But just out of curiosity, have you tried the default CD audio burner in Ubuntu? Serpentine. If you have the approriate Gstreamer plugins, you should be able to burn MP3 to audio. Plus the interface is very simple.

---

### Post by Kosimo on 2007-12-21
Thanks for your answer.

But I'm trying to figure out how to do it in Nero Linux 3.0.2.1 
  

I don't want  to discuss about witch one is better, and I know that Nero Linux is not very welcome on this forum because of its (Closed Source) But anyway, if someone knows how to add this plugins I still need to know how to do it.


Thank you again.

---

### Post by Kosimo on 2007-12-22
Bump:   Any help? ](*,)

---

### Post by Steve Zenone on 2007-12-22
Nero Linux 3 has an embedded audio decoder/encoder/transcoder with support for ogg, flac, mp3, and wav formats. Out of curiosity. in Nero go to FILE | OPTIONS | AUDIO. What audio driver do you have selected? I have OSS selected on two of my systems where Nero Linux is working correctly. 

Secondly, do a directory listing of your plug-ins directory. Do you have the file libMP3.so there?

Hope this helps.

---

### Post by Kosimo on 2007-12-22
> **Steve Zenone said:**
> Nero Linux 3 has an embedded audio decoder/encoder/transcoder with support for ogg, flac, mp3, and wav formats. Out of curiosity. in Nero go to FILE | OPTIONS | AUDIO. What audio driver do you have selected? I have OSS selected on two of my systems where Nero Linux is working correctly. 

Secondly, do a directory listing of your plug-ins directory. Do you have the file libMP3.so there?

Hope this helps.

Hi!

I'm using the same Audio driver, OSS.  (I think it doesn't really matter in this case anyway)

About the plugins, I can see 4 pugins in Decoders and Encoders sections:

And are the followings: 

libWav.so
libFLAC.so
libMP3.so
libOggVorbis.so


Curios... Looks like the mp3 plugin is installed... But I can ONLY use ogg files when creating an Audio CD. 

So, you didn't change anything and your Nero Linux is able to create Audio CD's from MP3 files... Right?  

:mad:

---

### Post by Steve Zenone on 2007-12-22
> **Kosimo said:**
> 
So, you didn't change anything and your Nero Linux is able to create Audio CD's from MP3 files... Right?  
:mad:

That's correct. I didn't change anything and I'm able to burn an audio cd from my collection of MP3s using Nero Linux. As a sanity check I *just* burned an audio cd and the conversion worked fine.

I don't believe that Nero is dependent on having ubuntu-restricted-extras installed.

There's probably no connection here, but don't you also have libDefConvertor.so within the plugins directory?

---

