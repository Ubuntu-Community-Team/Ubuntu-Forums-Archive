---
title: "convertverting wma and mp3 music files."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-24
Is there a way to convert windows media player files and mp3 into a format that plays on Ubuntu? I also need a way to convert Ubuntu music files to mp3 so I can play them on my Windows XP computer at work.

Thanks

---

### Post by fastpakr on 2007-04-24
Do you really want to convert all of your music to two separate formats?  Seems like it would be easier to make the adjustments one each side to handle the required formats instead.

---

### Post by compmodder26 on 2007-04-24
> **fastpakr said:**
> Do you really want to convert all of your music to two separate formats?  Seems like it would be easier to make the adjustments one each side to handle the required formats instead.

Agreed.  Just install the necessary codecs to make mp3 and wm* work.

---

### Post by orwellus on 2007-04-24
Thanks for the reply. Yeah sorry still new to Ubuntu, that would be better to make it all mp3. Where do I get the codes to do that?

---

### Post by compmodder26 on 2007-04-24
This guide should get you sorted out:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

edit:  The URL above is to get Ubuntu to play MP3 and windows media, not to convert anything.

---

### Post by fastpakr on 2007-04-24
> **orwellus said:**
> Thanks for the reply. Yeah sorry still new to Ubuntu, that would be better to make it all mp3. Where do I get the codes to do that?

What version are you on?

---

### Post by n3tfury on 2007-04-24
> **orwellus said:**
> Thanks for the reply. Yeah sorry still new to Ubuntu, that would be better to make it all mp3. Where do I get the codes to do that?

they mean to set up both of your workstations to handle both formats.  transcoding is bad news for audio quality anyway.

---

### Post by AlexenderReez on 2007-04-24
enable all repositories.....


then


> sudo apt-get install gstream* 

---

### Post by Najand on 2007-04-24
To convert music files you can use: soundconverter
```

sudo apt-get install soundconverter

```

---

### Post by nike984 on 2007-04-24
> **Najand said:**
> To convert music files you can use: soundconverter
```

sudo apt-get install soundconverter

```

to use soundconverter, you would also need to install ffmpeg package.

---

### Post by orwellus on 2007-04-24
Wow, thanks for all the responses. I have Ubuntu 6.0.6. I thought I installed the gstreamer codes, but I will install them again. I tried sound converter before but couldn't seem to get it to work right. I think that might have been before I installed the gstreamer codes, though, so I will try again.

---

