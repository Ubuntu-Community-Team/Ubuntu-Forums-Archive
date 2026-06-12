---
title: "finding a directory"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by beamo on 2005-07-03
I am trying to find ~/.mplayer directory.  I don't see it anywhere. Anyone know where it is? Thanks for the help.

---

### Post by Xian on 2005-07-03
Should be in the /home/username/.mplayer path.

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=beamo]I am trying to find ~/.mplayer directory.  I don't see it anywhere. Anyone know where it is? Thanks for the help.[/QUOTE]


Its in the home folder. Make sure you have enabled the option to see hidden files.

---

### Post by beamo on 2005-07-04
Thanks for the help, Xian  :grin: 

For any other newbies like myself who have had trouble getting MPlayer to install, I botched it three times, the guide that finally worked for me is [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)


It was very easy, too.

---

### Post by beamo on 2005-07-04
> Make sure you have enabled the option to see hidden files.


Oh my, that made all the difference. I knew to do that in windows but never thought to do it with Ubuntu. Thank you for the tip.

---

### Post by f1dave on 2005-07-04
other ways of doing similar findings are (from a terminal):

ls -lsa (a more powerful and complete listing of files, includes all hidden files)

and

locate blah

where blah is the file you're looking for. A note on locate: You may need to run the following command:

sudo updatedb

Beforehand, to update your system's database of files to search.

---

### Post by gammyhand on 2005-07-04
[QUOTE=f1dave]other ways of doing similar findings are (from a terminal):

ls -lsa (a more powerful and complete listing of files, includes all hidden files)

and

locate blah

where blah is the file you're looking for. A note on locate: You may need to run the following command:

sudo updatedb

Beforehand, to update your system's database of files to search.[/QUOTE]
 I don't like mPlayer but I can't get totem working with video files? I can hear them but not see them. Any ideas?

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=gammyhand]I don't like mPlayer but I can't get totem working with video files? I can hear them but not see them. Any ideas?[/QUOTE]

sudo apt-get install gxine

gxine+w32codecs = hella powerful media player.

---

### Post by gammyhand on 2005-07-05
[QUOTE=poofyhairguy]sudo apt-get install gxine

gxine+w32codecs = hella powerful media player.[/QUOTE]
 Will install it through synaptic. Thanks for the tip :)

---

### Post by gammyhand on 2005-07-05
[QUOTE=gammyhand]Will install it through synaptic. Thanks for the tip :)[/QUOTE]
 I can't get any video to display (even though it plays) through xine. Any ideas? It says it is actually playing the file.

Also - where does xine appear on the applications list? If it doesn't how do I add it?

---

