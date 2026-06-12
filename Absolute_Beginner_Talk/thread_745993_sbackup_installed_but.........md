---
title: "sbackup installed but........"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by sarum on 2008-04-05
Hello, I've installed sbackup, and :-

cjf@cjf-desktop:/var$ sudo find backup
Password:
backup
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful/ver
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful/excludes
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful/packages
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful/fprops
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful/files.tgz
backup/2008-04-05_17.19.20.792680.cjf-desktop.ful/flist
cjf@cjf-desktop:/var$
I chose the first (simple) option on 'sbackup config'. Being a cautious newby, I've stuck with Dapper Drake and am now looking forward to 8.04 (which will see me through till I'm nearly 80). What I want to know, in very simple language, is how to save backups to a cd or dvd.
I'd then like to clear (?fdisk?) my HD and repartition it - install 8.04 - and, then reinstall my home: bookmarks: address book: and things.
If any of you good people can help me on this, then I'll  try not to both you again till the Heron retires. Thanks for a good forum and the best OS.
sarum

---

### Post by mikeyphi on 2008-04-05
You can just burn the saved files as a data CD however, a couple of thoughts...... the backup is only good for the exact same setup and needs to be used through sbackup restore.
If you have more than one hard drive it's worthwhile backing up to a different drive in case of failures.
You (probably) WON'T be able to restore your Home personal data (as you list) by using these old backups.

I suggest you save a copy of all your personal data - burn to CD if needed - before you do a fresh install of Hardy.
The other option is to Upgrade to Hardy, that should preserve your data - but you should still do a backup of your data (not using sbackup) just in case!
There is a third option - if you have some space on your hard drive you could make a new partition, install Hardy and import your data (as part of the install process)

Ask again if further info required!

---

