---
title: "automatix gpg key error"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by idrinkwhisky on 2006-10-27
Hi i tried installing Automatix2, but when I do the
wget [http://getautomatix](http://getautomatix)....
gpg thing, it does not work. I have posted the error message below. Please help. Thank you

idrinkwhisky@whisky-laptop:~$ sudo gedit /etc/apt/sources.list
idrinkwhisky@whisky-laptop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--05:16:29--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.10'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

05:16:29 (78.56 MB/s) - `key.gpg.asc.10' saved [1730/1730]

idrinkwhisky@whisky-laptop:~$ gpg --import key.gpg.asc
gpg: can't open `/home/idrinkwhisky/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `key.gpg.asc': general error
gpg: import from `key.gpg.asc' failed: general error
gpg: Total number processed: 0
idrinkwhisky@whisky-laptop:~$ gpg --export --armor 521A9C7C |sudo apt-key add -
gpg: can't open `/home/idrinkwhisky/.gnupg/pubring.gpg'
gpg: WARNING: nothing exported
gpg: key export failed: file open error
gpg: no valid OpenPGP data found.

---

### Post by Archmage on 2006-10-27
I think you need to put a "sudo" in front of your gpg-commands. E.g.

sudo gpg --import key.gpg.asc

---

### Post by idrinkwhisky on 2006-10-27
thanks, for the help.

I tried it, I still got the same error message. But i just proceeded with downloading automatix2. For some reason it worked, so I'm happy!

again thnx for the help

---

