---
title: "Please help - package information problem"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by truet on 2007-08-11
**So I had to reinstall ubuntu (i installed it first time yesterday and messed it up so formated and started again). When i go to update manager the following error message shows...**

[I]"Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"[/I]

**So i was told to do the following by a friend, but then the error message you see below shows. (ive included the whole log) from terminal.**

[I]jonathan@Lalita:~$ sudo dpkg --configure -a
Password:
jonathan@Lalita:~$ sudo dpkg --configure -a
jonathan@Lalita:~$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
jonathan@Lalita:~$ 
jonathan@Lalita:~$ [/I]

**Any help atall is most apretiated. Thank you so much!**

---

### Post by RomeReactor on 2007-08-11
Hi. Did you copy and paste the error messages? The name of the offending file **should not** have a space in its name:
> E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_**di sts**_feisty_universe_binary-i386_Packages
see the space in "di sts"? It should read:
> gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
I can't guarantee that this will work, and I **strongly** suggest you wait for someone more experienced to answer you; however, if no-one does, you could try renaming the file:
```
sudo mv /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_di\ sts_feisty_universe_binary-i386_Packages /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
```

---

### Post by truet on 2007-08-11
**Thank you so much for the reply. Yeah i copy and pasted it. Since then ive gone into synaptic package manager and it came up with an error, the error is below. **

[I]An error occured

The following details are provided:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/I]
[B]
Any suggestions? its related isnt it?[/B]

---

### Post by RomeReactor on 2007-08-11
Did you run the command I posted? if so, run an update of the repositories:
```
sudo apt-get update
```
if that doesn't get rid of the error, then perhaps you should run the **sudo dpkg --configure -a** command:
```
sudo dpkg --configure -a
```
and then
```
sudo apt-get install -f
```
Just remember that what I posted before is to be a last resort option in case no-one else provides you with a better solution.

EDIT: Please post the output of the following command:
```
ls /var/lib/apt/lists
```

---

### Post by kronk on 2007-08-11
Well I'm no guru either but I am bopping away to "Together in Electric Dreams" so that's gotta be a bad sign ;)

Have you tried re running your dpkg to reset your sources ?

Possibly a stoopid question but is there any major problem with starting again with a new installation ? Or is this a direct result of your new install ?

EDIT: Opps soz check out RomeReactors advice above :)

---

### Post by truet on 2007-08-11
**the origonal command u told me to do comes up with this error-**

*mv: cannot stat `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_di sts_feisty_universe_binary-i386_Packages': No such file or directory*

**The second one comes up with **

[I]jonathan@Lalita:~$ sudo dpkg --configure -a
jonathan@Lalita:~$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/I]

**The third bit of code comes up with**

[I]jonathan@Lalita:~$ ls /var/lib/apt/lists
gb.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
gb.archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources
gb.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages
gb.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_source_Sources
gb.archive.ubuntu.com_ubuntu_dists_feisty_Release
gb.archive.ubuntu.com_ubuntu_dists_feisty_Release.gpg
gb.archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages
gb.archive.ubuntu.com_ubuntu_dists_feisty_restricted_source_Sources
gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_source_Sources
gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages
gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_source_Sources
gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_Release
gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_Release.gpg
gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_binary-i386_Packages
gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_source_Sources
lock
partial
security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_feisty-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_feisty-security_Release
security.ubuntu.com_ubuntu_dists_feisty-security_Release.gpg
security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_feisty-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_feisty-security_universe_source_Sources[/I]

Sorry im a total novice, no idea what that means. Hope you do.

---

### Post by truet on 2007-08-11
dpkg? No idea what that is (sorry im really dumb)

---

### Post by kronk on 2007-08-11
dpkg as per RomeReactor's advice above my initial post :)

---

### Post by truet on 2007-08-11
done the command in initial post and it chucked up the error message 

mv: cannot stat `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_d i sts_feisty_universe_binary-i386_Packages': No such file or directory

---

### Post by RomeReactor on 2007-08-11
Well, the file itself *is* there, but appears to be corrupt. The file contains a list of files for the Universe repositories. I came across a thread where someone had an similar situation a while back, and copying another poster's file and pasting it there solved the problem. If anyone around here pulls their packages from the British mirrors and is using Ubuntu 32-bit, they can upload their file here and you could use that in place of your corrupted one, by downloading it to your home folder, and running this command:
```
sudo cp ~/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
```

I'm using 64-bit at the moment, and I suspect the contents would be somewhat different, so I can't post my file here for you.

---

### Post by kronk on 2007-08-11
Well I'd expect you'd get simular errors however can you run "sudo apt-get update" at all ?

---

### Post by truet on 2007-08-11
heres what hapens when i do that. 

jonathan@Lalita:~$ sudo apt-get update
Password:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB [4827B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 6403B in 0s (13.2kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


Have you got the 32bit system that rome is talking about?

---

### Post by kronk on 2007-08-11
Ok tried that last tip RomeReactor posted ?

---

### Post by truet on 2007-08-11
im waiting for someone who pulls their packages from the British mirrors and is using Ubuntu 32-bit, to upload their file here. Do you fit into that category?

---

### Post by RomeReactor on 2007-08-11
Someone in the #ubuntu-uk IRC channel suggested deleting the file, so that APT rebuilds it. To do that,enter the flowing in the terminal:
```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
```
then:
```
sudo apt-get update
```

---

### Post by kronk on 2007-08-11
How'd that go Truet ? Any good

---

### Post by truet on 2007-08-11
RomeReactor u are a genius! IT WORKED. One other question whilst on the topic. I run windows aswell and the resolution is higher in widows then the top resolution in ubuntu. Any reason why? Thanks again both u guys for helping!

---

### Post by kronk on 2007-08-11
All RomeReactor's hard work !

Good job :)

What sort of Video card you running there Truet ?

---

### Post by RomeReactor on 2007-08-11
Don't thank me; it was **stdin** in the #ubuntu-uk IRC channel that gave me the answer! :popcorn:

As for your video problem, what video card do you have?

---

### Post by truet on 2007-08-11
ati readon think 350 not 100% sure but think its that one!

---

### Post by RomeReactor on 2007-08-11
Hmmmm... Radeon. I've always used nVidia, so don't know practically anything about those. I suggest you run this command so you can be sure what exact model of ATI card you have:
```
lspci | grep VGA
```
This other command will print out more details about your card:
```
sudo lshw -class display
```
Do a search of these forums for that model and/or start a new thread, here or in the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") section. Try to give your thread a title that reflects the model of the card and your issue, like "ATI Radeon XXXX low resolution" or something similar.

Sorry I can't be of help on that.

---

