---
title: "[SOLVED] Cut/Paste acting weird"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-29
Alright, I'm using Kubuntu with Gnome installed.

(I liked KDE until I started using it).

I was having this problem, where sometimes I'd cut something, and go to paste it, and nothing would be on the clipboard.  I asked around, and every linux friend thought I was nuts, and that it's possibly a problem with my keyboard, like the control key not functioning right or something.

After messing around with it and getting pissed about this problem I finally figured out that it's always copying, but it needs the copy source in order to paste.

For example, if I cut something (a URL) out of firefox, and then close firefox, I can't paste it into KEdit.  Though if I cut that URL out, minimize firefox, it pastes fine into notepad.

This works for EVERYTHING.  Regardless of what it is, nautilus, firefox, notepad, whatever, if I go to copy/cut something, the source I cut or copied it from needs to still be opened for me to be able to paste.

Does anybody have any idea what in the hell is wrong?  How do I get it to stay in the copy buffer when I close the window I copied it out of??

---

### Post by taurus on 2008-02-29
How did you do your cut 'n paste.  If you want to copy something, highlight it with the left button and paste it to wherever you want with the middle button.  Even if you close the app that you highlight, you can still paste the stuff that you copy into another app or window.

---

### Post by Oldsoldier2003 on 2008-02-29
> **Syndacate said:**
> Alright, I'm using Kubuntu with Gnome installed.

(I liked KDE until I started using it).

I was having this problem, where sometimes I'd cut something, and go to paste it, and nothing would be on the clipboard.  I asked around, and every linux friend thought I was nuts, and that it's possibly a problem with my keyboard, like the control key not functioning right or something.

After messing around with it and getting pissed about this problem I finally figured out that it's always copying, but it needs the copy source in order to paste.

For example, if I cut something (a URL) out of firefox, and then close firefox, I can't paste it into KEdit.  Though if I cut that URL out, minimize firefox, it pastes fine into notepad.

This works for EVERYTHING.  Regardless of what it is, nautilus, firefox, notepad, whatever, if I go to copy/cut something, the source I cut or copied it from needs to still be opened for me to be able to paste.

Does anybody have any idea what in the hell is wrong?  How do I get it to stay in the copy buffer when I close the window I copied it out of??

There is nothing wrong. the linux clipboard needs the source app to be open or it dumps your clipboard. With that said, actually it is wrong *grins* but thats the way it works until they rewrite the way the clipboard works.

** If you install glipper or another clipboard manager you can work around this behavior glipper for gnome, klipper for KDE** There are others out there as well if you look around and research the features you want.

```
sudo apt-get install glipper
```

be sure to save your session after you install glipper if you want it started every time you log in.

---

### Post by Oldsoldier2003 on 2008-02-29
> **taurus said:**
> How did you do your cut 'n paste.  If you want to copy something, highlight it with the left button and paste it to wherever you want with the middle button.  **Even if you close the app that you highlight, you can still paste the stuff that you copy into another app or window**.
Do you have a clipboard manager installed?

 On a stock gnome desktop i just tried to copy and paste using the left/middle buttons and closing the source and it failed. 

I know how to use the middle mouse button and use it extensively, because i often multi task with several terminals and browser tabs... and without glipper I can't middle mouse paste ("use the primary" ) unless my sources are open (they almost always are).

---

### Post by forrestcupp on 2008-02-29
This is one problem they should have fixed a long time ago.  The clipboard managers are great, but we shouldn't have to resort to them.

---

### Post by Oldsoldier2003 on 2008-02-29
> **forrestcupp said:**
> This is one problem they should have fixed a long time ago.  The clipboard managers are great, but we shouldn't have to resort to them.


I agree completely, and its a issue that really hurts Ubuntu's usability appeal to folks considering changing from windows. Sure its a little thing but they add up.

---

### Post by Syndacate on 2008-03-01
> **taurus said:**
> How did you do your cut 'n paste.  If you want to copy something, highlight it with the left button and paste it to wherever you want with the middle button.  Even if you close the app that you highlight, you can still paste the stuff that you copy into another app or window.

Yes, thank you, I realize how it's supposed to work, I'm just telling you what it's doing.

That's what it does in WIndows, and mac, apparently linux is an exception.

Nothing like trying to make me feel dumber than I already am :|.

[quote=Oldsoldier2003]There is nothing wrong. the linux clipboard needs the source app to be open or it dumps your clipboard. With that said, actually it is wrong *grins* but thats the way it works until they rewrite the way the clipboard works.

**If you install glipper or another clipboard manager you can work around this behavior glipper for gnome, klipper for KDE** There are others out there as well if you look around and research the features you want.[/quote]

Thanks, I remember Klipper from when I still had KDE installed.  I never looked into its function or anything.

Alright, I installed it and it works, I added it to the session startup too.

Thank you very much.

---

### Post by Endolith on 2008-05-04
I know this has been a problem in Pidgin for a while, even in Windows, but it's really a problem in all apps?  I've been having weird copy and paste problems since upgrading to Heron, but I don't think they're related to this.

---

