---
title: "making cds"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2007-11-06
alright., i am trying to make cd's using the serpentine cd creator, but when i try to transfer my files from frostwire it says that it cant create the cd because they are mp3 files

---

### Post by Inxsible on 2007-11-06
I am not really sure, if Serpentine can create mp3 CDs. Its been a long time since I removed it from my install.

You can use K3B for all your burning needs.
```
sudo aptitude install k3b
```or if you prefer not to install KDE apps you can use GnomeBaker. I don't know the package name for it, but you can find it in Applications>>Add/Remove or Synaptic Package Manager

---

### Post by az on 2007-11-06
I'm pretty sure that serpentine uses gstreamer.  If you install ubuntu-restricted-extras, it should work.

---

### Post by Giradman on 2007-11-06
New to Ubuntu myself, but was just reading the chapter on *Digital Audio* this AM from the Keir Thomas book on 'Beginning Ubuntu Linux' - additional codecs/packages for MP3 need to be installed for the Ubuntu programs to play, rip &  burn MP3 files - two mentioned are the Fluendo MP3 Codec (permits listening to MP3s) & gstreamer-plugin-ugly packages for 'ripping' & 'burning' MP3 files - I'm sure there are other options, as already mentioned.  I did not do the suggested downloads yet, but hopefully others w/ more experience will repsond about using them w/ Serpentine Audio-CD creator - good luck and please report your results back - thanks. :)

---

### Post by wolfen69 on 2007-11-06
> **Inxsible said:**
> I am not really sure, if Serpentine can create mp3 CDs. Its been a long time since I removed it from my install.

You can use K3B for all your burning needs.
```
sudo aptitude install k3b
```or if you prefer not to install KDE apps you can use GnomeBaker. I don't know the package name for it, but you can find it in Applications>>Add/Remove or Synaptic Package Manager

you will also need 
```
sudo apt-get install libk3b2-mp3
```

---

