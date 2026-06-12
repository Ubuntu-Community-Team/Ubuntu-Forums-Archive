---
title: "How do i open a file from xmms"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Draqshorul on 2007-04-02
Starting xmms is simple

But i want to start a certain song for example

```
///home/draqshorul/Desktop/Christina Aguilera - Back To Basics [2006]/CD2/03 - Christina Aguilera - Candyman.mp3
```

```
sudo ///home/draqshorul/Desktop/Christina Aguilera - Back To Basics [2006]/CD2/03 - Christina Aguilera - Candyman.mp3
```
dosen`t work 



Or just set up xmms to play a song when it starts
...


Help! :D

---

### Post by mills on 2007-04-02
are you trying to start a song the from from the terminal prompt?

you can press the small button on xmms labelled PL (playlist) and it will bring up a screen that you can drag and drop your music into

and also you may want to make sure xmms is your defualt mp3 player right click the file in nuatilus go to properties then open with and selct xmms

---

### Post by Loco_gr on 2007-04-02
Try:
```
xmms /home/draqshorul/Desktop/Christina Aguilera - Back To Basics [2006]/CD2/03 - Christina Aguilera - Candyman.mp3
```

There are other ways too:
1. You can Drag&Drop your songs to the playlist
2. There is an Add Button to the playlist, where you can add a url or a directory
3.Open xmms and
     a. Press L to open a single file
     b. Press Shift+L to open a directory with songs
     c. Press Control+L to open a web location (such as internet radio station)

---

### Post by mills on 2007-04-02
never knew about number 3 loco_gr

nice tip, cheers

---

### Post by Draqshorul on 2007-04-02
```
xmms /home/draqshorul/Desktop/Christina Aguilera - Back To Basics [2006]/CD2/03 - Christina Aguilera - Candyman.mp3
```

it works...but dosen`t play the song .... 

The thing is that i want to play the song not start xmms with this song on playlist

---

### Post by RedSquirrel on 2007-04-02
Try:

```
xmms -p <song-to-play>
```

Have a look at the manual page to see the other options.

```
man xmms
```

---

### Post by familyjules74123 on 2007-04-02
make sure its not a windows media file.  List the file as well as the filetype it is please. drag and drop should work, if that doesnt work, there is a good chance the file wont play in xmms.  Also, have you installed all of the correct codecs?

---

