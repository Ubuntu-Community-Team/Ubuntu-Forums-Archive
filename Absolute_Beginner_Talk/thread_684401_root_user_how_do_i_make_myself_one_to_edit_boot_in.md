---
title: "root user? how do i make myself one to edit boot info"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by dconnors on 2008-02-01
Hi, I'm new to ubuntu/linux, and I installed it on a hp dv6000 variant laptop, I need to add the commands "noapic" and "nolapic" to the grub boot command line file menu.lst 
I  managed to muddle thru with terminal to load the file into pica?   but when i edit the line i need and attempt to save it says i don't have permissions..  i attempt to change to root user, i get a password prompt, and i enter the only password i every created for the install and it says 
authentication failure Sorry...   

I have other issues trying to get wireless to work.. but that will be my next post.. so far the only way I can get internet is to boot back into vista.. (shudders)

cheers

---

### Post by Rocket2DMn on 2008-02-01
If you are trying to edit menu.lst, make a backup first and then edit:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```

Do be careful!

---

### Post by jan quark on 2008-02-01
try 
```
sudo gedit /path/to/directory/menu.lst
```

---

### Post by jaytek13 on 2008-02-01
Well, really it would be 

```

sudo pica /boot/grub/menu.lst

```

if you were looking to use pica. Most people automatically say gedit, but just prefacing any application with sudo will allow you to run it as root.

---

### Post by Arkenzor on 2008-02-01
(The command "pica" has nothing to do with text editing, so I'll assume you meant "pico".)

The two first solutions may not work for you, because gksudo is not installed by default in Kubuntu, and gedit is in neither Kubuntu nor Xubuntu. The backup is good advice, though. You should go for something like this:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo nano /boot/grub/menu.lst
```
(By the way, in Ubuntu nano and pico are the same command)
Then if you need to restore your previous menu.lst:
```
sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst
```




For a bit of explanation, if you tried using su to get a root prompt then it had to fail, because your root password was randomly generated during installation. In Ubuntu, the preferred way of getting root privileges is using sudo, which asks for your user password (the one you set yourself) instead of your root password.

If you still want to be able to use su, then you should first run
```
sudo passwd
```
to set your root password, or you could simply run su through sudo
```
sudo su -
```
to use your user password instead of your root password.

---

### Post by dconnors on 2008-02-01
lol, thanks for the answers,  i used to think I was a knowleadgeable computer user, but learning how to set up and use linux even one that seems   noob friendly as  ubuntu is  a lot like learning conversational klingon....

 me bad perhaps for trying to set it up on a non supported laptop..  but you go home with the girl what you brung..        cheers..

---

### Post by bodhi.zazen on 2008-02-01
> **Arkenzor said:**
> For a bit of explanation, if you tried using su to get a root prompt then it had to fail, because your root password was randomly generated during installation.

Just for clarification, by default the root account is locked (and is NOT set to a random password), and sudo is patched to account for this. It is a common misconception re: Ubuntu & the root account.

> **By default, the root account password is locked in Ubuntu.**

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you set a password and want to revert (ie lock the root account) :

```
sudo passwd -l root
```

---

