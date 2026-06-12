---
title: "locked out after messing with home permissions !"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Davi0 on 2008-04-20
I stuffed up obviously after changing my home folder permissions and now can't boot into Ubuntu 7.10.

How do I use the terminal to log in and what commands do I use when my normal admin login is not recognised because the home folder is not available.

I am very new to Linux and need to get some of my son's homework off the drive.

---

### Post by sayakb on 2008-04-20
Can you log in to recovery mode? If yes, then goto /home/username and change back your permissions.

---

### Post by Fixman on 2008-04-20
on login screen, options->sessions->failsafe terminal, from there chmod your home folder to the right permissions.

---

### Post by Davi0 on 2008-04-20
sorry fixman, I am with you up to chmod but don't understand what to do at this point.

---

### Post by Dr Small on 2008-04-20
Try:
```
chmod 755 /home/username/
```

But I am afraid this is more of an issue with .dmrc file.

---

### Post by Davi0 on 2008-04-20
terminal does not allow me to type this command, runs out of characters after chmod.

bash: /home/enigma/.bashrc: Permission denied

Where enigma is my user name.

---

### Post by Davi0 on 2008-04-20
BTW Dr Small. What is meant by "But I am afraid this is more of an issue with .dmrc file." 

Sounds serious to me.

---

### Post by sayakb on 2008-04-20
> **Davi0 said:**
> terminal does not allow me to type this command, runs out of characters after chmod.

bash: /home/enigma/.bashrc: Permission denied

Where enigma is my user name.
Do it as root:
```
sudo chmod /home/enigma
```

Also, do try the recovery mode at Grub menu to directly log in to the root terminal.

---

### Post by Hieronymus on 2008-04-20
All said before is correct, but in addition to that it could be necessary to apply the new ownership to the folder and all its subfolders as well.

To change the owner of a folder and all subfolders:

```

sudo chown -R username /foldername

```

If you also want to change the group of the folders, to for instance the group "users":

```

sudo chgrp -R users /foldername

```

Jeroen

---

### Post by Davi0 on 2008-04-20
Did this & it asked for password. However the cursor did not move as I tried to type. after 3 attempts it stated I should go to chmod --help which I did and I am still completely lost.

---

### Post by Davi0 on 2008-04-20
After giving sudo chown -R enigma/home as the command it askes for the password. Again the cursor just sits there and wont move when I try to type password.

It then states "chown: missing operand after "enigma/home

---

### Post by Hieronymus on 2008-04-20
The question about the password is because you try to run the command like root (sudo), it is the same as the password you use to log in to the system. 

If I'm correct your username is enigma and so your home folder is also enigma. Then this should work:

```

sudo chown -R enigma /home/enigma

```

```

sudo chgrp -R users /home/enigma

```

Jeroen

---

### Post by Davi0 on 2008-04-21
Ok, I'm back after sleep & work. Still no resolution. Anyone able to help please. At this point I do not know what to do.

I would simply wait until 8.04 is released and reinstall except some of my son's school work is on this disk and if possible I would like to save it for him.

---

### Post by Davi0 on 2008-04-21
If I use the above commands I get 

"[sudo] password for enigma: "

The cursor will not respond, just sits there as a black rectangle if mouse cursor is over terminal or white rectangular frame if mouse is off the terminal. Will not type.

Can anyone help please ?

---

### Post by hums07 on 2008-04-21
When you type the password, yes the cursor does not move. Just type it and then press Enter

---

### Post by jakupl on 2008-04-21
the cursor never moves when entering password in terminal... this is a security precaution. just imagine it's moving...:KS

---

### Post by Davi0 on 2008-04-21
When I do this hums07 it just returns to enigma@unbunu:/$ with nothing else happening.

Is there something else I should know ?

Can I login with a live cd ?

---

### Post by hums07 on 2008-04-21
It may have worked! The command does not give output.
Now check the permission of /home:```
ls /home -l
ls /home/enigma -l
```

---

### Post by Davi0 on 2008-04-21
Ok, thanks for the help. The first message when I try to boot is that X can't create enigma/home. This why I have arrived at the fail safe terminal.

BTW the cursor moves & displays the typed text with everything other than the password.

The 1st of your commands above give ls:-: no such file or directory

The second command states exactly the same but then lists the files & folders in the home directory.

Where to from here.

---

### Post by Davi0 on 2008-04-21
I have tried these commands again and this time no messages about not finding the files.

I am now at "enigma@unbunu:/$ "

How do I attempt to login or go forward from here ?

---

### Post by Davi0 on 2008-04-21
Bump

---

### Post by bartcramer on 2008-04-21
Try: 

cd /home
ls -l

This will show us the permissions you have on the enigma user folder. If possible, try then: 

cd /home/enigma
ls -l

Could you then post the output of these commands?

---

### Post by hums07 on 2008-04-21
```
ls -l  /home
```
if you type correctly should output at least your name (enigma). So you had not only changed /home permission, I think you have lost it. I dont know if /home can be created manually. I've never encountered such a problem. But if you want to try:
```
sudo mkdir /home
sudo mkdir /home/enigma
sudo chown enigma /home/enigma
```
I am not sure if this will work, at least you have lost settings for your application too.

---

### Post by philinux on 2008-04-21
Before you tinker anymore, lets just recover the important files.

If you have a usb stick, then boot the live cd and use it to copy the files off to the pen drive.

---

### Post by Davi0 on 2008-04-21
The outcome of the 1st command set was "enigma"

The second set was the same outcome"enigma"

---

### Post by hums07 on 2008-04-21
You type incorrectly
```
ls -l /home/enigma
```
it is a small letter L, not number one.
The result for my desktop is like this:
```
total 582209
drwxr-xr-x 2 harry harry      1024 2008-04-20 23:00 BackupX11
drwx------ 2 harry harry      1024 2008-04-20 22:51 Desktop
drwxr-xr-x 2 harry harry      1024 2008-04-21 05:15 hd-media

```
you should get similar output, not just enigma.

---

### Post by Davi0 on 2008-04-21
Sorry, you are correct. The answer is - 1st "total 0".
 
Then 2 columns. The L/H column consists of 15 lines "?---------? ? ? ?".

The R/H column consists of The folders and files in my home/enigma directory. ie "? /home/enigma/desktop"

While I was waiting for a reply I live booted from the Cd and I can still see these folders and files but they are grayed out and if I attempt to open them I get the message "you do not have permission to open this folder/file.

---

### Post by Davi0 on 2008-04-21
I have to sleep & work again. Will come back to this tomorrow night.

Please reply if you can help as I will not give up if I can avaid it.

---

### Post by hums07 on 2008-04-21
Before you ask more questions please read manual on
[B]chmod
mount
ls[/B]
Google for them.
Moreover, it is much faster if you save your data somewhere and do a clean install.

---

