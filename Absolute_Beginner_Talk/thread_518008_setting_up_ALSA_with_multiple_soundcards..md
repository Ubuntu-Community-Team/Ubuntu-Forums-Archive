---
title: "setting up ALSA with multiple soundcards."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by duncancan on 2007-08-05
Hi everybody,

This is just a simple matter of syntax, i think. i can't find the info i'm after in the ALSA wiki or elsewhere, so i'm asking here.

I use an echo indigo IO (snd-indigoio) for audio, and generic USB-MIDI interface, which i have found out is covered under snd-usb-audio.

When i was getting just the indigo IO working, this is what i typed:

```
cd alsa-driver-1.0.14
sudo ./configure --with-cards=indigoio --with-sequencer=yes
sudo make
sudo make install
```

what i'm wondering is, where it says "--with-cards=", what syntax do i use when there's more than one card? separated by commas? each one separated with an "and"?

sorry for the silly question!

---

### Post by Pragmatist on 2007-08-05
> **duncancan said:**
> Hi everybody,
```
cd alsa-driver-1.0.14
sudo **./configure** --with-cards=indigoio --with-sequencer=yes
sudo make
sudo make install
```what i'm wondering is, where it says "--with-cards=", what syntax do i use when there's more than one card?

Please post the configure file.

---

### Post by expatCM on 2007-08-05
There may be some interesting background reading in this link ....
[http://doc.gwos.org/index.php/Multisounds/](http://doc.gwos.org/index.php/Multisounds/)

---

### Post by duncancan on 2007-08-05
as in the whole of the configure shell script file?

---

### Post by Pragmatist on 2007-08-05
> **duncancan said:**
> as in the whole of the configure shell script file?

Yes.  Post it as an attachment.

---

### Post by duncancan on 2007-08-05
there it is. thanks pragmatist, and also thanks expat; i'll start reading that link now :)

---

### Post by Pragmatist on 2007-08-06
Lines 1517 and 1518 from the file you attached: 
>  
--with-cards=<list>     compile driver for cards in <list>;
                          **cards may be separated with commas;**


---

### Post by duncancan on 2007-08-06
ah, i see. thanks! before you asked for the config file, i actually thought configs were executable binaries (..but in hindsight that doesn't make sense..).

thanks :)!

---

### Post by Pragmatist on 2007-08-06
> **duncancan said:**
> ah, i see. thanks! before you asked for the config file, i actually thought configs were executable binaries (..but in hindsight that doesn't make sense..).

thanks :)!

It was a reasonable thought, especially since the files need to be executable.  One excellent command for determining a file's type is called, appropriately enough, "file":
```
file <filename>
```So, if "config" is located at */home/me/program/config*  you would type:
```
file /home/me/program/config
```The result would be:
> 
configure: Bourne shell script text executable


---

### Post by duncancan on 2007-08-06
awesome! thanks again!

because you seem to check this thread beyond your initial reply, i'll ask one more simple question along the same lines as the "file" command: what's the command to see the directory of an executable that's been added to the path?

if that didn't make sense, for example emacs is in the path; you can type it into the command line no matter the directory. what command would precede "emacs" to let me know where the actual executable is?

thanks again :)!

---

### Post by expatCM on 2007-08-06
try 

whereis

---

