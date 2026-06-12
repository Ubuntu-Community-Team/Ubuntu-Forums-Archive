---
title: "GnuPG with evolution or Thunderbird/enigmail"
date: 2005-08-17
forum: Apple PPC Users
---

### Post by Blase on 2005-08-17
I all !

I'm trying to use GnuPG with either evolution and
enigmail in thunderbird, but no one of both are working . . .

GnuPG seem to work fine in terminal, as I generate a key,
-- list-key show me the key correctly.

evolution error message:

Impossible to create the message,
cause "gpg: skipped '0x330BB...' : secret key not available.
gpg: signing failed: secret key not available


Wich is the path of the GnuPG executable to put on enigmail preferences ?
Cause each one I try are wrong . . .

What I'm doing wrong ?

Thanks in advance !

---

### Post by h4rdc0d3 on 2005-08-17
[QUOTE=Blase]Wich is the path of the GnuPG executable to put on enigmail preferences ?[/QUOTE]

Mine is "/usr/bin/gpg".

---

### Post by Blase on 2005-08-17
^^^
Thanks ! 
Looks a bit better now, but I have the folowing error when sending an email:

Send operation aborted

Error -encryption command failed

gpg command line and output:
/usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --clearsign --digest-algo sha1
-u <info@.......> --passphrase-fd 0 --no-use-agent

gpg: skipped <info@.......> : secret key not available
gpg: [stdin]: clearsign failed: secret key not available


Tia !

---

### Post by h4rdc0d3 on 2005-08-17
It looks like you don't have a secret key. Check if I'm right with 'gpg --list-secret-keys'. If so, you need to generate one using 'gpg --gen-key' or import a pre-existing one with 'gpg --import'.

Btw, try reading the output of 'gpg -h' and 'man gpg', while you're at it.

---

### Post by Blase on 2005-08-17
Unfortunately,
I reinstall all the packages, delete the old key
re- generate a new one, wich is listed with --list-keys
and --list-secret-keys.

But I got the same error when trying to send a signed message.

Any thought ??

Thanks Anyway !   ;-)

---

