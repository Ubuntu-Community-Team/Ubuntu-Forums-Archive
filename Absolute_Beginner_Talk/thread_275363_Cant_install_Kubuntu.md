---
title: "Cant install Kubuntu"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2006-10-11
I am running Ubuntu 6.06 and I tried to install Kubuntu using the Synaptic Package Manager but when I tried to install Kubuntu Desktop I get this error message.


    [LEFT][/LEFT]
    [LEFT]kubuntu-desktop:[/LEFT]
    [LEFT] Depends: language-selector-qt but it is not going to be installed

[/LEFT]
    [LEFT][/LEFT]
    [LEFT]Any ideas because I did install it successfully on a different computer.[/LEFT]

---

### Post by linuxuser28 on 2006-10-11
I also get this message when I hit reload in Synaptic.

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

### Post by Kateikyoushi on 2006-10-11
This should solve the second problem, copy to a terminal.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

---

### Post by linuxuser28 on 2006-10-11
> **Kateikyoushi said:**
> This should solve the second problem, copy to a terminal.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```
It did solve the second problem but Kubuntu still will not install.:(

---

