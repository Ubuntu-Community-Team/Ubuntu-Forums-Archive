---
title: "making a mp3 audio cd"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-07-15
I want to make an audio disk of MP3's.  I don't want to convert the mp3's, I just want to make sure that my mp3 cd player can recognize the disk and files.

I know Nero can do this, having done it many times on windows.  I would perfer not to go back to windows or buy Nero.  Any suggestions?

---

### Post by wolfen69 on 2007-07-15
k3b should be able to handle it. best cd burning for linux IMO. make sure to install libk3b2-mp3  also. it is in synaptic.

---

### Post by Riffer on 2007-07-15
[SIZE="3"]cool ... how?  The only options I saw was for a standard audio cd or a data disk[/SIZE]

---

### Post by wolfen69 on 2007-07-15
if you burn it as a data disk, it will keep the mp3's as is.

---

### Post by RomeReactor on 2007-07-15
Hi. If I read this correctly, you want to burn your MP3 files on a CD to listen in your MP3 player, right? If so, just insert a blank disc in Ubuntu, and a window will pop up asking whether to burn a disc or ignore. Choose Burn to disc and it will create a data disc readable by your MP3 player.

If you want to burn an audio CD (to listen on a CD player), then you can either use [Serpentine]("http://s1x.homelinux.net/projects/serpentine/") (it's already installed in Applications->Sound & Video->Serpentine Audio CD Creator), or use K3B with the ibk3b2-mp3 library installed, as **wolfen69** said.

---

