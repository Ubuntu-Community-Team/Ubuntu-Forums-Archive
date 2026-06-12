---
title: "forgot my root password"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2007-02-07
Hi all. Okay now i am maintaining the college file server ( Ubuntu's SAMBA) and every time i wanna get into root it simply tells me that i have entered the wrong password:confused: :confused: :confused: . Hence how do i get my root password back. Please help me or in two days the admins of the college will format the system and i will have to start all over again.:( :(  please help . Okay and for your info it is a ubunt 4.something distro its got long term support version. Now please dont ask why i am using a 4.something distro when 6.10 is released.

---

### Post by arochester on 2007-02-07
"https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html" says:

I Forgot My System Password-What Can I Do?
Although passwords are indefinably essential and useful, they are also prone to being forgotten. With an increasing number of nasties out there on the Internet wanting to suck your password away, you need to think of more complex passwords, which are in turn harder to remember and easier to forget.

If you forget the system password, you need to jump through a few more hoops to reset your password. Reset your computer and when you see the word GRUB appear on the screen, press Escape to see the boot menu. Select the recovery mode option from the menu. When the computer boots it will present you with a root shell. At the prompt type:

foo@bar:~# passwd <username>

Follow the prompts to set a new password. Finally, reboot the computer with the following command:

foo@bar:~# reboot

---

### Post by bodhi.zazen on 2007-02-07
> **quarkhirad said:**
> Hi all. Okay now i am maintaining the college file server ( Ubuntu's SAMBA) and every time i wanna get into root it simply tells me that i have entered the wrong password:confused: :confused: :confused: . Hence how do i get my root password back. Please help me or in two days the admins of the college will format the system and i will have to start all over again.:( :(  please help . Okay and for your info it is a ubunt 4.something distro its got long term support version. Now please dont ask why i am using a 4.something distro when 6.10 is released.

arochester' smethod will work as will : ```
sudo passwd
```

But, how did you set a password ?

Ubuntu uses sudo 

sudo <command> ; enter your log in PW

or 

sudo -i # to become root ; again enter your log in PW

FYI : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MaximB on 2007-02-07
> **arochester said:**
> "https://help.ubuntu.com/6.06/book/book/ubuntubook-ch6-html/SupportandTypicalProblems.html" says:

I Forgot My System Password-What Can I Do?
Although passwords are indefinably essential and useful, they are also prone to being forgotten. With an increasing number of nasties out there on the Internet wanting to suck your password away, you need to think of more complex passwords, which are in turn harder to remember and easier to forget.

If you forget the system password, you need to jump through a few more hoops to reset your password. Reset your computer and when you see the word GRUB appear on the screen, press Escape to see the boot menu. Select the recovery mode option from the menu. When the computer boots it will present you with a root shell. At the prompt type:

foo@bar:~# passwd <username>

Follow the prompts to set a new password. Finally, reboot the computer with the following command:

foo@bar:~# reboot

so you are basically saying that anyone who have access to my computer can without additional discs easily change my password ?
(I cnow it can be done, but I thought it was harder).

---

### Post by bodhi.zazen on 2007-02-07
> **MAXDDARK said:**
> so you are basically saying that anyone who have access to my computer can without additional discs easily change my password ?
(I cnow it can be done, but I thought it was harder).

Yep. Physical access is bad news ...

There are some things you can do, but not much. That is why people keep em locked up :p

That's why people often physically destroy HD with sensitive data.

I like a book "hardening Lniux" for a nice review :

[http://www.amazon.com/Hardening-Linux-James-Turnbull/dp/1590594444?tag2=gp04-20](http://www.amazon.com/Hardening-Linux-James-Turnbull/dp/1590594444?tag2=gp04-20)

Of course you can PW protect grub, disable/PW protect BIOS, and remove/hide the recovery mode on your grub list :

See here : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by quarkhirad on 2007-02-07
dear arochester 

I rebooted my system. pressed escape. Selected recovery mode. It booted and then said 

give root password for maintanance (or type control D for normal startup)  :

It expects me to enter the root password which i have forgoten. So please Help  

PLEASE NOTE I AM USING UBUNTU 4. SOMETHING . IT IS nOT I REPEAT NOT 6

---

### Post by quarkhirad on 2007-02-07
> **bodhi.zazen said:**
> arochester' smethod will work as will : ```
sudo passwd
```

But, how did you set a password ?

Ubuntu uses sudo 

sudo <command> ; enter your log in PW

or 

sudo -i # to become root ; again enter your log in PW

FYI : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Hey remember this is only true for ubuntu 6 onwards. I am using ubuntu 4. something.

---

### Post by nereid on 2007-02-07
Just boot your computer with a live cd. Create a new directory in the mount directory (the name doesn't matter)

```

mkdir /mnt/tmp

```

Then mount your root partition into the just created directory (I assume your root partition is hda1)

```

mount /dev/hda1 /mnt/tmp

```

Now you have mounted your root partition in the filesystem. Now you have to chroot your root partition (tell the terminal that this directory is now the root directory and use the bash shell)

```

chroot /mnt/tmp /bin/bash

```

Voila you're in your own home configuration, now you simply have to change the password of the root user

```

passwd

```

That's it. That's also why physical access to a server is a very Bad Thing(tm).

---

### Post by dannyboy79 on 2007-02-07
> **quarkhirad said:**
> Hey remember this is only true for ubuntu 6 onwards. I am using ubuntu 4. something.

I thought sudo is in Warty Warthog as well (Ubuntu 4.10). so to change the root password you simply type sudo passwd root, then it'll first ask you for YOUR password, (which is the sudo password)  then you need to enter a password for root 2 times in a row. that should do it. good luck

---

### Post by quarkhirad on 2007-02-07
Hey nereid . Thanks man. I will have to tell the admin to put a CD drive into the system. As the system for safety does not have a Cd rom drive. Then i shall try ur solution. Hope it works and thanks. I just knew i could depend on ubuntu forums for my answer. Thatnks again. U have just saved me about 3 days of work and about 5 days of brain storming.

:) :) :) :)

---

### Post by g3k0 on 2007-02-07
that passwd command is similar to the net user 'Username' 'password' in windows.

Its a little too vulnerable for my liking..

---

### Post by quarkhirad on 2007-02-07
> **dannyboy79 said:**
> I thought sudo is in Warty Warthog as well (Ubuntu 4.10). so to change the root password you simply type sudo passwd root, then it'll first ask you for YOUR password, (which is the sudo password)  then you need to enter a password for root 2 times in a row. that should do it. good luck

Ah thanks dannyboy but the problem is i do not remember the password

---

### Post by dannyboy79 on 2007-02-07
> **quarkhirad said:**
> Ah thanks dannyboy but the problem is i do not remember the password

you said you don't remember the root password. There's a HUGE difference between you fogetting your password and you forgetting the root password. You'll have to follow the chroot post which was posted prior to my suggestion.'

or follow this which I just found by doing a search in this forum, using forgot root password:

Or boot into recovery mode from GRUB menu and at the prompt, change the password for that user, john (assuming john is the username...)!

passwd john

---

