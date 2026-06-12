---
title: "[SOLVED] install error"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-14
i downloaded a video converter and its a tar file so i unpack it to the desktop and look inside and there is a file install.sh so i go to the directory and run sh install.sh and it goes along doin its thing and ends with this line:

nasm -O2 -f elf -Icommon/i386/ -o common/i386/dct-a.o common/i386/dct-a.asm
make: nasm: Command not found
make: *** [common/i386/dct-a.o] Error 127


any ideas? i appreciate it.

---

### Post by amingv on 2008-02-14
Try
```
sudo apt-get install nasm
```

---

### Post by brokenhachi on 2008-02-14
shoulda thought of that one i guess... thanks man. appreciate it.

---

