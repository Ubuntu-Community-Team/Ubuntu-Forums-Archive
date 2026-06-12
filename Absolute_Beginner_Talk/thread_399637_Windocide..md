---
title: "Windocide."
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Irmis on 2007-04-02
I decided to give a little more space to Linux and decided to take some from Windows. So as always I stated XP and opened partition magic. Which had never failed me, until a little while ago. While resizes the partitions it made an error. After the error Linux runs just fine but Windows is no longer mounted. (Although Linux did make me scan its partitions for errors) but when I try to start windows I get flashed a blue screen and its way to fast to read then the computer restarts and Grub takes over. 

I'm guessing I need to partition magic to fix it's partitioning mistake, but that is on the Windows partition which is beyond my reach at the moment. I have Qparted here but it won't work as I do not know how to do the "root" thing outside of a terminal. The computer itself wants to return to its factory settings, which I really don't want to do. Sooo any ideas?

---

### Post by Ephilei on 2007-04-02
To run any GUI as root, either sudo the GUI's terminal command or login as root (not recommended). To find a GUI's command (if it's on the main Gnome menu bar) right click to edit the menu, find the link, and click the Properties button. To login as root you'll have to enable it in the System Preferences because it's off by default. I don't remember where, but it's easy enough to find.

---

