---
title: "GIMP - how to dock two default tools"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-06
Hi,
I have started using GIMP, but I hate to have  multiple windows open for only one program. So when GIMP opens it opens toolbar. Then CTRL+N opens new window. How to dock toolbar window inside "new window" window - just like Windows Paint has (on the left site is toobar, on the right site is drawing window?
Thanks,
Abcuser

---

### Post by mac.ryan on 2007-04-06
If you google this question, you will discover it is a very debated issue among Gimp users... the main outcome being "this is the GIMP interface philosophy, take it or leave it".

From the official manual (you can install it from synaptics):

>        In GIMP 2.0 and 2.2, you have a lot of flexibility about the arrangement       of dialog windows on your screen. Instead of placing each dialog in its       own window, you can group them together using docks. A "dock" is a       container window that can hold a collection of persistent dialogs, such       as the Tool Options dialog, Brushes dialog, Palette dialog, etc. **Docks       cannot, however, hold image windows: each image always has its own       separate window.** They also can't hold non-persistent dialogs, such as       the Preferences dialog or the New Image dialog.

---

### Post by thomashauk on 2007-04-06
There are ways arround it though, you can, using a command which escapes me and is probably long and complex, bundle all the Gimp windows into a window although they'll still float about.

Or you chould try a tiling window manager like wmii to give you that effect although that involve learing a radically different way of managing windows.

---

### Post by airtonix on 2007-04-18
the thing you are thinking of is xnest. but you can then no longer drag-n-drop from the desktop into it...it acts like your vnc'ing into your machine again but without the peformance impact.

install metacity, xnest and gimp packages : 
> sudo apt-get install xnest metacity gimphere is the command : 

>  Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp --display :1

this comes from this link : 
> [http://ubuntuforums.org/showthread.php?t=240543](http://ubuntuforums.org/showthread.php?t=240543)

or you could explore beryl "expose" feature...or the window grouping feature....

yeah check out the window group feature...after you group a selection of windows you can tab between them and the window iteslef flips around to show the next app or window....much like the 3d cube rotation if it only had two workspaces.

---

