---
title: "Can't Install anything... and a Strange Message"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by milagre23 on 2006-10-12
Can't install anything using synaptic, GDebi or console. I have a lot of updates pending but, every time I try to install whatever I get this strange message:


"E: /var/cache/apt/archives/libclamav1_0.88.4-1ubuntu1~dapper1_i386.deb: files list file for package `gtk2-engines-mist' is missing final newline"

Can anyone help me?

Thanks for your attention.

Best regards.

---

### Post by randell6564 on 2006-10-12
> **milagre23 said:**
> Can't install anything using synaptic, GDebi or console. I have a lot of updates pending but, every time I try to install whatever I get this strange message:


"E: /var/cache/apt/archives/libclamav1_0.88.4-1ubuntu1~dapper1_i386.deb: files list file for package `gtk2-engines-mist' is missing final newline"

Can anyone help me?

Thanks for your attention.

Best regards.
Hey!  UN-install 'clamav' and then try and update again!  Let us know the result. Un-install it COMPLETELY!

If that does not work, then please post your **/etc/apt/sources.list**

---

### Post by milagre23 on 2006-10-13
> **randell6564 said:**
> Hey!  UN-install 'clamav' and then try and update again!  Let us know the result. Un-install it COMPLETELY!

If that does not work, then please post your **/etc/apt/sources.list**


I Can't uninstall "clamav" because can't complete the process and this message appears:

"E: clamtk: files list file for package `gtk2-engines-mist' is missing final newline"

And, how should I do to post my source list?

Thanks very much for your attention.

---

### Post by Khaotik on 2006-10-13
> **milagre23 said:**
> I Can't uninstall "clamav" because can't complete the process and this message appears:

"E: clamtk: files list file for package `gtk2-engines-mist' is missing final newline"

And, how should I do to post my source list?

Thanks very much for your attention.
Your Sources list is a file in /etc/apt/. The name of the file is sources.list

To display them do the following - 

gedit /etc/apt/sources.list

Just hold CTR and press A to highlight everything and CTR+C to copy.
Then CTR+V to paste it in the forums.

--Using the above command you can view the file without worrying about changing anything cause you arent sudo'd.

---

### Post by milagre23 on 2006-10-13
> **Khaotik said:**
> Your Sources list is a file in /etc/apt/. The name of the file is sources.list

To display them do the following - 

gedit /etc/apt/sources.list

Just hold CTR and press A to highlight everything and CTR+C to copy.
Then CTR+V to paste it in the forums.

--Using the above command you can view the file without worrying about changing anything cause you arent sudo'd.

Thanks Kahotik

Here is my sources list:

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by milagre23 on 2006-10-13
How can it be possible that an antivirus (clamav) can bloc all my system? I just install it because it appear on one of the automatic updates.

Can anyone help me. I cant install or uninstall for more then a week.

Thanks for your attention.

---

### Post by milagre23 on 2006-10-14
Since I install "clamav" in one of the automatic updates, I can't install or unistall anything else else on my computer. And I always get a message saying that there are to many problems and always finish with this line:

"`gtk2-engines-mist' is missing final newline"

I'm not really sure about the relation between "clamav" and this problem. The only thing I know is that I'm blocked for about two weeks and can't find a way out.  ](*,) 
Can anyone help me please?

---

### Post by milagre23 on 2006-10-15
My system is completed bocked to installation or upgrading (and can't even uninstall) and I can't get help.
I've tried in the General Help section and in the Installation & Upgrades section and I still can't get help.

I use UBUNTU for almost two years now but I'm just a very basic user (got much more interested with the change to Linux, specially to UBUNTU). So I'm always a beginner. So I'm going to do a last try in this section.

The problem:

I can't install, or unistall by any means and I always get a "to many problems message" and depict all the variations I always get this line:

"files list file for package `gtk2-engines-mist' is missing final newline"

Does anyone have clue? Can anyone, please, help me?

Thanks for your attention

---

### Post by capn_hector on 2006-10-15
well to uninstall is easy (if you dont want to save any thing)  start up the live cd and do a mkfs to your hard drive (format the drive)  as far as the error goes, you might try reinstaling the package that gives the error.  but the good news is that if you do have to start over you learn more every time you set up ubuntu.

---

### Post by Abstract on 2006-10-15
> **capn_hector said:**
> well to uninstall is easy (if you dont want to save any thing)  start up the live cd and do a mkfs to your hard drive (format the drive)  as far as the error goes, you might try reinstaling the package that gives the error.  but the good news is that if you do have to start over you learn more every time you set up ubuntu.

I think he means apt-get.

Anyway, try this:

```
sudo apt-get install -f
```

---

### Post by milagre23 on 2006-10-15
> **capn_hector said:**
> well to uninstall is easy (if you dont want to save any thing)  start up the live cd and do a mkfs to your hard drive (format the drive)  as far as the error goes, you might try reinstaling the package that gives the error.  but the good news is that if you do have to start over you learn more every time you set up ubuntu.

I'm not quite sure if I understood your answer. Are you suggesting that the better thing to do is re-install all the system?

---

### Post by milagre23 on 2006-10-15
> **capn_hector said:**
> well to uninstall is easy (if you dont want to save any thing)  start up the live cd and do a mkfs to your hard drive (format the drive)  as far as the error goes, you might try reinstaling the package that gives the error.  but the good news is that if you do have to start over you learn more every time you set up ubuntu.

> **Abstract said:**
> I think he means apt-get.

Anyway, try this:

```
sudo apt-get install -f
```

Thanks Abstract. 
I've tried that already and it simply doesn't work.

---

### Post by John.Michael.Kane on 2006-10-15
Have you tried 
sudo aptitude update
sudo aptitude remove -f (name of program) 
sudo aptitude install gtk2-engines-mist

---

### Post by capn_hector on 2006-10-15
> **milagre23 said:**
> I'm not quite sure if I understood your answer. Are you suggesting that the better thing to do is re-install all the system?

i misunderstood your question.  now that your question is about apt-get then no you do not need to reinstall your system.

---

### Post by milagre23 on 2006-10-15
> **SD-Plissken said:**
> Have you tried 
sudo aptitude update
sudo aptitude remove -f (name of program) 
sudo aptitude install gtk2-engines-mist


I allways get error messages...

---

### Post by capn_hector on 2006-10-15
can you post the exact error messages??

---

### Post by milagre23 on 2006-10-15
> **capn_hector said:**
> can you post the exact error messages??

Yes I could but, unfortunately they are in Portuguese:

milagre23@milagre23-desktop:~$ sudo aptitude update
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
A ler informações extendidas de estado
A inicializar os estados dos pacotes... Erro !
E: Impossível o parse ao ficheiro de pacote /var/lib/aptitude/pkgstates (1)
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
A ler informações extendidas de estado
A inicializar os estados dos pacotes... Erro !
E: Impossível o parse ao ficheiro de pacote /var/lib/aptitude/pkgstates (1)
milagre23@milagre23-desktop:~$

---

### Post by milagre23 on 2006-10-15
Is it possible to change the console to english easily?

---

### Post by dmizer on 2006-10-15
yes ... when you log in at the gdm, just choose english as your language before you log in.  then everything will be in english.

this change will not be perminant.

---

### Post by aysiu on 2006-10-15
I've merged the threads, since they seem to be the same problem.

By the way, this is what Google's language tools did with the output--not sure if it helps: ```
milagre23@milagre23-desktop: ~$ sudo ability update  Ler It list of Packages… Soon  Constructing Tree of Dependences… Soon  To read extendidas information of state  To inicializar the states of the packages… Error!  E: Impossible parse to the filing-cabinet of /var/lib/aptitude/pkgstates package (1) To read Lists of Packages… Soon  Constructing Tree of Dependences… Soon  To read extendidas information of state  To inicializar the states of the packages… Error!  E: Impossible parse to the filing-cabinet of /var/lib/aptitude/pkgstates package (1) milagre23@milagre23-desktop: ~$  Edit/Delete Message 
```

---

### Post by misha680 on 2006-10-16
Just a random stab in the dark, how about:

```
sudo aptitude reinstall gtk2-engines-mist
```

Misha

---

### Post by milagre23 on 2006-10-16
> **aysiu said:**
> I've merged the threads, since they seem to be the same problem.

By the way, this is what Google's language tools did with the output--not sure if it helps: ```
milagre23@milagre23-desktop: ~$ sudo ability update  Ler It list of Packages… Soon  Constructing Tree of Dependences… Soon  To read extendidas information of state  To inicializar the states of the packages… Error!  E: Impossible parse to the filing-cabinet of /var/lib/aptitude/pkgstates package (1) To read Lists of Packages… Soon  Constructing Tree of Dependences… Soon  To read extendidas information of state  To inicializar the states of the packages… Error!  E: Impossible parse to the filing-cabinet of /var/lib/aptitude/pkgstates package (1) milagre23@milagre23-desktop: ~$  Edit/Delete Message 
```

I know its the same subject but I have a very serious problem in my system and I'm just a very basic computer user (that changed to Ubuntu for political reasons) and very dependent of the help of others and, as you know, some subjects just die in the forum so I was just trying to get someones attention.

---

### Post by milagre23 on 2006-10-16
> **misha680 said:**
> Just a random stab in the dark, how about:

```
sudo aptitude reinstall gtk2-engines-mist
```

Misha

Thanks Misha.

I've tryed your advice but I get a this error message:

E: Impossible to parse the file of the package /var/lib/aptitude/pkgstates (1)
milagre23@milagre23-desktop:~$

---

### Post by podunk on 2006-10-16
Have you used your file browser to go tot hat directory and see if the file is there?
The file browser is under "Places" at the top of the screen.

When I go to 
/var/lib/aptitude/pkgstates

I find a file that is 1.7 megabytes. I opened the file with gedit

```
gedit /var/lib/aptitude/pkgstates
```

and found a bunch of stuff related to clamav. 1 example of what is in the file is:
```

Package: clamav
Unseen: no
State: 1
Dselect-State: 1
Last-Change: 0
Remove-Reason: 0

```

Also in the same directory is pagstates.old which is a backup file from the last time I updated.

Do you have a backup file in that folder? Is the date from before the problem started? If it is why don't you save the present file and restore the backup copy?

---

### Post by milagre23 on 2006-10-17
> **podunk said:**
> Have you used your file browser to go tot hat directory and see if the file is there?
The file browser is under "Places" at the top of the screen.

When I go to 
/var/lib/aptitude/pkgstates

I find a file that is 1.7 megabytes. I opened the file with gedit

```
gedit /var/lib/aptitude/pkgstates
```

and found a bunch of stuff related to clamav. 1 example of what is in the file is:
```

Package: clamav
Unseen: no
State: 1
Dselect-State: 1
Last-Change: 0
Remove-Reason: 0

```

Also in the same directory is pagstates.old which is a backup file from the last time I updated.

Do you have a backup file in that folder? Is the date from before the problem started? If it is why don't you save the present file and restore the backup copy?


Thanks for your attention.

First I try to open with gedit and couldn't and gave-me a error messagem saying that didn't recognize the characters of the file.

But I did open it with openoffice.

And, in this directory, there is no pkgstates.old only pkgstates and a file  named lock (wich is really locked).

---

