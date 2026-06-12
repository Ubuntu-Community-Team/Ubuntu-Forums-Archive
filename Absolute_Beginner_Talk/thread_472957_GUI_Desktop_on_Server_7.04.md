---
title: "GUI Desktop on Server 7.04"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by tamays on 2007-06-13
I installing Ubuntu Server 7.04, and with a little trouble I was able downloading and installing the Desktop. Once the installation was complete (little over an hour) I rebooted the server only to find my old friend, the command prompt. I asked myself, did I miss something? Is there a command or script I need to run? regrettably myself didn't have a clue. I turned to my books only to find that all the books I have, and all the web pages I have read assume I have the desktop up and running. So, a little hint would be nice, a complete answer would be great... Any help is welcome.

Thanks, Tom. ;)

---

### Post by ctsiow on 2007-06-13
if you want to run kde try this:
[COLOR="Blue"]sudo aptitude install kubuntu-desktop[/COLOR]

---

### Post by infol on 2007-06-13
try ```
sudo rc-update add gdm default
``` which will add gdm to your default runlevel and restart...

---

