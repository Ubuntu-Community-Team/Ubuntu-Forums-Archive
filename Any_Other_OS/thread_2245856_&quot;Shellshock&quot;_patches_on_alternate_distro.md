---
title: "&quot;Shellshock&quot; patches on alternate distros"
date: 2014-09-26
forum: Any Other OS
---

### Post by PondPuppy on 2014-09-26
(This could go in the security forum, I suppose...)

Mint, Manjaro (Arch), and Salix (Slackware) all have the partial patch for the Bash vulnerability in their update stream. 

Manjaro:

```
sudo pacman -Syyu
```

(This is the full rolling update, I needed to do that anyway but it takes awhile.)

Salix:

Use gslapt or

```
sudo slapt-get --update
sudo slapt-get --install bash
```

Haven't gotten around to OpenSUSE yet.

---

### Post by QIII on 2014-09-26
Just do your normal updates on openSUSE.  I got the patch last night.

Same for Fedora, Debian, Trisquel, Bodhi.

Don't know if Solaris got it because after running my updates the new boot environment promptly barfed on me and wouldn't load.

---

### Post by PondPuppy on 2014-09-26
Yes, just got there. Thanks.

---

