---
title: "I need big help"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by wonderland on 2005-07-16
Hi everyone

I cant install my modem, ADSL usb modem, there is a folder in the CD-ROM named Linux, in the README file it says it can be installed on Mandrake and Suse but i dont know if Ubuntu can still work, becuase i think i heard that mandrake is in the family of ubuntu or something like that, but anyway i really cannot understand that concept of installing things on linux, and i need php, i saw that you need to type in "apt-get install apache2-mpm-prefork apache2-prefork-dev libapache2-mod-php4 php4-dev php4-mysql php4-pear" in the universe component. I dont have a clue what that is, but first help me install my modem please man, i really wana learn linux.

---

### Post by stevenyu on 2005-07-16
[QUOTE=wonderland]i heard that mandrake is in the family of ubuntu or something like that[/QUOTE]

Nope, Mandrake was based on Redhat, and Ubuntu is based on Debian

Is the modem driver in source format or in builed module

---

### Post by poofyhairguy on 2005-07-16
[QUOTE=wonderland]Hi everyone

I cant install my modem, ADSL usb modem, there is a folder in the CD-ROM named Linux, in the README file it says it can be installed on Mandrake and Suse but i dont know if Ubuntu can still work, becuase i think i heard that mandrake is in the family of ubuntu or something like that, but anyway i really cannot understand that concept of installing things on linux, .[/QUOTE]

Hold off on PHP for. What is the exact kind of modem you have? Make and model number please.

And time to learn a little. Please read this:

[https://wiki.ubuntu.com/HowToAccessTheUniverseRepository?highlight=%28universe%29](https://wiki.ubuntu.com/HowToAccessTheUniverseRepository?highlight=%28universe%29)

I wait for your response, and I like your enthusiasm

---

### Post by wonderland on 2005-07-17
man u guys well cool, man i really appreciate the quick help, but i managed to install my modem, however i need help on installing php, please read my other recent thread to see or actually ill copy and paste it, hold on.  here it is please help.

Hi every one, i have used ubuntu for 2 days including now, i spent yestarday trying to find out how install my modem which i finally did. Now i want to start coding PHP. My problems are listed below : -

1) I installed apache well i think i did, but the folder /var/www/ is not writeable, i cannot create any folders or copy and files in there. Oh yeah and there seems to be a folder called "Apache2-default" in there also, which is not writeable. I know that this folder is the localhost location.

2) How do i install PHP, PHP5 prefered. Also how do install MySQL and phpMyAdmin.

What i really want to know is how to install the whole thing so i can start coding. Please some one help, and if anyone can, can you please give instruction step-by-step.

Oh yeah iv also tried out that "Unofficial Ubuntu 5.04 Starter Guide" (from [http://ubuntuguide.org/](http://ubuntuguide.org/)) and where it says "Q: How to install PHP for Apache HTTP Server?", it tells me to enter this in to the terminal, (iv tried both terminal and root terminal):

sudo apt-get install php4
sudo /etc/init.d/apache2 restart
sudo gedit /var/www/testphp.php

This is what i got for typing in"sudo apt-get install php4":

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4


Someone help please? ??:

---

### Post by varunus on 2005-07-17
1.  /var/www will not be writable by you, but only by the "superuser," or administrator of the computer.  Ubuntu starts with the root account disabled by default.  You can still write files to /var/www by entering "sudo cp file1 /var/www/file1" but make sure to add the sudo.  It will ask you for your password when you do this.  (Security reasons.)

2.  In the ubuntu guide instructions, it states that you need to "add extra repositories" before you install PHP (step 2 of the howto).  To do this, follow the instructions here:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

