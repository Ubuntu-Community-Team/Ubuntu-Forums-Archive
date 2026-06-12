---
title: "[SOLVED] Envy low resolution"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by perezmaximus on 2008-04-02
Installed envy in my laptop and now it is running at low resolution.Does anybody know why?I tried to update drivers and now it is all messed up.I have an IBM thinkpad a22m P3 1Ghz 256 ram.It was running fine before.:confused:

---

### Post by overdrank on 2008-04-02
> **perezmaximus said:**
> Installed envy in my laptop and now it is running at low resolution.Does anybody know why?I tried to update drivers and now it is all messed up.I have an IBM thinkpad a22m P3 1Ghz 256 ram.It was running fine before.:confused:

Hi and what is the model of the graphics card? and have you tried to reconfigure your xorg with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and also did you uninstall the previous driver before using Envy?

---

### Post by perezmaximus on 2008-04-02
It has an ATI 128 mobility card.No I did not remove previous drivers.I really don't know how to use envy.

---

### Post by overdrank on 2008-04-02
> **perezmaximus said:**
> It has an ATI 128 mobility card.No I did not remove previous drivers.I really don't know how to use envy.

Ok what version of Ubuntu are you using, Feisty, Gusty? The driver that come with both should be the best you can get for that graphics card. But you may try and reconfigure you card with the previous command.

---

### Post by perezmaximus on 2008-04-02
> **overdrank said:**
> Ok what version of Ubuntu are you using, Feisty, Gusty? The driver that come with both should be the best you can get for that graphics card. But you may try and reconfigure you card with the previous command.

It's 7.10. So all I have to do is enter the command?
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by overdrank on 2008-04-02
> **perezmaximus said:**
> It's 7.10. So all I have to do is enter the command?
sudo dpkg-reconfigure -phigh xserver-xorg

Yes and that should reconfigure you xorg and hopefully have the GUI you desire.

---

### Post by perezmaximus on 2008-04-02
Tonight after work I'll try it and post results,Thank you.

---

### Post by overdrank on 2008-04-02
> **perezmaximus said:**
> Tonight after work I'll try it and post results,Thank you.

You are welcome and please post back with the results. Good luck! :KS

---

### Post by perezmaximus on 2008-04-02
Thank you again overdrank=D>, worked like a charm.\\:D/

---

