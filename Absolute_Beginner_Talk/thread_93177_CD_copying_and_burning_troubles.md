---
title: "CD copying and burning troubles"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by olavi on 2005-11-21
How do you make an 1:1 copy of an audio CD? I've done: Right click -> Copy CD -> make .iso. Now I have .iso and .iso.toc files, but none of the bundled programs accept them!

BTW, what's the .toc file - yeah, table of contents, but why is it needed? Haven't seen that one in Windows.

I think I'm slightly disappointed with Ubuntu's CD burning applications. I really like the simple interfaces, but the fact that there's no option to make a copy of a disc to an another disc using the same burner... it's not very intuitive, I'm afraid. Plus, cdrdao library is missing by default and it must be installed separately for the Gnome CD copying to work at all!

I think Gnome and Ubuntu need something like Nero Express: Select the disc format or image file, drag & drop files, click the large burn button. It should also work with iso files and decompress audio if needed.

And a right click -> Copy CD that can copy discs using a temporary image and the same drive. And a right click -> Write ISO Image that works with Audio CDs...

I wonder how easy it'd be to write programs like that using the available libraries. I'm a fair C/C++ programmer myself, so maybe if I had time... :)

---

### Post by steve.horsley on 2005-11-21
You don't say what program you are using. I suggest you install and try k3b or gnome-baker. I think those should keep you happy.

---

### Post by olavi on 2005-11-21
Serpentine doesn't like the iso file ("converting files failed"), although you can select the .toc file like if it's supposed to understand the format. Right click -> Burn ISO to CD (whatever it's called in the English version) doesn't like it either. GnomeBaker hangs when trying to read or burn a cd. Other programs can read cds just fine, at least.

I wonder if there's something wrong with my configuration? I'm using a Lite-On CD-RW drive. It burns just fine under Windows.

I'm trying not to install Qt libraries, and I suspect that k3b won't work better than any of the above.

---

### Post by janne5011 on 2005-11-21
[QUOTE=olavi]

I'm trying not to install Qt libraries, and I suspect that k3b won't work better than any of the above.[/QUOTE]

well.I had  similar problems but tried k3b and it works:). And I have a Liteon...

---

### Post by olavi on 2005-11-21
K3b actually worked, at least in a way. :smile: My 52X burner actually used 8X - 12X speed and most of the time the buffer underrun protection was enabled, orange light instead of red one. Do I have to enable DMA or something, or is my Athlon 900 MHz simply too old for Ubuntu? I think I'll have to keep Windows XP for a while longer, then. :( 

What does k3b use to burn cds? Cdrecord? I wonder how do you use that from the command line. I could try if it can prevent buffer underruns better when k3b isn't hogging all the resources.

---

### Post by Cuppa-Chino on 2005-11-21
hi - using gnomebaker at the moment and that is okay but which programme can do **on the fly copying**? now that is what is missing - or at least I cannot find it... :???: (which for me right now amounts to the same thing!) :razz:

---

### Post by olavi on 2005-11-21
Woohoo! "hdparm -d1 /dev/cdrw" did the trick! Buffer is 99% filled all the time and I'm getting 15% CPU use - not 100%.

I think the iso file created by the basic Gnome Copy CD function was incompatible with anything else for some reason.

GnomeBaker still just hangs, though.

---

### Post by olavi on 2005-11-21
[QUOTE=Cuppa-Chino]hi - using gnomebaker at the moment and that is okay but which programme can do **on the fly copying**?[/QUOTE]

Try the following:
1) Right click the cd you want to read and click Copy disc... (or something like that)
2) Select the burner you want to burn with as the target
3) Click Write to disc

You must have cdrdao installed, otherwise it complains it can't find it.

The solution above may not be the most full-featured optical disc burning suite in existence, mind you. :)

---

### Post by matthis on 2006-11-08
I did the same thing, in gnome, right-click --> write disc, and then selected write to image, and obtained iso + toc files.

I don't have the cd anymore, only the image file left, and can't open it with anything. Is there any solution?

thanks

---

### Post by sicofante on 2007-02-15
I'm having this exact same problem. After using the right-click->Copy Disc solution for copying data CDs and all types of DVDs, I was very happy about the simplicity of the procedure. Now I'm so disappointed about audio CDs. I can't believe it doesn't work for them. I was really really happy about Gnome being so user friendly regarding disc copies. Now this is really sad.

I consider this a bug, so I'll see if I'll find some time to properly file it as the bug it is.

---

