---
title: "Error With Add/Remove Programs"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by bryansworld on 2008-01-14
So I recently connected my computer to the internet and decided to install some cool programs for my favourite operating system. When I clicked to add a program to the download box a message would come up saying "Cannot Install Program at this time" then it would refresh the list. After that I tried again with the same answer. I tried everything!!!! What do I do guys???????

---

### Post by SOULRiDER on 2008-01-14
Open a terminal and type
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Post any errors you come accross. If there are no errors at all that will update your system and I dont see a reason why you cant install anything. If theres an error somewhere preventing you to install the programs you want, youll see it ina  temrinal when you type those two commands.

---

### Post by Khalis7 on 2008-01-15
Hello guys..

I'm facing a problem, almost similar to Bryansworld but mine is a bit different. Whenever I would like to add new program from Add/Remove, it just couldn't download. I clicked in the program I wanted and then the add/remove will ask me to click refresh button to reload the Internet connection, then it would show downloading some files but it was way too fast for me to see what the files were. After that, it terminates itself without installing the program I wanted. For me this is strange although I'm connected to the Internet...and it's even more peculiar because this the first time happened to me ever since I have been an Ubuntu user.

Any ideas guys??

---

### Post by SOULRiDER on 2008-01-15
Post the output of those two commands and lets see whats wrong. Its possible that a program was left unconfigured so you cant install enw ones, but the GUI won't tell you that, only trying to install froma  temrinal will.

Paste the output of those commands using the **[CODE]** tags please.

---

### Post by SergeantScar on 2008-01-20
> **Khalis7 said:**
> Hello guys..

I'm facing a problem, almost similar to Bryansworld but mine is a bit different. Whenever I would like to add new program from Add/Remove, it just couldn't download. I clicked in the program I wanted and then the add/remove will ask me to click refresh button to reload the Internet connection, then it would show downloading some files but it was way too fast for me to see what the files were. After that, it terminates itself without installing the program I wanted. For me this is strange although I'm connected to the Internet...and it's even more peculiar because this the first time happened to me ever since I have been an Ubuntu user.

Any ideas guys??

I am having the same problem i think.

---

### Post by forestpixie on 2008-01-20
what is the output of this 

```
sudo apt-get update
```

---

### Post by Eberulf on 2008-01-20
I have the same problem. It could relate to when I tried to install the build-essential package.  It looked for the CDROM and could not find it, although I do have the install CDROM in the drive.

------------------------------
jane@jane-desktop:~$ sudo apt-get update
[sudo] password for jane:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
jane@jane-desktop:~$

---

### Post by SOULRiDER on 2008-01-27
> **Eberulf said:**
> I have the same problem. It could relate to when I tried to install the build-essential package.  It looked for the CDROM and could not find it, although I do have the install CDROM in the drive.


Check out the last post in [http://ubuntuforums.org/showthread.php?t=674877](http://ubuntuforums.org/showthread.php?t=674877)

---

### Post by ajmorris on 2008-01-29
hi,
could you both upload your /etc/apt/sources.list files.
The name of the mirror you are using
and have you tried using sudo apt-get install <package> in the terminal, or synaptic, as opposed to using the Add/remove option?

---

### Post by Oldsoldier2003 on 2008-03-30
> **Eberulf said:**
> I have the same problem. It could relate to when I tried to install the build-essential package.  It looked for the CDROM and could not find it, although I do have the install CDROM in the drive.

------------------------------
jane@jane-desktop:~$ sudo apt-get update
[sudo] password for jane:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
jane@jane-desktop:~$

edit your sources list and comment out the cd.
```
 sudo nano /etc/apt/sources.list
```
Then
```
sudo apt-get update
sudo apt-get upgrade
```

---

