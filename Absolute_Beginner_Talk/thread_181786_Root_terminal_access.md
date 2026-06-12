---
title: "Root terminal access"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by chirolon on 2006-05-24
Hello everybody.
I have been using ubuntu for a weak and so far It has been a good experience.
Ubuntu is great!!
A couple of times I tried to use mandrake, but I had problems intalling it.
Here is my question.
When I'm in the command line "user@computername:~$" and tried to access the root directory. It saids that doesn't exist.
I can see the the "file system" directory from the desktop environment", but I can't get there through the command line.
If I write "su root" in the prompt line It will then ask for the Password. But when I installed Ubuntu It din't ask me to create a password for the root directory.
Anyway Could someone explain how to use the command line and access diretories in the root directory or file system?
Thanks.

---

### Post by rado_london on 2006-05-24
Ubuntu doesnt use root by default. It uses sudo. This basically gives your user the root permission. Every time when you do something that requires root type in the command like this:
```
sudo apt-get update
```

Then it will ask for password. Entr your password. Thats it now you can do admin stuff with your user.

---

### Post by an.echte.trilingue on 2006-05-24
There is no root password on a default installation of Ubuntu.  As the first user account, open a terminal and type sudo su, then put in your own password and you will have a root environment.

---

### Post by aysiu on 2006-05-24
Read these two links:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by user1397 on 2006-05-24
[quote=an.echte.trilingue]There is no root password on a default installation of Ubuntu.  As the first user account, open a terminal and type sudo su, then put in your own password and you will have a root environment.[/quote]
However, creating your own root password is not necessary and not secure.  There is no reason to anyway, if you can just use sudo.  Plus, being root, you are opening yourself up for possible malware on the internet.

---

### Post by chirolon on 2006-05-24
Thank you for the quick response.
 The one's that know will rule the kingdom of the newbies.
I just started in this new quest and it looks like it is going to be a good experience after all.

---

### Post by simonn on 2006-05-24
[QUOTE=erik1397]However, creating your own root password is not necessary and not secure.  
[/quote]

That is debateable considering the vastly greater number of *nix systems with a root user who can log in than a root user who cannot.

> 
There is no reason to anyway, if you can just use sudo.  Plus, being root, you are opening yourself up for possible malware on the internet.

No more or less so than using sudo.

The only real argument you have is by allowing root access via ssh you give crackers and script kiddies the user they will try and brute force first. There are several ways to counter this, not least by disallowing root logins via ssh - which is a sensible thing to do anyway.

If you disallow root logins via gnome/kde etc then the only way to browse the web is via a text browser in the console (very limited chance of getting malware by accident instead of idiocy, if there is a chance at all) or starting a browser from the command prompt.

Now really, what is the difference between:

$ sudo firefox

$ su -c firefox

$ su
# firefox

You could even argue that running a browser as a normal user is insecure and you should run it in a chroot jail because you are still risking you personal data if you browse as you. I know that my personal data is far more valuable than my ubuntu install (which is why I maintain backups of it!).

The only arguement left is that root could still log in via a terminal screen (e.g. CTRL + ALT + F1 - F6), however, in this case they would need physical access to the machine and they could just as easily insert a Knoppix or Ubuntu live CD/USB memory stick reboot and have complete control, steal the hard drive, steal the whole goddamn PC etc, the latter two of which I would be most concerned about.

The argument could be made that, potentially, having multiple passwords to gain root access could make things more insecure. This is what sudo *can* do.

I am not arguing that the sudo approach is a bad thing. It is just one form of security implementation which has it's positives and negatives, real or potential, like every other implementation. For essentially a consumer desktop system, like Ubuntu and OS X (which does the same thing), I actually think it is a very good idea from the perspective of being secure AND useable (the user does not need to concern themselves with the concept of switching users), just no more or less secure than having a root account with a login.

---

### Post by catlett on 2006-05-24
If you want to use su and root, you can make a root password.```
 sudo passwd root
``` If you just want a root terminal ```
sudo su
``` If you want to browse file as root and chamge permissions through the gui and hitting on properties<permissions ```
gksudo nautilus
``` Or of course you could ```
sudo su
nautilus
``` as well.
Debian is the base and Debian uses su and root not sudo so the su/root capabilities are there. I don't know why  the ability to get root are not easily found in the ubuntu forum?
But in ubuntu you only have to enter sudo before a command to invoke root priveleges ```
sudo *command*
```
I don't know why people are saying being at a root terminal is a big security risk? You are not logging in as root. You are only at a root terminal. If you invoke sudo and issue a command it is the same thing as switch user to root and run a commnad. Where is the difference at the terminal? If you use sudo command or switch to root command then switch back? You don't log in with su, you only switch to root for a command. Or am I missing something?

---

### Post by nalmeth on 2006-05-24
> If you disallow root logins via gnome/kde etc then the only way to browse the web is via a text browser in the console (very limited chance of getting malware by accident instead of idiocy, if there is a chance at all) or starting a browser from the command prompt.

Now really, what is the difference between:

$ sudo firefox

$ su -c firefox

$ su
# firefox

You could even argue that running a browser as a normal user is insecure and you should run it in a chroot jail because you are still risking you personal data if you browse as you. I know that my personal data is far more valuable than my ubuntu install (which is why I maintain backups of it!). I wanted to ignore but sorry, 
There's no difference between su and sudo in this manner, regarding security.
Running a browser as a normal user is ten-fold more secure than running as root.
Who in their right mind needs to run firefox as root?

---

### Post by simonn on 2006-05-25
[QUOTE=nalmeth]
Running a browser as a normal user is ten-fold more secure than running as root.
Who in their right mind needs to run firefox as root?[/QUOTE]

See the quote which I was refering to.

---

### Post by nalmeth on 2006-05-25
> There is no reason to anyway, if you can just use sudo. Plus, being root, you are opening yourself up for possible malware on the internet. I think he was refering to using sudo for admin stuff rather than logging in as root to avoid using sudo. At least that's how I understood it. Maybe I misinterpreted the statement. Entirely possible.

I was just taken aback by your example of running:
sudo firefox

Which of course, as you said, is effectively the same as being root (or becoming root) and running firefox, making you very susceptible to 'malware' on the net. 

I think I was just shocked by the idea of running firefox as root, while already your normal user. :-?

---

### Post by an.echte.trilingue on 2006-05-25
[QUOTE=erik1397]Plus, being root, you are opening yourself up for possible malware on the internet.[/QUOTE]

That is not true.

---

