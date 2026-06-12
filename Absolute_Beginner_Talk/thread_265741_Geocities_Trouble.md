---
title: "Geocities Trouble"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-09-26
OK, here's a question I'll bet you guys have not addressed before.

My website is hosted by geocities (yahoo).
I use their online site-builder tools to update it--or, at least I did with Windows.

When I try to use the site-builder with Ubuntu, it says I need the Java Runtime Environment. Of course, when I try to download that module via Mozilla, it won't work with Linux.

So, actually, I have two questions.

1) Is there a way to make the site-builder work with Linux.
2) If not, is there a similar deal to geocities (where you can use gui tools to work on your site online) that works with Ubuntu?

Best,
Tom

---

### Post by bluefrog on 2006-09-26
install jre and you will be fine
have a look at your ubuntu help guide.
James

---

### Post by pbaehr on 2006-09-26
The easiest way to install JRE is to use automatix. Here are the instructions for installing automatix (pasted from their FAQ)

 Installing on Ubuntu 6.06 Dapper Drake
> 
Edit your sources.list:

sudo gedit /etc/apt/sources.list

Substitute gedit with the text editor of your choice.

Add the following to your sources.list:

NOTE: Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Next you must get our GPG key in order to authenticate our repository:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:

sudo apt-get update
sudo apt-get install automatix

Xubuntu users will also need to install Zenity:

sudo apt-get install zenity

Run Automatix either with the command "automatix" or by its launcher in Applications>System Tools>Automatix.


Automatix can also be used to add several other handy tools to your Ubuntu install. It's a good program to have for new users.

EDIT: By the way, all those commands are to be run from the terminal. You'll find it under Applications, Accessories, Terminal, if you didn't already know that. Good luck!

---

### Post by thomasaaron on 2006-09-26
Excellent!
Thanks.

---

### Post by thomasaaron on 2006-09-27
OK, I tried to install JRE via automatix.

Now when I try to get onto the site-builder program, the Java applet trys to start up, but then it "fails to initialize."

Any ideas?

Best,
Tom

---

### Post by petit.padavoine on 2006-09-27
I don't know how to fix the JRE problem, but you can use an off-line site-builder or something like Writely and upload it to GeoCities.

---

### Post by thomasaaron on 2006-09-28
Thanks. I check that out.

---

