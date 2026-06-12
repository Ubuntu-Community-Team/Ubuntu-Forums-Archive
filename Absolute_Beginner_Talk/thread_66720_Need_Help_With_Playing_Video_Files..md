---
title: "Need Help With Playing Video Files."
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by davio on 2005-09-18
i've just installed ubuntu 2 days ago and absolutely love it. however, i' unable to play any video files. when i open the files, i get this error message.

Totem could not play 'file:///home/davio/Desktop/116698_c1cf8_256k.wmv'.
There were no decoders found to handle the stream in file "file:///home/davio/Desktop/116698_c1cf8_256k.wmv", you might need to install the corresponding plugins

can anyone please guide me along this problem?

---

### Post by xmastree on 2005-09-18
You need to download the relevant [ codecs]("http://www.ubuntuguide.org/#codecs").

For WMV, [mplayer]("http://www.ubuntuguide.org/#mplayer") seems to work pretty well.

While you're there, take a look through that file. Most of the answers you're likely to need in the near future will probably be there.

---

### Post by davio on 2005-09-18
i've done what u suggested but i still can't get the video file to work. still getting the same error message. or do i need to download mplayer or something ?

---

### Post by xmastree on 2005-09-18
It's worth a try. Did you go through all the steps in that first link I sent you?

---

### Post by davio on 2005-09-18
i did everything. u linked me to. copy and paste the stuff to terminal. yep.

---

### Post by davio on 2005-09-18
another thing is that i've downloaded the file for mplayer but then where do i extract the files to or did i download the wrong thing ?

---

### Post by xmastree on 2005-09-18
if you followed the guide, and did: ```
sudo apt-get **install** mplayer-386
``` then it should be installed already.

Open a terminal and type mplayer

---

### Post by ccsalesman on 2005-10-31
Hi, (just installed ubuntu)

I am typing all the commands in the terminal however i recieve a message that says i.e. "e: couldn't find package clamav"

do i need to download something from the internet onto my linux partition? anyhelp would be great cuz i am lost.:confused: 

i tried doing a search for the words 'couldn't find' but nothing came up. thanks.

---

### Post by nike984 on 2005-10-31
[QUOTE=xmastree]You need to download the relevant [ codecs]("http://www.ubuntuguide.org/#codecs").

For WMV, [mplayer]("http://www.ubuntuguide.org/#mplayer") seems to work pretty well.

While you're there, take a look through that file. Most of the answers you're likely to need in the near future will probably be there.[/QUOTE]

as far as i know you cann't download w32codec from synaptics by legal issue, which is crucial for playing wmv file.
Download it directly from

[http://download.gna.org/praksys/praksys/w32codecs_20040916-0.0_i386.deb](http://download.gna.org/praksys/praksys/w32codecs_20040916-0.0_i386.deb)

and open a terminal and type
```
cd 
sudo dpkg -i w32codecs_20040916-0.0_i386.deb
gst-register-0.8
```

and also,Install Mplayer in this method written in the link.
[http://www.ubuntuforums.org/showthread.php?t=31061&page=1&pp=10&highlight=quicktime](http://www.ubuntuforums.org/showthread.php?t=31061&page=1&pp=10&highlight=quicktime)

---

### Post by ccsalesman on 2005-10-31
i think i am starting to figure this out.  i have to download debian files to my pc and then i will be able to install them?

or i can just download real player 10 for linux or this easy ubuntu ?; i'm assuming that this will be a lot easier.

---

