---
title: "Share names with spaces?"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by Mr. Electric Wizard on 2005-06-14
Hello all,
I am trying to mount-to-location to be able to play music files I have on another computer on my network.
The share name is My Music.
Samba isn't liking the space on this folder, so does anybody know the syntax that I should use?
I thought that %20 = Space, but that isn't working...
 :?

---

### Post by Knome_fan on 2005-06-15
Disclaimer: I don't use samba, so my suggestion might be totally wrong. 

Anyway, at least in bash the character you are looking for is \, so that the folder would become My\ Music. As I said, I don't have a clue if that works with samba, but you could give it a try.

---

### Post by trash on 2005-06-15
i'm in windows at the moment so i can't check this to see if it works.... all this while i've been changing the names of files like yours (my music -> mymusic) but just reading this post made me remember reading on this forum somewhere about using quotes so it's read as one item and not two... so try "My music"

---

### Post by Mr. Electric Wizard on 2005-06-15
Nope, no workie...  Still Invalid share name.

---

### Post by trash on 2005-06-15
Just tried it here(not with samba) but you need to have the whole location in quotes, ex: 
$ cd "home/My music"

---

### Post by Mr. Electric Wizard on 2005-06-15
Ahh, I see...
I'll try when I get home tonight!
Thnx!

---

### Post by Mr. Electric Wizard on 2005-06-16
The "quotes around the path" worked like a charm!
Thanks! :razz:

---

