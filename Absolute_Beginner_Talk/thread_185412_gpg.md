---
title: "gpg"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by rcarring on 2006-05-31
I am trying to sign the coc on the Ubuntu site but when I follow the code

[FONT="Courier New"] gpg --clearsign ~/UbuntuCodeofConduct-1.0.txt[/FONT]

(I adjusted the filename to reflect actual filename I downloaded)

I get an error about a missing secret key.

If I am signing a clear text signature why would I need a secret key, and if I need one, how do I generate one?

Thanks

---

### Post by nanotube on 2006-05-31
[QUOTE=rcarring]I am trying to sign the coc on the Ubuntu site but when I follow the code

[FONT="Courier New"] gpg --clearsign ~/UbuntuCodeofConduct-1.0.txt[/FONT]

(I adjusted the filename to reflect actual filename I downloaded)

I get an error about a missing secret key.

If I am signing a clear text signature why would I need a secret key, and if I need one, how do I generate one?

Thanks[/QUOTE]
"man gpg" for details :)
to generate a key, use command
```
gpg --gen-key
```

---

### Post by az on 2006-05-31
You will also need to tell launchpad about your public key.  See here:

[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)

---

