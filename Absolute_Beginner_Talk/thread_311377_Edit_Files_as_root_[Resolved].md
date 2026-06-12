---
title: "Edit Files as root [Resolved]"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-02
Hi all, I'm new to Linux and this is my first post so please be gentle.

I've read a lot on this forum and in 2 books I've purchaesd before installing Ubuntu, so have gotten a good start.
I wnet with a dual drive install - thanks to the posts here and it worked great. Now I'm on to tuning my system

_First issue - ATI Radeon X300SE_
Based on info in "Ubuntu Hacks" -O'Reilly Press, I installed xorg-driver-fglrx to update my video driver.
After the driver install the next step is to edit /etc/X11/xorg.conf to change the Driver setting from "ati" to "fglrx"

When I try to run this command I get the following error, but I think I am correclty acting as root ( I ran sudo -i before trying the edit)

root@main-desktop:/etc/X11# edit xorg.conf
[B]Warning: unknown mime-type for "xorg.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
[/B]root@main-desktop:/etc/X11#

Any ideas or suggestions would be appreciated.

Thanks

---

### Post by disc on 2006-12-02
Try "gedit" or "nano" in place of "edit".

---

### Post by angkor on 2006-12-02
try:

```
sudo gedit /etc/X11/xorg.conf
```

or at the console:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Shatrat on 2006-12-02
I type slow.

---

### Post by 56phil on 2006-12-02
Welcome to Ubuntu.

I suggest you avoid *sudo -i*. It's dangerous. Have you considered ```
sudo gedit /etc/X11/xorg.conf
```
It's what I used to edit configuration files and I haven't had an error like that, not yet anyway.

---

### Post by dkenny on 2006-12-02
Wow, you guys are fast!

Thanks

Can I ask a follow on Q? I want to learn this stuff properly, so..
Why did gedit work when edit didn't

Thanks

---

### Post by Shatrat on 2006-12-02
I'm not sure what edit is, but its not a text editor.
gedit is.

---

### Post by IYY on 2006-12-02
To edit a text (ASCII) file, you need to open it in a text editor. The command `edit' is not a text editor. Examples of text editors are: **nano** (a simple editor you can use in the terminal), **vim** (a much more complicated editor for the terminal which you shouldn't bother with yet), **gedit** (a graphical text editor installed with Ubuntu), **mousepad** (a text editor that looks just like notepad on windows). There are many more, of course.

I'd suggest to familiarize yourself with gedit (for everyday editing of files) and nano (in case you get stuck in the terminal).

---

### Post by 56phil on 2006-12-02
I don't know anything about the edit command. I just did a ```
man edit
``` and I still don't know enough to use it. gedit is the standard GUI text editor. You may want to learn a non-GUI editor, like nano or VIM so you can fix things when your Xserver is broken. I didn't and had to do a clean install to get things running again.

Additionally, it's a good idea make backups of configuration files before you edit them.```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` So you can just do a copy instead of an edit.

---

### Post by dkenny on 2006-12-02
Thanks all, I guess it must have been a typo

Quick forum Q - do I need to mark my thread as resolved?

---

### Post by CatKiller on 2006-12-03
> **dkenny said:**
> Quick forum Q - do I need to mark my thread as resolved?

It's certainly polite to do so, so that when people are searching for similar problems they know which threads are likely to contain solutions.

---

### Post by Indras on 2007-01-12
I just did a quick check on the 'edit' command... it's designed to automatically open a compatible editor for a given file, based on its extension.  So, for instance, at the command line if you type:
```

edit ~/somefile.doc

```
Openoffice will automatically start and open somefile.doc.  (assuming a default install)

In this particular case, you tried to use edit on a file with an unrecognized extension, so it returned an error telling you it didn't know what editor to use.

---

