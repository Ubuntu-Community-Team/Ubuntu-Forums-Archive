---
title: "you are not the owner..."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by rsfeller on 2007-07-25
so you can't change these permissions. 

Ok, I understand I don't own every system file but ndiswrapper created driver files and dropped them in the /etc/ndiswrapper/ folder. I note why I'm going out of mind trying to get my wifi to work that I'm getting permissions errors while trying to unload (and then delete) the config files. So I surfed tot he directory the error message says Permission Denied on and guess what, I am not the owner.

So I cannot get the software to unload these nor do I have permission?

How do I take ownership of this directory so I can attempt to get my freak'n wifi to work! I'm only on the 5th PCI card, 2nd laptop and two broadcoms for a total 12 attempts in 12 hours!

How am I every going to enjoy Ubuntu on the internets if I cannot get through this wifi setup w/o being a linux sys admiN!?!!?!?

thanks all!

---

### Post by Orochi on 2007-07-25
If you're in the terminal, you can prefix your commands with 'sudo' to execute them as the root user (administrator). That should let you do whatever you want to the files (becareful though, they're probably locked down for a reason).

---

### Post by Naci Sey on 2007-07-30
I also want to access the /etc folder - to copy my former cookies and passwords files to Firefox on ubuntu -, but am getting the same message, that I'm not the owner. How does one change ownership for that particular folder? This is one absolute beginner who is just as happy to keep her fingers out of the root directory.

---

### Post by shae on 2007-07-30
Firefox stores profiles in ~/.mozilla/firefox

**Under no circumstances should you alter permissions of files stored in /etc or any other system folder unless you know what you are doing.**  You can access these folders through the use of sudo for command line needs and by launching nautilus in root mode.  However, I strongly recommend against doing so.  Terminal is your friend and once you learn to use it, it becomes a powerful tool.  Also remember most programs store their settings in hidden files in your home folder.  These can be edited without root privileges.

---

### Post by Tomosaur on 2007-07-30
> **Naci Sey said:**
> I also want to access the /etc folder - to copy my former cookies and passwords files to Firefox on ubuntu -, but am getting the same message, that I'm not the owner. How does one change ownership for that particular folder? This is one absolute beginner who is just as happy to keep her fingers out of the root directory.

You should never change the permissions / ownership of the actual directory / file you wish to modify. All you need to do is assume the role of a user who DOES have ownership. On Linux, the 'root' user has ownership over everything. This is essentially the system admin. To temporarily gain root priveleges, you should prefix the command with the 'sudo' command. For example, if you wish to edit the /etc/X11/xorg.conf file:

```

sudo nano /etc/X11/xorg.conf

```

If you wish to copy a file from your home directory to the /etc directory:
```

sudo cp ~/myFile /etc/

```

The sudo command will ask for your password (the same one you use to log in) to ensure that it's not a virus or something trying to gain root priveleges. You will not see your password being typed, so be sure to spell it correctly.

Remember - if you change the actual ownership of files outside your home directory, you can cause serious damage to your system. You need to just assume the role of a user who does have permissions.

---

### Post by Naci Sey on 2007-07-30
> **shae said:**
> Firefox stores profiles in ~/.mozilla/firefox

**Under no circumstances should you alter permissions of files stored in /etc or any other system folder unless you know what you are doing.**  ...Remember most programs store their settings in hidden files in your home folder.  These can be edited without root privileges.

I didn't know that! THANK YOU, Shae and Tomosaur, for those warnings. I made the hidden files visible under the /home folder and found exactly the files I'd been wanting to replace.

---

### Post by aysiu on 2007-07-30
If you ever want access to the /etc or other non-home directories, check this link out:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by az on 2007-07-30
The files created in /etc/ndiswrapper belong to the devices that you installed/attempted to install.  You don't need to remove them manually (although you can) but you should be able to remove them using the ndiswrapper comand-line utility

sudo ndiswrapper -
that will list the drivers you have installed (in /etc/ndiswrapper)

sudo ndiswrapper -e (name) 
that will delete the driver named (name) from /etc/ndiswrapper

---

