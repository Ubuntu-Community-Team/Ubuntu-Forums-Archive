---
title: "Can't remove an empty from the all programs folder."
date: 2011-11-19
forum: Any Other OS
---

### Post by LinuxFan999 on 2011-11-19
I am having a problem with the start menu's all programs menu. Someone who uses my computer installed a program that he wasn't supposed to, called iLivid. I uninstalled the program, but the folder in the all-programs menu remains, but is empty. I cannot delete this folder, because when I right click the folder, it only gives me the option to expand (which does nothing, because I removed the program). Can anybody help me remove this folder? The folder in question is circled in red in the screenshot.

EDIT: Sorry for the fact that the title is missing the word "folder".

---

### Post by qyot27 on 2011-11-19
Not sure about Vista/Win7, but in XP those sorts of menu items are stored in the Documents and Settings area.  Deleting items from there will remove them from the menu, just in case a program's uninstaller doesn't clean up after itself properly and running CCleaner on it doesn't solve the problem either.

The relevant areas:
C:\Documents and Settings\username\Start Menu\Programs
C:\Documents and Settings\All Users\Start Menu\Programs

On Vista/Win7, the path is different - instead of C:\Documents and Settings, it's C:\Users.  I'm not sure if the structure after that is different or not, but it's still something to check.

---

### Post by pastalavista on 2011-11-19
That folder is probably created by the registry. Run (Windows key + R) 'regedit' and search for and remove all instances of 'iLivid'. Reboot and if the folder isn't gone, it should at least be deletable now.

---

### Post by LinuxFan999 on 2011-11-19
> **pastalavista said:**
> That folder is probably created by the registry. Run (Windows key + R) 'regedit' and search for and remove all instances of 'iLivid'. Reboot and if the folder isn't gone, it should at least be deletable now.
Just tried it and it worked. Thanks. I just finished removing the remaining traces of I livid.

---

