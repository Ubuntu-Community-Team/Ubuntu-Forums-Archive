---
title: "KDAR, unable to work with enrypted archives"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by mike.thorton on 2007-01-22
Hello, I've found KDAR, which is frontend to DAR.

I've just created few encrypted archives, but now I'm unable to work with them.

If I choose File/Open archive and select encrypted archive, the error appears. It tells me that it is an encrypted archive and I didn't put a password. But I didn't have any opportunity to give it!

If I don't encrypt them, everything works fine.

Can anyone help me,* how to work with encrypted archives* in Kdar?

Thank you very much for your answers =D>

---

### Post by mike.thorton on 2007-02-06
any ideas?

---

### Post by kwilliam on 2007-04-19
I've never tried using encrypted archives in Kdar, but I'm sure there isn't a way you could *not* have provided a password.  Have you tried all the logical default passwords?  An empty "" password, your user password, maybe your kwallet password?  Why does Kdar insist on using Kwallet anyway? Maybe the password is in there somewhere?
Or, you could try making another (small) encrypted archive, and probing around in the settings until you find a password box.

I'm surprised nobody's answered you before now.  I like dar because it seems so much better than tar, but it seems like nobody uses it.  It's always tar, tar, tar.  :-(

---

### Post by kwilliam on 2007-05-28
I finally got Kdar installed and have tried it.  I have a similar problem: I can provide a password to create an encrypted archive, but when I try to open the archive it fails with the message:
> The archive test-archive-encrypted is encrypted and no encryption cypher has been given, cannot open archive.
Error: unable to open the archive.
Kdar stores the encryption password (and there is just one universal password) in the KDE wallet, and stores it successfully, but Kdar doesn't appear to be using it when opening encrypted archives!  The encrypted archives are valid however; you can use plain old dar to extract it.

```
$ cd empty-folder-to-extract-archive-to
$ dar -K ':' -x /path/to/encrypted-archive
Archive encrypted-archive requires a password:
```
Enter the password and it should extract the archive. The full documentation for "dar" can be found [here](http://dar.linux.free.fr/doc/man/dar.html).

---

