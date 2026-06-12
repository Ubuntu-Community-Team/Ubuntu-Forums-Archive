---
title: "do the Samba"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by SpikeyMike on 2007-07-11
Hi
I installed Samba because I want to share my Ubuntu pc on my home network and then followed this How To:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

After several attempts I still couldn't get it to work properly. I could see the linux pc from the windows pc but when I tried to open it it said I didn't have the right permissions. Anyway I decided I would restore the samba.conf file and start again but I couldn't find out how to restore it so I decided to uninstall samba from the synaptic package manager and start again. After uninstalling samba I restarted linux but now when I log in I get the following message:

[COLOR="Red"]User's $HOME/.dmrc file is being ignored. This prevents  the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.[/COLOR]

Can anyone tell me how I can correct this and where I can find a good How To on how to set up samba?

Spikey

---

### Post by compwiz18 on 2007-07-11
> **SpikeyMike said:**
> Hi
I installed Samba because I want to share my Ubuntu pc on my home network and then followed this How To:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

After several attempts I still couldn't get it to work properly. I could see the linux pc from the windows pc but when I tried to open it it said I didn't have the right permissions. Anyway I decided I would restore the samba.conf file and start again but I couldn't find out how to restore it so I decided to uninstall samba from the synaptic package manager and start again. After uninstalling samba I restarted linux but now when I log in I get the following message:

[COLOR="Red"]User's $HOME/.dmrc file is being ignored. This prevents  the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.[/COLOR]

Can anyone tell me how I can correct this and where I can find a good How To on how to set up samba?

Spikey

Well, to fix the error message, you can open a terminal and run ```
sudo chmod 644 ~/.dmrc
``` and then, to set up Samba, you may be able to follow [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) (I haven't tried it, but it looks complete)

---

### Post by SpikeyMike on 2007-07-12
Hi
Thanks for your reply, I tried running sudo chmod 644 ~/.dmrc but it didn't work, I am still getting the same error message :( I
I also tried opening the properties of the file directly and changing the permissions there but it didn't help........

Spikey



> **compwiz18 said:**
> Well, to fix the error message, you can open a terminal and run ```
sudo chmod 644 ~/.dmrc
``` and then, to set up Samba, you may be able to follow [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) (I haven't tried it, but it looks complete)

---

### Post by compwiz18 on 2007-07-12
> **SpikeyMike said:**
> Hi
Thanks for your reply, I tried running sudo chmod 644 ~/.dmrc but it didn't work, I am still getting the same error message :( I
I also tried opening the properties of the file directly and changing the permissions there but it didn't help........

Spikey
The other thing you could try is changing the owner of the file:

if SpikeyMike is your username on your computer, do ```
sudo chown SpikeyMike:SpikeyMike ~/.dmrc
```

---

### Post by SpikeyMike on 2007-07-12
Hi
I tried that too but I am still getting error message :(
not sure what it is but I think it might have something to do with when I added users when I tried this 'how to'

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Spikey



> **compwiz18 said:**
> The other thing you could try is changing the owner of the file:

if SpikeyMike is your username on your computer, do ```
sudo chown SpikeyMike:SpikeyMike ~/.dmrc
```

---

### Post by compwiz18 on 2007-07-12
Did you add a user who doesn't have a home directory?

---

### Post by SpikeyMike on 2007-07-13
Yes I think I did, the way I understood the 'how to' was that I had to add all windows users, that is the user names and passwords for all the windows machines that needed access to the linux pc. So I added the username and password that I use to log on to my windows laptop, I am guessing that is not right? How can I remove them?

Spikey





> **compwiz18 said:**
> Did you add a user who doesn't have a home directory?

---

### Post by SpikeyMike on 2007-07-16
Please help!!!! :confused::confused:

---

### Post by compwiz18 on 2007-07-16
Undo what ever you did to add those usernames.  You can probably edit /etc/samba/smb.cnf and fix it.

---

### Post by SpikeyMike on 2007-07-18
> **compwiz18 said:**
> Undo what ever you did to add those usernames.  You can probably edit /etc/samba/smb.cnf and fix it.

The thing is I uninstalled samba, that is when the problem started so I don't have a smb.cnf to edit. If I reinstall samba should it revert to my  previous configuration so that I can edit it or will it just install it as a completely new installation? In which case I am still left with the problem of undoing whatever i did :(

Spikey

---

### Post by compwiz18 on 2007-07-18
Apt has a nifty trick: --purge.

if you do apt-get remove --purge samba, samba will be _completely_ removed, including configuration files.  You can then reinstall it.

---

### Post by codmate on 2007-07-18
Don't forget to do:
$ useradd [username]
$ passwd [username]
$ smbpasswd -a [username] [password]
..for all your users.

---

### Post by SpikeyMike on 2007-07-23
> **codmate said:**
> Don't forget to do:
$ useradd [username]
$ passwd [username]
$ smbpasswd -a [username] [password]
..for all your users.


Ok, I managed to fix the error message by playing around with the permissions of my folder. So do I need to do the above for all the Ubuntu users or the usernames on the windows computers I want to connect to Ubuntu?

Spikey

---

