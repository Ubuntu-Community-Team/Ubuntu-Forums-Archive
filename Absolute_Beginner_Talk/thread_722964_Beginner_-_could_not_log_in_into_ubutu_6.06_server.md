---
title: "Beginner - could not log in into ubutu 6.06 server"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by peterjc on 2008-03-13
hai, i am really a new beginner for linux.  Never use it before.  So, i give it a try. 

I am using the ubuntu 6.06 LTS server.  I install the ubuntu using LAMP.  After finish installation, computer restart and i was prompt to log in.  So, during installation, i create an account.  The name i gave was "home user", user name = home, password = 123.  So, i try to login using the user name and password but i was promt invalid password.

what is the problem?  could someone help me?  Thank in advance

---

### Post by scragar on 2008-03-13
I know it's possible to reset passwords, but I've always done it using a liveCD for the desktop version, so my advice may be off, sorry if that's the case.

using the liveCD boot into it, then go to
system > administration > disks
find your ubuntu partition and mount it by setting a mount point(somewhere in /mnt or /media would be fine), then you need to launch the text editor with root permitions, so
applications > accessories > terminal
then from the terminal ```
sudo gedit
```once it opens up go to
file>open
and find where you mounted your HD, from there go to /etc/shadow and open it
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/) <-- guide on the shadow file
you want to delete the entire password string for your username, save the file, close the text editor and reboot, you should now be able to log in without using a password

---

### Post by joshrobinson on 2008-03-13
restart the computer, at the grub screen select recovery mode
when you get to the root prompt type the following command, make sure to write it down or print it out

```
grep x:1000 /etc/passwd | cut -d: -f1
```
this will print out the username you chose, make sure it says home

now, you cant get it to display your password, but you can type
```
passwd username
```
replacing username with the username the last code printed out, which should be home
it will then ask you to re-set the password

make sure to print out what i said, unless your computers are close enough you can see/remember the commands

---

### Post by peterjc on 2008-03-13
Before that, i forgot to ask a question.  May i know why when i key in the password, nothing come out? no asterisk key, just blank?  Does this mean no password is keyed in?  May be this cause the problem for me to log in!

thank for the reply.:)

---

### Post by joshrobinson on 2008-03-13
do you mean it doesnt show your password when you are in a terminal? or do you mean at the graphical login screen? because at the graphical login screen it should show dots for your password, but in a terminal it wont show anything, but its still being typed

---

### Post by peterjc on 2008-03-13
yes, at the terminal. Ok, thank.

where is the graphical log in actually?  is it after the terminal log in, i need to log in again at the graphical log in?  

Thank

---

### Post by Sef on 2008-03-13
> where is the graphical log in actually? is it after the terminal log in, i need to log in again at the graphical log in? 

For the server there is not a graphical log in installed.   If you want to download one:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

