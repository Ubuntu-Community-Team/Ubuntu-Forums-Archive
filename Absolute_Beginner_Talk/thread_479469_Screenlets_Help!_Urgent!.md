---
title: "Screenlets Help! Urgent!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-06-20
Just now my frnd told me abt screen lets can any 1 help me by providing some info how to install it :)

Thanks its pretty urgent! Kudos again 

Regards;)

---

### Post by yagood on 2007-06-20
Screenlets homepage would a good place to start:

[http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/)

"Installation" section in particular. Good luck!

---

### Post by Dark Star on 2007-06-20
> **yagood said:**
> Screenlets homepage would a good place to start:

[http://hendrik.kaju.pri.ee/screenlets/](http://hendrik.kaju.pri.ee/screenlets/)

"Installation" section in particular. Good luck!
Is this the code for installation through terminal

```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by lamalex on 2007-06-20
no, that just gets you the PGP key for the repo so that it's authenticated. the command to install is ```
apt-get install screenlets
```

---

### Post by yagood on 2007-06-20
Open Synaptic, go to Settings > Repositories > Third-party software, click Add and paste:

```
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```

Reload package information in Synaptic and search for "screenlets".

Before you may want to import the key with the command that you quoted.

---

### Post by Dark Star on 2007-06-20
> **Iamalex said:**
> no, that just gets you the PGP key for the repo so that it's authenticated. the command to install is ```
apt-get install screenlets
```
Thanks btw done its```
 sudo apt-get install screenlets
```

---

### Post by Dark Star on 2007-06-20
> **Dark Star said:**
> Thanks btw done its```
 sudo apt-get install screenlets
```
An error E could not get package screenlets .. Help ,me :(

---

### Post by yagood on 2007-06-20
> **Dark Star said:**
> An error E could not get package screenlets .. Help ,me :(

You need to add the repository first. Follow the instructions from my previous post.

---

### Post by Dark Star on 2007-06-20
> **yagood said:**
> Open Synaptic, go to Settings > Repositories > Third-party software, click Add and paste:

```
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```

Reload package information in Synaptic and search for "screenlets".

Before you may want to import the key with the command that you quoted.
[[IMG]http://www.imgx.org/pthumbs/large/593/Screenshot.png[/IMG]]("http://www.imgx.org/public/view/full/593")

I can't find any rep. there help :o

---

### Post by lamalex on 2007-06-20
at the top, in the settings menu. pick repositories, and then the third party repos tab, and then add that repo.

---

### Post by Dark Star on 2007-06-20
Oops I got that done now what to do ? :S

---

### Post by yagood on 2007-06-20
> **Iamalex said:**
> at the top, in the settings menu. pick repositories, and then the third party repos tab, and then add that repo.

Off-topic: nice avatar :-) Greetings to fellow AD fan! :popcorn:

---

### Post by yagood on 2007-06-20
> **Dark Star said:**
> Oops I got that done now what to do ? :S

Click Reload, then click Search, enter "screenlets" and install the package.

---

### Post by lamalex on 2007-06-20
now update and search for screenlets and install it like you would any other software.

---

### Post by Dark Star on 2007-06-20
> **Iamalex said:**
> now update and search for screenlets and install it like you would any other software.
U mean by enering this command in Terminal 
> 
sudo apt-get install screenlets

Then this 1

> wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by Dark Star on 2007-06-20
> **Dark Star said:**
> U mean by enering this command in Terminal 


Then this 1
Installed thanks all .. .Btw why their corner appearing black :o

---

