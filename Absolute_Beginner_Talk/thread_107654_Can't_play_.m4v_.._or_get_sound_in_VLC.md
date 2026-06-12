---
title: "Can't play .m4v .. or get sound in VLC"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Deaf_Head on 2005-12-23
Totem works fro everything but .m4v and VLC doens't give me any sound. If I can get help for either of these problems I'd love you for ever or something.

---

### Post by Perfect Storm on 2005-12-23
Have you tried changing the diffrent Audio setting in VLC?

**Settings** ---> **Preferences**.

Make sure to select advance (a little box in the buttom right)
**Audio** ---> **Output modules**

Try changing the diffren settings there.

By the way any error output when running vlc in the terminal? To run vlc in the terminal type:

```
wxvlc
```

and run a test with it.

---

### Post by Deaf_Head on 2005-12-24
.m4v problem:

```
 [00000334] access_file access error: file /home/duncan/iPodderData/downloads/Rev ision3 - Diggnation wKevin Rose & Alex Albrecht/diggnation--0025--2005-12-15--sm all.m4v is empty, aborting
```

It says taht a couple of times and than says

```
[00000260] main playlist: nothing to play
[00000260] main playlist: stopping playback
```

VLC Problem:

Whenever I open VLC from terminal or menu and use the in program browser to find the files it works ... if I use the OS explorer to find and open teh files it doesn't.

Sometimes when I up teh number of audio channels in preferences it will though.. but when i try it again i have to up it even more to get it to work again.

---

### Post by Deaf_Head on 2005-12-24
.m4v problem:

```
 [00000334] access_file access error: file /home/duncan/iPodderData/downloads/Rev ision3 - Diggnation wKevin Rose & Alex Albrecht/diggnation--0025--2005-12-15--sm all.m4v is empty, aborting
```

It says taht a couple of times and than says

```
[00000260] main playlist: nothing to play
[00000260] main playlist: stopping playback
```

VLC Problem:

Whenever I open VLC from terminal or menu and use the in program browser to find the files it works ... if I use the OS explorer to find and open teh files it doesn't.

Sometimes when I up teh number of audio channels in preferences it will though.. but when i try it again i have to up it even more to get it to work again.

*edit*

I did a search for VLC in synaptics and installed anything with plugin attached to it .. generally it now works .. and has made totem able to open some files VLC still cant' run (lol)

still hoping for .m4v help though =D

---

### Post by BoyOfDestiny on 2005-12-24
[QUOTE=Deaf_Head].m4v problem:

```
 [00000334] access_file access error: file /home/duncan/iPodderData/downloads/Rev ision3 - Diggnation wKevin Rose & Alex Albrecht/diggnation--0025--2005-12-15--sm all.m4v is empty, aborting
```

It says taht a couple of times and than says

```
[00000260] main playlist: nothing to play
[00000260] main playlist: stopping playback
```

VLC Problem:

Whenever I open VLC from terminal or menu and use the in program browser to find the files it works ... if I use the OS explorer to find and open teh files it doesn't.

Sometimes when I up teh number of audio channels in preferences it will though.. but when i try it again i have to up it even more to get it to work again.

*edit*

I did a search for VLC in synaptics and installed anything with plugin attached to it .. generally it now works .. and has made totem able to open some files VLC still cant' run (lol)

still hoping for .m4v help though =D[/QUOTE]


If you mean mkv, it's broken in the vlc in breezy. It's verison is 0.8.4-test1. Before I upgraded (from .8.2) (they added the new one about 3 days before breezy was released) it could play mkvs... Go figure... 
Everything should be peachy for dapper though. :)

---

### Post by Perfect Storm on 2005-12-24
You can try my VLC .deb file, though it aren't build for the masses but optimzed for my system, perhaps it works for you. By the way it's build with enable gtk2 too.

Just remove the .zip from the name and dpkg it(sudo dpkg -i vlc-0.8.4a_0.8.4a-1_i386.deb).

[http://thilockdominus.freehomepage.com/download/vlc-0.8.4a_0.8.4a-1_i386.deb.zip](http://thilockdominus.freehomepage.com/download/vlc-0.8.4a_0.8.4a-1_i386.deb.zip)

---

