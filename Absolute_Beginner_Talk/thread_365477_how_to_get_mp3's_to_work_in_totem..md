---
title: "how to get mp3's to work in totem."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-02-19
Hello, I asked this question in the general help forum, but it appears that it's too broad of a subject, and my questions rarely get answered there, so I thought I'd try here.

My mp3's used to work in totem, after I installed "**gstreamer0.10-fluendo-mp3**", and i could listen to them and have my repeat option, with totem. But now, totem won't play mp3's, and I've tried the same ones that I used to play, and different ones, but it won't play.

It gives me an error message, and says:
> Audio codec 'MPEG 1 Layer 3 CBR' is not handled. You might need to install additional plugins to be able to play some types of movies

I did install "**libdvdread3** and **libdvdcss2** to get my DVD's to work, and never checked to see if my mp3's worked until today. I don't know if that may have anything to do with it or not, but I tried uninstalling **libdvdcss2** and it never helped the problem.

If anyone could supply me with some help, I would greatly appreciate it, as I can't play any mp3's with totem right now!

Thanks,
Dr Small

---

### Post by Maestro23 on 2007-02-19
Did a quick search for your error on the forums, found a few threads.  Did you see/try the info in this thread?: [http://www.ubuntuforums.org/showthread.php?t=194114&highlight=MPEG+1+Layer+3+CBR%27+is](http://www.ubuntuforums.org/showthread.php?t=194114&highlight=MPEG+1+Layer+3+CBR%27+is)

If that doesn't help, run a search for your error, and you will see a few more threads.

---

### Post by Dr Small on 2007-02-19
> **Maestro23 said:**
> Did a quick search for your error on the forums, found a few threads.  Did you see/try the info in this thread?: [http://www.ubuntuforums.org/showthread.php?t=194114&highlight=MPEG+1+Layer+3+CBR%27+is](http://www.ubuntuforums.org/showthread.php?t=194114&highlight=MPEG+1+Layer+3+CBR%27+is)

If that doesn't help, run a search for your error, and you will see a few more threads.
I think I have installed w32codecs before, but just for security, I installed it again, and played an mp3 with still no success. I guess I'll do a search now....

Dr Small

---

### Post by solar george on 2007-02-19
[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

Try this.

---

### Post by petri on 2007-02-19
My Totem works flawlessly after I installed **totem-xine** with Synaptic. Try it. ;)

---

### Post by jvc26 on 2007-02-19
This may well probs help: [Ubuntu Guide multimedia codecs section]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")
Hope thats of assistance,
Il

---

### Post by Dr Small on 2007-02-19
> **petri said:**
> My Totem works flawlessly after I installed **totem-xine** with Synaptic. Try it. ;)
I searched for []totem-xine[/b] and found it to be already installed. So, I tried reinstalling it, and still no success with mp3's.

I'll check out 
[http://www.getautomatix.com/wiki/ind...tion&Itemid=38](http://www.getautomatix.com/wiki/ind...tion&Itemid=38) next.

Dr Small

---

### Post by jvc26 on 2007-02-19
You can get automatix2 from the repos:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)
Il

---

### Post by Dr Small on 2007-02-19
> **Illuvator said:**
> You can get automatix2 from the repos:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)
Il
Ok, but is automatix2 going to help me?
I thought I read somewhere that it wasn't stable or Ubuntu didn't give support for it.
And just exactly how is this going to help?

Dr Small

---

### Post by jvc26 on 2007-02-19
The first time I used Ubuntu I used Automatix2 as you can just merely click a button and tell it to install all your multimedia codecs - i.e. the ones you need to play .mp3s. I dont bother with it now myself - I tend to use the old:
```

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

```
Which has enabled me to play .mp3s every time I've used it. Automatix2 just makes it a one click process.
Il

---

### Post by Dr Small on 2007-02-19
> **Illuvator said:**
> The first time I used Ubuntu I used Automatix2 as you can just merely click a button and tell it to install all your multimedia codecs - i.e. the ones you need to play .mp3s. I dont bother with it now myself - I tend to use the old:
```

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

```
Which has enabled me to play .mp3s every time I've used it. Automatix2 just makes it a one click process.
Il
Whew. I finally got it to work with your final code! Save that code! It's priceless! lol.
I've tried just about everything, from everything on the RestrictedFormats to Automatix, and finally I tried the last code :)

Thanks again!
I'll save the code for future referrence in my command list :D

Dr Small

---

### Post by chenel on 2007-10-20
I had the same problem and it was fixed by installing 'libxine-ffmpeg' (which is contained in the libxine-extracodecs package, I think).

---

### Post by dehughes on 2007-12-31
> **petri said:**
> My Totem works flawlessly after I installed **totem-xine** with Synaptic. Try it. ;)

This worked PERFECTLY for me!  I'm a total Linux newbie, so if I can do it.... ;)

Thanks petri!

---

