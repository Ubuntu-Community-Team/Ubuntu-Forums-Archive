---
title: "Small Key problem..."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-09
I seem to have a small problem... I have followed the entire guide on Ubuntuguide.org for getting XGL compiz working for Nvidia ([http://ubuntuguide.org/wiki/Ubuntu_Edgy#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Eye_Candy), first section) and gotten all the way to adding the source to the sources list successfully. 

Then I enter this command that they say to...

```

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9 ; gpg --export -a 0x483170E9 | sudo apt-key add -

```

and I get this after the server times out...

```

gpg: requesting key 483170E9 from hkp server wwwkeys.eu.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

```

I have visited the site manually at [http://gandalfn.club.fr/ubuntu/index.php](http://gandalfn.club.fr/ubuntu/index.php) and they have a PGP key right there on the public page, is the key script invalid? Can I then install the key another way? Someone told me to wait a while, and I've been patiently running the script every 15 or so minutes for a while this afternoon and no change...

anyone know whats wrong?

---

### Post by Kateikyoushi on 2007-03-09
Use another keyserver, replace KEy with your KEY

> gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -

---

### Post by starcraft.man on 2007-03-09
> **Kateikyoushi said:**
> Use another keyserver, replace KEy with your KEY

Thank you :), will have to keep those somewhere just in case.

---

