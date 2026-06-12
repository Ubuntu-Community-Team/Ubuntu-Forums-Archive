---
title: "Installing Java through add/remove"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by rannasjem on 2007-01-31
Everytime I go to install java through add/remove programs I get a screen that says "java is commercial... blah blah.... do you want to 'cancel' or 'install'"  I click the install button and nothing happens.  The add/remove programs screen seems to stop responding, although any other apps will continue to work.  I left the computer on all night after clicking install thinking that it may just be taking a while but no luck.  Any ideas

---

### Post by OldTimeTech on 2007-01-31
Go to [www.automatix2.com](www.automatix2.com) and download, it will help you load java without those irritating "java is commercial screens".

---

### Post by Brunellus on 2007-01-31
For Java and Flash, please consult

[https://help.ubuntu.com/RestrictedFormats](https://help.ubuntu.com/RestrictedFormats)

---

### Post by rannasjem on 2007-01-31
i thought the add/remove programs in ubuntu was automatrix

---

### Post by jvc26 on 2007-01-31
No you have to install automatix2 its a GUI app which makes installing some of the apps commonly used very easy and pretty painless.
Follow these instructions:
```

gksudo gedit /etc/apt/sources.list

```
Then add these lines at the bottom:
```

## Automatix repo
deb http://www.getautomatix.com/apt edgy main

```
Save and close the file.
Then run these lines one by one from terminal.
```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

```
Then type:
```

sudo apt-get update

```
Then after updating, go for:
```

sudo apt-get install automatix2

```
And you shall have it working, then you can use it to install java etc.
Il

---

### Post by rannasjem on 2007-01-31
thanks for the help and I'll try it tonight, i hope i am not annoying people too much with my elementary questions

---

