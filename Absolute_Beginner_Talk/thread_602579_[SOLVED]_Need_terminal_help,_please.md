---
title: "[SOLVED] Need terminal help, please"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-11-04
I'm trying to install a HLIP prog and don't know what terminal command to do this:

> # You will need to have root/su access to run the installer.

Can someone help this addlepated geezer?

Many thanks,

Jon

---

### Post by llamakc on 2007-11-04
sudo NAME_OF_COMMAND

It will prompt you for your USER password.

---

### Post by NilsE on 2007-11-04
Put

sudo

in front of the command with a space between

---

### Post by PmDematagoda on 2007-11-04
Simply append the install command with sudo, so the command should look like this:-

```
sudo nameofcommand
```

enter the password when it is requested, please note that you cannot see the password you type in the terminal, just type the password normally and press Enter after you type the password.

---

### Post by Wikzo on 2007-11-04
Yes, sudo (SuperUser DO) and then command.

You'll have to write your password. Note: You won't see any letters or "****" when you type in the password. Just hit Enter.

---

### Post by Romin-1 on 2007-11-04
Thanks guys, did as instructed and got this:

> jon@jon-desktop:~$ sudo sh hplip-2.7.10.run
Password:
sh: hplip-2.7.10.run: No such file or directory
jon@jon-desktop:~$


The file is on my desktop, I can see it but terminal does not, sheesh!!!

Checked the HP compatables page before buying this printer just for my Ubuntu machine and now have problems getting it to work.

Don't suppose the CD that came with it would work, Huh?

Thanks again,

Jon

---

### Post by PmDematagoda on 2007-11-04
Isn't HPLIP built-in? The option to see the GUI is hidden so you have to go to System>Preferences>Main Menu and go to the System>Preferences and enable HPLIP toolbox to be shown.

---

### Post by schorsch on 2007-11-04
Please try
```
sudo sh ./hplip-2.7.10.run
```
"./" tells the shell that the wanted command is in your actual directory. I assume you are standing in the directory with the file "hplip-2.7.10.run" .....

---

### Post by eph1973 on 2007-11-04
Actually, if the file is on your desktop, you need to type the following:
```

sudo sh ./Desktop/hplip-2.7.10.run
```

assuming you are starting from your home directory like it looks like you are.

---

### Post by llamakc on 2007-11-04
> **eph1973 said:**
> Actually, if the file is on your desktop, you need to type the following:
```

sudo sh ./Desktop/hplip-2.7.10.run
```assuming you are starting from your home directory like it looks like you are.

If the OP is in ~ (/home/USER) they do not need the "./".

sudo sh Desktop/hplip-2.7.10.run

Will work with less key strokes.

---

### Post by Romin-1 on 2007-11-04
My hats off to all you guys. 

Seems like it took forever for the installation to run but it is now working like a charm. The fax, scanner, all the bells and whistles...

Once again, many thanks,

Jon

---

