---
title: "help with my comp"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-01
wat do i do if i get a message saying

```
Failed to run gparted as user root:
 Unable to copy the user's Xauthorization file.
```

i get it when opening anything that requires a password

---

### Post by catlett on 2006-04-01
You have to type```
 sudo
```Anytime you need administrator priveleges you activate them by typing sudu before the command. In this case ```
sudo gparted
```With Ubuntu you always run as a user. You only become root temporarily by typind sudo. If you follow directions from a guide or source that is talking about Linux, and they say "log in as root". You don't do that with Ubuntu. With Ubuntu you type sudo before the command and you become root temporarily. In some distros you have to log out. Type in the word root instead of your username. Do the command. Then log out and enter your username. Ubuntu makes it easy with the sudo command. No logging in and out. Just type sudo before the command. Any time you get permission denies or not able to write etc, it is usually a sign you need to type sudo before the comand. Regards, Catlett.

---

### Post by ferebee on 2006-04-01
[QUOTE=slipk487]wat do i do if i get a message saying

```
Failed to run gparted as user root:
 Unable to copy the user's Xauthorization file.
```

i get it when opening anything that requires a password[/QUOTE]


These two threads describe a problem like yours.
If these posts sound like they're similar to your problem, it may be your .Xauthority file.

[http://www.ubuntuforums.org/showthread.php?t=104962&highlight=Unable+copy+user%27s+Xauthorization]("http://www.ubuntuforums.org/showthread.php?t=104962&highlight=Unable+copy+user%27s+Xauthorization")

Note Amohanty's second post in this thread. That's one thing you might try, or,  Xian's post here:

[http://www.ubuntuforums.org/showthread.php?t=139821&highlight=Unable+copy+user%27s+Xauthorization]("http://www.ubuntuforums.org/showthread.php?t=139821&highlight=Unable+copy+user%27s+Xauthorization")

Your .Xauthority file is located in your home folder, but is hidden in Nautilus'  default view. 
To show it in Nautilus click **View**, and then check the box marked **show hidden files**.

Hope this is helpful.

---

