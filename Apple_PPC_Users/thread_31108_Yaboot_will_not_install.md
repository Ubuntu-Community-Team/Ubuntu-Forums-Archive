---
title: "Yaboot will not install"
date: 2005-05-01
forum: Apple PPC Users
---

### Post by binder on 2005-05-01
I instaled ubuntu but it was not able to install yaboot. I am using a powerbook g4. How do i boot to ubuntu or get yaboot installed?

---

### Post by Chunga on 2005-05-01
Did the installer give you any clues as to the reason why the yaboot install failed?  Do you have an Apple_Bootloader partition?  Did any of the previous steps in the install fail?

---

### Post by chascon on 2005-05-02
Are you sure you did not instal; yaboot?
You might have it installed. Just boot with option key held down, select linux, and boot.  Once in, run 'sudo ybin'.

You really don't need yaboot, you can boot with the 'option' key or if you want a really geeky way you can get into OF and boot from there.  'Option' key is wasy.

---

### Post by binder on 2005-05-02
Ok i got it to install but know i can not boot to os x with yaboot. How do i go about fixing this and what is the defalt root password?

---

### Post by binder on 2005-05-02
ok i figered out the root password but still cant login as root. I still cant boot in to os x.

---

### Post by Chunga on 2005-05-02
You did set the root password during the install right?

---

### Post by chascon on 2005-05-02
He just said he figured the password.

Can't reboot into OS X,.  Just clear pram till 3 chimes, then it should boot straight into OS X.  Then do what I said to get linux.  Unless you're talking about setting /etc/yaboot.conf to allow you to select either OS X or ubuntu.  Goto 
[http://penguinppc.org/bootloaders/yaboot/](http://penguinppc.org/bootloaders/yaboot/)
to learn.

---

### Post by Chunga on 2005-05-02
Yes, but he always asked earlier what the root password was.  It's just a little bit odd that the root password is set by the installer, yet he wasn't sure what it was after he had apparently finished the installation.  It could be related to the apparent trouble he had with the installer and also the trouble he's having now with not being able to log in.

---

### Post by phlug on 2005-05-22
[QUOTE=Chunga]Did the installer give you any clues as to the reason why the yaboot install failed?  Do you have an Apple_Bootloader partition?  Did any of the previous steps in the install fail?[/QUOTE]

I too am having this problem, on a PowerMac recently upgraded to Tiger.1.  I don't have an Apple_Bootloader partition and during Ubuntu installation I get the error message pointing this out.  Anybody know how can I correct the situation and complete the installation?

Thanks.

---

