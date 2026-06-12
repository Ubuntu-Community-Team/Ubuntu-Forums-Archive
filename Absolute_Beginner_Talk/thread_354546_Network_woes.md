---
title: "Network woes"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-02-06
Hi

I am currently trying to use Nautilus to connect to my Windows gateway nachine to access the shared files stored there. When I try and go to "Network" in Nautlus it shows me an icon for windows network but when I click it an error comes up saying that "smb:/// is not  a valid location".

I have tried installing smbclient and smbfs as I would normally but it say that I already have the latest version when I try. 

I have install Konqueror as well (but i dont really like using it so this is a short term solution) and this IS able to access the share on the other PC so anyone got any clues as to what has gone wrong?

cheers in advance
niteblind

---

### Post by niteblind on 2007-02-06
Hi All,

In case any of the people that viewed my post are looking for the answer this problem was caused by missing libraries. If you are having the same problem then you need to:

```

sudo apt-get install libgnomevfs-extra

```

It appears this library allows nautilus to interact with the smbclient.

hope this helps someone in future.
niteblind

---

