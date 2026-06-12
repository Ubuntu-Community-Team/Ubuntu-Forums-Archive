---
title: "How to install Bonfire on Dapper"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by WaterWalker on 2006-06-01
I've just donwloaded the bz2(cause there wasn't a deb) from bonfire.
I've heard you install this with
./configure
make
install

./configure went fine but when I type make, I get the following:
didn't found a target or makefile.
What did I do wrong do I have to type make «some file» or something?
Plz healp me. Thanks.

---

### Post by Jagot on 2006-06-01
You may need to install compilers if you have not done so already:

```
sudo aptitude install build-essential
```

Read this:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Dr. Nick on 2006-06-01
Look here
[http://ubuntuforums.org/showthread.php?t=175536]("http://ubuntuforums.org/showthread.php?t=175536")

Toward the end of that thread their are links to a deb one of the forum members made with the newest bonfire for dapper. Look at pages 6-7 if you dont want to read it all :)

---

### Post by rjcsc on 2006-06-29
Anyone has a .deb for the new 0.3.90 version?

Thanks

---

### Post by it.henrik on 2006-06-29
I made this with checkinstall .. enjoy

[http://rapidshare.de/files/24456661/bonfire-0.3.90_0.3.90-1_i386.deb.html](http://rapidshare.de/files/24456661/bonfire-0.3.90_0.3.90-1_i386.deb.html)

---

### Post by ketsugi on 2006-06-30
[QUOTE=it.henrik]I made this with checkinstall .. enjoy

[http://rapidshare.de/files/24456661/bonfire-0.3.90_0.3.90-1_i386.deb.html](http://rapidshare.de/files/24456661/bonfire-0.3.90_0.3.90-1_i386.deb.html)[/QUOTE]
I've updated my repo to 0.3.90.

Instructions [here](http://ubuntuforums.org/showpost.php?p=1015464)

---

### Post by lazyd2 on 2006-06-30
[quote=ketsugi]I've updated my repo to 0.3.90.

Instructions [here]("http://ubuntuforums.org/showpost.php?p=1015464")[/quote]Thanks!

---

### Post by keith whitehouse on 2006-06-30
hi ketsugi,

I have just installed the new version of Bonfire, and it does not open.

In "Terminal" I have

keith@ubuntu:~$ bonfire
bonfire: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory
keith@ubuntu:~$

any advice please

best regards keith

---

### Post by emix on 2006-07-01
[QUOTE=keith whitehouse]keith@ubuntu:~$ bonfire
bonfire: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory[/QUOTE]
I've the same problem.

**Edit**: solved installing libglitz1 (it should be installed automatically as a dependency), but there are other problems:
```
emix@desktop:~$ bonfire

** (bonfire:6692): WARNING **: icon /usr/local/share/bonfire/icon-final-48x48.png can't be loaded


(bonfire:6692): Gtk-WARNING **: Error loading icon from file '/usr/local/share/bonfire/icon-final-48x48.png':
        Apertura del file «/usr/local/share/bonfire/icon-final-48x48.png» fallita: Nessun file o directory

** (bonfire:6692): WARNING **: ERROR loading background pix : Apertura del file «/usr/local/share/bonfire/logo.png» fallita: Nessun file o directory
```

Icons are in /usr/share/bonfire and not in /usr/local/share/bonfire.

---

### Post by ketsugi on 2006-07-01
Hey guys, sorry for the errors in my deb. I've uploaded a corrected version which should rectify those problems.

Just update your sources and upgrade.

---

### Post by emix on 2006-07-01
Your package requires libglitz1 (>= 0.5.6-0ubuntu1), but the version in dapper repositories is 0.5.3-0ubuntu2:
```
emix@desktop:~$ sudo aptitude install bonfire
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
Lettura delle informazioni sullo stato esteso
Inizializzazione dello stato dei pacchetti... Fatto
Building tag database... Fatto
I seguenti pacchetti sono DIFETTOSI:
  bonfire
I seguenti pacchetti NUOVI (NEW) saranno automaticamente installati:
  cdda2wav
I seguenti pacchetti NUOVI (NEW) saranno installati:
  cdda2wav
0 pacchetti aggiornati, 2 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prelevare 471kB/624kB di archivi. Dopo l'estrazione, verranno occupati 1271kB.
I seguenti pacchetti hanno dipendenze non soddisfatte:
  bonfire: Dipende: libglitz1 (>= 0.5.6-0ubuntu1) ma non è installabile
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
bonfire [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?]
```

---

### Post by ketsugi on 2006-07-01
Crud, sorry, I should've checked that. I have newer libraries from the Xgl/Compiz repos.

I've changed the version number again. It's hard for me to figure out these errors cause all the debs I've produced so far have installed fine on my system (naturally) and I don't have any other system to test it out on.

---

### Post by keith whitehouse on 2006-07-01
hi ketsugi,

that works for me

thank you for your time and effort

best regards keith

---

### Post by ketsugi on 2006-07-09
Updated to 0.3.91 (worksforme).

---

### Post by 1c3d0g on 2006-07-10
Thank you, Ketsugi, for the updated packages. It's much appreciated. :-D

---

### Post by 1c3d0g on 2006-07-13
Hmm...looks like v.0.4.0 has been released...any .deb packages on the way? ;)

---

### Post by INMCM on 2006-07-14
Ketsugi, could you sign your repo with a GPG key?


(0.4.0 would be awesome as well)

---

### Post by ketsugi on 2006-07-14
I've been trying my darndest to get signing to work, but no go. >:(

If anyone would like to help me with this I'd be very appreciative.

Contact me via email.

---

### Post by ketsugi on 2006-07-14
By the way, bonfire 0.4.0 is up on the repo.

---

### Post by lazyd2 on 2006-07-14
> **ketsugi said:**
> By the way, bonfire 0.4.0 is up on the repo.
Great, thanks;)

---

### Post by s6dalane on 2006-07-14
Bonfire 0.4.1 is out! Hopefully your repository will be updated soon :).

---

### Post by ketsugi on 2006-07-15
/me shakes a fist at rouquier for releasing so quickly

Bonfire 0.4.1 is up ;p

---

### Post by 1c3d0g on 2006-07-15
Hehe...thanks Ketsugi. :cool:

---

### Post by keith whitehouse on 2006-07-15
hi ketsugi,

I will second that, thank you very much

best regards keith

---

### Post by PingunZ on 2006-07-15
I quickly made a .deb from the newest version of the official site
view attached ;)

Grtz PingunZ

---

### Post by paridoth on 2006-07-18
after its installed how do you run it? i tried "bonfire" in terminal but no good, and i dont see any menu entries

---

### Post by ketsugi on 2006-07-18
Applications > Sound & Video > Disc Burning Application

---

### Post by paridoth on 2006-07-18
> **ketsugi said:**
> Applications > Sound & Video > Disc Burning Application

its not there =(

[[IMG]http://img208.imageshack.us/img208/9766/screenshotae1.th.png[/IMG]](http://img208.imageshack.us/img208/9766/screenshotae1.png)

can someone tell me what the command is in there menu entries so i can try to run it from the shell and create my own enty? thanks

---

