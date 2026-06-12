---
title: "Truecrypt - Get into Home folder from Windows"
date: 2011-07-22
forum: Any Other OS
---

### Post by insane9 on 2011-07-22
Hi all,

I was dual booting win7 and linux mint (mint is based off ubuntu as you know, so i believe this question is still valid).

I used truecrypt to encrypt my entire HDD. Now linux mint refuses to boot. Not sure why.

Now the problem is i encrypted my home folder when i installed Linux, so:

I've got some data in my /Home folder i need access to, so i installed an ext2 to IFS viewer and i can see the home folder now but have no permission to get into it.

Can anyone tell me how to get into the /Home folder??

I guess it'll have something to do with booting off a linux live disk and mounting the drive??


thanks guys

---

### Post by Dave_L on 2011-07-22
Mounting your Encrypted Home from an Ubuntu LiveCD
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by insane9 on 2011-07-22
> **Dave_L said:**
> Mounting your Encrypted Home from an Ubuntu LiveCD
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

Hi Dave,

i did come across a similar method, but the problem i'm having there is:

When you boot up a live disk, it boots into the disk right away, you don't need to type in the truecrypt password.

The downside to this, is that you cannot see the HD in 'my computer'

and when i tpyed in the first command in the terminal, it says : you must specify the filesystem type

---

### Post by Dave_L on 2011-07-22
> When you boot up a live disk, it boots into the disk right away, you don't need to type in the truecrypt password.

The Live disk boots into a RAM disk that it creates, not a hard disk.

> The downside to this, is that you cannot see the HD in 'my computer

Normally your hard disk will show up as media that you can mount.  I've never encrypted an entire disk with Truecrypt before, and I don't know what complications that may cause.

> and when i typed in the first command in the terminal, it says something along the lines of: please type in the correct file extention/path

Can you post exactly what you typed, and the exact error message?

---

### Post by insane9 on 2011-07-22
> **Dave_L said:**
> The Live disk boots into a RAM disk that it creates, not a hard disk.



Normally your hard disk will show up as media that you can mount.  I've never encrypted an entire disk with Truecrypt before, and I don't know what complications that may cause.



Can you post exactly what you typed, and the exact error message?

Hi again Dave,

I realize the live disk uses the virtual memory and doesn't touch the HDD. What i mean is, when i boot up the live cd, i cannot see my HDD, it's hidden because you need to log into truecrypt before the drive becomes visible - However, when you boot up your PC, it asks for a truecrypt password and once this is entered, it doesn't boot from disk, it boots into the OS.

I typed: 

[FONT=monospace][FONT=Georgia]**sudo mkdir /mnt/sda **[/FONT]

[FONT=Verdana]i got the error message:[/FONT][/FONT][B]
[FONT=Georgia]
[/FONT][FONT=Georgia]you must specify the filesystem type[/FONT][/B]

---

### Post by Dave_L on 2011-07-23
I've only used Truecrypt by creating a file as a container, and don't know enough about full disk encryption to solve this issue.

If you don't get further assistance here, you might try the Truecrypt forum: [http://forums.truecrypt.org/](http://forums.truecrypt.org/)

---

### Post by Perfect Storm on 2011-07-23
Moved to Other OS/Distro Talk.

---

### Post by insane9 on 2011-07-23
Ok, thanks Dave & AI. 

I'll see if i get more help here, if not, i'll ask the guys at TC forums. cheers

---

### Post by insane9 on 2011-07-23
Managed to fix it :) 

Basically, don't install Win 7, then Linux then encrypt your entire drive... If you do, you have to go to Truecrypt and the System tab and 'Permanently Decrypt' . Takes a few hours like it did to encrypt the entire drive.

So now the plan is: Encrypt Win7 partition only and then changing the bootloader so i can boot into Linux :)

all explained here: 

[http://post.ryanoshea.com/howto-dual-boot-system-encryption-windows-ubu](http://post.ryanoshea.com/howto-dual-boot-system-encryption-windows-ubu)

---

