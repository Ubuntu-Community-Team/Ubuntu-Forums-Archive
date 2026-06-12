---
title: "Problems Downloading libdvdcss2"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Wolfraptor1 on 2007-07-30
Alright here's the problem. I can't get the libdvdcss2 packages from medibuntu.org. I've tried again and again following the instructions in their repository for "Feisty" which is what I'm running. I got my audio working through my VIA onboard chipset, and I got it to read UNENCRYPTED DVDs, but I haven't been able to pop in a DVD and read it directly.
     I have it on good authority that I need it to play regular old DVDs, but I can't get ahold of it because the website won't let me download the key and the update repositories. Can anyone help me out at all?

---

### Post by Inxsible on 2007-07-30
The other way could be to install VLC from videolan.org. The package includes libdvdcss2 in it.

---

### Post by p_quarles on 2007-07-30
If you're using the default installation of Totem, it won't play very well with DVDs. Try Totem-xine or (my personal preference) VLC.
```
sudo apt-get install vlc
```
As for the medibuntu repository key, you can load that manually by following these instructions:
```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Hope this helps.

---

### Post by deadgobby on 2007-07-30
I use ogle to play DVD's Have you try ogle and get the same error.
Gobby

---

### Post by regomodo on 2007-07-30
you need to add the medibuntu repo to you sources.list and it's key can be found on ubuntuguide website.. If that means nothing to you install automatix2 from its site and install codecs through that. I find that slower but easier for a beginner.

---

### Post by Inxsible on 2007-07-30
I, personally, would recommend against installing automatix because I have seen just too many people having too many problems with it. I used it too, but gave it up when I installed Feisty.

Until Feisty, i think automatix eased quite a few things. But the Add/Remove and Synaptic is a breeze now and i dont think automatix is needed.

just my 2 cents :)

---

### Post by p_quarles on 2007-07-30
> **regomodo said:**
> you need to add the medibuntu repo to you sources.list and it's key can be found on ubuntuguide website.. If that means nothing to you install automatix2 from its site and install codecs through that. I find that slower but easier for a beginner.
Just be forewarned, though, that automatix2 has caused problems on some computers, and it makes it more difficult to update some applications. 

The command line instructions I posted above can be run in a terminal to add the repo and key without having to manually edit the files.

---

### Post by Wolfraptor1 on 2007-07-30
The problem is fairly specific, I often do backups of my DVDs and the like, so I have a few DVDs of my own that are unencrypted (Dveoid of CSS/Macrovision Protection) and I can play those using Ogle. However, when I insert a regular DVD that I own, (With CSS/Macrovision Encryption, or whatever it uses) I get an error message. I know I need libdvdcss2. is there any other ways that I can get it?

---

### Post by stchman on 2007-07-30
> **Wolfraptor1 said:**
> Alright here's the problem. I can't get the libdvdcss2 packages from medibuntu.org. I've tried again and again following the instructions in their repository for "Feisty" which is what I'm running. I got my audio working through my VIA onboard chipset, and I got it to read UNENCRYPTED DVDs, but I haven't been able to pop in a DVD and read it directly.
     I have it on good authority that I need it to play regular old DVDs, but I can't get ahold of it because the website won't let me download the key and the update repositories. Can anyone help me out at all?

Here is how to do it?

```


wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get install libdvdcss2


```

This will work.

---

### Post by regomodo on 2007-08-01
> **p_quarles said:**
> Just be forewarned, though, that automatix2 has caused problems on some computers, and it makes it more difficult to update some applications. 

The command line instructions I posted above can be run in a terminal to add the repo and key without having to manually edit the files.

fair enough. I used to use it in Edgy when i 1st got started but haven't bothered since. Just using the cli now.

---

