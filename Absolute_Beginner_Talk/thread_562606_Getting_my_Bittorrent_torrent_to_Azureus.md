---
title: "Getting my Bittorrent torrent to Azureus"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by PmDematagoda on 2007-09-29
Okay, now the thing is the download of the Ubuntu Ultimate x64 is about to finish, but the big problem is that the torrent is located in my Windows copy, but right now I don't want to go anywhere near it(Stability reasons). So is it possible to get the torrent to my Ubuntu installation from the Windows one? The Torrent client in XP is Bit Torrent, the Torrent Client in Ubuntu is Azureus.

---

### Post by mikewhatever on 2007-09-29
Can you rephrase, because I do not understand.  Neither the Ubuntu iso, nor its *.torrent file can harm your Windows in any way. The same *.torrent file can work on any torrent client no matter what OS. Lastly, if you meant the downloaded iso, you have to burn it to a CD to install, haven't you.

---

### Post by PmDematagoda on 2007-09-29
No, it's not the .iso file, my XP was unstable before that. 

My question is how do I get my nearly finished Ubuntu iso from Bit Torrent in XP to be finished by Azureus in Ubuntu?

---

### Post by southernman on 2007-09-29
You should be able to (never had the need to do this) just copy the torrent file itself, and the torrent download from your ntfs over to your azureus folder in ubuntu.

I can't say that the advice will work with absoulete certainty, but it can't hurt to try it.

Once copied over, you may need to add the new torrent in azureus, so it knows you want to download that torrent?

Clear as mud yet? *wink*

---

### Post by mikewhatever on 2007-09-29
Why not just finish it in Windows? You can load the *.torrent file in Azureus, and when it asks where to save the download, point it to the directory with that 'nearly finished' file. Azureus will run a check on it and pick up from where Bittorrent stopped. However, you have to make sure Azureus can write to the file system on that partitions, since it could be ntfs.

---

