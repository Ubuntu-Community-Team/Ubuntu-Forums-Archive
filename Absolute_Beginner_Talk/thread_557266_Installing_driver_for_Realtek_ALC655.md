---
title: "Installing driver for Realtek ALC655"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by jlyn on 2007-09-22
Hello,
I need to find drivers that will work with Dapper Drake 6.06 for REALTEK ALC 655 audio (on board the mother board).
Does anyone know if such exists?
Yesterday I found a set of files (that were downloaded to this old computer remade into a new Ubuntu machine) that purported to be a driver.  The computer rebooted after updating it's software files and I lost the download window.   The information in the download window showed that the files went into     ./  
Where do I find the contents of ./    ?
I can't remember the name of the file (it is a .zip), but I will recognise it if I can see it. 
While waiting for the software updates yesterday I read the accompanying files; one of them said I would have to compile the driver.
For that I need "hand-holding" as I have no idea how to go about that.
Anybody feeling patient and able to talk baby-talk?
:shock:

---

### Post by logos34 on 2007-09-22
I could be wrong but your sound card should work out of the box with the alsa **snd_intel8x0** module

run 

**lspci -n**

then post the output in the [box here]("http://kmuto.jp/debian/hcl/").  It will show all the opensource drivers you need, including audio.

---

