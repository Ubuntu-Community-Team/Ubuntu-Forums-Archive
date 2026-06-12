---
title: "Id3"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-03
Hey, is there a way to edit ID3 tags for .mp3 files in ubuntu, or do i need to download a program to do so?

---

### Post by forestpixie on 2007-11-03
I use kid3 which is a kde program but iot works in ubuntu - there's probably a gnome one bu t I don't know it

install from terminal

```
sudo apt-get install kid3
```

---

### Post by Madpilot on 2007-11-03
EasyTag is nice for id3 tag editing; it'll handle mp3/ogg/flac.

It's in Universe repository, so in Add/Remove, make sure you've got "All Available Sources" selected in the dropdown on the top right corner.

I assume  you've already got the mp3 codecs installed?

---

### Post by jordank on 2007-11-04
i couldn't find easytag, and sudo apt-get install EasyTag didn't work.
as for kid 3, it asked me if i wanted to unpack 78 mb for it, that seems ridiculously high for just an id3 viewer/editor program.  Is there another alternative that is just a very simple and basic id3 viewer/editor?

---

### Post by jordank on 2007-11-10
bump

---

### Post by bluepowder7 on 2007-11-10
i once found and used a program called "mp3tag" on my winxp machine, and it was great for batch tagging - it was able to modify tags based on file names, and vice-versa.  my winxp machine is currently tore down, so i can't verify where i downloaded it from or who the author was...  do a google, see if you can find it.

---

### Post by jordank on 2007-11-10
Well i'm looking for something for linux.  I noticed when i right click an mp3 file, i cant edit artist/title/album/etc.. i just want a small little program to do this.
anyone know of any?

---

### Post by jordank on 2007-11-13
no? there's no way of editing mp3 tags on ubuntu?

---

### Post by FuturePilot on 2007-11-13
EasyTag is a great ID3 tag editor.```
sudo apt-get install easytag
```

---

### Post by shad0w_walker on 2007-11-13
Do you have all your repos enabled? easytag is definitely there and remember to be careful about capitals in the command line. Linux actually takes notice so if you used 'EasyTag' it wouldn't have found it because the package name is 'easytag'

---

### Post by jordank on 2007-11-14
yeah i think i put the caps in. it installed i believe. not exactly sure how to use it or find it, but i'll play around.

---

### Post by FuturePilot on 2007-11-14
It should be under Applications>Sound & Video

---

### Post by jordank on 2007-11-15
I used easytag but didnt' like it. Sure it allows you to edit/view your id3 tags, but i need something that is good for bulk renaming/editting tags.  Anyone know of similar programs to this?

---

### Post by Inxsible on 2007-11-15
> **jordank said:**
> I used easytag but didnt' like it. Sure it allows you to edit/view your id3 tags, but i need something that is good for bulk renaming/editting tags.  Anyone know of similar programs to this?Easy Tag does bulk editing.

But I agree, the process is not intuitive.

---

### Post by jordank on 2007-11-16
I dont think it does bulk renaming.  I dont think it can pull an artist from the id3 tag, set it as first part of file name, then pull the title of the track from the id3 tag and put it as the second part of file name.. like

Artist - Title

I've only seen programs on windows do this.

---

### Post by Inxsible on 2007-11-16
> **jordank said:**
> I dont think it does bulk renaming.  I dont think it can pull an artist from the id3 tag, set it as first part of file name, then pull the title of the track from the id3 tag and put it as the second part of file name.. like

Artist - Title

I've only seen programs on windows do this.It does that exactly.

Unfortunately, I won't be able to describe how right now, since I am not on my Linux box at this moment

---

### Post by jordank on 2007-11-16
I'll take another look at it.

---

### Post by CatKiller on 2007-11-17
I use Audio Tag Tool, which you might like better.

```
sudo aptitude install tagtool
```

---

### Post by jordank on 2007-11-17
thanks, i'll take a look

---

