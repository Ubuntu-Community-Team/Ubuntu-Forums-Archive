---
title: "root password?"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by mszl_1 on 2005-12-17
im running fedora core 4 at the moment and all seems well, however i need root priviledges to do some changes. i cant recall setting up a root password to change things. does fedora have a default or hidden password for root users or am i too forgrtful to remember the flaming thing?
if it has a default password, what is it or do i have to reinstall and see if ti offers the option for root passwords?
thanks.:confused:

---

### Post by Gustav on 2005-12-17
In Fedora I think that you hace to set up a root password during the installation.

In Ubuntuit's standard not to, instead you use the sudo command and when a password is asked for, type your userpassword. Look at wiki.ubuntu.com/RootSudo for a full explenation

---

### Post by mszl_1 on 2005-12-17
thanks gustav i just notuiced this when reistalling fedora.:D 
also how do i get a signature like you have when you reply to threads?

---

### Post by Gustav on 2005-12-17
Look at the link "User CP" at the top left

---

### Post by mszl_1 on 2005-12-17
thankx gustav. did the signature thing, now i cannot login as root when i want to install apps s it tells me i dont have permissions to extract files. how do i log in as root?

---

### Post by Gustav on 2005-12-17
It's bad to log in as root, it opens your computer to all sorts of trouble.

You should use the terminal for most stuff were you have to be root. You become root by typing ```
su
``` and then your password. if you're not comfortable with the terminal you can start graphical programs from the terminal and use them (for example if you want to browse your files as root you can type ```
nautilus
``` while you are root.

Dont forget to exit root-mode by typing ```
exit
``` when you're ready (it's enough just to exit the terminal if you don't want to continue useing it as normal user)

---

### Post by bscbrit on 2005-12-17
Try this link for instructions on resetting your root password under FC4

[http://www.fedorafaq.org/basics/#resetroot](http://www.fedorafaq.org/basics/#resetroot)

HTH

---

### Post by mszl_1 on 2005-12-17
thanx gustav, i understyand that working as root is not a good idea however i need ? to when i want to install new programms appls etc. do you mean that when i go to terminal i could install from there? what does [SU]mean ?
when and where do i type exit when i m finished with the install etc? never done this as ive only been using FC for about 4 days now. the things you learn is great innit?

---

### Post by bscbrit on 2005-12-17
SU - means switch user.  You can change to any user on the system as long as you know the correct password.  Without specifying another user it means 'switch user to root'.  On FC4 root has a separate password, on Ubuntu a slightly different system is used called sudo.  This gives a user temporary root powers but allows him/her to use his own password.  In fact, as default, one cannot log on to Ubuntu directly as root.  Although you would never guess, all the instructions for 'su' and every other linux command that exists on you computer are already stored on your computer.  Open a terminal or console, depending on your version of linux and type the following:

man su

That will print the information about 'su' - or its 'manual'.  Most of the documentation is accurate but not very easily understandable to someone who is new to linux.  But as you learn more, you can always go back and run 'man' to see how it all fits together.  Try running the following just for practice:

man ls
man cd
man man

It is all there if you know where to look....

---

### Post by mszl_1 on 2005-12-17
thanx again, will have a look at what you suggested. 
im told you cannot have ommeletes without breaking eggs, i like ommeletes. one only learns best once things dont work and by trying to fix what went wrong, good thing there is this forum to help out.

---

### Post by bscbrit on 2005-12-17
No problem - we all start out from the same position. But, if you don't find the answers anywhere else, come back here.  There is usually someone who has already solved the same problem....

---

