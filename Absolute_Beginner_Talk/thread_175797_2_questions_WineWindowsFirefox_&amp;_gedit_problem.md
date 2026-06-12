---
title: "2 questions Wine/WindowsFirefox &amp; gedit problem"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-13
1st.  I have windows firefox on my ubuntu using wine.  How do I start windows firefox using Wine?

2nd.  After installing the codecs for my shockwave player, I have to configure mozplugger to use the Windows version of Firefox for Shockwave files. i use the command

 sudo -b gedit /etc/mozpluggerrc

and i get the following error

(gedit:19398): Gtk-WARNING **: cannot open display:

and I am unable to edit the file because it wont open.

Any advice?

---

### Post by WolfJay_83 on 2006-05-13
Just a dumb question... you are running this from a terminal program in gnome or are you running this from a real (or virtual) terminal outside of an X session?  That's the error you get when running stuff without an x session running, so I thought I'd just check.

Have a good night!

edit:  Incase you didn't understand my previous jabber... If you're looking at an all text screen, you cant open gedit because it requires a graphical desktop (hence X).  Either try it from a terminal window, or use nano instead of gedit.  nano is a text based editor.

---

### Post by aysiu on 2006-05-13
Is this some kind of experiment...?

Can we assume you already know that Firefox can be run natively in Ubuntu?

As for this: > sudo -b gedit /etc/mozpluggerrc

and i get the following error

(gedit:1939: Gtk-WARNING **: cannot open display: For any graphical application (like Gedit, which is a graphical text editor), you should use *gksudo*: ```
sudo cp /etc/mozpluggerrc /etc/mozpluggerrc_backup
gksudo gedit /etc/mozpluggerrc
```

---

