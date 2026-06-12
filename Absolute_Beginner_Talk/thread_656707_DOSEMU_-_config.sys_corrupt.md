---
title: "DOSEMU - config.sys corrupt"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Raja Lakshminarayan on 2008-01-02
Hi,

I installed DOSEMU in Gutsy and it was working fine till I tried to edit the config.sys and managed to corrupt it.
Now when I start DOSEMU, I see a error in one of the config.sys lines and refuses to proceed with the boot. I tried complete uninstalling and re-installing with synaptic. But again I get stuck i the same place.

I'm a newbie and very frustrated that I destroyed a perfectly working program. Please help me get DOSEMU working again.

Raja.

---

### Post by Raja Lakshminarayan on 2008-01-03
Hi,

I'm attaching the screen shot of the error I get when starting DOSEMU.
Hope somebody finds me a solution.

I just found that I can start DOSEMU as a super user using the command line:
sudo /usr/bin/xdosemu

I found out that the line in the config.sys that is used when starting DOSEMU as an ordinary user has error in the line:
install- d:\dosemu\lredir.com z: linux\fs\${DOSEMU_LIB_DIR}/drive_z ro

When editing I used "-" instead of "=" after install

How can I correct the damage ?

Raja.

---

### Post by Raja Lakshminarayan on 2008-01-04
I've solved the problem myself :guitar:

Maybe elementary for  the 'experts', but for a newbie it's a real killjoy. So here's my bit to help out newbies like me who are foolish enough to manage to corrupt the DOSEMU config.sys file.

DOSEMU writes a few files into a hidden folder called .dosemu located under the home>username folder. Here you will find a few files and among them config.sys and autoexec.bat 

Simply make necessary corrections to these files or overwrite them them with 'clean' files! As simple as that - once u know what to do :lolflag:

Hope this helps somebody.

Raja.

---

