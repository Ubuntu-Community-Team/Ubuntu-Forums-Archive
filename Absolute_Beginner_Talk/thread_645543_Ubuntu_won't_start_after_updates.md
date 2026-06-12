---
title: "Ubuntu won't start after updates"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by mq23 on 2007-12-20
Hello!

I've been using Ubuntu for about 8/9 months, never had too many problems, until a ran the updates this morning.

I restarted my PC, and it stops at the grub prompt.

I've followed the install Grub from live cd guide by Catlett, but it still does the same thing.


Could someone give me some advice?.

Thanks in advance.

---

### Post by spiderbatdad on 2007-12-20
might be able to help if your having the same problem I had. When the boot process stops, try hitting escape a few times (probably doing nothing) but be patient and wait several minutes to see if the splash screen finally comes up. If it does, I believe your usplash.conf settings are wrong and screen resolution settings are off, causing boot to hang

---

### Post by ukripper on 2007-12-20
> **mq23 said:**
> Hello!

I've been using Ubuntu for about 8/9 months, never had too many problems, until a ran the updates this morning.

I restarted my PC, and it stops at the grub prompt.

I've followed the install Grub from live cd guide by Catlett, but it still does the same thing.


Could someone give me some advice?.

Thanks in advance.

Try booting from super grub disk and then fix if it is a grub problem.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by mq23 on 2007-12-20
> **spiderbatdad said:**
> might be able to help if your having the same problem I had. When the boot process stops, try hitting escape a few times (probably doing nothing) but be patient and wait several minutes to see if the splash screen finally comes up. If it does, I believe your usplash.conf settings are wrong and screen resolution settings are off, causing boot to hang

Thanks Spiderbatdad!

But that deosn't make ubuntu start.

---

### Post by GSF1200S on 2007-12-20
What do you mean it stops at the Grub prompt? Does it return a Grub error, is it locked at the selection menu or do you have a black screen? If you have a black screen, try hitting Alt+F1 (or F2, cant remember). Be forewarned, you may be at a command prompt. If you are, type:

startx

If you get an X error, regenerate xorg.conf with the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

Select your resolution and the VESA drivers, and youll at least have a GUI. What video card do you have?

---

### Post by spiderbatdad on 2007-12-20
just read another post where menu.lst was fouled up and grub was pointing to wrong hd location.[http://ubuntuforums.org/showthread.php?t=645116](http://ubuntuforums.org/showthread.php?t=645116)

---

### Post by mq23 on 2007-12-20
> **GSF1200S said:**
> What do you mean it stops at the Grub prompt? Does it return a Grub error, is it locked at the selection menu or do you have a black screen? If you have a black screen, try hitting Alt+F1 (or F2, cant remember). Be forewarned, you may be at a command prompt. If you are, type:

startx

If you get an X error, regenerate xorg.conf with the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

Select your resolution and the VESA drivers, and youll at least have a GUI. What video card do you have?

Thanks GSF1200s,

I'm at the black screen with a prompt that says,

GRUB>

with a msg at the top which starts off, [ Minimal BASH-like editing is supported etc

Alt and F1 or F2 doesn't do anything

When I enter startx I get an Error 27 unreconied command

---

### Post by mq23 on 2007-12-20
> **spiderbatdad said:**
> just read another post where menu.lst was fouled up and grub was pointing to wrong hd location.[http://ubuntuforums.org/showthread.php?t=645116](http://ubuntuforums.org/showthread.php?t=645116)

I checked that also, it's looking at the right place, or at least when i run the find /boot/grub/stage1 cmd
it says (hd0,0), which is the same it the menu.ist file.

---

### Post by mq23 on 2007-12-20
> **ukripper said:**
> Try booting from super grub disk and then fix if it is a grub problem.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Thanks ukripper!

I've tried the super grub disk, but I still end up with the same problem.

---

### Post by mq23 on 2007-12-20
Is there any way of doing a reinstall of ubuntu without formatting the hard drive?

---

### Post by snkmad on 2007-12-20
Hope this can help:
[http://ubuntuforums.org/showpost.php?p=3988594&postcount=56](http://ubuntuforums.org/showpost.php?p=3988594&postcount=56)

---

