---
title: "[SOLVED] problem getting sound for macbook 4.1 with hardy"
date: 2008-09-02
forum: Apple Hardware Users
---

### Post by hloupy on 2008-09-02
hiya

im a beginner, let me state that first. 

installing ubuntu on the macbook is nowhere near as easy as i had hoped it would be, but nevertheless by banging my head against the wall repeatedly, i seem to be making some progress. it's been two weeks now and everything seems to be going ok except getting wireless to work and sound.

here i would like to ask for help with sound.

my specs are macbook 4 (santa rosa apparently) with hardy heron.

im following the enormously helpful guide, but i got stuck here:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Sound](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Sound)

i cant get into "/etc/modprobe.d/options" to edit it because it is owned by root and although im the admin i have no permissions. does anyone know how to change this?

there is a solution, namely:
"You need to be the root user when editing. Try:
sudo vi /etc/modprobe.d/options"

which was posted here:
[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/](http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/)
 
but unfortunately although that allows me to open the file, i still dont know how to edit it (when i try to edit, i dont know how to move around and then the arrow keys give values like "B" or "D" and i just confused).

can anyone help me get sound?

thanks in advance!

---

### Post by pierrelux on 2008-09-02
I have the exact same hardware and performed quite a few installs on it. Simply follow the instructions on the wiki and it will work:

[https://wiki.ubuntu.com/MacBookPro/Penryn#Enabling%20Sound/Microphone](https://wiki.ubuntu.com/MacBookPro/Penryn#Enabling%20Sound/Microphone)

---

### Post by cyberdork33 on 2008-09-02
> **hloupy said:**
> i cant get into "/etc/modprobe.d/options" to edit it because it is owned by root and although im the admin i have no permissions. does anyone know how to change this?

there is a solution, namely:
"You need to be the root user when editing. Try:
sudo vi /etc/modprobe.d/options"

which was posted here:
[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/](http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/)
 
but unfortunately although that allows me to open the file, i still dont know how to edit it (when i try to edit, i dont know how to move around and then the arrow keys give values like "B" or "D" and i just confused).
sudo allows you to temporarily have root permission for whatever command you are running. vi is an editor (the problem is you likely do not know how to use vi, don't worry you are not the only one. You can find all kinds of info on using vi on the net.)

If you want to use a simple editor, try nano.

```
sudo nano /etc/modprobe.d/options
```

---

### Post by hloupy on 2008-09-02
> **pierrelux said:**
> I have the exact same hardware and performed quite a few installs on it. Simply follow the instructions on the wiki and it will work:

[https://wiki.ubuntu.com/MacBookPro/Penryn#Enabling%20Sound/Microphone](https://wiki.ubuntu.com/MacBookPro/Penryn#Enabling%20Sound/Microphone)

hiya, thanks for replying but thats not quite true, because i am macbook 4.1 santa rosa and you seem to be a macbook pro penryn

---

### Post by hloupy on 2008-09-02
> **cyberdork33 said:**
> sudo allows you to temporarily have root permission for whatever command you are running. vi is an editor (the problem is you likely do not know how to use vi, don't worry you are not the only one. You can find all kinds of info on using vi on the net.)

If you want to use a simple editor, try nano.

```
sudo nano /etc/modprobe.d/options
```

hmmm thanks for that, i will try out nano and see if that works. as you probably guessed, i had no idea what  vi is, let alone how to use it!

---

### Post by hloupy on 2008-09-02
wow it worked! i'm very chuffed.

thanks!

---

### Post by cyberdork33 on 2008-09-02
> **hloupy said:**
> wow it worked! i'm very chuffed.

thanks!
No problem.

Please mark this thread as solved from the thread tools menu.

---

