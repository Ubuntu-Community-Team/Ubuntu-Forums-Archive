---
title: "SSH Keygen"
date: 2011-05-29
forum: Apple Hardware Users
---

### Post by marcusww on 2011-05-29
I am trying to install a private public keypair on my mac, to connect to my server.


For some reason the process just isn't working...

I open my Mac

run 

<ssh-keygen -t rsa>

get my keys

Open my server 

open my .ssh/authorized_keys folder

vim and paste in my public key

<chmod 600 .ssh/authorized_keys>

then go back to my Mac and log in at

ssh root@123.45.678.901

but it is not implementing the keygen protocol

...........it just goes straight to password


Any ideas?

---

### Post by marcusww on 2011-05-30
Problem solved....just about I think.....

if you have a problem with the same, give me a shout

---

### Post by marcusww on 2011-05-31
Actually, problem not solved.

I can create a keypair that works for my root login, but then when I login as the USER I have created, it just asks for a normal password.

I suppose I could disable password authentication, and just carry logging as root.

Is that considered safe / good practice?

-----------

Alternatively, I am trying to set up my user permissions....

<useradd Joblow>

....Name..Mr Smith

..unix password....ty53nn75ty53t
...unix passwd ....ty53nn75ty53t

<visudo>

....

root     ALL=(ALL:ALL) ALL
joblow  ALL=(ALL:ALL) ALL


[I've also tried the      {ALL=(ALL) ALL}         configuration]

-----------

I've done that and then when I try to put my authorized_keys folder in .ssh

<mkdir /home/joblow/.ssh>
<nano /home/joblow/.ssh/authorized_keys>

copy and paste public key

when I go to save out (CTR + X), it says I don't have the permissions.....

DO I need to CHMOD something ??

Cheers

---

### Post by iclestu on 2011-05-31
cant you use

```
ssh-copy-id <username>@<host>
```

from the client machine?

---

### Post by marcusww on 2011-06-01
Thanks Iclestu. As soon as I am back on the server I will experiment

---

### Post by iclestu on 2011-06-01
> **marcusww said:**
> Thanks Iclestu. As soon as I am back on the server I will experiment

yeah, but you run that command from the client not the server..... :) (assuming we are not talking at cross purposes - when you say 'server' you mean the machine you want to ssh INTO, yeah? the ssh server....)

---

### Post by brettg on 2011-06-01
As far as I know your .ssh directory (and its contents) must have drwx------ permissions otherwise "strict checking", which is on by default will bail.

---

### Post by tapi0n on 2011-06-01
you need to add the key to the authorized_keys file of the user in /home/user. I'm assuming you added the key to the authorized_keys file of your root, thus only allowing your root to log in with that key.

And of course you can disable passwordless login. I don't know if it's considered safe but as far as I know you won't be able to log in without a propper key.

And as iclestu suggested use

```
ssh-copy-id username@host
```to add the key isntead of just pasting it.

Also, the owner and group of your .ssh and .ssh/autorized_keys should be that of your  user, but that's done automatically I think.

> As far as I know your .ssh directory (and its contents) must have  drwx------ permissions otherwise "strict checking", which is on by  default will bail.

In my setup .ssh has *drwx------* permission but .ssh/authorized_keys has *-rw------- *and it works like a charm so the content doesn't have to be *drwx------* I think

---

### Post by marcusww on 2011-06-02
Thanks for all the replies...I'll work on it later today

---

### Post by marcusww on 2011-06-02
the ssh-copy-id command doesn't work


$ ssh-copy-id barnaby@178.79.157.220
-bash: ssh-copy-id: command not found


SO I tried the other ideas, but they too don't work

I have an ssh directory, but can't write to it.
 [ Error writing /home/barnaby/.ssh/authorized_keys: Not a directory ]

------------------------------------------------------

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Thu Jun  2 15:05:00 2011 from host81-155-71-240.range81-155.btcentralplus.com
barnaby@midsomer:~$ nano /home/barnaby/.ssh/authorized_keys
barnaby@midsomer:~$ touch /home/barnaby/.ssh
barnaby@midsomer:~$ nano /home/barnaby/.ssh/authorized_keys
barnaby@midsomer:~$ mkdir .ssh
mkdir: cannot create directory `.ssh': File exists
barnaby@midsomer:~$ sudo /home/barnaby/.ssh/authorized_keys
sudo: unable to resolve host midsomer
[sudo] password for barnaby: 
barnaby is not in the sudoers file.  This incident will be reported.
barnaby@midsomer:~$ nano /home/barnaby/.ssh/authorized_keys

  GNU nano 2.2.6      File: /home/barnaby/.ssh/authorized_keys        Modified  

ssh rsa.....................$el8PvpvVyoQ8DR+Tw== [email]marcuswest@unknown-c8-bc-c8-c3-57-ad.home[/email]

     [ Error writing /home/barnaby/.ssh/authorized_keys: Not a directory ]

---

### Post by iclestu on 2011-06-02
> **marcusww said:**
> the ssh-copy-id command doesn't work


$ ssh-copy-id barnaby@178.79.157.220
-bash: ssh-copy-id: command not found


thats WIERD! :)

You using openssh???

---

### Post by marcusww on 2011-06-03
am using the terminal on my mac

---

### Post by sixcorners on 2011-06-03
Is the user account's home directory encrypted? If so your .ssh folder is not available to sshd.
You can fix it by either making it not encrypted or logging in as root while the directory is not mounted and add the .ssh/authorized_keys file in the home directory next to the Access-Your-Private-Data.desktop and README.txt files.

---

