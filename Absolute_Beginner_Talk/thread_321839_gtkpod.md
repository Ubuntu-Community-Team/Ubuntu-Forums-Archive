---
title: "gtkpod"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Smitty_203 on 2006-12-19
[FONT="Fixedsys"]i am completely new to Ubuntu and i need a program to use to manage my songs on my iPod. I have Rythmbox, but it's no use to me when it comes to adding or managing anything! ](*,). I heard about a system called gtkpod but i have no idea how to download it. Can anyone help me? [/FONT]

---

### Post by maxamillion on 2006-12-19
open a terminal and type this in 
> sudo aptitude install gtkpod

it will ask for your password (or if you are the secondary user of the machine, it will need the administrators password)

it will download and install for you, welcome to the power of apt :)

---

### Post by 23meg on 2006-12-19
You can install it with ```
sudo apt-get install gtkpod 
```
Make sure you have the Universe repository enabled.

---

### Post by Smitty_203 on 2006-12-19
wow, thanks. Are most all downloads like that or can you just click and download some things  like windows as well? Just a thought...

---

### Post by Preserved Killick on 2006-12-19
> **Smitty_203 said:**
> wow, thanks. Are most all downloads like that or can you just click and download some things  like windows as well? Just a thought...

Wow is right!  Most all downloads you can do using the Synaptic Package Manager.  You click System > Administration > Synaptic Package Manager

Once you supply your password you can use Synaptic to add or remove programs.  Pressing Control f will give you search window if you're looking for a specific title.  Synaptic helps prevent conflicts between different programs that use different versions of the same libraries (bits and pieces of software that would be tedious to recreate for every program).  

If you can't find the program you want in Synaptic, you can add other repositories, or you can download the program and tell synaptic where it is on your system and do the install.  Aptitude can do this, too.  You'll need what is known as a deb file.  Try to download an Ubuntu-specific deb if there is one.

I try to use Synaptic for every installation because I have completely borked my system adding "cutting edge" software on my own.  For newer users, I believe a package manager like aptitude or synaptic is the safest way to keep from creating conflicting library depencies among your various software packages.

Happy computing!

-- Preserved Killick

---

