---
title: "aiff files not working"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-11
I am trying to play and also burn to CD aiff files from an exernal hard drive. None of my players play them and gnomebaker and serpentine don't burn them. What to do? 

Ah, I did instal Banshee thinking that might work but it didn't.
Thanks
Justin

---

### Post by panzer21st on 2006-09-11
Audacity maybe?  I haven't used it for that, but you may want to look at its features.

---

### Post by 3rdalbum on 2006-09-13
```
sudo apt-get install sox
```

Or install Sox in Synaptic Package Manager. Then:

```
sox infile.aif outfile.wav
```

Where infile.aif is your input file, and outfile.wav is the file you want to be created. When you've got your AIFFs converted to WAVs, Serpentine should recognise them.

I'm afraid, unless you want to open and convert using Audacity (slow), the command-line is the only way. But don't be scared of the terminal; the command I've given you is easy, and very quick.

---

### Post by woodlandjustin on 2006-09-13
> **3rdalbum said:**
> ```
sudo apt-get install sox
```

Or install Sox in Synaptic Package Manager. Then:

```
sox infile.aif outfile.wav
```

Where infile.aif is your input file, and outfile.wav is the file you want to be created. When you've got your AIFFs converted to WAVs, Serpentine should recognise them.

I'm afraid, unless you want to open and convert using Audacity (slow), the command-line is the only way. But don't be scared of the terminal; the command I've given you is easy, and very quick.

What if the file name is in Japanese? I tried it and the terminal displayed the japanese font but it wouldn't convert it! If I remenamed it in English it worked, but does that really mean I must rename ***all*** (about 200!) of them?
Thanks
Justin

---

