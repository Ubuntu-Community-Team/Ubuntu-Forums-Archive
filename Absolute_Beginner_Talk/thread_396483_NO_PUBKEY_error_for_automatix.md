---
title: "NO_PUBKEY error for automatix"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-03-29
I get the following error everytime I reload synaptic :

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

I did have automatix installed once but removed it because it would not load...HELP
How do I get rid of this error.

---

### Post by wscheer on 2007-03-29
rggavubt,

I got a PUBKEY error while following this guide, but it did install.
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

There was a part where  I had to add a line to the repository list
```

gksudo gedit /etc/apt/sources.list

```

then add this
```

deb http://www.getautomatix.com/apt dapper main

```

maybe try removing that line.

---

### Post by rggavubt on 2007-03-29
I installed it using synaptic I think.  I do see that line....do I delete it and resave or comment it out...not sure what you are telling me to do??

---

### Post by eljalill on 2007-03-29
That error just tells you, that the origin of the packages couldn't be verified.
They will still install.

If you are reasonably sure, that these packages do not pose a safety risk, just don't do anything click on OK and install.

---

### Post by wscheer on 2007-03-29
rggavubt,
If you open up a terminal window, you can type 
```
gksudo gedit /etc/apt/sources.list
```
and see a list of your repositories.

like eljalill said, "That error just tells you, that the origin of the packages couldn't be verified."
but I was going to have you take a look at the repository list and see if 
```
deb http://www.getautomatix.com/apt dapper main
```
appeared there. 

If its there you might be able to comment it out
```
#deb http://www.getautomatix.com/apt dapper main
```
and stop the error. If not you can always uncomment that line back to the way it was.

I just installed automatrix lastnight so when i get home (around 6:00 eastern time) I can try and do an update and see if i get the error too.

---

### Post by zvacet on 2007-03-29
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -


Just insert pubkey


gpg --keyserver hkp://subkeys.pgp.net --recv-keys CC919A31E23C5FC3
 gpg --export --armor CC919A31E23C5FC3  | sudo apt-key add -

---

### Post by rggavubt on 2007-03-29
Thanks, That fixed it!:popcorn:

---

### Post by vboyznewbi on 2007-06-23
follow the step above but still got the same problem.

---

### Post by r4ik on 2007-06-23
> **vboyznewbi said:**
> follow the step above but still got the same problem.

Have a look at,

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Copy and paste,

Good luck !

---

