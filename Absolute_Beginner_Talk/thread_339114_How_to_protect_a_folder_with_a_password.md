---
title: "How to protect a folder with a password?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2007-01-15
What can I do to protect some of my folders from access with passwords? So that even if somebody can get inside my system, there is an additional protection for some files with sensitive information?
For example in Windows I used a zipping program to create archives that required passwords, but archiving tools in Ubuntu don't seem to give that option.

---

### Post by bodhi.zazen on 2007-01-15
Are you wanting encryption ?

[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=encryption&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=encryption&titlesearch=Titles)
	[http://johnleach.co.uk/words/archives/2006/12/06/245/](http://johnleach.co.uk/words/archives/2006/12/06/245/)
	[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)
	[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)
	[http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO)

---

### Post by 1002285 on 2007-01-15
> **bodhi.zazen said:**
> Are you wanting encryption ?

[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=encryption&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=encryption&titlesearch=Titles)
	[http://johnleach.co.uk/words/archives/2006/12/06/245/](http://johnleach.co.uk/words/archives/2006/12/06/245/)
	[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)
	[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)
	[http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO)

Im not sure. These howtos seem to be for encrypting whole partitions - did I understand it correctly?
It's not a good option for me at the moment, as I don't have space for backing up whole partitions. But do you think making encrypted partitions would be the best way to secure my things? Are there any negative sides? For example, could I be certain that after a system crash I would be able to access the files using another system or a live CD or sth?

At the moment, though, I was just looking for a way to set an additional password for just some of the most sensitive folders (I really don't know so much about computer security, so I am not even sure whether this would actually improve the security of these folders in case of a malicious attack).

---

### Post by Arisna on 2007-01-15
You can use gpg (GNU Privacy Guard, a free PGP replacement) to encrypt archives so that they require a passphrase to open.

---

### Post by Richard Kut on 2007-01-15
Hello. I tried this out this past weekend, and it works very well. Have a look at [http://www.ubuntuforums.org/showthread.php?t=148600](http://www.ubuntuforums.org/showthread.php?t=148600) I hope that it works for you too!

---

### Post by mlissner on 2007-01-15
The simplest thing I can think of to do would be to change the owner of the directories to root so that only root can open them. This'll mean that you can't just click them to open them anymore (you'll have to do sudo nautilus folderlocation to get into it yourself, which will prompt for the root password). 

If you want to do this, run chown root folderlocation, and then modify the permissions until you're comfy with it by using the chmod command. If you want more info on the chmod command, do man chmod, it's a bit of a tricky one.

---

