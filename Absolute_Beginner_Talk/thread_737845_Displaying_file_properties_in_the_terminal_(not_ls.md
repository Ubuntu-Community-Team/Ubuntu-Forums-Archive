---
title: "Displaying file properties in the terminal (not ls -l)"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by dan06 on 2008-03-28
I'm fairly new to ubuntu, but I've been trying to use terminal as much as possible. When I'm going through a music folder and I want to find the properties of a .mp3, is there any way to display the audio properties such as bitrate and artists, etc in the terminal?

This is not just "ls -l" because i don't want to know the read/write type properties, I want properties that are mostly specific to audio files.

---

### Post by wormser on 2008-03-28
Try using the file command.

```
file 02\ -\ Just\ One\ Fix.ogg
```

The results will look like this:
> 02 - Just One Fix.ogg: Ogg data, Vorbis audio, stereo, 44100 Hz, ~160000 bps, created by: Xiph.Org libVorbis I

There might be some other commands that give more information.

---

