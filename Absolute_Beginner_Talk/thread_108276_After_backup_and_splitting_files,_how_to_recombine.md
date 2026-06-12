---
title: "After backup and splitting files, how to recombine and restore"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2005-12-25
Hi:

I recently backed up my entire Linux hard drive to a .tgz file. There was advice on the howto page that files should not be larger than 2 GB. So I split using the "split" command files into two 1 GB files and a 380MB file.

Now I have three files

Backupaa
Backupab
Backupac

and the original backup file

backup.tgz

I imagine I must recombine the three Backup* files before doing a restore, but the howto doesn't mention the best way to do this.

Any help is appreciated! Thanks and Happy Holidays.

--gmachine

---

### Post by dcraven on 2005-12-25
I would probably use a LiveCD of your choice, mount the harddrives in question (the one you wish to restore to, and the one that holds the data to be restored), and untar accordingly.

HTH,
~djc

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
Cat them through a pipe.

Example: 

Split file into 1M chunks:

split -b 1m Grokking-the-GIMP-v1.0.tar.gz Grokking-the-GIMP-v1.0.tar.gz.

Which gives us...

Grokking-the-GIMP-v1.0.tar.gz.aa 
Grokking-the-GIMP-v1.0.tar.gz.ab
Grokking-the-GIMP-v1.0.tar.gz.ac
Grokking-the-GIMP-v1.0.tar.gz.ad
Grokking-the-GIMP-v1.0.tar.gz.ae
Grokking-the-GIMP-v1.0.tar.gz.af
Grokking-the-GIMP-v1.0.tar.gz.ag
Grokking-the-GIMP-v1.0.tar.gz.ah
Grokking-the-GIMP-v1.0.tar.gz.ai

...and so forth.  

Join them back and restore the archive:

cat Grokking-the-GIMP-v1.0.tar.gz.* | tar xvz

Cool, huh?

---

### Post by GMachine_24 on 2005-12-26
Thanks for your help. I had read about the 'cat' function but wasn't sure it would work with the split files. Nice to know it does.

Thanks again.

gmachine

---

### Post by goombah88 on 2006-01-21
hey guys, when i use the cat function above all it does it start extracting my archive into the folder where the backup files are.  if it makes any difference my backup file is *.tar.bz2.  i tried changing the last part of the command to 
*.tar.bz2* | tar xvj
to reflect the change in compression.

any help you guys can offer would be really nice since i can't restore any files at the moment.

---

### Post by ysse on 2006-01-21
goombah88: tar will uncompress files to your current directory by default. Either you move to where you want them before you use tar, or you use the -C option, as in:

```
tar xvj -C /home/me/destination
```

---

