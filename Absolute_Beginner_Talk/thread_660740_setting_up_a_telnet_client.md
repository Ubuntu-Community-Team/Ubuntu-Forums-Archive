---
title: "setting up a telnet client ?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-07
I have just managed to finally get by server conected to the web! big step for me.
now i want to log in from access the computer remotely.

so first should i just teleet in ???

if so how do i set that up ?

i will be mainly logging in from work - and i CANT  install any new software on my work pc (well anything that needs administrator privaleges) , but have access to telnet.

any help ??

---

### Post by hyper_ch on 2008-01-07
use Putty and login over SSH.

On the server do:

```

sudo apt-get install openssh-server

```

And then, if you are behind a router, you will need to forward port 22 from the router to your server.

Download the Putty.exe file from here:  [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Start it, type in your IP address and your username/password and run it. It's a standalone-program, so no need to to install anything.

---

### Post by Borbus on 2008-01-07
Or if you use Linux on your desktop PC just open a terminal and use ssh. The basic command for sshing into a server is
```
ssh -l username address
```
Where username is your usernam on the **remote** box and address it the address of the box.

Note that telnet is extremely insecure and you shoud never use it on the internet. With telnet every piece of information that is transferred between you and the server (ie. shell commands, **your password**) are in plain text completely unencrypted. SSH gives you industry standard encryption and is considered safe to use on the internet.

---

### Post by lupgop on 2008-01-07
on the router i should forward port 22 to 22 right ?
TCP ?

---

### Post by hyper_ch on 2008-01-07
or you could use:

```

ssh username@address

```

---

### Post by Borbus on 2008-01-07
> **lupgop said:**
> on the router i should forward port 22 to 22 right ?
TCP ?

You will need to forward port 22 to the server, yes. The client does not need a port forwarded for it.

---

### Post by The Cog on 2008-01-07
> **lupgop said:**
> on the router i should forward port 22 to 22 right ?
TCP ?

Yes that's right.

You should also look at configuring the SSH server to be selective about who can connect and log in, or you will find lots of bots connected to you spending all day guessing usernames and passwords. In /etc/ssh/sshd_config you can specify something like:
```
AllowUsers bill@1.2.3.4,ben@5.6.7.8
```
see **man sshd_config** and **man ssh_config** for details.

---

### Post by hyper_ch on 2008-01-07
in order to prevent brute-force bot cracking methods you can do two things:

(1) Use a complex password for your user account, that include small and capital letters, numbers and special characters and it should not be an existing word. (E.g. xde3kKs89)

(2) Use DenyHosts (or similar programs):

[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

--> is there are too many wrong password entries from the same IP within a time limit, that IP will be banned on the allowed access list. By using a complex password it would take years and years before brute-forcing it.

---

### Post by lupgop on 2008-01-07
out of interest - once i have installed shh client;
sudo apt-get install openssh-server
how do i sett up users and passwords for clients ???
im guess the allow bob@1.2.3.4 is to allow user bob from IP 1.2.3.4 but what about validating bob's password ? where do i set this up ?

---

### Post by hyper_ch on 2008-01-07
Well, you install the server on your linux machine. Normal system users can then login through ssh (except if you have altered their default behaviour). So if your username is normally "bob" then your login password is the same that you normally use on that computer.

When you setup a ssh connection through the command line (ssh user@host) or a gui client like putty you will then be prompted to enter your password.

---

### Post by Seti on 2008-01-07
You may also want to change the port ssh listens on from the default 22 to something else. This will prevent all those annoying ssh brute-force attacks.
see /etc/ssh/sshd_config.

---

### Post by The Cog on 2008-01-07
The ssh server uses the standard Linux usernames and passwords, so you will use the same username and password as you would to log in locally. And if you want other users to be able to connect with SSH, you will have to use the normal users and grouops administration tools to add them as users to the machine.

---

### Post by Borbus on 2008-01-07
> **Seti said:**
> You may also want to change the port ssh listens on from the default 22 to something else. This will prevent all those annoying ssh brute-force attacks.
see /etc/ssh/sshd_config.

Security by obscurity, eh?

---

### Post by hyper_ch on 2008-01-07
If you use an auto-ban tool like HostsDeny and a "complicated" password I don't see much reason to change port. Smart scanners scan all ports ;) and also port 22 has been my only way back at university to use IRC. IRC was blocke so I had to ssh into my box and use irssi.

---

### Post by stalker145 on 2008-01-07
> **hyper_ch said:**
> use Putty and login over SSH.

Download the Putty.exe file from here:  [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Start it, type in your IP address and your username/password and run it. It's a standalone-program, so no need to to install anything.

There's also PuTTY from [Portable Apps]("http://www.portableapps.com") to run right from your thumb drive :D

---

### Post by Borbus on 2008-01-08
> **stalker145 said:**
> There's also PuTTY from [Portable Apps]("http://www.portableapps.com") to run right from your thumb drive :D

I recommend this in conjunction with PuTTY tray: [http://www.xs4all.nl/~whaa/putty/](http://www.xs4all.nl/~whaa/putty/)

Just replace putty.exe in the portable one with the one from PuTTY Tray.

---

