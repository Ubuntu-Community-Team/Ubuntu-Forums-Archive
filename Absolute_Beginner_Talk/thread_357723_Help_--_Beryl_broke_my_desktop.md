---
title: "Help -- Beryl broke my desktop"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-02-10
Hi,
 So here I was fiddling with beryl, making water effects possible without making the windows black, when suddenly on changing some settings the desktop froze. Ditto on reboot. Even failsafe gnome runs beryl manager. Now I want to correct the start up programme from running the beryl manager, and I will have to do it from terminal, the question is how? Please help.

---

### Post by shareMenaPeace on 2007-02-10
Check my beryl link from the signature ,,,

---

### Post by tonyr1988 on 2007-02-10
> /home/[username]/.config/autostart/beryl-manager.desktop

Should be the autostart file. You can delete it (or move it into another folder) and it shouldn't load by default.

When you fix it, you may also want to add Beryl as a separate session to help in the future:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Configuring_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Configuring_Beryl)

---

### Post by mahiyar on 2007-02-10
ShareMenaPeace-- Thanks for the link, I will certainly do that, but currently my main problem is how to stop loading beryl on start up.

---

### Post by mahiyar on 2007-02-10
Thanks, Ubuntu and Beryl is now up and running as before.

---

