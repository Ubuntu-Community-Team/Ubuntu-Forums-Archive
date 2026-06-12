---
title: "Dual monitor issue (or how to restart X)"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by nir78 on 2006-04-13
Hi,

I try to enable the dual monitor option in my ATI drivers.
Right after I click the enable I receive this message:
[IMG]http://uploaded.fresh.co.il/2006/04/13/99769853.jpg[/IMG]
Than I restart the computer and nothing happens ](*,) 
Am I doing something wrong ???

Nir

---

### Post by dragonfyre13 on 2006-04-13
No, restarting the computer restarts the Xserver. I would think that it isn't taking the settings.

Also, you can press Ctrl+Alt+Backspace to restart the Xserver, and log you out. That avoids the shutdown and startup process.

---

### Post by nir78 on 2006-04-13
[QUOTE=dragonfyre13]No, restarting the computer restarts the Xserver. I would think that it isn't taking the settings.

Also, you can press Ctrl+Alt+Backspace to restart the Xserver, and log you out. That avoids the shutdown and startup process.[/QUOTE]

Ctrl+Alt+Backspace throw me into a text screen... how do I run the graphical gui again ?

---

### Post by Roger Mudd on 2006-04-13
[QUOTE=nir78]Ctrl+Alt+Backspace throw me into a text screen... how do I run the graphical gui again ?[/QUOTE]

I believe "startx" is the command you want to use.

---

### Post by Phryxus on 2006-04-14
I'm having exactly the same problems as discribed on my laptop with ATI Radeon X700. I haven't found a solution yet.:(

---

### Post by Phryxus on 2006-04-14
Found the solution [here]("http://www.ubuntuforums.org/showthread.php?t=159996&highlight=Dual+Monitor")! :D Do what nir78 did and it will work fine.

The only problem left is that I can't change the resolution of both monitors seperate.

---

### Post by mrchrisblau on 2006-04-14
[QUOTE=Phryxus]Found the solution [here]("http://www.ubuntuforums.org/showthread.php?t=159996&highlight=Dual+Monitor")! :D Do what nir78 did and it will work fine.

The only problem left is that I can't change the resolution of both monitors seperate.[/QUOTE]

Will doing what nir78 did but on an nVidia card work too? Of course one would need to change some of the xorg.conf settings to make it work with nVidia, but which ones?

---

