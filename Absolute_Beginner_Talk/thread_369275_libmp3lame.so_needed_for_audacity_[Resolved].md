---
title: "libmp3lame.so needed for audacity [Resolved]"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-24
Hi i am just starting to learn how to use audacity and i wanted to export the file as an mp3 but it needs libmp2lame.so to do it. i googled and looked on the audacity site but can't seem to find the exact name/file. lots of lame downloads available but i don't know if they are it and there were many versions. can anyone help me out. also if there are some other plugins available that do effects etc then i would appreciate some knowledge on that as i have been a windoze/mac engineer producer for some time but want to learn what i can do with audacity and rosegarden etc.

---

### Post by Maestro23 on 2007-02-24
.

---

### Post by aysiu on 2007-02-24
[This thread](http://ubuntuforums.org/showthread.php?t=254550) should help.

I found it with this Google search: ```
site:ubuntuforums.org libmp3lame
```

---

### Post by rapattack1 on 2007-02-24
ok i should have mentioned that that machine is not on the net. i need to download the file and transfer it over to the machine via usb flash stick. thanks

---

### Post by aysiu on 2007-02-24
Download this file to whatever machine *is* on the net:
[http://mirrors.kernel.org/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-2_i386.deb)

Transfer that file to your Ubuntu machine and the double-click it. Then *Install this Package*.

Finally, you can follow the instructions in post #4 of the thread I linked to.

---

### Post by rapattack1 on 2007-02-24
great that is done. will try it out later.
is there a central place where i can download other plugins for audacity? like an ftp directory?

---

### Post by aysiu on 2007-02-24
There's a plugins page on the Audacity website:
[http://audacity.sourceforge.net/download/plugins](http://audacity.sourceforge.net/download/plugins)

Here's what is says: > **Plug-In Effects**
You can download and install plug-ins to add extra effects to Audacity. Plug-ins appear at the bottom of the "Effect" menu. To install new plug-ins, place them in the Plug-Ins folder inside the Audacity installation folder. On Windows computers, this is usually under "Program Files." On Mac OS X, it is usually under "Applications." I'm not sure where the folder is in Ubuntu, but you can try searching for it using the search tool. I think it's Places > Search for Files and Folders. You can go to it directly by pressing Alt-F2 and typing ```
gnome-search-tool
``` or you can also search with the [terminal](http://www.psychocats.net/ubuntu/terminal): ```
locate audacity
```

---

### Post by rapattack1 on 2007-02-25
The pc with Audacity is not connected to the net. I am still finding it hard to get libghttp1, libid3-3.8.3c2a, libjack0.100.0.0-0, liblrdf0,libqt3-mt, libraptor1, fftw2, fftw2-double.  i can't seem to find them individually to download. i installed rosegarden and it needs these as dependencies i think is the word. maybe i should have stayed in the page where i downloaded so i could get these but i only just figured ou t this happens with linux. oh and it said that i needed to configure libgtk1.2. how do i do that? i did install quite a few other plugins successfully.

---

### Post by rapattack1 on 2007-02-25
bad news the plugin is not installed as when i got to export as an mp3 it says that libmp3lame.so is not installed. i checked both machines as i have it now installed on my laptop too. both have the same error and it is also mentioned as not installed in the preferences. is this file really part of the   liblame0 pack?

---

### Post by NoTiG on 2007-03-09
I had the same problem. THe problem is that you DO have lame installed... but audacity is not asking for the correct file name. When it brings up the box asking for libmp3lame.so you have to add an .0 to it so it reads: libmp3lame.so.0

---

### Post by rapattack1 on 2007-03-10
Ah so how do I do that? Sorry I am still learning. Thanks!

---

### Post by NoTiG on 2007-03-10
it should bring up a box asking where the file is.... and have the name of it already typed in... libmp3lame.so   add a .0 so it looks like libmp3lame.so.0

---

### Post by rapattack1 on 2007-03-11
Ah that worked thanks so much!

---

