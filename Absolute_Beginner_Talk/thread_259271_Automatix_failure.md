---
title: "Automatix failure"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-17
Can someone look at this and tell me what I done wrong it will not download:

toby@toby-desktop:~$ sudo gedit /etc/apt/sources.list
toby@toby-desktop:~$ wget [http://getautomatix.com/apt/key.gpg.asc](http://getautomatix.com/apt/key.gpg.asc)
--11:24:45--  [http://getautomatix.com/apt/key.gpg.asc](http://getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.2'
Resolving getautomatix.com... 82.165.194.143
Connecting to getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

11:24:45 (2.41 MB/s) - `key.gpg.asc.2' saved [1730/1730]

toby@toby-desktop:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
toby@toby-desktop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -sudo apt-get update
gpg: conflicting commands
toby@toby-desktop:~$ sudo apt-get install automatix
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
toby@toby-desktop:~$ automatix
bash: automatix: command not found

---

### Post by xyz on 2006-09-17
Did enable universe/multiverse repositories?

---

### Post by Tobster on 2006-09-17
I dont understand what you mean?:confused:

---

### Post by Tobster on 2006-09-17
I did the copy and paste thing on the other screen

---

### Post by missmoondog on 2006-09-17
isn't automatix obsolete now? it's not listed in the third party projects anymore. i know i remember reading something about that.
easyubuntu is the tool to use now.

---

### Post by xyz on 2006-09-17
> **Tobster said:**
> I dont understand what you mean?:confused:
When you open Synaptic > Settings > Repositories > Add...check the universe/multiverse boxes.

---

### Post by Tobster on 2006-09-17
Here a screen shot...

IF it out of date then I need to take it off. How do I do that?

---

### Post by xyz on 2006-09-17
Could you please post the output of:
```
 sudo gedit /etc/apt/sources.list

```

---

### Post by Tobster on 2006-09-17
Should I put that command in the Terminal....  :confused:

---

### Post by Tobster on 2006-09-17
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) [http://www.getautomatix.com/aptuniverse](http://www.getautomatix.com/aptuniverse) multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updateshttp://www.getautomatix.com/apt main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[http://www.getautomatix.com/apt](http://www.getautomatix.com/apt)

---

### Post by oyvindaa on 2006-09-17
> **missmoondog said:**
> isn't automatix obsolete now? it's not listed in the third party projects anymore. i know i remember reading something about that.
easyubuntu is the tool to use now.


Is it?

I've got two updates from automatix the last two days.

---

### Post by xyz on 2006-09-17
That's what I have in my sources.list about Automatix:
> #############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

How about starting all over?
```
sudo apt-get remove automatix
```
Go to Applications > Accessories > Terminal
and then try to reinstall again following precisely here:
[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

Let me know...

---

### Post by Tobster on 2006-09-17
Mate that not really helping :rolleyes: :rolleyes:

---

### Post by xyz on 2006-09-17
> **oyvindaa said:**
> Is it?

I've got two updates from automatix the last two days.
Me too and everything works fine. Did you have a problem with the recent Automatix updates?

---

### Post by Tobster on 2006-09-17
toby@toby-desktop:~$ [http://getautomatix.com/wiki/index.p...tion&Itemid=38](http://getautomatix.com/wiki/index.p...tion&Itemid=38)
[1] 9047
toby@toby-desktop:~$ bash: [http://getautomatix.com/wiki/index.p...tion:](http://getautomatix.com/wiki/index.p...tion:) No such file or directory

---

### Post by oyvindaa on 2006-09-17
> **xyz said:**
> Me too and everything works fine. Did you have a problem with the recent Automatix updates?

Not at all.

---

### Post by Tobster on 2006-09-17
This is what i got so far:

toby@toby-desktop:~$ wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
--12:10:00--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
           => `automatix-installer'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,256 (9.0K) [text/plain]

100%[====================================>] 9,256         --.--K/s

12:10:00 (178.39 KB/s) - `automatix-installer' saved [9256/9256]

toby@toby-desktop:~$ chmod 755 ~/automatix-installer
toby@toby-desktop:~$ ./automatix-installer
Password:
--12:11:27--  [http://www.getautomatix.com/keys/automatix.key](http://www.getautomatix.com/keys/automatix.key)
           => `automatix.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

12:11:27 (5.03 MB/s) - `automatix.key' saved [1730/1730]

gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK
pub   1024D/437D05B5 2004-09-12
Codename:       dapper
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
toby@toby-desktop:~$ sudo gedit /etc/apt/sources.list
toby@toby-desktop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--12:14:33--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.3'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

12:14:34 (103.12 MB/s) - `key.gpg.asc.3' saved [1730/1730]

toby@toby-desktop:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
toby@toby-desktop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
toby@toby-desktop:~$ sudo apt-get update
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
toby@toby-desktop:~$ sudo apt-get install automati

---

### Post by Tobster on 2006-09-17
Now what should i do :)

---

### Post by Tobster on 2006-09-17
toby@toby-desktop:~$ wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
--12:10:00--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
           => `automatix-installer'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,256 (9.0K) [text/plain]

100%[====================================>] 9,256         --.--K/s

12:10:00 (178.39 KB/s) - `automatix-installer' saved [9256/9256]

toby@toby-desktop:~$ chmod 755 ~/automatix-installer
toby@toby-desktop:~$ ./automatix-installer
Password:
--12:11:27--  [http://www.getautomatix.com/keys/automatix.key](http://www.getautomatix.com/keys/automatix.key)
           => `automatix.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

12:11:27 (5.03 MB/s) - `automatix.key' saved [1730/1730]

gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK
pub   1024D/437D05B5 2004-09-12
Codename:       dapper
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
toby@toby-desktop:~$ sudo gedit /etc/apt/sources.list
toby@toby-desktop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--12:14:33--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.3'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

12:14:34 (103.12 MB/s) - `key.gpg.asc.3' saved [1730/1730]

toby@toby-desktop:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
toby@toby-desktop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
toby@toby-desktop:~$ sudo apt-get update
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
toby@toby-desktop:~$ sudo apt-get update
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
toby@toby-desktop:~$ sudo apt-get install automatix
E: Type ‘[http://www.getautomatix.com/apt’](http://www.getautomatix.com/apt’) is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
toby@toby-desktop:~$
toby@toby-desktop:~$
toby@toby-desktop:~$

---

### Post by xyz on 2006-09-17
Do you have this line
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
at the end of your sources.list file?
We'll get there somehow...

---

### Post by Kilz on 2006-09-17
> **missmoondog said:**
> isn't automatix obsolete now? it's not listed in the third party projects anymore. i know i remember reading something about that.
easyubuntu is the tool to use now.

The reason the forum isnt here is  Arnieboy got mad and [had the forum here closed. ]("http://www.ubuntuforums.org/showthread.php?t=237901"). I guess he wanted to take all his toys home. Support anyone you want.

---

### Post by Tobster on 2006-09-17
So that the reason.... I need to do the whole lot again but I need to get off the computer or else I be on it all day so I do will have enough crack at it later thanks

Toby

---

### Post by Tobster on 2006-09-17
The thing is it suck now in my Snypatic Package manager so if it out of date i need to get rid of it so how do i do that?

---

### Post by catlett on 2006-09-17
This is your problem
```
http://www.getautomatix.com/apt
```
You entered the automatix line in your source list wrong. Enter ```
sudo gedit /etc/apt/sources.list
```
At the bottom change that line 
```
http://www.getautomatix.com/apt
```
To this 
```
deb http://www.getautomatix.com/apt
```
Save the file and run```
 sudo apt-get update
```Then run the command to install automatix.

P.S. In case you have more issues [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_6.06_Dapper_Drake](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_6.06_Dapper_Drake)

---

### Post by szekelyrobi on 2006-09-17
Try this in Terminal, this is an automatic installer of automatix:

wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer

---

### Post by arnieboy on 2006-09-17
the line to be added to sources.list is the following:
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
if you are using Dapper. The original poster only entered the hyperlink. That was causing the errors.

---

### Post by picpak on 2006-09-17
Since you seem to be having trouble editing your sources.list, try running

```
sudo sh -c "echo 'deb http://www.getautomatix.com/apt dapper main' >> /etc/apt/sources.list"
```

in the terminal. It will automatically add it in.

Then run:

```
sudo apt-get update
```

---

### Post by szekelyrobi on 2008-02-10
Thank you. I ve just stopped using it, I might look into that again.)

---

### Post by PmDematagoda on 2008-02-10
This thread is rather old, so what is mentioned here may not apply to the current applications or methods.

The thread is closed.

---

