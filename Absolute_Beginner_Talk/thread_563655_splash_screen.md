---
title: "splash screen"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-09-30
I didn't know where else to put this, so I posted here: Following these directions ([https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)) I can't seem to get the fingerprint thing to show up.

The reasons I'm deducing is two things: one, when I copy everything into a .so file, does that mean I have to make a directory with the .so extension?  Or do I take the .tar file and mv that to .so?

Also, when I type in the line, 
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so 
```\
I get this error
```
update-alternatives: --install needs <link> <name> <path> <priority>

Usage: update-alternatives [<option> ...] <command>

```

Finally, I'm baffled by this line: ```
/usr/lib/usplash/usplash-theme-fingerprint.so 10
```
Wait, so a .so file is an executeable?

Thanks in advance!

---

### Post by Vixis on 2007-09-30
It is one line:

```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
```

---

### Post by japtar10101 on 2007-09-30
> **Vixis said:**
> It is one line:

```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
```

Oh, wow, thanks!  I have to restart the machine to test it out, but it sounds like it's going to work!

---

