---
title: "editing /usr/ib question"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-20
i need to do this 

This may be fixed by replacing /usr/lib/libGL.so.1.2 with libGL.so.1.2 from the previous driver version (8.24.8). To do so download this file: libGL.so.1.2 and then copy it to the /usr/lib/ directory.

can someone tell my exatclt how to do this im completely clueless

---

### Post by Najand on 2006-09-20
It is not a very good way to install a library package...
But if all you need to know is how to copy...
Then:
1st, back up your last directory, if the soultion you are
trying does not work:
```

cd /usr/lib/
sudo mkdir libGL.so.1.2.bak
sudo mv libGL.so.1.2 libGL.so.1.2.bak

```
Then Extract your downloaded file and 
copy it afterwards using:
```

sudo cp -r ~/Desktop/libGL.so.1.2 /usr/lib/

```

---

### Post by swp6499 on 2006-09-20
i dont really understand what u are saying..sorry im fairly new to this but not completely...the lib file i want to copy to my /usr/lib directory is on my desktop where i downloaded it...can u walk me through this...im sorry to be a pain but i want to learn this stuff..thanks

---

### Post by swp6499 on 2006-09-20
also when i try to paste copy and paste the file or ctrl v the file it says access denied...

---

### Post by Najand on 2006-09-20
Yes, because /usr/lib is owned by the root and needs root privileges. 
The way I told you is using terminal which can be found at:
Applications -> Accessories -> Termianl

Have you extracted the downloaded file?

---

### Post by swp6499 on 2006-09-20
theres nothing to extract its just the file itself right click gives no option to extract...

---

### Post by Najand on 2006-09-20
then just back up your old one using:
```

sudo mv /etc/lib/libGL.so.1.2 /etc/lib/libGL.so.1.2.bak

```
and then copy using:
```

sudo cp ~/Desktop/libGL.so.1.2 /etc/lib/

```

---

### Post by swp6499 on 2006-09-20
tried that it says no such file or directory??

---

### Post by Najand on 2006-09-20
Hmm, which command says that. And which file or directory is not available?

---

### Post by swp6499 on 2006-09-20
i tried with the post u made earlier and it worked thanks alot for ur help...i appreciate ite alot...now if i could only get avi files to play...

---

### Post by Najand on 2006-09-21
Try to install the following in the termianl using command:
```

sudo aptitude install totem-xine totem-xine-firefox-plugin libxine-extracodecs libxinerama1

```
and then try to open files using totem

---

### Post by swp6499 on 2006-09-21
did that...it still says there is no plugin to handle this movie?

---

