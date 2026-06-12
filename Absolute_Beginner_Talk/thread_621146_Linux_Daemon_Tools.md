---
title: "Linux Daemon Tools"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-11-23
I've seen some other threads of people looking for a Daemon tools alternative for Linux.  The replies seemed to just warrant that you can already mount .iso files without installing any application.

The thing is, ahem, let's say you're download something that has a filetype(s) that need to be mounted and aren't images.

Is PowerISO my best option here?

---

### Post by oneadvent on 2007-11-23
cd's don't use a specific file type. you can download an iso of xp and burn it.

I hope that answers your question.

---

### Post by siciliancasanova on 2007-11-23
So I can mount DAA and BIN image files without any additional software?  Because that's what I'm asking.

---

### Post by oneadvent on 2007-11-23
wait, mount or burn?

---

### Post by stunner on 2007-11-23
[http://www.acetoneteam.org/download.html]("http://www.acetoneteam.org/download.html") handles .bin

Only PowerISO handles DAA (proprietary format): [http://poweriso.com/download.htm]("http://poweriso.com/download.htm")

---

### Post by siciliancasanova on 2007-11-23
Mount.  Like I said, an alternative to Daemon tools.  I'm downloading PowerISO right now and will try it out.  I don't want to use WINE to run my emulator and also run the application that's mounted in the emulator.  I would rather have a native Linux app do the emulation.

---

### Post by mellowd on 2007-11-23
> **siciliancasanova said:**
> I've seen some other threads of people looking for a Daemon tools alternative for Linux.  The replies seemed to just warrant that you can already mount .iso files without installing any application.

The thing is, ahem, let's say you're download something that has a filetype(s) that need to be mounted and aren't images.

Is PowerISO my best option here?

.daa is an image, just a different one so your request is slightly wrong

---

### Post by siciliancasanova on 2007-11-23
> **stunner said:**
> [http://www.acetoneteam.org/download.html]("http://www.acetoneteam.org/download.html") handles .bin

Only PowerISO handles DAA (proprietary format): [http://poweriso.com/download.htm]("http://poweriso.com/download.htm")



DAA and BIN/CUE are both disk image formats - fyi.

Would "So I can mount DAA and BIN image files without any additional software? Because that's what I'm asking." not presuppose that I already know that?  Guess not.

---

### Post by oneadvent on 2007-11-23
mounting iso's is something I have never tried, however, both the programs the guy mentioned above run natively in linux.

---

### Post by stunner on 2007-11-23
It would indeed presuppose such a notion, but the following excerpt from your first post indicates otherwise:

> **siciliancasanova said:**
> The thing is, ahem, let's say you're download something that has a filetype(s) that **need to be mounted** and **aren't images**.

*emphasis added*

Personally, I would blame it on tryptophan-induced lethargia :D

---

### Post by siciliancasanova on 2007-11-23
Ok this thread isn't about a mistype/mispelling.  I say *******, you say george bush.  Whatever, I apologize for mistyping, or not explaining what I meant.

But I do know what I'm talking about, I never ran Daemon tools in the past without knowing what it does.

I just want opinions on the best program to mount image files.  Not on the technicality of my language.

---

### Post by mellowd on 2007-11-23
I don't think we were attacking your language. By saying that you want to mount a file that isnt an image and saying you want to mount different types of image is completely different though

---

### Post by oneadvent on 2007-11-23
Okay, so he's clarified, and lets move on.

Is there an answer that would fit his needs.

(I have never done it, so i dunno what it is.)

Help him out, now that we have clarified the language.

---

### Post by stunner on 2007-11-23
No biggie man.

Just in case...

If you want to mount files that aren't in an image, you can use the instructions [here]("http://www.granneman.com/techinfo/linux/burningcds/makeanisoimage.htm") to make an ISO out of them and mount the usual way.

---

### Post by SaltyCrak on 2007-11-27
i recently converted from windows to linux and i used to use daemon tools and alcohol 120% for my virtual cd needs.

what i'm looking for is a GUI that will let me create a virtual cd-rom device and mount cd "images" to that device as needed so that i don't have to burn them to cd/dvd. the cd image format is irrelevant (iso, mdf, etc.)

---

### Post by CatKiller on 2007-11-27
> **siciliancasanova said:**
> Would "So I can mount DAA and BIN image files without any additional software? 

You can use **bchunk** to convert bin/cue files to .isos, and **mdf2iso** to convert MDF files to .isos. Both are in the Universe repository.

I don't know about DAA files.

---

### Post by exactopposite on 2007-11-27
I'm looking for soemthing like this too. Something i can use to mount disk images. I used alcohol 120 for this in windowsand it would make a virtual drive that could be used to mount disk images. It's often useful to be able to mount the image without having to burn it.

---

### Post by EspressoRulz on 2007-11-27
No matter what your view of Bush is or how rude some people are when asking for help...see if this will work for you.

[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

### Post by _sAm_ on 2007-11-27
Hi 

> I just want opinions on the best program to mount image files. 
If the image file contains a movie(like a ripped DVD and so on), then you dont need to mount it. Just open the file with the VLC mediaplayer. 

If the image file contains data, then you could use the following: 
Make a mount point for the ISO file; 
```
sudo mkdir /media/iso
```
Mount the iso file: 
```
sudo mount -t iso9660 filename.iso /media/iso -o loop
```
Where **filename.iso** is the complete path to the image you want to mount. After this it will show up as a cd/dvd on your desktop. 

To umount it later run: 
```
sudo umount /media/iso
```

Here is a better guide for you; [http://blogs.pcworld.co.nz/pcworld/tux-love/2007/10/hidden_linux_iso_magic.html](http://blogs.pcworld.co.nz/pcworld/tux-love/2007/10/hidden_linux_iso_magic.html)


This is cli, and I know there is GUI for this built in program&#8211; but not in Synaptic. 

If you cant mount the image file this way, then you could install Kiso(from Synaptic). Very nice GUI program that lets you convert a lot of different image files to ISO &#8211; and then you can mount them as mention above. 
Kiso: [http://kiso.sourceforge.net/info_ks.php](http://kiso.sourceforge.net/info_ks.php)
[I]* Open ISO and NRG images.

* Create an ISO image from CD.
* Easy and convenient creation of own ISO images.
* Convert NRG to ISO images.
* Convert BIN/CUE to ISO images.
* Convert MDF to ISO images.
* Convert CDI to ISO images.
* Convert CCD/IMG to ISO images.
* Convert C2D to ISO images.
* Mount ISO/NRG images as virtual drive.
* Extract the content of an ISO/NRG image.
* Create bootable images.[/I]

Hope this helps

Edit;
I just tried; you can also open cd/dvd image files with Kiso(with GUI). I tried with a image that ended with .nrg Kiso told me it was not a valid image, so I changed the filename to .iso and it worked fine.

---

### Post by EspressoRulz on 2007-11-27
Great post _sAm_! I am sure this is what the original poster wanted to know. Sometimes there are too many ways of doing things with Linux. Everyone has had a different experience in what works for them. This is why these forums work and its why people like you that offer assistance are much appreciated.

---

### Post by Kingsfan on 2007-12-09
thanks sam! this is exactly what i've been looking for

---

### Post by neoragexxx on 2008-03-02
thanks for the info esspressorulz . that cdemu seems interesting project

---

