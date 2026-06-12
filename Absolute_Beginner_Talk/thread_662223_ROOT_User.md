---
title: "ROOT User"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Kosmos21 on 2008-01-08
Totally totally new. MAC user with Mostly Windows experience, needs a bit of help. Thanks to posts elsewhere I was able to penetrate Ubuntu.

I recently boungt a very old (circa 1999) ThinkPad 390E laptop for 20 bucks. Searching thru there forums I was able to get past the login - which I didn't know since I bought this laptop at a Thrift Shop. Now armed with the one user name that came up and having reset the password, I have found (and am enjoying) the Linux Ubuntu world. Needing it primarily as a word processor, I am satisfied with the OpenOffice that is on this machine. 

To get to the question, I was trying to watch a 3gp (video) file but the correct codecs arent installed. It asks me if I want it to search for some codecs. I say yes, it finds them, I try to have the program apply it, but I do not have (is it?) root or administrative priveleges. 

How do I get them? DO I have to create a root user. I don't know how!

---

### Post by Pevichaey5 on 2008-01-08
slightly confusing are you running ubuntu 7.10? or mac? i'm confused lol

---

### Post by Kosmos21 on 2008-01-08
LOL So Sorry. that was rambling!

My Ubuntu is on a ThinkPad 390 so it is not a mac. I am not sure how to see the version. How do I see the version???

---

### Post by Pevichaey5 on 2008-01-08
System>> About Ubuntu

---

### Post by durrell on 2008-01-08
Did you install Ubuntu on the machine? You need the root password to do pretty much anything administrative-wise. If you have the password, to gain access to a root terminal you can use "sudo -s" or "sudo su" and then type the password. But from what it sounds, you're using a graphical utility to install the codecs so your root password must be different from that user's password if it is denying you access.

You may need to reinstall Ubuntu, because without root privileges you can't create a new user that has root privileges. If you just reset the password of the user account (I'm not sure what you did or how you did it), the root password may not have changed.

---

### Post by Kosmos21 on 2008-01-08
Funny, I had seen that then couldn't find it again. Whoa... Anyway, thanks:

Fiesty Fawn 7.04 is the version.

When I try to install the codecs that the the Media player finds on the computer and offers to allow me to install, I get a message that the Synaptic Password Manager" needs the password to perform administrative tasks. I am assuming that is the same as a root or administrative password. But assumptions are dangerous!

---

### Post by durrell on 2008-01-08
Yes, when Synaptic prompts you it wants your user password (assuming you have sudo privileges). If it's declining you, you must not have full privileges, which to change you would need the root password.

---

### Post by monte48lowes on 2008-01-08
Should just be the user password since by default ubuntu uses 'sudo' instead of a root account.

Mike

---

### Post by Kosmos21 on 2008-01-08
> **durrell said:**
> Did you install Ubuntu on the machine? You need the root password to do pretty much anything administrative-wise. If you have the password, to gain access to a root terminal you can use "sudo -s" or "sudo su" and then type the password. But from what it sounds, you're using a graphical utility to install the codecs so your root password must be different from that user's password if it is denying you access.

You may need to reinstall Ubuntu, because without root privileges you can't create a new user that has root privileges. If you just reset the password of the user account (I'm not sure what you did or how you did it), the root password may not have changed.

Thanks, yes. Following instructions on how to retrieve a user name and then reset the password I was able to use the user name that allowed me to use the machine. I did not install Ubuntu. In fact I was trying to erase to - God Help Me! - put Windows 98 or something light on this machine.

Now that I have started using and and have found this forum, I want to do no such thing.

If I have to install, I do not have access to the internet on this machine yet, but do have a 1gb USB drive that I might be able to use to dl the program onto it and then load it onto the machine. Since nothing on 6 gb harddrive is important to me I might do that assuming ly limitations make that a viable option...

---

### Post by durrell on 2008-01-08
The only thing about using a USB drive is that a PC that old probably doesn't have the capability to boot from the USB drive. If you have access to a CD burner (on another machine with internet access of course), I'd recommend burning the Alternate Install CD (since it's text based) and reinstalling that way. Of course that is assuming the laptop has a CD drive. This would give you full access, as well as a fresh install.

---

### Post by Kosmos21 on 2008-01-08
> **durrell said:**
> The only thing about using a USB drive is that a PC that old probably doesn't have the capability to boot from the USB drive. If you have access to a CD burner (on another machine with internet access of course), I'd recommend burning the Alternate Install CD (since it's text based) and reinstalling that way. Of course that is assuming the laptop has a CD drive. This would give you full access, as well as a fresh install.

Thanks... Indeed. There is a CD drive. I was thinking that I could load the program onto the harddrive, but of course I'd wipe what I was trying to install (now that I think about it). LOL

Is there anyway to get the sudo/root password? When I got the username in Grub (is that like DOS?) I got the user name, and then with instructions elsewhere in this great forum, I reset that password. 

So any chance, or no?

---

### Post by durrell on 2008-01-08
There's no way to reset the root password without the old root password. At least, to my knowledge. And if there is I would imagine it's much harder than simply reinstalling.

---

### Post by Kosmos21 on 2008-01-08
> **durrell said:**
> There's no way to reset the root password without the old root password. At least, to my knowledge. And if there is I would imagine it's much harder than simply reinstalling.


Thanks... Yeah. I'll try to get a cd burned with the install of the latest???

I wonder since with a 196 mb of Ram, I may not want to put A newer version of Ubuntu... I have to check out the specifications and hardware needs.

Again, thanks...

---

### Post by durrell on 2008-01-08
Well that's why I suggested the alternate install CD which has no GUI but is still graphical enough to be easy. The Live CD runs totally off of RAM basically, so running it on such old hardware would probably be painful. You can either upgrade to 7.10 or stick with 7.04, either should be fine.

---

### Post by Kosmos21 on 2008-01-08
> **durrell said:**
> Well that's why I suggested the alternate install CD which has no GUI but is still graphical enough to be easy. The Live CD runs totally off of RAM basically, so running it on such old hardware would probably be painful. You can either upgrade to 7.10 or stick with 7.04, either should be fine.

Thanks...

So, the alternate is a lighter version altogether. I was assuming that the installation was different, whereas it is the actual finished product that is different. I wonder what I have on my machine. Seem pretty graphical.

---

### Post by durrell on 2008-01-08
Well the alternate install installs the same system (the one you have) without having to boot into a Live environment. Its purpose is to prevent older hardware users from having to boot into an environment that uses a ton of RAM. Once its done and you reboot, you'll boot into the same graphical environment you're in now.

By the way, you can click the little medal next to the quote button in my posts if you want to say thanks. :p

---

### Post by zipperback on 2008-01-08
Since the system had the operating system installed on it, I would strongly urge you to do a fresh installation of Linux on it.

- zipperback
:popcorn:

---

### Post by Kosmos21 on 2008-01-08
> **durrell said:**
> Well the alternate install installs the same system (the one you have) without having to boot into a Live environment. Its purpose is to prevent older hardware users from having to boot into an environment that uses a ton of RAM. Once its done and you reboot, you'll boot into the same graphical environment you're in now.

By the way, you can click the little medal next to the quote button in my posts if you want to say thanks. :p

I see, about the thanks I mean. And Thanks:)

I've already ordered a disk, however, as I mentioned in a previous post, I will download and burn a cd witht he alternate version, as you instruct, and proceed from there.

Thanks again :)

---

### Post by durrell on 2008-01-08
Sounds good. Good luck. You should have no problems with it. But if you do, you know where to find us. ;)

And thanks for the "thanks".

---

### Post by monte48lowes on 2008-01-09
Two things:

Starting the computer in 'Recovery Mode' boots into a command line with root access.

You can add the your user to the 'admin' group from the recovery prompt. This will allow you to use sudo, which will give you the access you need.

Mike

---

### Post by Kosmos21 on 2008-01-12
I found another way to get the password reset and access the user and group windows so that I can make myself or anyone else admins...:


If you forgot you password for your ubuntu system you can recover using the following steps

Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot 

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html#more-267]("http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html#more-267")

---

### Post by ByteJuggler on 2008-01-12
> **Kosmos21 said:**
>  I try to have the program apply it, but I do not have (is it?) root or administrative priveleges. 

How do I get them? DO I have to create a root user. I don't know how!

Ubuntu by default locks the root account so no-one can use it.  Instead, users are granted the ability to "sudo", thereby gaining root only when needed for specific actions.  To verify it's really you, the system then asks again, for *your* password.  So, if the system is asking for a password to gain adiministrative privileges, that password is *your* password, not root's.  (Aside: It is possible to assign a password to the root account and log in as it, but this is not recommended.)

HTH

---

### Post by ByteJuggler on 2008-01-12
> **durrell said:**
> Did you install Ubuntu on the machine? You need the root password to do pretty much anything administrative-wise. If you have the password, to gain access to a root terminal you can use "sudo -s" or "sudo su" and then type the password. But from what it sounds, you're using a graphical utility to install the codecs so your root password must be different from that user's password if it is denying you access.

You may need to reinstall Ubuntu, because without root privileges you can't create a new user that has root privileges. If you just reset the password of the user account (I'm not sure what you did or how you did it), the root password may not have changed.

Ummm, no.  You don't need the *root* password to sudo, you need *your* password... root by default doesn't have a password on ubuntu!

Question to Original Poster:  Does your user account not have sudo privileges then?

---

### Post by ByteJuggler on 2008-01-12
> **Kosmos21 said:**
> Thanks...

So, the alternate is a lighter version altogether. I was assuming that the installation was different, whereas it is the actual finished product that is different. I wonder what I have on my machine. Seem pretty graphical.

No, the installer is ligther, the end product is the same.  However, the graphical installer is heavier than the end product, due to having to run entirely from RAM and CD.

---

### Post by Kosmos21 on 2008-01-12
OK...When I went into the user and groups I saw "root" and then gave it a passoword. I there should get erase it and leave "root" without a password???

Also. since I could not tell of the two names other then what I added who is root, I changed the password to them both and addedd them to the Group "root"

Is this ok?

---

### Post by ByteJuggler on 2008-01-15
> **Kosmos21 said:**
> OK...When I went into the user and groups I saw "root" and then gave it a passoword. I there should get erase it and leave "root" without a password???

Also. since I could not tell of the two names other then what I added who is root, I changed the password to them both and addedd them to the Group "root"

Is this ok?

You should ***_not _***leave root without a password.  Edit the password file and put a * in the password field.  (I can't remember if there's a way from the GUI to lock an account.) 

Alternatively just put a really long random password on the root account.

---

