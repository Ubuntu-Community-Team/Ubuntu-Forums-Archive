---
title: "How do I make a folder have a password?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-17
I want it because I'll have users on my account and I don't want people to be nosy and snoop around and look at something that I don't want someone to see :(.

---

### Post by click4851 on 2007-07-17
you could change the permissions of the "folder" so only you could read it after typing the root password? But thats just one way, I'm sure there are others using GPG or pictures (stego..?)

---

### Post by ~~Tito~~ on 2007-07-17
I tried that but I can't.

---

### Post by Motoxrdude on 2007-07-17
> **~~Tito~~ said:**
> I want it because I'll have users on my account and I don't want people to be nosy and snoop around and look at something that I don't want someone to see :(.

Go to your terminal and open root nautilas.
```
gksudo nautilus
```
Then navigate to that folder, right click>>properties>>permissions. Then change owner to root, and set the groups access to none and other folder access to none.

Note-You will need to start nautilus as root each time to access this folder.

---

### Post by ~~Tito~~ on 2007-07-17
I did that but it doesn't ask me for a password it just says I don't have access to it....................

---

### Post by whitingx on 2007-07-17
Have you looked at [Truecrypt]("http://www.truecrypt.org/") and [Forcefield]("http://bockcay.de/forcefield") ?

Hope this helps.

---

### Post by b20963a2 on 2007-07-17
or you could give [TrueCrypt]("http://www.truecrypt.org/") a try...

---

### Post by ~~Tito~~ on 2007-07-17
I don't know how to use it.

---

### Post by KIAaze on 2007-07-17
> **~~Tito~~ said:**
> I did that but it doesn't ask me for a password it just says I don't have access to it....................

You have to launch Nautilus as root:
```
gksudo nautilus
```

edit:
I have never used truecrypt, but I've found this tutorial on how to use it:
[http://polishlinux.org/howtos/truecrypt-howto/]("http://polishlinux.org/howtos/truecrypt-howto/")

---

### Post by 3rdalbum on 2007-07-17
I'll ask the best question: Why will there be users on your account?

The whole point of having an account is so different users can have different accounts, and so they CAN'T look at your files. If you want a "drop-box" where different user accounts can put all sorts of stuff, you can create a folder inside / that has read/write permissions for everyone.

If you want the other user accounts to have the same Gnome and application preferences that you currently have, you can put the preference folders from your home directory (all the folders that begin with a dot) inside the /etc/skel directory before creating the new users.

If there's a reason why you really need them to be on the same account, you can encrypt individual files with bcrypt. Sudo apt-get install bcrypt.

Bcrypt is quite secure for casual snoopers, and to be honest I use it to store some files that I know my father wouldn't like to know that I have, as he knows the password to my account (but not my Bcrypt password!).

---

### Post by ~~Tito~~ on 2007-07-17
Ok, now that I know that, how do I know that the exact system settings will load, and all or I just highlight all of the ./ folders and drag and drop?

How do I uninstall Forcefield? I installed it and now that this guy made it simpler I want to do what he suggested.

---

### Post by KIAaze on 2007-07-17
This always depends on how you installed something.
I'll assume you followed the instructions on the forcefield website:
> wget [http://www.truecrypt.org/downloads/truecrypt-4.3a-ubuntu-7.04-x86.tar.gz](http://www.truecrypt.org/downloads/truecrypt-4.3a-ubuntu-7.04-x86.tar.gz)
wget [http://bockcay.de/stuff/programs/forcefield/forcefield_current_all.deb](http://bockcay.de/stuff/programs/forcefield/forcefield_current_all.deb)

sudo apt-get install python-crack python-pexpect cracklib2

tar xfz truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
sudo dpkg -i truecrypt-4.3a/truecrypt_4.3a-0_i386.deb
rm -rf truecrypt-4.3a truecrypt-4.3a-ubuntu-7.04-x86.tar.gz

sudo dpkg -i forcefield_current_all.deb

_Uninstallation:_
```

#remove the forcefield package
sudo dpkg -r forcefield_current_all.deb

#redownload and extract the truecrypt package
wget http://www.truecrypt.org/downloads/truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
tar xfz truecrypt-4.3a-ubuntu-7.04-x86.tar.gz

#uninstall truecrypt
sudo dpkg -r truecrypt-4.3a/truecrypt_4.3a-0_i386.deb

#remove dependencies installed previously
sudo apt-get remove python-crack python-pexpect cracklib2

#remove the downloaded and extracted files
rm -rf truecrypt-4.3a truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
rm forcefield_current_all.deb

```

---

### Post by dragonwings on 2007-07-17
1. Encrypt:

      gpg -c file

      You will be asked to enter (and re-enter) a password which will used to create the encrypted file called file.gpg
   2. Decrypt:

      gpg file.gpg

---

### Post by ~~Tito~~ on 2007-07-17
I really screwed up big time i messe dup some files and i need to recover my loss. BRB. :(:(:(:(:(

---

### Post by ARandomKid on 2007-07-17
Heck, I've got a simpler solutioh.

A.) Rename the files to something odd that nobody would ever have a reason to search for, and place then in a maze of folders with various numbers as the names. (like foldrs 7, 8, 1, 2) and have each folder contain the same folder names (7, 8, 1, 2)...kind of like a code of sorts.

Yea, really easy to beat if you know what you're searching for in Find (which is why you rename them), but it'll be time consuming if you have enough folders, and the person will get bored fast.

But going with somebody else's idea is probably best.

-Alex

---

