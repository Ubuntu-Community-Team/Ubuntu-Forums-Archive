---
title: "Shared Folders"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by TailsAndy on 2006-09-20
I'm trying to share folders from an ubuntu computer to an ubuntu computer that are connected to the same router.

The first ubuntu computer, [my dad's] is a recent install and there is a file on the computer that I want to get onto my ubuntu computer. I can set up files for me to share to his, he can set up files for him to share to mine. The problem is, I can't get in without a password, while he can.

Any help?

---

### Post by newlinux on 2006-09-20
Can you tell us a little more about your setup? Are you using Samba? If so how did you set it up? are you using static or dynamic IPs behind your router? You want to have no password security on the documents?

Thanks

---

### Post by benfindlay on 2006-09-20
Just put the relevant username and password into the login box and tick the option to remember it.

If you're wanting to set up YOUR user account, then you will need to edit the samba config files on your dad's pc to allow your username to connect I believe, although I'm not entirely sure, hopefully someone else can verify/refute this.

Hope this helps

---

### Post by TailsAndy on 2006-09-20
The router is dynamic IP, and I installed Samba through Synaptic Package Manager.

EDIT: What's the command for Samba Config?

---

### Post by benfindlay on 2006-09-20
not entirely sure, but I believe its ```
sudo gedit /etc/samba/smb.conf
```

But if you're not entirely sure of what you're doing, then type ```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
``` to make a backup of the file first

---

### Post by TailsAndy on 2006-09-20
Ok, and in there, what do I type to allow my user to access these?

---

### Post by benfindlay on 2006-09-20
Actually, now that I think about it, you can probably sort it from terminal, try the following:

```
cd /etc/samba
```
This puts you in the relevant directory

```
sudo smbpasswd -L -a your_username
```
This will prompt you to set a password for said username

```
sudo smbpasswd -L -e your_username
```
This enables the account

---

### Post by benfindlay on 2006-09-20
Just realised as well, samba users are stored in ```
/etc/samba/smbusers
``` not in the config file. Not switched on today! ](*,) 


You can however use the config file to allow guest access by changing the line marked ```
guest ok = no
``` to ```
guest ok = yes
``` and this IS located in /etc/samba/smb.conf ;)

HTH

---

### Post by Iowan on 2006-09-20
> **benfindlay said:**
> 
But if you're not entirely sure of what you're doing, then type ```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
``` to make a backup of the file first
Not a bad idea anyway - then you can strip away all the extra comments (and commented options) to make a more streamlined **smb.conf**... and have the original for reference, if required.

---

### Post by TailsAndy on 2006-09-20
It hasn't worked yet. It's just strange because neither he nor I ever set up a password.

I don't want to get rid of the password, I just want to get into the files.

Also, in 'Domain,' it says MSHOME, but in the router info [on the linksys website, when you go to the info that's saved in the router] there's no domain.


EDIT: It also already said ```
Guest ok = yes
```

---

### Post by benfindlay on 2006-09-21
I always set the domain in linux to my workgroup. Not sure if this is correct, but it works for me!

Did you do the following?
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

If this doesn't add your user name, then type
```
sudo useradd -s /bin/true your_username
```
And then type the password commands:
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

Another thing to note is that you will need to set their username and password to the same as on the other pc.

HTH

---

