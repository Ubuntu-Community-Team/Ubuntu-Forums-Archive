---
title: "shared folders????? Mount not working"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-10-02
good day ubuntu members!!!

I need some assistance with respect to nfs.

I'm presently using a fingerprint identification board that has an embedded linux kernel version 2.4.19 rmk7. I have a PC that has UBUNTU installed on it. My aim is to create code that will design applications for this board. This board is referred to as [COLOR="Red"]SM01[/COLOR].

The board came with an cd that needed to be installed on the PC so that I will have all the required libraries, etc neccesary for coding the board. During installation of this cd an nfsshare working directory was created. I went to SYSTEM -->ADMINISTRATION ---->SHARED FOLDERS and I found my nfsshare directory in the SHARED FOLDERS.

When I typed this command in the SM01 terminal it gives an error:

```
mount -t nfs host:/nfsshare /mnt/nfs
```

NB. Host is replaced with my PC ip address which is 10.10.10.10. this is the error that I get.

```
mount: 10.10.10.10:/nfsshare failed, reason given by server: No such file or diy
```

I even tried replacing /nfsshare with /home/bee/nfsshare and the error returned said permission denied but in the sm01 terminal I am already logged in as root](*,)

---

### Post by llamakc on 2006-10-02
The permission denied error is coming from the 10.10.10.10 computer. Fix the nfs permissions on that side and give it another try.

---

### Post by cinderella on 2006-10-02
> **llamakc said:**
> The permission denied error is coming from the 10.10.10.10 computer. Fix the nfs permissions on that side and give it another try.

how do i fix the nfs permissions from my PC?????

---

### Post by llamakc on 2006-10-02
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Look to the Installation & Configuration | Shares part.

---

### Post by cinderella on 2006-10-02
> **llamakc said:**
> [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Look to the Installation & Configuration | Shares part.

in my home directory of my PC typed in the followin.

ifconfig eth0 10.10.10.10

and then in my sm01 terminal I typed:

ifconfig 10.0.0.1

when I pinged it they both worked.

i looked at my ip table and it told be that

destination 10.0.0.0 
gateway  0.0.0.0

Why is my destination 10.0.0.0 and how do i change it to 10.0.0.1

or should i change it to 10.10.10.10??????

:confused:

---

### Post by llamakc on 2006-10-02
What have you put in /etc/exports on the HOMEPC(Ubuntu)?

Separate issue, but is your network setup properly?

---

### Post by cinderella on 2006-10-04
> **llamakc said:**
> What have you put in /etc/exports on the HOMEPC(Ubuntu)?

Separate issue, but is your network setup properly?

i put the following in my /etc/exports:

/nfsshare *(rw,all_squash)

The board came with an installation cd and during installation the working directory : nfsshare was created.

I found this directory in the System ---> Administration ---> Shared Folders.

But when I type the followingon in my home PC I get file or directory not found:

ls -l /nfsshare

why can i not find this directory


I really appreciate ur help!!! since u seem like the only one helping me!!!! :D 

I'm quite new to linux and ubuntu so If u want me to be more clear or tell u step by step what i did i will let u know.

Really thanks for ur help

---

