---
title: "Can't install VMware after failed install."
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-10-07
Hi!

I have tried to install VMware in my home directory but the installation failed. So I decided to install it in the default place, and deleted the files it created in my directory. 

So now when I try to reinstall VMware I get this message:

```
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/hilal/vmware_installed/vmware-uninstall.pl.

Failure
```

what can I do now? I use Ubuntu 6.06

thnx in advance.

Execution aborted.

---

### Post by zappa on 2006-10-07
Try to reinstall vmware-player-kernel-modules via sysnaptic, then remove vmware via the script, finally reinstall vmware. Should work.

---

### Post by Kuraboy on 2006-10-07
Hi

thnx for your answer.

I am trying to install VMware Server. 

what do you mean by 'then remove vmware via the script' ? 

I tried to install the packages you mentioned and remove them from synaptic but it still didnt work.

thnx again

---

### Post by zappa on 2006-10-07
The server is not in your repo's, right? 
You downloaded a tarball from vmware. In there there is a script for installing it, but also to uninstall it.

---

### Post by Kuraboy on 2006-10-07
Hi!

yes, thank you. It worked I am installing it now.

another thing if you dont mind, the installer asks me for 

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 
```

but it wont work, I have the latest linux header 686 installed. And when I checked the path, I could only find /usr/src/linux-headers-2.6.15-27. 

and I have installed: 
```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

thnx again :)

---

### Post by zappa on 2006-10-07
Ubuntu does not store the source of the kernel by default. 
So install it with
sudo aptitude install linux-source

---

### Post by Kuraboy on 2006-10-07
Hi!

I have installed the source, and when I type the path for the source file I get: 

```
what is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-source-2.6.15

The path "/usr/src/linux-source-2.6.15" is an existing directory, but it does 
not contain a "linux" subdirectory as expected.
```

should I change the name of the folder from linux-source-2.6.15 to just linux?

thnx

---

### Post by zappa on 2006-10-07
If I remember correctly, there is a folder linux in that folder. So no name-changes are necessary. linux-source is a dummy package that will install your version.

---

### Post by Kuraboy on 2006-10-07
Hi!

it seems after that I installed the package you gave me I should I have stopped the install and re run it, because then everything worked out fine
```

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-686/build/include] 
```

it found the packge by itself. Thank you again very much for your help :)

---

### Post by zappa on 2006-10-07
NP, my pleasure ;)

---

