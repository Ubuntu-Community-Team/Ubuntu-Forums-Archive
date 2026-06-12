---
title: "how to remove movie player"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by timmins on 2006-12-05
Hi, I use mplayer as my movie player, but both my movies and music use "movie player" as the default player. When I try to remove "movie player" I get this message:  
One or more applications depend on 'totem-gstreamer'. To remove 'totem-gstreamer' and the dependent applications, please switch to the advanced software manager.

Should I remove the totem-gstreamer? is it a necessary program?


also, can anyone tell me how to make XMMS the default player for audio files? I can't find the option for it.


Thanks

---

### Post by timmins on 2006-12-05
when I mark totem-gstremer for unistallation, I get a message saying:

to be removed

totem
ubuntu desktop



is this ok?

THanks

---

### Post by kevinlyfellow on 2006-12-05
To change the default app to open a file with, right click on one of the files and go to properties and go to the "Open With" tab.  You probably shouldn't remove gstreamer, but if you know that you don't use it for any other programs I'd guess it'd be ok.  In your situation it sounds like you'd be better off to leave it in.  Gstreamer is used by a lot of audio applications.

Oh, and you can remove totem without removing gstreamer.  Just go to synaptic and remove the package called totem (thats the program called movie player on Ubuntu)

---

### Post by timmins on 2006-12-05
that's exactly what I needed thanks.

---

### Post by dolphinsonar on 2006-12-13
That is one of those little annoying things that I could never figure out how to do.  What a releif to finally figure it out!  Thanks so much.

---

### Post by rico16135 on 2007-10-30
im using ubuntu 7.1, and if i go to synaptic manager and remove the package totem it will let me, but it also says its a dummy package.  Even after synaptic says its removed i can still go start it up again.  This is not a fix.  How can I get this program off my computer safely.

---

### Post by rico16135 on 2007-10-30
ok after removing that dummy package, i marked totem-gstreamer for removal.  in turn it marked the mozilla plugin for removal as well.  that is good because i won't need that after i get this beast off my computer.  Just don't mark libtotem-plparser7 for removal, as u will still need that.  It marks ubuntu-desktop for removal if u do, among other things.  just don't  do it.  I've decided to use vlc instead, and this method seems to remove the unwanted player.

---

