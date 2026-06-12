---
title: "[SOLVED] How to log-in as root?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-10
One fellow is giving me instructions (see below) on how to install something. He tells me to "log-in as root" in order to create a folder in the usr/bin/local directory. I know that normally, in order to execute commands in root using a terminal window, one uses the prefix "sudo". But in the below explanation, it does not sound like this fellow is giving me instructions to execute in terminal. Rather, I am indicated to  just go to "places" and trace the path to the indicated place and then create a folder there. So how does one "log-in as root" to carry this out?



> What you do is create a folder, i call mine wg111v2, in this you put the .inf and .sys windows files for the USB Dongle.
This folder is created in the usr/bin/local directory, you may need to log-in as root to make the files executable for NDIS to use them.
It's likely you will need to be logged in as root to make the folder anyway, so just log-in as root, open the above mentioned folder DIRECTLY, not using terminal, so you open filesystem in the browser, then clear the location address bar and just put in " / " and hit enter, this opens the root directory, open usr folder, then bin folder, then local folder, then create wg111v2 folder, then open this and paste the .inf and .sys files here.

---

### Post by Dr Small on 2007-09-10
```
gksudo nautilus
```

---

### Post by diatribe on 2007-09-10
sudo -i will also allow you root access at a terminal

---

### Post by runemaste644 on 2007-09-10
No, ```
sudo nautilus
```
or```
sudo -i
nautilus
```
Either one will do

---

### Post by sumguy231 on 2007-09-10
Use either:
```
sudo su
```
or
```
sudo -i
```

Edit: Beaten, again, but at least I thought of a third way. :)

---

### Post by Dr Small on 2007-09-10
Your not supposed to use sudo with X display applications, as it is said to mess things up, but rather use gksudo, which is "graphical super user do".

Dr Small

---

### Post by diatribe on 2007-09-10
gksudo is actually more proper when running a gtk app

---

### Post by swarup on 2007-09-10
> **Dr Small said:**
> ```
gksudo nautilus
```

Thank you Dr. Small and to all the others who contributed so incredibly quickly.

So I could just do "gksudo nautilus", and then whatever I do in Nautilus will be done as root, correct? Then when I'm done and want to go back to normal user, how do I then "log-out" of root and become a normal user again?

---

### Post by diatribe on 2007-09-10
all you would have to do is close nautilus, when using sudo or gksudo it grants root privelages only temporarily, and for that particular program/command

---

### Post by Dr Small on 2007-09-10
Using "gksudo nautilus" will run Nautilus as Root User. Be careful above everything.
When you are done, just close nautilus, and it will log you out of Nautilus as root.

Anything preformed in "gksudo nautilus" is preformed by root, therefore you can do virtually anything. Hence my warning above.

Dr Small

---

### Post by swarup on 2007-09-10
I see. Thanks to you both for clarifying that. And i will be very careful. One final question on this-- if you look on the directions in my first post, the fellow directs me to create a folder in user>bin>local. But I went into user>bin, and in bin could not find a "local" folder. However, in user>local, there is a 
"bin" folder and indeed, it turns out there are personal user files kept there. So my guess is that he made a small error and meant this location instead. Would that make sense to you?

---

### Post by diatribe on 2007-09-10
this is more than likely the case

---

### Post by swarup on 2007-09-10
> **diatribe said:**
> this is more than likely the case

Thank you.

---

### Post by eph1973 on 2007-09-10
Would it matter to use gksudo rather than just sudo in the terminal if all you are doing is shuffling files around and changing the permissions?  (which it sounds like the OP is wanting to do that).  My question is one of curiosity.

---

### Post by diatribe on 2007-09-10
terminal commands should use sudo, gui commands should use gksudo, ie

sudo mkdir /etc/something
gksudo synaptic

---

### Post by santy_kushwaha on 2007-09-10
i dont know that all the other commands which people gave u work or not but the easiet way which i found out is that u go to the login setup box and check up the login as root enable it and then log in as a root with root password

---

### Post by diatribe on 2007-09-10
running x as root is a large security risk, and if you are not careful you can destroy your system

---

### Post by sumguy231 on 2007-09-10
> running x as root is a large security risk, and if you are not careful you can destroy your system
This is true. It's always a bad idea to run as root for extended periods of time. You should use sudo not only to save yourself from others but to save you from yourself.

> Linux is easier if u know what are u doing Otherwise it will suck u 
Heh. :) (No offense meant, of course.)

---

### Post by diatribe on 2007-09-10
> **sumguy231 said:**
> This is true. It's always a bad idea to run as root for extended periods of time. You should use sudo not only to save yourself from others but to save you from yourself.


Heh. :) (No offense meant, of course.)

LOL

---

