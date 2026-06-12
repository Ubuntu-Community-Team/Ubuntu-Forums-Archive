---
title: "Smb.cnf...read only.."
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by makko on 2006-11-10
Hi,
I have just installed samba but I cannot edit the smb.cnf file in /etc/samba I do not have permissions to create files or folders in that folder.. I am on the account that I used to install Ubuntu.. Is this root user?

Also I haven't a clue how ubuntu works in general like directories, where things get moved to etc etc..any very basic guides to getting used to ubuntu.
I am sick of looking my head is nearly fried ](*,)

---

### Post by madmetal on 2006-11-10
read this first about root permission in ubuntu.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

open a terminal then and type
gksudo nautilus 
and open the file from there in order to edit it.

---

### Post by taurus on 2006-11-10
You need to be root to modify anything outside of your own home directory, $HOME.  You can accomplish that with the sudo command.  So, open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/samba/smb.cnf
```
And if you want to move things around outside of your home directory, you can use the mv (for moving or renaming) or cp (for copying)...

```
sudo mv <filename> <destination>
```

---

### Post by podunk on 2006-11-10
I made my first how to this morning:
Podunk's Point and Click Samba.
If you have repositories enabled you don't have to use the terminal at all. If you haven't "enabled the extra repositories you'll need to do this first:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

After you do that try this. I hope it works, you're my first guinea pig. :-D
[http://ubuntuforums.org/showthread.php?p=1740634#post1740634](http://ubuntuforums.org/showthread.php?p=1740634#post1740634)

---

### Post by makko on 2006-11-10
Ok i;ve done all thats in the guide and it still wont work.. I dont get the whole thing about the WINS I can't find it in XP..
Also I IP scanned the Linux box and it is now called YOUR_WORKSPACE, thats the netbios name aswell??](*,) ](*,)

---

### Post by podunk on 2006-11-11
Man - I am very sorry! That was the way I got 2 Linux computers networked together - I should have said that right off the bat! :-(

I wasn't trying to get my windows able to see my Linux, I just wanted to swap stuff between my Linux computers and copy files from the Windows ones..

I just followed this how to here:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

so my Windows could get to my Ububntu (why do I feel dirty here?) and it worked fine! It took about 30 minutes I guess.

Something that he didn't talk about is you will have to create a Windows log in with a password for this to work. If you boot straight to the desktop, go to Control Panel, chose Classic View, then click users. 

I chose the administrative account and changed the name from Compaq-Owner to something easy to type -remember, no spaces!, then created a password. If you run into problems give me a shout and I'll help all I can.

Also - if you have Firestarter (the firewall) running on your Ubuntu box, turn it off until you connect the first time.

---

