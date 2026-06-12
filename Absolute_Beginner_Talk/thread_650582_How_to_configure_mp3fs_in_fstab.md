---
title: "How to configure mp3fs in fstab"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ceejay on 2007-12-26
Hello

not sure if this is a bit obscure but... I've just installed mp3fs ( [http://mp3fs.sourceforge.net/](http://mp3fs.sourceforge.net/) ) and can successfully use it from a commandline to mount a pseudo file system containing "mp3" shadows of my FLAC collection. Excellent.

Now I want to add the mount to fstab so it mounts on startup: I've seen some notes that suggest that this should be possible, but no sample syntax for the fstab entry.

Can anyone help?

TIA

---

### Post by jpkotta on 2007-12-26
[http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab](http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab)

---

### Post by ceejay on 2007-12-26
Yeah, I'd found that page while googling, but how do I tell it that this is an mp3fs file system as opposed to a vanilla fuse one? Or doesn't it matter? There is a specific option (bitrate) that mp3fs needs, as well, so where would that go?

An explicit example for mp3fs would be really helpful...

TIA

---

### Post by Kirk Wolf on 2007-12-27
This line in /etc/fstab worked for me under Ubuntu Gutsy:

[FONT="Courier New"]mp3fs#/home/kirk/Music,256  /home/kirk/mp3_music  fuse  allow_other,ro  0 0[/FONT]

---

### Post by ceejay on 2007-12-27
Kirk

many thanks for that, I would never have guessed!

The "mp3fs#" bit at the beginning is puzzling, I don't suppose you could explain? Not critical, though, it seems to work...

Regards
ceejay

---

