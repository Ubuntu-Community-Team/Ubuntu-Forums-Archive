---
title: "Installing XQDE help"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by wconstantine on 2007-05-02
I've downloaded the program but when I'm trying to run the app it says I lack some files. It's one of the requirement files and I wouldn't be surprised if I lack the others as well.

        libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb7efd000)
        libQtXml.so.4 => /usr/lib/qt4/libQtXml.so.4 (0xb7ebd000)
        libQtGui.so.4 => /usr/lib/qt4/libQtGui.so.4 (0xb784f000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7805000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7669000)
        libQtNetwork.so.4 => /usr/lib/qt4/libQtNetwork.so.4 (0xb7612000)
        libQtCore.so.4 => /usr/lib/qt4/libQtCore.so.4 (0xb74a6000)
        libstdc++.so.6 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libstdc++.so.6 (0xb73a0000)
        libm.so.6 => /lib/libm.so.6 (0xb737c000)
        libgcc_s.so.1 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libgcc_s.so.1 (0xb7372000)
        libc.so.6 => /lib/libc.so.6 (0xb7251000)
        /lib/ld-linux.so.2 (0xb7f1e000)

Is there any easy way to get these files? Is there a package that automatically installs all these files or something?

Edit: Nevermind. I checked the INSTALL file and it said QT4 there. I downloaded python-qt4 and it worked!

---

### Post by Ptero-4 on 2007-05-05
Hi. Can you send me the XQDE source code pls. My email is [email]Ptero.4@gmail.com[/email] (They removed it from their site).

---

### Post by wconstantine on 2007-05-06
I don't have the source sorry. Didn't download the source either. Maybe I should have named it Running XQDE help.

---

### Post by chaumurky on 2007-07-05
Hmm,  have all the deps but I get the following when running the precompiled binary

> ./xqde: symbol lookup error: ./xqde: undefined symbol: _ZN9QListData7detach2EvBad runtime error - QT4 version mismatch? Maybe I need to compile it?

---

### Post by Ptero-4 on 2007-07-13
I just compiled the new xqde 2007-07-07 on my relatives PC. The binary tarball and theme are attached.

---

### Post by wconstantine on 2007-07-13
Ok. Could you post a screenie so we can se if it's something to go for yet? =)

---

### Post by Ptero-4 on 2007-07-16
I removed it. Didn't like it to much b/c it's corners are square and I found kiba-dock better.

---

