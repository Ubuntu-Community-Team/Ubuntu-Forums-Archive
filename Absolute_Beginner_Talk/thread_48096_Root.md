---
title: "Root"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-11
Hello,

I've just installed Ubuntu for the first time. (i previously used SuSE)
It feels very warm and cozy in this new environment. 

Installation went smooth enough, but i got a bit stuck at the end about updating and downloading. It seemed like a problem, i'm an absolute beginner so i hope i'm in the right place now, but i managed to circumvent all that and here i am discovering my new 'world'

In the final stages of set-up i was asked a username and password and i just went through the motions. However, i don't remember being asked to setup a superuser password??!

Or i forgot but sure enough i haven't got one at hand when asked for example when i went into console. 
I hope this can be rectified and that it doesn't mean i have to reinstall the os all over again,

Any true advice and knowledge in this regard much appreciated,

regards,

sophtpaw

---

### Post by Leif on 2005-07-11
[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

---

### Post by frodon on 2005-07-11
Generally the root password is the same than your user password. What's happened when you type in a terminal : ```
sudo su
```Maybe you can find here interesting informations : [http://ubuntuforums.org/showthread.php?t=46532](http://ubuntuforums.org/showthread.php?t=46532)

---

### Post by sophtpaw on 2005-07-11
Thanks for the brew people,

In fact i seem to have made some progress. What i thought was my su password still is in fact. But in SuSE i'm used to just putting in 'su' in the console, to which i got back, wrong password or authentication, or words to that effect, which threw me. 
Is this more complicated in Ubuntu for a reason?
Anyways, typed in something with sudo and that has now worked
I've just discovered synaptic and in the process of updating and patching (i hope) with the hope of being able to install Thunderbird.

many thanks, and any other advice to a newbie welcome,

regards,

conrad

---

### Post by Leif on 2005-07-11
The best advice I can give is that ubuntuguide.org is your friend

---

### Post by sophtpaw on 2005-07-11
Salut Froddon,

By the way i thought the whole point of the su password is that it is different from the user password, both for safety reasons and as to enable the root user 'root' priviledges?!

I'm sure that is a universal principle found in all Linux distros

qu'est-ce- que tu pense?

ciao

sophtpaw

---

### Post by Leif on 2005-07-11
The reasons for using sudo over su are given in the first link I posted. There are also dozens of threads arguing the points, just search for sudo in the title.

---

### Post by sophtpaw on 2005-07-11
Leif,

Thank you for kind advice. I will follow-up your advice and befriend ubuntuguide and the other link you shared with me,

i hope to bump into you again 

cordially,

sophtpaw

---

### Post by Leif on 2005-07-11
No problem ! I hope you have a great time using Ubuntu, and the forums.

---

### Post by frodon on 2005-07-11
[QUOTE=sophtpaw]Salut Froddon,

By the way i thought the whole point of the su password is that it is different from the user password, both for safety reasons and as to enable the root user 'root' priviledges?!

I'm sure that is a universal principle found in all Linux distros

qu'est-ce- que tu pense?

ciao

sophtpaw[/QUOTE]
 Yes, the first time it's a little bit strange to use sudo su instead of su but it's the ubuntu behaciour. You don't have root account in ubuntu, that's why all is based on sudo. It's an other way to secure root operations ... why not.

mais oui c est vrai que ca fait drole au debut de ne pas avoir de compte root, mais le fait de ne pas en avoir et d utiliser sudo est une autre maniere de rendre la chose securisee.

---

### Post by sophtpaw on 2005-07-11
[QUOTE=frodon]Yes, the first time it's a little bit strange to use sudo su instead of su but it's the ubuntu behaciour. You don't have root account in ubuntu, that's why all is based on sudo. It's an other way to secure root operations ... why not.

mais oui c est vrai que ca fait drole au debut de ne pas avoir de compte root, mais le fait de ne pas en avoir et d utiliser sudo est une autre maniere de rendre la chose securisee.[/QUOTE]


Bravo Frodon,

Merci pour avoir m'assurer et pour l'aide aussi,

sophtpaw

---

### Post by roots on 2005-07-11
hi...!

the root confusion goes on..at least for me it does.

the password i provided when installing ubuntu now seems to be the superuser password. however, what i did after installation was opening a console and (as in suse...) typing "su -". this worked (as i remember) without providing a password. after that the shell prompt showed "root@..."
i was a bit confused and set a password using the "passwd" command.
now what happens is, when i'm changing from standard user to user root via "su -" i have to enter the new password, if i switch via "sudo su" i have to use the one i provided during installation.

I AM REALLY CONFUSED, so...can anyone explain to me the ubuntu difference between root and root?  :-? 

cheers,
.roots

---

