---
title: "How to decrypt encrypted files the GUI way?"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by papangul on 2006-05-26
Ok, I have installed  seahorse and now can encrypt files from the context menu.
But how do I decrypt the file in similar way? I have to use commandline:
$gpg --output file.ext --decrypt file.ext.pgp

---

### Post by nanotube on 2006-05-26
maybe make a nautilus script? here are some examples:
[http://doc.gwos.org/index.php/Nautilus_Scripts](http://doc.gwos.org/index.php/Nautilus_Scripts)

---

### Post by papangul on 2006-05-26
There is a bug filed in bugzilla already about this, hopefully, it will be acted upon before dapper release.
[https://launchpad.net/distros/ubuntu/+source/seahorse/+bug/42869](https://launchpad.net/distros/ubuntu/+source/seahorse/+bug/42869)

---

### Post by samir85 on 2006-05-26
I'm running Ubuntu Dapper here and also using a Seahorse.
When I right click on an encrypted file in nautilus I can choose "Open with: decrypt file". By doing that seahorse will try to decrypt the file ...

---

### Post by papangul on 2006-05-27
This is strange, I am also using Dapper also but I'm not getting the 'decrypt' option in the context menu ! :confused:
Is the encrypted file you are talking about a '.pgp' file? The bug report says that '.gpg' file gets decrypted just fine...

---

### Post by samir85 on 2006-05-27
[QUOTE=papangul]This is strange, I am also using Dapper also but I'm not getting the 'decrypt' option in the context menu ! :confused:
Is the encrypted file you are talking about a '.pgp' file? The bug report says that '.gpg' file gets decrypted just fine...[/QUOTE]

Ok, sorry. Next time I will read the bug report properly before posting. ;)
PGP files can't be decrypted from nautlius at me, too.

---

