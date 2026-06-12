---
title: "acroread adobe"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by rugby82 on 2007-05-23
i have install adobe reader 8.0 in ubuntu 7.04......
i have download the .rpm file.....and i make:
[PHP]sudo alien adobe.....etc[/PHP]
and it create the deb file.......now i have install adobe acrobat but he don't run and say that permis is denied!!!!

in /usr/bin/acroread is a file of text and not an application!?!?!?!?!?!?!?!!??!?!?!?
now i want
1 repair software 
or
2 delete adobe acrobat!!!

what i must do???

---

### Post by BarfBag on 2007-05-23
Slow down.  Let me get this straight.  You downloaded the .rpm for Adobe Reader, converted it to a .deb via alien, installed it, but it won't run because of permission?

You don't really need Adobe Reader in Ubuntu.  It comes with a PDF reader.  But if you really need it, the easiest way would be with Automatix.

---

### Post by wpshooter on 2007-05-23
> **BarfBag said:**
> Slow down.  Let me get this straight.  You downloaded the .rpm for Adobe Reader, converted it to a .deb via alien, installed it, but it won't run because of permission?

You don't really need Adobe Reader in Ubuntu.  It comes with a PDF reader.  But if you really need it, the easiest way would be with Automatix.

Using automatix MAY perhaps be the easiest way but **IMO**, it is not the correct way because when in the past I tried using this automatix program, it resulted in causing more problems than it solved.

---

### Post by Viskovitz on 2007-05-23
First of all, you should uninstall the debian package:

```
sudo dpkg -r adobe...
``` 

or whatever the name of the program.

Then follow this steps to get Acrobat Reader from the non-free repositories:

[https://answers.launchpad.net/ubuntu/+question/6608](https://answers.launchpad.net/ubuntu/+question/6608)

As BarfBag says, you can already read PDFs with evince (just double click on the file and should work), but Acrobat's reader allows you to do other things. If you need that, well, go ahead with those steps and good luck.

---

### Post by rugby82 on 2007-05-23
it say me that acroread is not installed!!!!?!?!?!??!?!?!?!??!?!?!?!?!??!?! this means that the package deb is not found!!!:confused::confused: therefore i can delete software manually, whitout problem, isn't true?

---

### Post by Viskovitz on 2007-05-24
Yes, you can delete it manually, but if you installed a deb you don't need to. Actually if you open synaptic and look in state>installed (local or obsolete) you should see it there. You can also look for it by name. Remove it completely and then follow the steps in the link I have you to install it properly.

---

### Post by rugby82 on 2007-05-26
if o make :

sudo apt-get remove acroread

it say that it don't know acroread!!!!
where can i see list of software that are installed?

---

### Post by Viskovitz on 2007-05-27
You can see the software you have installed in Synaptic. As I told you, if you really have it installed you should see it in the local/obsolete section. If you don't have it, as it looks, just follow the instructions of the link in my first post and you will get it.

Good luck, it's all about paying attention!

---

### Post by kelvin spratt on 2007-05-27
i've never had a problem installing reader make sure alian is installed right click on rpm package open with Kpackage thats it.

---

### Post by rugby82 on 2007-05-28
thank you for help!

---

