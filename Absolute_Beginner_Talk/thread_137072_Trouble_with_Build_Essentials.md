---
title: "Trouble with Build Essentials"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2006-02-27
Heya

Everytime i try make a file i get an error telling me a certain file is missing. I've tried installing it through Synaptic but it gives me another error about an incorrect version or something.

Here's the error i'm getting.

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev

Does anyone know what is causing this, or better yet, how do i fix it?

Thanks in advance
SW

---

### Post by Klaidas on 2006-02-27
Try installing what's missing, like:
```
sudo apt-get install libc6-dev
```

---

### Post by Stone_Wolf on 2006-02-27
Thanks, but i've tried that already.

This is what i get.


The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-8.1 is to be installedE: Broken packages


I go to Synaptic and get to that file and try reinstall and it gives me an error.

Regards
SW

---

### Post by yooper4ever on 2006-02-27
Have you tried:

```
sudo apt-get build-essential

```

[QUOTE=Stone_Wolf]Thanks, but i've tried that already.

This is what i get.


The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-8.1 is to be installedE: Broken packages


I go to Synaptic and get to that file and try reinstall and it gives me an error.

Regards
SW[/QUOTE]

---

### Post by Stone_Wolf on 2006-02-28
Hello again

I tried running "sudo apt-get install build-essentials" and this is what i get.


Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev

I hope this sheds a little more light on the subject for some help. 

Thanks again to everyone trying to help
SW

---

### Post by Jucato on 2006-02-28
It seems that somewhere along the way, your libc6 got upgraded to a more recent version (2.3.5-8.1), but the build-essential package in the ubuntu repositories depend on an older version (2.3.5-1ubuntu12).

---

### Post by Stone_Wolf on 2006-02-28
Hiyas

Yet another update. I've used Synaptic to install all the recommended dependancies for libc6-dev then tried to mark libc6-dev itself for instillation. This is what i get when i try installing it.

libc6-dev:
  Depends: libc6 (=2.3.5-1ubuntu12) but 2.3.5-8.1 is to be installed

Thanks again
SW

---

### Post by Stone_Wolf on 2006-03-03
Hiyas

After a while of trial and error i've finally managed to sort out this problem. 

A simple search for "libc6-dev download" returned the .deb for downloading from the debian servers. On the same page is the updated "libc6.deb" i needed to install the first file. I downloaded both and updated these two files. Now i have no more hassles ;)

Regards
SW

---

