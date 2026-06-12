---
title: "can't install bitchx"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by imsmark on 2007-04-04
Im new at ubuntu, and linux. im looking for an easy way to install packages from the web. i downloaded the server edition. now when it comes to install a program like bitchx. im running into trouble. can someone give me a step to step idea on how to continue using this OS on retaining packages.

---

### Post by Skrynesaver on 2007-04-04
Ubuntu uses Debian's  Advance Package Tool, don't dowload from the web use apt and things will stay working ;)
There are two main routes, the terminal, faster but involves scary typing stuff and Synaptic, couldn't be easier.
to use synaptic, 
Panel->System->Administration->Synaptic.
Enter your password
click on search on the toolbar
search for bitchx
mark for instalation
Click on apply on the toolbar.
Done.
Or the scary terminal way,
```

apt-cache search bitchx

```
returns the following:

bitchx - Advanced Internet Relay Chat client
bitchx-dev - Header files for BitchX
bitchx-gtk - GTK interface for BitchX
bitchx-ssl - SSL support for BitchX
pork - Console-based AOL Instant Messenger & IRC client

Those are the packages that mention bitchx we probably want the first one so
```
sudo apt-get install bitchx
```

---

### Post by imsmark on 2007-04-04
im on a server.. only a terminal. the 

root@shellweb:~# apt-cache search bitchx
root@shellweb:~#

does not work, also ...

root@shellweb:~# sudo apt-get install bitchx
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bitchx
root@shellweb:~#

---

### Post by ThrobbingBrain66 on 2007-04-04
you have to add universe to your repo list to get bitchx

---

### Post by imsmark on 2007-04-04
so how do i go about that?

---

### Post by Maestro23 on 2007-04-04
> **imsmark said:**
> so how do i go about that?

Managing Repositories: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Server Guide link: [https://help.ubuntu.com/6.10/](https://help.ubuntu.com/6.10/)

---

### Post by george29 on 2007-04-04
you need to edit your sources list.

so 

```
cd /etc/apt 
```

then 

```
ls
```

should list all the files you should see one called sources.list 
make a back up with


```
sudo cp sources.list sources.list_backup
```

then open it to edit with 


```
sudo nano sources.lst
```

uncomment multiverse and universe - remove # symbols in appropriate places.

save and exit by pressing [ctrl + X]

answer yes to the question about saving the file.

then 

```
sudo apt-get update
sudo apt-get install bitchx

```

or alternatively use aptitude

```
sudo aptitude
```

press u to reload repositories

then / to search for bitchx

and g to download and install.

? gives you the help page.

q to quit

---

### Post by imsmark on 2007-04-04
thanks ... its werking now

---

### Post by Zodi on 2007-05-22
I downloaded and installed BitchX but it is not in my applications.  What am I doing wrong?

---

### Post by AntonioCS on 2007-05-24
I followed the same thing and I don't know were bitchx is either :(

---

### Post by feylya on 2007-06-04
It won't show up. You need to run bitchx from a terminal ;)

---

