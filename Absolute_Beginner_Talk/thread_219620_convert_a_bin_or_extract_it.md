---
title: "convert a bin or extract it"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-07-20
how do u convert a bin file to avi or mpeg in linux.what program do u use.

---

### Post by taurus on 2006-07-20
No need to convert it if it's a video file.  Use mplayer to play it direct!!!

---

### Post by jonathan21 on 2006-07-20
will vlc medi player play bin files

---

### Post by taurus on 2006-07-20
> **jonathan21 said:**
> will vlc medi player play bin files

Probably although I only use mplayer as my media player since it can handle everything that I throw at it.  So, try it with vlc and if it can't handle your .bin, then install mplayer and you are on your way...

---

### Post by jonathan21 on 2006-07-20
thanks taurus will give it a try taurus

---

### Post by taurus on 2006-07-20
Good luck, mate.

---

### Post by Todd_Z on 2006-10-01
I would rather have all my movies in the same format, however some are downloaded as bin/cue files, does anyone know a method for converting them to avi?

---

### Post by sbergman27 on 2006-10-01
> **Todd_Z said:**
> I would rather have all my movies in the same format, however some are downloaded as bin/cue files, does anyone know a method for converting them to avi?

Well, I'm not sure what a bin file is.  Usually it is some sort of executable or script.

Linux has a utility called "file" which will identify most different kinds of files, based upon their contents, regardless of the extension.

It's a handy thing, really.  Open up a terminal and go to where the file is.  Say it is on your desktop.  Open a terminal with:

Applications->Accessories->Terminal

In the terminal type:

```

cd Desktop
file the_file_name.bin

```

The file command will tell you what it is if it recognizes it.

You can type 'exit' to exit the terminal.

Once you know what it is, perhaps we can come up with a method to  open it.

---

