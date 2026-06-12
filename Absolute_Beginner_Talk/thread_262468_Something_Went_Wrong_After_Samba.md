---
title: "Something Went Wrong After Samba"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by kcgreg on 2006-09-21
After having downloaded Samba my screen went black and my desktop items were just words and no icons so I panicked and removed Samba and now my root password doesn't work....?

I cannot even access Synaptic Manager....HELP!!!!!!:sad: :confused: :confused: :confused: :confused:

---

### Post by Kurdt on 2006-09-21
Did you downloaded and installed it from packages ?

---

### Post by kidders on 2006-09-21
Oh hell!

Something else is happening here, I'd say. The samba installation was probably just coincidence.

If your root password doesn't work, then either someone hacked your system and changed it, or one of your filesystems has been oddly specifically corrupted. I can't think of another possibility off the top of my head ... at least not a reasonable one!

Is there any way you can log into your system? If not, we'll have to go in with a bootable CD.

---

### Post by [S|G] on 2006-09-21
I had the same problem when I first tried to install samba+ldap on my system, but haven't been able to reproduce the error. 

You could try this: when grub asks you what is your OS, press "e". That will take you to edit your boot parameters. Highlight your kernel and press "e" again. At the end of the line write this: "init=/bin/bash". Press "esc" and then "b".

Your system should boot without asking for the root password. Then check your /etc/nsswitch.conf. It should look something like this:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         files
group:          files
shadow:         files

hosts:          files nis dns 
networks:       files

protocols:      files
services:       files
ethers:         files
rpc:            files

netgroup:       nis

```
I'm really not sure if this will help, but you can try it. It's just one of the theories I had when I foobar'ed my system, but didn't have time to check it.

---

### Post by kcgreg on 2006-09-21
Hi Guys,

Thanks for all the help. I installed Ubuntu a week ago today and have made it to a point where I had SKype, Adobe reader etc. until today with Samba and the problems with myroot password - my icons in the top panel disappeared and only the words e.g. applications > terminal = there is no icon in the terminal just the word etc. 

So what I did was I reinstalled it and updated with at least 176 new updates again. Is this the right thing to do? :confused: 

I have reset my Evolution Mail (again) for my emails and now I am going to get automatix so that I am able to run the gerenal daily activities on my old computer. I am trialling Linux on an old pc before shifting fully to my laptop which is still running Windoze XP.

Thanks guys.

---

