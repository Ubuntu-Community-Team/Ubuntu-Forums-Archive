---
title: "Banshee Problem"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Darkblizz on 2007-10-05
K so i did everything it said to install it i got to the last step and did the "make" which i think installed it >.> sorta noob lol anyways where is it i dont see it anywhere to open it!

---

### Post by joecool362 on 2007-10-05
Could you better define your problem I'm not sure what you mean???:confused:

---

### Post by misfitpierce on 2007-10-05
Banshee I believe is also found in repos. Terminal

sudo apt-get install banshee

---

### Post by tgalati4 on 2007-10-05
Generally: (inside the directory that contains the uncompressed source files)

>./configure
>make
>sudo make install

To run it:

>banshee --debug

0.13.1 is running OK on Dapper.  Lyric plug-in doesn't work, nor does Gnome multimedia key-bindings.  These are things that are in active development.

---

### Post by Darkblizz on 2007-10-05
k all i had to do was this sudo apt-get install banshee lol im bad :( sorry for ur time! thxs though

---

### Post by trak87 on 2007-10-05
Just install it from the repositories. No need to compile it.

Run the Synaptic program in the Administration menu and look for Banshee. Select and install. Easy.

---

### Post by Darkblizz on 2007-10-05
K i thought banshee was used as an alternative for itunes how do i put my music onto my ipod?

---

### Post by Darkblizz on 2007-10-05
*bump* :P

---

### Post by tgalati4 on 2007-10-05
The reason you need to compile it is because the repository version is old.  The latest version 0.13.1 is mostly working and has some cool features.

Here's the main page:

[http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

Follow the instructions in the Getting Started section.

The iPod support is plug-N-play for the most part (depending on what model you have) but playlists on the iPod are not recognized.  These are playlists that I created in gtkpod and filled with tracks from a smart playlist.  The tracks show up in Banshee, but you can't add tracks to a specific playlist because the playlists don't show up.

In general, you need to have some music in your Banshee library.  Then drag the tracks into the iPod.

---

