---
title: "amsn questions! -Skins... oh and keyboard"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by TomParker on 2006-07-29
How do I make amsn look better? I tried intallin a skin but I got this error

> 
Extraction not performed

You don't have the right permissions to extract archives in the folder "/usr/share/amsn/skins"

How would I get access into that foldr to drop some skins in there i´m currently using 0.96 rc1 :) 

---- Keyboard Question ---

My keyboard types ¨ <--- them instead of " <--- these thus it doesnt work i&#324; terminal and i end up googing for a speech mark lol how do I like set it up to do them the keyboard is britsh and all proper setup

---

### Post by Mike Tomasello on 2006-07-29
Not entirely sure about aMSN (I'm still a newbie :(), but with the keyboard:

System Menu->Preferences->Keyboard->"Layouts" Tab->"Add" Button and select United Kingdom from the list, then set that as your default/remove any other.

(I think)

---

### Post by TomParker on 2006-07-29
Dvorak has the speechmarks but the international one thts in there doesnt US does but the @ is in the wrong place lol :(

Arrrr fixed :D found out if you just click United Kingdom that option works :D thanks now I just need the amsn skin help and i'm sorted :)

---

### Post by ironfistchamp on 2006-07-29
For the skins the reason you can't put them in there is you need root permissions to write there (i think). When I install skins for amsn I put them in /home/USERNAME/.amsn/skins

That does the trick for me. If you then wanted them system wide you could do

```

sudo cp ~/.amsn/skins/SKINFOLDER /usr/share/amsn/skins

```

~/ means home dir if you didn't know;) 

Hope this is relavent/helps

Ironfistchamp

---

### Post by aeto on 2006-07-29
yes thats right. root permission is needed. if u dont like to type much, u can try this:

```
gksudo nautilus
```

then u can just copy/paste/cut. its a waste of time no doubt. u can try ctrl+h to unhide folders. i suggest u get used to the terminal..tasks like this can b carried out much faster.

---

