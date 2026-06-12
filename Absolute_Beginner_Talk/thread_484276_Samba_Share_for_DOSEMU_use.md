---
title: "Samba Share for DOSEMU use"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by jamillikan on 2007-06-25
Does anyone know how to assign a drive letter to a Samba Share on a local machine so DOSEMU can write data to it?  I have a vfat partition that's mounted at /F.  It's also a samba share.  I'd like to assign a DOSEMU drive letter to it and mount it within DOSEMU in order to output data to it that Windows clients can view.  Am I reaching for the stars here or on the wrong path?

Joe

---

### Post by klytu on 2007-06-26
> **jamillikan said:**
> Does anyone know how to assign a drive letter to a Samba Share on a local machine so DOSEMU can write data to it?  I have a vfat partition that's mounted at /F.  It's also a samba share.  I'd like to assign a DOSEMU drive letter to it and mount it within DOSEMU in order to output data to it that Windows clients can view.  Am I reaching for the stars here or on the wrong path?

Joe

Is [**_[COLOR="Red"] [U]Lredir_[/COLOR][/U]**]("http://dosemu.sourceforge.net/docs/README/1.4/lredir.html")  what you are looking for maybe?

---

### Post by jamillikan on 2007-06-27
I tried that and when I tell it to write to F: it says it doesn't exist or cannot be used for Total Access files.  I'm ready to give up.  Thing is, this worked perfectly in Xandros.  I'm truly surprised it doesn't here, given how great Ubuntu is otherwise.  I'm sure it's just something I'm doing incorrectly, but no one seems to have an answer.  

You see, I'm trying to output to a Network share from DOSEMU.  So, DOSEMU needs to think that that particular "folder" is on a Network share and not part of the regular /home/<username>.  Of course, I've tried mkdir ASG and mounting the Samba share there and, still, it says is doesn't exist.

I'm clueless.  Oh, well, maybe I should just forget about it.

---

