---
title: "How do I back up Feisty before switching to Gutsy?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by persofi on 2008-01-11
Hey folks,
I finally want to make the move from Ubuntu Feisty to Ubuntu Gutsy. As far as I know, a fresh install is highly recommended. Now I have some questions about backing up my old system.

1) I have a dual boot system with Ubuntu/Windows XP. Is it ok to copy files to the Windows XP partition to back them up? Or is it possible that the installation of Ubuntu Gutsy may also wreck the data stored on the Windows partition?

2) I would like to have Ubuntu Gutsy configured exactly like my Ubuntu Feisty version. Which configuration files do I have to save and where can I find them? Im especially worried about Wine and some difficult hardware drivers.

3) Does this [http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207) 
work if I switch from Feisty to Gutsy? Is it recommended for backups?

I appreciate any help very much, thx!
- persofi

---

### Post by mikeyphi on 2008-01-11
Since you want to keep your configuration (as much as the new OS will let you!) you should try an upgrade and not a fresh install.
However, first make a copy of all your data - it's OK to keep it as a file on your windows system.

Your personal settings are kept in hidden files in your Home/user folder - a fresh install (whilst always a good idea) will wipe these!

---

### Post by wieman01 on 2008-01-11
Follow suggestion in post #2 and do your backup using Partimage. See signature for more.

---

### Post by seventhc on 2008-01-11
I would make the backup on an external source just in case you have any problems possibly resulting in a loss of your xp partition. It isn't  likely that you will lose anything, but it is a possibility.

---

### Post by Mze on 2008-01-11
I've tried the backup tool from the thread "Back-Up Solution" to restore previous systems to their original state. 

I usually backup my HOME directory only, however you also have the option of backing up your configuration files. Run a fresh install of Gutsy and you should be good to go.

---

### Post by Jake90 on 2008-01-13
If you have an HP 6600 or 9000 don't do it. I don't know about upgrading but I tried installing gutsy and the wireless card and graphics aren't compatible and I couldn't find a way to make it compatible. Right now I am trying to install feisty.

---

