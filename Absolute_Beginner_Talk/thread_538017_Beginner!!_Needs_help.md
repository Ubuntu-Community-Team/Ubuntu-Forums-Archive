---
title: "Beginner!! Needs help"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by diseasedmind on 2007-08-29
Hi guys, I have a quick question, I have just installed Ubuntu on a machine with Xp Pro on it, and as i expected it gave me an option of which o/s to boot into when it loaded up, but there was about 4-5 for linux and then xp was at the bottom
is there a way to put XP at the top and then just have one saying Ubuntu which lets me in?:confused:

Thanks guys

---

### Post by whizbaby on 2007-08-29
> **diseasedmind said:**
> Hi guys, I have a quick question, I have just installed Ubuntu on a machine with Xp Pro on it, and as i expected it gave me an option of which o/s to boot into when it loaded up, but there was about 4-5 for linux and then xp was at the bottom
is there a way to put XP at the top and then just have one saying Ubuntu which lets me in?:confused:

Thanks guys
Hi!
Of course theres a way!
I dont know if its the easiest, but I would do:
edit the grub configuration file

sudo nano /boot/grub/menu.lst

find the line  saying
default 0

and change 0 (which points to the FIRST entry) to the place of your winXP entry (this is its position - 1 because you starrt counting with 0 here, e.g. if its the third for grub its 2)

another possibility is to change this line to

savedefault

and to remove all other  'savedefault' from the entries that are not XP (add savedefault to your XP entry if it isnt there)

---

### Post by stevebakerj on 2007-08-29
This gives you all the info you need:

[http://ubuntuforums.org/showthread.php?t=400247&highlight=editing+Grub+menu.lst](http://ubuntuforums.org/showthread.php?t=400247&highlight=editing+Grub+menu.lst)

---

### Post by s26c.sayan on 2007-08-29
Yes, you'll have to edit the /boot/grub/menu.lst file while you are in Ubuntu.

[This little guide]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/") should get you started!

---

### Post by diseasedmind on 2007-08-29
Thanks for the guide, its making sense, but i cant save the file, i cant change the permissions of it either, it says i'm not the owner :S

---

### Post by s26c.sayan on 2007-08-29
Try prepending a 'sudo' to the command with which you open the file....
e.g. sudo gedit /boot/grub/menu.lst

---

### Post by svalding on 2007-08-29
hit alt f2 and type gksudo nautilus. Unlock it using your root password. This give you root access to your directory tree. navigate to /boot/grub/menu.lst and open it in text editor, you will be able to save it then. If you do not want to do it that way use ```
 sudo gedit /boot/grub/menu.lst 
``` inside the terminal. This will open the document with root priviledges once you supply your root password.

---

### Post by diseasedmind on 2007-08-29
forgive my ignorance but what is sudo? is it like a command line? if so how do i find it?

---

### Post by svalding on 2007-08-29
If I would read carefully, I would see that I restated the exact post above mine. Sorry mate!

---

### Post by diseasedmind on 2007-08-29
> **svalding said:**
> hit alt f2 and type gksudo nautilus. Unlock it using your root password. This give you root access to your directory tree. navigate to /boot/grub/menu.lst and open it in text editor, you will be able to save it then. If you do not want to do it that way use ```
 sudo gedit /boot/grub/menu.lst 
``` inside the terminal. This will open the document with root priviledges once you supply your root password.

sorry just got this

---

### Post by svalding on 2007-08-29
sudo is just another command you run within the terminal. 


It means su (superuser) do (action you want executed)

You'll see this mentioned all the time in the linux community. Any time you need to install something it is always good to run sudo in front of it, to ensure that you install things as root. 


Another way to do things, and basically the exact same thing as using sudo, just adding one more step is to use the su command and hit enter, authenticate by typing your root password, and then run the command you wish to execute. As you use linux more, it will become second nature to run sudo in the front of every command.

---

### Post by ubuntu27 on 2007-08-29
> **diseasedmind said:**
> forgive my ignorance but what is sudo? is it like a command line? if so how do i find it?

Here is a little guide:

[Where is the Terminal (Konsole/CommandLine)?]("http://www.psychocats.net/ubuntu/terminal")

[What is sudo & what about File Permissions?]("http://www.psychocats.net/ubuntu/permissions")

---

### Post by diseasedmind on 2007-08-29
Oh right fair enough! Thanks

I'm really intriuged about Linux and i'd like to learn alot more, so thats a bgi start! What does the Nautilus mean?

---

### Post by amosharper on 2007-08-29
> **diseasedmind said:**
> Oh right fair enough! Thanks

I'm really intriuged about Linux and i'd like to learn alot more, so thats a bgi start! What does the Nautilus mean?

Nautilus is the program you use to browse your files. In Windows, the default equivalent is Windows Explorer.

EDIT: In the context of the command ```
gksudo nautilus
```
This means you're using the root account (an account that has full administrator priviledges) to open Nautilus, the file explorer. This means that you can open, edit and save any file.

---

### Post by schorsch on 2007-08-29
> **s26c.sayan said:**
> Try prepending a 'sudo' to the command with which you open the file....
e.g. sudo gedit /boot/grub/menu.lst
When starting a graphical application like "gedit" you should use "gksudo" instead of "sudo" because otherwise you can mess up with some permissions.
So:
To use terminal  apps: Use sudo
To use graphical apps: Use gksudo (or kdesu when running KDE)

Look at [this]("http://www.psychocats.net/ubuntu/graphicalsudo") for more information about this issue.

---

### Post by gundumfx on 2007-08-29
> **stevebakerj said:**
> This gives you all the info you need:

[http://ubuntuforums.org/showthread.php?t=400247&highlight=editing+Grub+menu.lst](http://ubuntuforums.org/showthread.php?t=400247&highlight=editing+Grub+menu.lst)

hey diseasedmind  here you see this person  i am quoting he is right go to this web i an did checked it out an saw it might help you so good luck

---

