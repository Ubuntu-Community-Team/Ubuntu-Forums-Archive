---
title: "Searching for a find command"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Anonii on 2006-09-29
Hello,

I have a music collection and I know that many of the files in there are double. Possibly not the filename, but the song. Any ideas on how to find some of them or all, so that I can delete them?

For example I just found a: "02 - Symphony No.2 in D, II-Larghetto" and a: "Symphony 2 in D, II-larghetto Beethoven"

Thanks!

---

### Post by aysiu on 2006-09-29
I think AmaroK has an option in Playlist to remove duplicate or dead entries.

---

### Post by Anonii on 2006-09-29
> **aysiu said:**
> I think AmaroK has an option in Playlist to remove duplicate or dead entries.
And if I use GNOME => Dont have Amarok?

(I also dont want to install it. <: )
Are there any scripts or anything?

---

### Post by bodhi.zazen on 2006-09-29
Try locate.

```
locate *.mp3
```

you will get a long list to the terminal.

Pipe to to a file:
```
locate *.mp3 > ~/Music.list
```

Now gedit ~/.music.list

To limit the search to your music file, use grep:

```
locate * | grep /path_to/Music_collection > ~/Music.txt
```

or something like that.

---

