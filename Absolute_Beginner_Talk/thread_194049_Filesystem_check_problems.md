---
title: "Filesystem check problems"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-06-10
Hello there! I know this might not be an ubuntu issue, but couldn't find a better place to ask for help.
Since I've installed 6.06 (I've formated the old 5.1 partition and started fresh) I'm getting this messages during boot:

"There are differences between sector and its backup (lot of hex numbers here 71:4d/00)"
"not automatically fixing this"

Happens every boot and takes forever... what should I do to fix this?

Regards

---

### Post by Dr. Nick on 2006-06-10
that could be alot of things, Does the system feel responsive while in the gui after all that is over? Did you have trouble installing it or have files dissappear?

I would guess either a failing hard drive, or just not set up right in the bios.

Thats just a guess though,. maybe post specifics on drive type and system and someone who has expierenced it may help

---

### Post by viniciuscarvalho on 2006-06-11
Well the system is ok after booting. It complains about the boot sector. I've found a solution somewhere here in the forums instrucing to change the fstab from:
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

to:

/dev/hda1       /media/windows  ntfs     iocharset=utf8,umask=000 0       0

but that did not help either. Any ideas?

Regards

---

### Post by Dr. Nick on 2006-06-11
Dont have many ideas, Never have seen this before so am not real sure what causes it.

If the system acts fine and doesnt crah I would say your hard drive is probably good, not sure if a bios setting would cause this sort of problem or not

---

### Post by ihavenoname on 2006-06-15
[QUOTE=Dr. Nick]Dont have many ideas, Never have seen this before so am not real sure what causes it.

If the system acts fine and doesnt crah I would say your hard drive is probably good, not sure if a bios setting would cause this sort of problem or not[/QUOTE]
I have the same exact problem....weird thing is It only gives me the error with Ubuntu, my SUSE partition does not do this. It seem that Ubuntu's filesystem check is more picky then most. Hmm...

---

### Post by viniciuscarvalho on 2006-06-15
So anyone has a clue on how to fix this? Maybe disable filesystem check for my dev/hda1 partition...

---

### Post by ihavenoname on 2006-06-15
hmm...how is that done exactly?

---

### Post by Dr. Nick on 2006-06-15
is this similar? may be worth a try

[http://ubuntuforums.org/showthread.php?t=176025&highlight=disable+fsck](http://ubuntuforums.org/showthread.php?t=176025&highlight=disable+fsck)

---

