---
title: "cx5000 epson scanner worked in feisty but not gutsy"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2007-11-08
Had this working fine in Feisty, but following the same process in Gutsy there is no joy. Anybody have an idea how to get your scanner working. This is really a deal breaker for Ubuntu and the ONLY reason I have to boot back into XP. Development teams need to be really aware of this and I am hoping that they indeed are aware and working on this for future upgrades.
Thanks for the help

---

### Post by taysider on 2007-11-10
> **Tucatts said:**
> Had this working fine in Feisty, but following the same process in Gutsy there is no joy. Anybody have an idea how to get your scanner working. This is really a deal breaker for Ubuntu and the ONLY reason I have to boot back into XP. Development teams need to be really aware of this and I am hoping that they indeed are aware and working on this for future upgrades.
Thanks for the help

Hi Tucatts,
Try the following link [http://ubuntuforums.org/showthread.php?t=599673&highlight=epson+dx6000](http://ubuntuforums.org/showthread.php?t=599673&highlight=epson+dx6000)
I have a DX 6000 and it works fine

---

### Post by cotcot on 2007-11-10
I had my epson printer and scanner in gutsy working as described in [[COLOR="Red"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=576594&highlight=recent+epson"). I think you have to check /etc/sane.d/dll/conf for the epkowa driver instead of the epson (delete 'epson' and add 'epkowa').

---

