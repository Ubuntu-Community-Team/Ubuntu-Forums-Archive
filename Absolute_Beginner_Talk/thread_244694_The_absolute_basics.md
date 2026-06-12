---
title: "The absolute basics"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by koryo on 2006-08-26
Hi, my names koryo (obviously) and im now starting to experiment with Ubuntu. i have just downloaded the Server edition of Dapperdrake (i think thats it) 6.06

iv installed it onto a SCSI server correctly, and am able to log in and get into the main section (selecting sudo and such)

im absolutely stuck, i have NO idea where to begin, and the Sudo manual isn't helping either, can i have a complete retards guide (yep, thats me, retard at linux) on how to use linux (sudo, heck even getting a bloody GUI to work, cause once iv done that im home free ish)

what i would prefer is a complete guide to every command line and extension usable and what they do. and not like the Sudo manual, cause i cant understand how to type in the commands properly, is it:

sudo-k?
sudo k?
sudo -k?
suodk?

i mean come on i know im a little dumb but i cant understand the manual at all. any help would be greatly apreshiated (spelt wrong i know english sux) and would recieve my greatest apreciation

p.s. i installed a LAMP server, if that makes a difference

---

### Post by Tomosaur on 2006-08-26
Heh, you'll have difficult finding an explanation of EVERY command, but this link should help for most of them:
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

And usually, when you have a command followed by other options, it's typed like this:
```

sudo -k

```
with a space between the command and the option.

---

### Post by koryo on 2006-08-26
thanks your a genious, id like to keep this topic open cause i know im gona need more help soon enough lol

thanks so far

---

### Post by Jerome36 on 2006-08-26
Have you checked out the [Ubuntu Server Guide](https://help.ubuntu.com/ubuntu/serverguide/C/index.html) at the Ubuntu Wiki?  It's farily informative.  Also, the server installation doesn't come with a desktop enviornment (GUI), but you can download and install one yourself, quite easily.  Gnome, KDE, Xcfe, etc.  Example:

> sudo aptitude update
> sudo aptitude install ubuntu-desktop

I believe I put that in correctly.

---

### Post by koryo on 2006-08-27
i love wiki, usually so easy to use, but it confused me this time, il have a more detailed look later, but for now its puzzled me lol

thanks for the commands, with those i should be ok, i want to learn the CMD Line codes first

i have a small problem tho

whenever i type in 

DIR or LS

it comes up blank. im running from 4 SCSI hdd's, i know Ubuntu server edition supports SCSI drivers as i read it on this site. Why is there nothing on the HDD? is it an install error?

scratch that, getting GUI, i have 2 servers so il use GUI on one and learn about CLI on the other :D a practicle use for both

---

### Post by Tomosaur on 2006-08-27
you should use ls, and it needs to be lower case.

---

### Post by koryo on 2006-08-27
How do i copy files in Linux?

google is NO help on the absolute basics

i need to copy MadWifi from a disk to a server. i am copying the files

    *  madwifi_1.7-3.dsc
    * madwifi_1.7-3.tar.gz

from my disk to my hdd so i can uncompress and install them, however there is no copy command line, no offence but why not?

how can i do this and why is there no copy command line?

and how do i delete files? there is no remove or delete command lines. Please explain asap as im trying to set this up at almost midnight :P

---

### Post by koryo on 2006-08-27
sorry am absolutely stuck now, edited above instead of posting so people haven't read it.

---

### Post by Tomosaur on 2006-08-27
To copy, you use the cp command, like this:

```

cp /home/me/myFile.txt /home/me/myDocs/

```
This will copy myFile.txt into the myDocs folder.

---

### Post by koryo on 2006-08-28
ok, so how do i get it to copy files off of the CDROM? the only way i have been able to access the CDROM so far is byusing the apt-cdrom command, and its not recongnised as a debian disk so i need to de-compress the files, but i cant do that unless the files are copied from the disk to the hdd

---

### Post by 916 on 2006-08-28
the cdrom stuff is stored in the media/cdrom folder, so you'll have to just access it

---

### Post by stimpsonjcat on 2006-08-28
never mind..

---

