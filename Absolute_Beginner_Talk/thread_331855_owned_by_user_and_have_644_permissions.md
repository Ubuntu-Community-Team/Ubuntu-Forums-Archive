---
title: "owned by user and have 644 permissions"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-05
user's $home/. dmrc file is being ignored.
this prevents the default session and language from being saved.
file should be owned by user and have 644 permissions.
user's $home directory must be owned by user and not writeable by outher user's..

how do i fix this it appears just as i sign in 
if i click ok i can browse but i cant use firefox or swiftfox or terminal

in terminal i get sudo must be setuid root

firefox and swiftfox just dont hook up to the net

thanks

---

### Post by jem7v on 2007-01-05
I had this issue at one point. It's easier to find the answer with Google than browsing the forums here, though the answers might actually Be here.  Just search Google for the text of the error message - that's how I found the solution.

And if that user can't use sudo in the terminal, you might have to do the work from another user's account.

---

### Post by bapoumba on 2007-01-05
Hi,
logout from your session, then CTRL+ALT+F2 will get you to a tty, then :
```
$ sudo chmod 700 /home/<your_user>
$ sudo chown <your_user> /home/<your_user>
$ sudo chgrp <your_user> /home/<your_user>
```

If this does not work because you do not have access to sudo, boot in recovery mode (from grub menu, should be second line) and do the procedure again. Then you'll be root, your prompt wil show a **#** instead of a **$**. Just use the same commands without the sudo.

<your_user> is your current login.

---

### Post by STREETURCHINE on 2007-01-05
thanks i am in recovery but i cant make head nor tails from what it is i have to do when i type in th commands
.

i end up with missing operands ane invalid user 

any idea's  thanks


$ sudo chmod 700 /home/<your_user>
$ sudo chown <your_user> /home/<your_user>
$ sudo chgrp <your_user> /home/<your_user>

done all these in recovery without sudo(missing operand...invalid user)

---

### Post by bodhi.zazen on 2007-01-05
sudo chmod 644 /home/username/.dmrc
	sudo chown username /home/username/.dmrc
	sudo chmod 755 /home/username
	sudo chown username /home/username

	OR, if that fails:

	sudo chown  username /home/userfolder 
	sudo chmod 755 /home/userfolder
	sudo rm -rf /home/userfolder/.dmrc

	[http://www.ubuntuforums.org/showthread.php?t=168015](http://www.ubuntuforums.org/showthread.php?t=168015)
	[http://ubuntuforums.org/showpost.php?p=875518&postcount=8](http://ubuntuforums.org/showpost.php?p=875518&postcount=8)

substute your actual user name for "username"

---

### Post by STREETURCHINE on 2007-01-05
thanks i tried

sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

but no success the error message at login has gone but i still get .
sudo:must be setuid root.

so i will try  

sudo chown username /home/userfolder
sudo chmod 755 /home/userfolder
sudo rm -rf /home/userfolder/.dmrc

but one question i know i replace username with rex but what about userfolder do i change that as well(cause i have no idea what my user folder is )

---

### Post by bodhi.zazen on 2007-01-05
LOL STREETURCHINE !

Every user has a home directory in /home

/home/username

shorthand = ~

This is the directory referred to as "/home/userfolder"

---

### Post by STREETURCHINE on 2007-01-05
Every user has a home directory in /home

/home/username

shorthand = ~

This is the directory referred to as "/home/userfolder"

sorry but i dont no such file or directory

i thought i did but when i got the above error i thought it must be something else

still need a solution to this problem i am running out of web pages to read,tried the solutions on google ,
even in recovery mode i dont seem to be able to get my permissions back

---

### Post by bodhi.zazen on 2007-01-05
what is the output of:

```
ls /home
```

---

### Post by STREETURCHINE on 2007-01-05
what is the output of:

Code:

ls /home

rex , wonderdog

---

### Post by bodhi.zazen on 2007-01-05
OK so is your user name rex or wonderdog ?

or are you missing a home directory ?

---

### Post by STREETURCHINE on 2007-01-05
my name is rex

 i created wonderdog to try to migrate my setting accross(failed)

---

### Post by bodhi.zazen on 2007-01-06
Did you try this```
sudo chown rex /home/rex/.dmrc
sudo chmod 644 /home/rex/.dmrc
sudo chown rex /home/rex
sudo chmod 755 /home/rex
```

??

---

### Post by STREETURCHINE on 2007-01-06
> **bodhi.zazen said:**
> Did you try this```
sudo chown rex /home/rex/.dmrc
sudo chmod 644 /home/rex/.dmrc
sudo chown rex /home/rex
sudo chmod 755 /home/rex
```

??

yes i tried that in recovery since i cant use terminal on my linux machine.

sudo: /etc/sudoers is mode 0777,should be 0440

---

### Post by bodhi.zazen on 2007-01-06
> **STREETURCHINE said:**
> yes i tried that in recovery since i cant use terminal on my linux machine.

sudo: /etc/sudoers is mode 0777,should be 0440

Have you tried:

sudo chmod 440 /etc/sudoers

---

### Post by STREETURCHINE on 2007-01-06
> **bodhi.zazen said:**
> Have you tried:

sudo chmod 440 /etc/sudoers


just giving it a try now.ok that has given me back my permissions but i now have no internt.

if i boot into my second hard drive with edgy on it i have internet,
so how do i get my internet back 

i have a dlink usb router

---

### Post by ahmatti on 2007-03-16
> **bodhi.zazen said:**
> sudo chmod 644 /home/username/.dmrc
	sudo chown username /home/username/.dmrc
	sudo chmod 755 /home/username
	sudo chown username /home/username



This fixed the .dmrc problem for me :) . Thanks!

---

### Post by Campingman on 2007-03-16
Thanks all, this fixed it for me as well

sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

Anybody know what happened to cause this?  (i want to avoid doing it again)

---

### Post by wilsonsamm on 2007-09-23
that fixed it for me aswell.
What caused the error to arise for me was that I changed my ~ directory. Anyone know any other possible causes?

---

### Post by lyceum on 2008-07-20
I had this issue, and found nothing here in the forums, but this was the first link when I googled the issue. Just wanted to say thanks to bodhi.zazen 

:guitar:

---

