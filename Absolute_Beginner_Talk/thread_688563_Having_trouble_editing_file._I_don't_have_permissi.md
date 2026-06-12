---
title: "Having trouble editing file. I don't have permission?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by rustyDusty on 2008-02-05
I am a complete newbie and just installed Ubuntu the other day.

Its been nice so far but I have permissions trouble.

I am trying to use mgetty and I was editing the voice.conf file but it won't let me save changes telling me that : "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Well I am the only account on this pc and I thought the first account had admin privileges.

How do I fix this problem?

I went into System - Administration - Users and Groups. "Administer the system" box was checked so I'm confused.

I also noticed that when I look at file properties I will see a notice telling me that I am not the owner.

Well who is the owner then?

Any advice will help.

---

### Post by samb0057 on 2008-02-05
Go into the directory where the voice.conf file is, and type "ls -l"
The 3rd column will be the owner of the file.

---

### Post by Mitchlb on 2008-02-05
You haven't set a root password yet.

---

### Post by Mitchlb on 2008-02-05
When you do, it will let you.

---

### Post by emarkd on 2008-02-05
You don't have to set a root password.  You can do anything with your account, but if the file is owned by root, you'll have to edit it using sudo or gksu commands.  Be very careful when you're acting as root.

---

### Post by Mitchlb on 2008-02-05
All i know, is when i started ubuntu a while back, i hadn't set the root password. I just assumed it was the same as my log-in pw. I was wrong. It didn't let my type anything until i created a root password.

---

### Post by aysiu on 2008-02-05
You do not have to set a root password, and you don't even have to use the terminal.

How to edit files that are owned by root:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

If you decide to use the terminal, how to deal with the frustration of it apparently not letting you type your password:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by jrothwell97 on 2008-02-05
You need to run it under gksudo to save it. This is achievable (I think) using the 'run as administrator' app in the Applications menu. Otherwise, go into the Terminal and run

```
gksudo gedit
```

That should work.

---

### Post by samb0057 on 2008-02-05
By checking the box "administer the system", this does not give you automatic superuser privileges.

What this does is allow you to use the "sudo" command. By putting the sudo command in front of another command, you are running it with root privileges.

For example, if I type "sudo do-stuff", that will run the "do-stuff" application with superuser privileges.

So go the command line and type "sudo nano voice.conf" or "sudo gedit voice.conf"
The first will put you into a command line text editor editing voice.conf, the second will give you a graphical editor with voice.conf open. You should then be able to make the changes and save the file.

When sudo asks for a password, just type your user password.

---

### Post by rustyDusty on 2008-02-05
First I wanna say that the title of this thread is wrong.

I'm having permissions issues.

So are you guys telling me that I have to restart my pc and log on as "root"

I have a user name but that account clearly isn't working for me.

---

### Post by steveneddy on 2008-02-05
Listen to** aysiu**.

He is wise and his advice is invaluable.

---

### Post by Het Irv on 2008-02-05
alot of times config files are owned by root. To edit or change anything owned by root you have to give yourself root privileges.  Because of security you can only do this temporarily.  When you are in the terminal you precede your command with **sudo**, to change a file like you are you would type
```
gksudo gedit /"file location here"
```

both of these commands will prompt you for the root password.  This is usually the same as the password for the first account created during installation.  When you use sudo **BE CAREFUL** all commands will be accepted no matter what damage it will do to the system.

---

### Post by emarkd on 2008-02-05
No, you can't login as root on a normal Ubuntu installation.  To edit your file, from the commandline run:

```
gksu gedit path/to/file
```

It'll ask you for your password and then you can edit the file.

---

### Post by aysiu on 2008-02-05
> **rustyDusty said:**
> First I wanna say that the title of this thread is wrong.

I'm having permissions issues. I'll change the subject title, then.

> So are you guys telling me that I have to restart my pc and log on as "root" **No**! you should definitely not do that. Read the link I posted earlier.

---

### Post by aysiu on 2008-02-05
> **emarkd said:**
> No, you can't login as root on a normal Ubuntu installation. More importantly, you don't need to.

---

### Post by jgrimm on 2008-02-05
Hangon - a little more explination, then:

As a general rule, it's never a good idea to use your Ubuntu PC, on a daily doing-normal-stuff basis, as root.  it's insecure, it's dangerous - and... well.  Just not a good idea.

To sum up - root has no controls over modifying system files that you run across, and no real warning that what you're modifying may be an incredibly bad thing to modify without knowing what you're doing with it - monkeying in the system isn't /bad/, and is often /necessary/, but putting the extra layer in there is a Darned Good Idea.

In Ubuntu, you get around this by /temporarially/ elevating your status - and you do that by the command 'sudo'.

Think of it as 'Do As Superuser', or 'Do As Root'.

It neatly solves your permissions problems without having to /be/ root to accomplish what you're doing .... even though you /can/ be root if you really wish.  Think of being root as an insecure hack, though - when you're root, you've got no protection and you're circumventing the best parts of using Ubuntu for its security features.

So, to edit the file (assuming you're using 'gedit' - put in what's appropriate)

You'd just type 'sudo gedit <filename>' - and when it asks for a password, put in /your/ password.  The password of the account you're using.  You become root for the duration of that command, your permissions issues are solved without having to login /as/ root, and you can make any necessary system changes in that way.

By NOT having a root user, you keep your system much more secure.

Does that make a bit more sense?

Grimmy

---

### Post by rustyDusty on 2008-02-05
> **samb0057 said:**
> By checking the box "administer the system", this does not give you automatic superuser privileges.

What this does is allow you to use the "sudo" command. By putting the sudo command in front of another command, you are running it with root privileges.

For example, if I type "sudo do-stuff", that will run the "do-stuff" application with superuser privileges.

So go the command line and type "sudo nano voice.conf" or "sudo gedit voice.conf"
The first will put you into a command line text editor editing voice.conf, the second will give you a graphical editor with voice.conf open. You should then be able to make the changes and save the file.

When sudo asks for a password, just type your user password.

I did open the voice.conf file from terminal. At first it gave me password grief, then it just started to work.It opened the voice.conf file in gedit 2.20.3 and this is where I was unable to save changes.

So what will allow me to save changes?

---

### Post by jrothwell97 on 2008-02-05
Logging in as root is rarely advisable. It sometimes pays to have a working root account, but rarely. This applies not only to Ubuntu, but also to Fedora, Slackware, Debian, Gentoo, and to other Unixes such as Mac OS X, BSD, Darwin, etc.

root is the supreme administrator on Unix. According to the computer, root is God and its word is taken above anyone else.

I strongly advise against logging in as root unless you have a full firewall in place, and can't manage what you need to do any other way. This is why, in Debian/Ubuntu, and other UNIX clones such as Mac OS X, root is disabled as a login option by default.

However, there is a better way to use root. It involves the su and sudo commands. *su* switches the terminal to the root account. It's not as safe as sudo, which runs the command you typed after it as root. gksudo (aka gksu) is the graphical version.

When you use sudo, it will ask for your password (a sort of standard security question). If you're in the terminal, the password (not even stars or dots replacing the letters) will appear. Don't be unfazed: this is normal. Just keep typing, and press Enter to complete.

---

### Post by aysiu on 2008-02-05
> **rustyDusty said:**
> 
So what will allow me to save changes? Alt-F2 will bring the Run dialogue up.

Once that is up, if you're using Ubuntu ```
gksudo nautilus
``` if Kubuntu ```
kdesu konqueror
``` if Xubuntu ```
gksudo thunar
``` Then you will be able to browse as root temporarily and edit whatever you want.

Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by seventhc on 2008-02-05
open a terminal and type:
```
sudo gedit /etc/mgetty/voice.conf
```assuming the file is located in /etc/mgetty/

What is this password grief you speak of??
Are you logged into the account that was created during the installation of Ubuntu?

---

### Post by magicman5421 on 2008-02-05
In most linux distros, system files by default are not owned by the user, they are owned by root. This is to prevent clueless people from screwing up their system. Write priveleges are also restricted. The file you're trying to edit is obviously owned by root. Sudo makes you root for a short time. By the way, if you type the password in the terminal to become root at the "enter password:" dialog, **Nothing will appear. This is normal. just type your user password in and it will run.** For that terminal session, i.e until you close the terminal, you will be able to use the sudo command without having to enter the password.

---

### Post by rustyDusty on 2008-02-06
Ok I forgot the sudo command.

I would use it for the first command and forget about it for the next.

My mistake.

Always use sudo when changes are made.

Thanx for the helpful responses.

---

### Post by kindafunnylookin on 2008-02-06
No Absolutly not.
Re read the post by aysiu


> **aysiu said:**
> You do not have to set a root password, and you don't even have to use the terminal.

How to edit files that are owned by root:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

If you decide to use the terminal, how to deal with the frustration of it apparently not letting you type your password:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by kindafunnylookin on 2008-02-06
Absolutely not.
Re-read the post by aysiu

---

