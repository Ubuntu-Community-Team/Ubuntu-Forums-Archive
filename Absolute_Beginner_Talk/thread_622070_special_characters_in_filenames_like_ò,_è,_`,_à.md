---
title: "special characters in filenames like ò, è, `, à"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by dstomov on 2007-11-24
hi,
i have to backup some files.
backup-manager is my choise, but filenames are with special characters.
when i use nautils in gnome i can see filenames with proper chars, but when i ls in command promt the result looks like:
piace???.pdf and all special chars are repalced with ?
i think that this is the reason why backup-manager skip them.
can you tell me what program do i need to install for reading filenames with strange chars in terminal

---

### Post by dstomov on 2007-11-24
pls help

---

### Post by JThundley on 2008-05-27
I have a similar problem with international characters. They show up weird in the terminal, here are some examples:

Stormbl?st autocompletes to Stormblï¿½st/
it should be Stormblåst (with a circle above the a)

Every file with international characters is screwed up like this, and it causes sendxmpp to barf when working with these files. (sendxmpp sends jabber messages). It also screwd up files shared over nfs.

Any help is greatly appreciated.

---

### Post by gib2800 on 2008-06-30
I am having a similar problem in Kubuntu 8.04.  I installed Kubuntu on a laptop that had been running XP, but XP doesn't work anymore so I am trying to backup files from XP to an external hard drive through Kubuntu using Dolphin.  Many of my files (especially music) have special or international characters in the filenames or folders. These characters cause an error and will not copy/backup unless I rename them without the characters. Very annoying. The error says:
"Could not write to /location/file.ext" 
Does anyone know of a solution?

---

