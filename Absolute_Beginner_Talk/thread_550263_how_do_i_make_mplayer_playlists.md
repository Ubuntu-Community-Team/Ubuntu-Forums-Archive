---
title: "how do i make mplayer playlists?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-09-13
i know how to do it from various gui style media players, but not mplayer.

---

### Post by jrib on 2007-09-13
```

-playlist <filename>
              Play files according to a playlist file (ASX, Winamp, SMIL, or  one-file-
              per-line format).

```

So I suppose the easy way would be to put one file per line

---

### Post by fuscia on 2007-09-13
> **_jason said:**
> ```

-playlist <filename>
              Play files according to a playlist file (ASX, Winamp, SMIL, or  one-file-
              per-line format).

```

So I suppose the easy way would be to put one file per line

i hate to say it, but you lost me there. i know how to do drag and drop only. i'm clueless otherwise.

---

### Post by jrib on 2007-09-14
I thought you were using mplayer on the command line, but I see now what you meant.  I don't see a way to save the playlist in mplayer.  I know it can use playlists from other programs like VLC though.

---

### Post by JBAlaska on 2007-09-14
If your a drag n' drop kinda person, maybe you should use the totem frontend to mplayer. In totem you simply manage your playlists in the sidebar. 
Nice easy interface including the coveted drag n' drop.

Edit: or possibly I'm missing the point lol

---

### Post by philinux on 2007-09-14
Right click in the player and select playlist then add files.

---

### Post by fuscia on 2007-09-14
sorry for the confusion. i'm using mplayer from the command line and don't have even the beginning of a clue how to create playlists from the cl. (i should probably just stick to audacious and the like, but where's the fun in that?)

---

### Post by brunoaco on 2008-06-04
can you guys show me how a command line for mplayer is?

can i run mplayer from any folder?

i'm a newbee to, sorry.

---

### Post by jrib on 2008-06-04
> **fuscia said:**
> sorry for the confusion. i'm using mplayer from the command line and don't have even the beginning of a clue how to create playlists from the cl. (i should probably just stick to audacious and the like, but where's the fun in that?)

just put the path to each file on a separate line with your favorite text editor

---

### Post by jrib on 2008-06-04
> **brunoaco said:**
> can you guys show me how a command line for mplayer is?

can i run mplayer from any folder?

i'm a newbee to, sorry.

Why not use the gui if you are a newbee?  If you want to open a file on the command line with mplayer you just run: ```
mplayer /path/to/media/file
```

---

### Post by KingTermite on 2008-06-04
> **_jason said:**
> just put the path to each file on a separate line with your favorite text editor
That's how I've done it for years! You can even use command line redirection and create a playlist using your 'ls' command ('dir' in DOS).

I even wrote a Perl script to create play lists in every directory it found MP3 files once. PM me if interested, I can dig it out.

---

