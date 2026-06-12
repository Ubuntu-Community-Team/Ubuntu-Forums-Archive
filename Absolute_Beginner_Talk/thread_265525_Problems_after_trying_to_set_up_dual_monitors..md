---
title: "Problems after trying to set up dual monitors."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-26
So I tried to set up dual monitors using a tutorial on here and now when I turn on my computer I just get a blue dos-type screen that basically says "Good going, stupid, you broke me."

I'm pretty sure what I need to do is get the xorg.conf backup that I made and replace the current xorg.conf file with it, but I don't know how. How would I do this?

---

### Post by wieman01 on 2006-09-26
1. Boot until the system does not get further.
2. Press alt + F1.
3. Log on to the system using your username & password.
4. Do: > sudo cp [COLOR="Red"]/etc/X11/xorg.conf_YOUR_BACKUP_FILE[/COLOR] /etc/X11/xorg.conf
5. Restart the computer: > sudo reboot
That's it. Replace "/etc/X11/xorg.conf_YOUR_BACKUP_FILE" with the name & path of your safety copy.

---

### Post by wieman01 on 2006-09-26
And for dual monitor you may want to try this. It just WORKS. :-)

[http://www.ubuntuforums.org/showthread.php?t=221908]("http://www.ubuntuforums.org/showthread.php?t=221908")

---

