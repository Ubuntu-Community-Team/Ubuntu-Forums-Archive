---
title: "Samba slow finding Windows shares"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-01-21
Ubuntu Gutsy's shares can be accessed quickly by my Windows PC's, but Ubuntu can't seem to find the Windows shared folders and when it does, it takes a long time before they show up in the Network File Browser.

I guess I have Samba as a file server set up pretty good.  How do I get Ubuntu to find the Windows shared folders?

Carl

---

### Post by spiderbatdad on 2008-01-21
how is the windows side configured to allow sharing? This guide gives some hints, but I wouldn't go beyond the windows aspects as long as ubuntu is sharing.[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide) the permissions are not correctly applied in the samba configuration section. ie, 770 is not an octal...you'll get an error...1777 should work, but I think it's the way windows is set up...ie. password expires, or simple sharing is set.

---

