---
title: "where does Rhythmbox keep music's tags and info?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-04
hey I have changed my music files tags (like Artist , Album name and...) in linux using rhythmbox, 

when I go to linux and play the music I dont see the tags which I entered in linux... why is that ?

and if I reinstall ubuntu , will I all those entered data to my music files ? how can I make rhythmbox to write these info the Music Files , so they be there foreever ?

---

### Post by aysiu on 2007-05-04
Music tags are stored in the actual music file itself. There are two versions of tags: ID3v1 and ID3v2. It may be trying to read ID3v2 but you have only ID3v1.

A good tag editor is TagTool, available in the repositories.

Rhythmbox store only what songs are available for the library, how many times you've played them, and your ratings and such.

---

### Post by medya on 2007-05-04
but Rhthmbox lets u change the title and stuff ... do I have to install a Tag Editor to do that ?
is amaroK like this too ?

---

### Post by aysiu on 2007-05-04
> **medya said:**
> but Rhthmbox lets u change the title and stuff ... do I have to install a Tag Editor to do that ?
is amaroK like this too ?
When Rhythmbox lets you change the title and stuff, it is acting as a tag editor.

The tag information still lives in the music file itself, not in any Rhythmbox settings.

---

### Post by medya on 2007-05-04
> **aysiu said:**
> The tag information still lives in the music file itself, not in any Rhythmbox 
settings.

thats what I am telling you should be ! I changed the the music's tag info like artist name and album name .
but when I go to windows, I dont see them !
does any body know ?

---

### Post by aysiu on 2007-05-04
Install TagTool and take a look at the tags. You can see if they're ID3v1 tags, ID3v2 tags, or both.

What program in Windows are you using to read the tags?

---

### Post by medya on 2007-05-05
mediaplayer...

by the way do u know where R.B stores the other info ? like music rate or stuff?

---

### Post by aysiu on 2007-05-05
/home/medya/.gnome2/rhythmbox/rhythmdb.xml

Also known as ~/.gnome2/rhythmbox/rhythmdb.xml

---

