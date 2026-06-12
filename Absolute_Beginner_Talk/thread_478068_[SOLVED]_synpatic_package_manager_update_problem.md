---
title: "[SOLVED] synpatic package manager update problem"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mike g on 2007-06-18
I am running Feisty Fawn and when I attempt to use the Synaptic update manager i get the following error message no public key with a bunch of numbers.  Hopefully there will be a screen shot attached to this message with the complete error message.

It also appears that, even though, 57 of 57 updates are being downloaded, none are actually being updated as the same 57 are downloaded every time I attempt to update.

Any help 1. with the error message
                 2. the download problem

or are they one in the same?

Thanks

Mike

---

### Post by reset3x on 2007-06-18
Go here and download the keyring package....  [http://www.debian-multimedia.org/faq.html](http://www.debian-multimedia.org/faq.html)

---

### Post by machoo02 on 2007-06-18
Firstly, why are you using the Debian Multimedia repository?  Although Ubuntu is based off of Debian, the binary packages for the two distributions are not always compatible with one another.  A better repostiory for you to use for multimedia would be [Medibuntu]("http://www.medibuntu.org/").  Secondly, the error that you show is one of a missing GPG key.  Apt uses these keys to identify trusted repositories.

---

### Post by some_random_noob on 2007-06-18
About the updates being downloaded over and over again: That happens when you click "reload" - it gives you an updated list of software. It doesn't actually download any programs or updates, it just updates the software list. (goto settings>repositories and dis-select anything you don't need to protect your beloved data-cap. I only have the Dapper Drake 6.06 "universe" repository selected. Also, you don't need to click "reload" more than once.)

... Someone correct me if I'm wrong; I'm only 16.

---

### Post by zvacet on 2007-06-18
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


gpg --keyserver hkp://subkeys.pgp.net --recv-keys 07DC563D1F41B907
 gpg --export --armor  07DC563D1F41B907 | sudo apt-key add -

---

### Post by mike g on 2007-06-20
Thank you all for your input.....still plugging along.

Mike

---

