---
title: "[SOLVED] extra repositories"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-09-24
how do i go about getting these extra repositories it keeps sayin no public key?

---

### Post by overdrank on 2007-09-24
> **maryjanua said:**
> how do i go about getting these extra repositories it keeps sayin no public key?

Hi it would help if you would give us the errors it is reporting.

---

### Post by maryjanua on 2007-09-24
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
billym@billym-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
there u go

---

### Post by overdrank on 2007-09-24
> **maryjanua said:**
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
billym@billym-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
there u go

Hi if you run this in the terminal it should fix the key
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update
```
Also the other error, do you have synaptic or add and remove open at the same time you are trying to update through the terminal?

---

### Post by maryjanua on 2007-09-24
never mind i give up :(
looks like i wont get beryl or any desktop effects everything i try i get a black screen with failed to start xserver and i have to do sudo apt-get install xorg-driver-fglrx to get my desktop back
im not going to bother anymore
sigh but i wish i could have 3d....... mibbe in another life(or graphics card)
also that envy thing doesnt work for me either

no i dont have synaptic open at the same time as terminal but thanks i'll try that

---

### Post by overdrank on 2007-09-24
> **maryjanua said:**
> never mind i give up :(
looks like i wont get beryl or any desktop effects everything i try i get a black screen with failed to start xserver and i have to do sudo apt-get install xorg-driver-fglrx to get my desktop back
im not going to bother anymore
sigh but i wish i could have 3d....... mibbe in another life(or graphics card)
also that envy thing doesnt work for me either

no i dont have synaptic open at the same time as terminal but thanks i'll try that

Ok sorry to hear but if you would like to try again this thread has worked for many
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
Good luck! :)

---

### Post by zvacet on 2007-09-24
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -[/B]


So,in your case

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2D6CFB44DD800CD9
gpg --export --armor 2D6CFB44DD800CD9  | sudo apt-key add -

---

### Post by maryjanua on 2007-09-24
thanks but every time i do sudo apt-get-update i get this:
billym@billym-desktop:~$ sudo apt-get update
Password:
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_GB                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_GB              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Get: 4 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]        
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_GB       
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_GB
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_GB
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                    
  
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Get: 7 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release [2195B]                     
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Fetched 2389B in 1s (1871B/s)
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
billym@billym-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by overdrank on 2007-09-24
Maybe this link will help
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by maryjanua on 2007-09-25
sorry nope iv already tried that but thanx anyway

---

### Post by ellgor on 2007-09-25
Hi,

Just a thought, had a look through your hit list and there seems to be one problem:

W: GPG error:   >>   [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com)     <<

Now if you were to bring up your sources list amd put a couple ## before that entry( stops it being read) then see what happens, if not you can easily remove the ##.

Regards, Ellgor.

---

### Post by maryjanua on 2007-09-25
how do i bring up a sources list?

---

### Post by overdrank on 2007-09-25
> **maryjanua said:**
> how do i bring up a sources list?

You can use this command in the terminal
```
gksudo gedit /etc/apt/sources.list

```

---

### Post by maryjanua on 2007-09-25
yeah i did that then did sudo apt-get update and got no errors tho the end is now different


Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [78.3kB]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6360B]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [13.9kB]
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [953B]
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [35.6kB]
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [4866B]
Fetched 198kB in 2s (71.7kB/s)                      
Reading package lists... Done

security wasnt there before

---

