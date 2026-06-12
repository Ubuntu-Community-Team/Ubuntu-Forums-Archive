---
title: "Forgotten Password"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Bill de Garis on 2006-03-07
I have forgotten both my user name and my password after doing my 1st instal of Linux.
1) How do I get in (dual boot system W2K and Ubuntu 5.10)
2) How do I get it to boot with full access but no passwords etc.
W2K works just fine.

---

### Post by christhemonkey on 2006-03-07
Quite simply:
[http://www.ubuntuforums.org/showthread.php?t=133102&highlight=howto+password](http://www.ubuntuforums.org/showthread.php?t=133102&highlight=howto+password)

---

### Post by christhemonkey on 2006-03-07
You can always add a new user as well and then just delete your old acount.
```
sudo adduser <username>
```
and then maybe take a look in your /home/ directory and there should be a folder with your old usernames name.
You can then do what is stated in that howto.

---

### Post by Bill de Garis on 2006-03-07
Nothing seems to work.
I booted in recovery mode, set up a new user and password, rebooted and logged in but it says there is no /home <username> directory and asks if I want to use the root directory.
Then it basically dumps me back at the login sequence again. (after some error messages).

I tried sudo adduser <username> but the command line just gives me an error: Unable to lookup Linux via gethostbyname()
This is just about format and reinstal time I guess.
I'm beginning to understand why Linux is not used on desktops.

---

### Post by AndrewCaul on 2006-03-08
[QUOTE=Bill de Garis]
I tried sudo adduser <username> but the command line just gives me an error: Unable to lookup Linux via gethostbyname()
This is just about format and reinstal time I guess.
I'm beginning to understand why Linux is not used on desktops.[/QUOTE]
Ah. You're having trouble using sudo. I've been having trouble using it too, but I think I have the solution.
It seems that sudo does not know the IP address of "Linux" (your computer's name) and can't resolve it using DNS. First you should boot up in recovery mode or use a live CD to get root access to Linux. Open /etc/hosts in a text editor such as nano and add "Linux" (no quotes) at the end of the line that starts with 127.0.0.1. Save the file (Ctrl-W in nano) and restart Ubuntu.
It should now know that the host Linux is at 127.0.0.1, which simply means the computer you are currently using.

Hopefully sudo will work after that. I haven't had a chance to try it out yet, but I don't see why it won't.

---

### Post by mlind on 2006-03-08
simplest way to fix this without livecd's or other stuff, if you're GRUB is not password
protected. just append '1' to your kernel parameters. To do this press 'e' on grub
menu and append so it looks something like this. 

```

kernel          /vmlinuz-2.6.15-17-k7 root=/dev/hda3 ro nosplash 1

```

and boot. This will drop you on runlevel 1 and you will be logged as root user.

Then do
```

passwd login

```
where login is your username.

---

### Post by mcduck on 2006-03-08
There is option in Grub menu to boot in recovrery mode (text-only login as root). No need for password. Then run 'ls /home' to find out names of all users created on the machine. Now you know your old username. Then run 'passwd username' (replacing username with the username you found out with previous command. No sudo, as you are already root) and enter the new password. Then run 'reboot' to boot the computer, and login in the normal way with your old username and new password. Easy.

If you add new user, it won't have admin rights and won't be able to use sudo or any admin tools, so you'd have to fix that in recovery mode too. It's much easier to just change the password for the original user who already has admin rights. ;)

---

### Post by christhemonkey on 2006-03-08
Ok didnt know that! cheers mcduck for sorting that out, sorry about my misinformation.

---

### Post by AndrewCaul on 2006-03-08
If you prefer the GNOME environment to the console in recovery mode you should be able to start it up by typing **startx**. Then you can edit your configuration files and such in a graphical environment. :cool: 
But not all commands have GNOME equivelents, so it can't be used for everything.

---

### Post by mcduck on 2006-03-09
[QUOTE=AndrewCaul]If you prefer the GNOME environment to the console in recovery mode you should be able to start it up by typing **startx**. Then you can edit your configuration files and such in a graphical environment. :cool: 
But not all commands have GNOME equivelents, so it can't be used for everything.[/QUOTE]
I wouldn't recommend this. Logging in to X as root is not safe but something that one should never ever do. That's why it's disabled even if you enable root account..

Instead, after sorting out the problem with users password, you can log in as that user, and run 'gksudo nautilus' to open file manager as root. Then you can do almost anything that you could do if you logged in as root, but it's safer. You can even create icon for that if you need it a lot. (or there's available nice nautilus script that allows you to right-click any file and select to open it as root)

---

### Post by mcduck on 2006-03-09
[QUOTE=christhemonkey]Ok didnt know that! cheers mcduck for sorting that out, sorry about my misinformation.[/QUOTE]
We're all learning new things here :)

Anyway, you _could_ just add the new user to admin group, but it's nicer and easier to get the old user working. This way you don't need to configure every program again, chmod all your old files to new user etc..

---

### Post by AndrewCaul on 2006-03-09
[QUOTE=mcduck]I wouldn't recommend this. Logging in to X as root is not safe but something that one should never ever do. That's why it's disabled even if you enable root account..

Instead, after sorting out the problem with users password, you can log in as that user, and run 'gksudo nautilus' to open file manager as root. Then you can do almost anything that you could do if you logged in as root, but it's safer. You can even create icon for that if you need it a lot. (or there's available nice nautilus script that allows you to right-click any file and select to open it as root)[/QUOTE]
Oh, sorry. I didn't know that it's bad. I'm kinda new to all this too. But my hosts file is edited now and I can use sudo and gksudo properly. Maybe I *should* create a launcher icon for loading up nautilus as root.

---

### Post by trorion on 2006-03-09
so...

How do I prevent this entire situation from being possible?  I would really like to set it up so that people CAN'T easily change my password and what not.

Do I need to add a password to GRUB or something right?  And then disable the use of "recovery" in the default grub loader, add a password to my bios and lock it to boot from HDD only?

I guess I figure if someone can come on this board and say "hey, lost my password/uname how do I get it back" and inside of 10 minutes have an easy route to open my computer then I might as well just eliminate my password.

---

### Post by mlind on 2006-03-09
One can still access filesystem using livecd's like Knoppix, which will bypass GRUB
loader. If you want to be sure no-one can tamper your information, you may have
to encrypt your filesystems (like using cryptoloop), but imo it's bit overkill for normal desktop use.

---

### Post by mcduck on 2006-03-09
[QUOTE=trorion]so...

How do I prevent this entire situation from being possible?  I would really like to set it up so that people CAN'T easily change my password and what not.

Do I need to add a password to GRUB or something right?  And then disable the use of "recovery" in the default grub loader, add a password to my bios and lock it to boot from HDD only?

I guess I figure if someone can come on this board and say "hey, lost my password/uname how do I get it back" and inside of 10 minutes have an easy route to open my computer then I might as well just eliminate my password.[/QUOTE]
Best way is to make sure that nobody has physical access to your machine, as someone could always just take the HDD out and put it in his own machine to get your files. If that's not possible, lock your case and set Grub password. 

BIOS passwords are useless in most cases. They can usually be cleared simply by removing battery from motherboard for some time (and there's often even quicker ways to clear BIOS settings)..

If you are really paranoid, you can ofcourse crypt your drives ;)

---

