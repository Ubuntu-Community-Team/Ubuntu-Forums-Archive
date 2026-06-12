---
title: "[SOLVED] Encryption"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-01-13
How can I encrypt a file with a single right click and assign it a password

---

### Post by szymon_g on 2008-01-13
did you installed gnu privacy guard (gpg)? if yes, there should be an option under leftclick on file in nautilus

---

### Post by anderskitson on 2008-01-13
No i haven't, but im grabbing it from add/remove right now, thanks , just wasn't sure where to find it.

---

### Post by szymon_g on 2008-01-13
like always - in repository(-ies) ;p

---

### Post by Dr Small on 2008-01-13
Yup, that will do it.
Or, from the command line:
```
gpg -c filename
```

Dr Small

---

### Post by anderskitson on 2008-01-13
Im a little lost i just encrypted a file, it asked me for a key phrase, i chose one but the file doesn't seem to be encrypted when i go to open it it doesn't ask me for any keyphrase

---

### Post by Dr Small on 2008-01-13
It won't exactly, encrypt it. It will create a new file called *filename.ext.**gpg***. You would have to remove the original file in order that no one can view it without a passphrase.

Dr Small

---

### Post by kevdog on 2008-01-13
For gpg (if you want to use this program, others would work also) it would be

gpg --encrypt --symmetric <filename>

Its encrypted by default with the CAST5 algorithm (which I would rate just as OK).  If you want to choose your cipher algorithm (like AES256), it would be

gpg --encrypt --symmetric --cipher-algo AES256 <filename>

The --personal-cipher-preferences could be set within the gpg.conf file to avoid you having to use the --cipher-algo all the time where you could specifiy the priority of cipher algorithms.

gpg -v --version  <-- This command will give you the possible ciphers that are available with your gpg binary.  You can add more than the default set, if you choose to compile gpg from source

Sorry to be so long winded.

---

### Post by anderskitson on 2008-01-14
Um i get > You did not specify a user ID. (you may use "-r")

Current recipients:

Enter the user ID.  End with an empty line: 
No such user ID.


I try entering -r , didn't work

---

### Post by kevdog on 2008-01-14
Sorry, if you dont want to use public/private keysets and simply password protect the file, the format would be:

gpg --symmetric <filename>

or 

gpg --symmetric --cipher-algo <cipher> <filename>

This will produce a file with the .gpg extension

To decrypt the file

gpg <filename>.gpg

Hopefully that will help.
Dr. Small's instruction's above were correct.  gpg -c is equivalent to gpg --symmetric

---

### Post by anderskitson on 2008-01-14
Perfect Exactly what I wanted, thanks Everyone

Everything Worked great but it did give me this warning, not sure what it means

> gpg: WARNING: message was not integrity protected

---

### Post by kevdog on 2008-01-14
I dont get that error -- perhaps you could try the gpg mailing lists:

[http://www.gnupg.org/documentation/mailing-lists.en.html](http://www.gnupg.org/documentation/mailing-lists.en.html)

---

### Post by anderskitson on 2008-01-14
All right will do, thanks a lot for your help again. This is what makes Ubuntu so great a community that is just happy to help.

---

