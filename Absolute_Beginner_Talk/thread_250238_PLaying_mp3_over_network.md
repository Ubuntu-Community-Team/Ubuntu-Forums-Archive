---
title: "PLaying mp3 over network?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Nicarlo on 2006-09-03
I have two computers at my home one is a desktop running windows xp pro and the other one is my laptop running ubuntu. I installed mplayer but when i try to access and play music on my desktop through the network i get an error. Is there a way i can stream my mp3s straight from a networked pc ?

thanks alot for the help guys

---

### Post by Rebeca on 2006-09-03
First, can you play local mp3s? If not, click [here]("https://help.ubuntu.com/community/RestrictedFormats").

If you can play local mp3s, can you access other types of files over your network normally? If not and you need to set up a network or something of the sort, [read this]("https://help.ubuntu.com/community/SettingUpSamba").

If you can access other files normally, but have problems playing mp3s, you can try mounting or this: [http://www.ubuntuforums.org/showthread.php?t=223284](http://www.ubuntuforums.org/showthread.php?t=223284) (it's for avis, but you can try it with mp3s)

---

### Post by aaronbeekay on 2006-09-03
What's the error you get when you try to play the the file?

Also, perhaps you could use software like iTunes on the XP machine and listen to the music through a program like Banshee or rhythmbox?

---

### Post by Nicarlo on 2006-09-03
This is the error i am getting. 
Totem could not play 'smb://nicarlo/D/My Documents/My Music/intro.mp3'.

I use to stream it straight through windows media player. Is there a program simular to windows media player that i can use/download ?

---

### Post by Rebeca on 2006-09-03
I thought you said you tried it with mplayer, but you can try playing the file with any program. I don't think there's something very similar to Windows Media Player, but there are plenty of media players that you can try:

Xine
Mplayer
VLC
XMMS or Beep Media Player (similar to winamp)
Amarok or Banshee (similar to iTunes)

After you get the totem error, does it say why it can't play the file? If so, you might want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=46487").

---

