---
title: "find username for 5.10"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by jsparlin on 2007-06-26
just installed v5.10 and somehow can't find username although i know password and how to change it.  any way to do this? thanks

---

### Post by greg_g on 2007-06-26
If you are logged in you can always type in the command line: whoami

I hope that is what you wanted to know,

greg

---

### Post by KIAaze on 2007-06-26
I am not sure if I understood your problem correctly, since it's strange not to know the username.
here are a few ways:
personal username
```
whoami
pwd
```

Other usrnames:
```
ls /home
```

I don't know how to change it though.

edit:
If you can't login at all, then you might have to boot into some special mode allowing you to change the root password.
Here's how:
[QUOTE=zaichik]When you reboot, at the grub menu (assuming your bootloader is grub), hit "e" to edit the commands before booting.  You should then see a line like ```
kernel /vmlinuz-2.4.20-6 ro root=LABEL=/
```  Type a space after the slash, and then type a 1 to go into single-user mode.  You should be root at that point.[/QUOTE]
source: [http://www.linuxquestions.org/questions/showthread.php?t=555800]("http://www.linuxquestions.org/questions/showthread.php?t=555800")

---

### Post by scxtt on 2007-06-26
if you boot into "recovery mode" (should be an option from grub when your box is booting - might have to hit escape when it tells you) you'll be automatically logged in as root ... then if you do **cat /etc/passwd** you'll see all the users ...

---

### Post by jsparlin on 2007-06-26
i go into dos? and get-root@jim~#.  what does it mean.  can't seem to find username.

---

### Post by KIAaze on 2007-06-26
DOS?
Nobody here talked about DOS.

I suppose by DOS, you mean white text on black background. That's called a "terminal".
DOS is from Microsoft. ^^

Anyway, "get-root@jim~#" is probably your "command-line prompt".
All you have to do know is type one of the commands suggested above and press <enter>.

The terminal should then display lines of text containing your username.

To change the password:
Change the password of the account under which you are currently logged in:
> passwd
Change the password of another account:
> passwd <username>

Here are the different commands suggested and what they do:
> whoami =>outputs the username under which you are currently logged in
cat /etc/passwd =>lists all user accounts with additional info (usernames are the first words on the left)
pwd =>"print working directory": will look like /home/<username>
ls /home =>list contents of /home: since the contents of /home are directories named after the users, it's equivalent to the usernames


---

### Post by jsparlin on 2007-06-26
thanks, that cat/etc/passwd command got it, appreciate the help

---

### Post by Nekiruhs on 2007-06-26
5.10? Why would you install Ubuntu 5.10? The latest is all the way up to 7.04!

---

