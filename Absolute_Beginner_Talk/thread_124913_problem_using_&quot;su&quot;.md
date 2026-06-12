---
title: "problem using &quot;su&quot;"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Rorgy on 2006-02-02
ok when im trying to use 
su
when it asks for my password, i type it in and it says that verification failed..
ive tried everything.
and when i need to be a root to do other stuff like use the "add application tool" my root password works...i dont understand why "su" isn't working..what do i do

---

### Post by alamba on 2006-02-02
sudo passwd root
enter user passwd then new root pwd

---

### Post by Rorgy on 2006-02-02
i love you..thanks

that was like the only thing i didn't try....besides umm uknow 

ill stop talking now

---

### Post by Klaidas on 2006-02-02
MOre info about [sudo]("http://wiki.ubuntu.com/RootSudo")

---

### Post by deBaas on 2006-02-02
[QUOTE=Rorgy]ok when im trying to use 
su
when it asks for my password, i type it in and it says that verification failed..
ive tried everything.
and when i need to be a root to do other stuff like use the "add application tool" my root password works...i dont understand why "su" isn't working..what do i do[/QUOTE]
You clearly missed a bit of text while installing.

---

### Post by towsonu2003 on 2006-02-02
from [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) about enabling root account
> This is not recommended!
Now that you've got root enabled, you might wanna read the above link ;)

In brief, root account is by default disabled in Ubuntu for security reasons and users are encouraged to to use ```
sudo somerootcommand
``` instead. So if you wanted to run ifconfig with root privileges: ```
sudo ifconfig
```

Use gksudo instead of sudo for graphical programs. 

Don't use root privileges if you can do the same thing as yourself (e.g. don't browse web, don't use openoffice, don't do anything not related to configurations etc etc)... A small glitch in the program you use as root can trash your install (or if you mistype a command).

---

### Post by Rorgy on 2006-02-03
the only reason i wanna use SU
is because thats how i learned i learned to do most thing using su...for example

./configure
make
su
make isntall

---

### Post by hashimoto on 2006-02-03
[QUOTE=Rorgy]
./configure
make
su
make isntall[/QUOTE]

Well, with sudo it goes like:
```
 ./configure
make
sudo make install
```

---

### Post by steve.horsley on 2006-02-03
Actually, I'm not really happy with Ubuntu's use of sudo. It means that any old tosser who gets into my normal user account automatically has root access to the whole machine. At worst they have to change my password before they can become root. At best, the sudo timer is still running because I just used it, and they get root without having to enter a password at all.

Is there any way of fixing the GUI utilities so they ask for the root password instead? Then I can disable sudo and feel safer.

---

### Post by gravediggers on 2006-02-03
[QUOTE=steve.horsley]Is there any way of fixing the GUI utilities so they ask for the root password instead? Then I can disable sudo and feel safer.[/QUOTE]

You can edit /etc/sudoers (remember to use visudo to do this) and find the line that begins:
```
Defaults
```
and add the following line (subtitute in your own user name unless you want me to change thing on your box:)  )
```
Defaults:gravediggers   timestamp_timeout=-1,runaspw
```
the -1 means your pwd won't time out
runaspw will have it prompt for the root password instead of your own.

Word of caution though: if you have the root password enabled, there is only one thing for other people to guess. If you have it locked, they will also have to guess your username!

---

### Post by jonim8or on 2006-02-03
I have tried changing my SU password to something different than my normal user password, using the commandline:
su
passwd

But now when i want to change some settings with a gui (like synaptic package manager, or so), The new password is rejected and the old one is accepted, even after logging out and in.

How do I change my SU password so that I can use the same SU password for sudo, su and windowed password requests?

---

