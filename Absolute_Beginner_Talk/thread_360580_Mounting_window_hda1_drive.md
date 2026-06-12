---
title: "Mounting window hda1 drive"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-02-13
How do you mount the windows drive (hda1)?

I know many ask this question but I tried to login as root and it won't take my password!

Is this line correct to add to fstab?
/dev/hda1 /mnt/win ntfs nls=iso8859-1,ro,umask=0 0 0

This is what I get at the prompt:

davek@davek-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
davek@davek-desktop:~$ 

Why does this happen? This should be easy. Since you only have one password in Ubuntu. What else can it be? I can't add a line to fstab if I can't su in as root, can I?

---

### Post by taurus on 2007-02-13
```
/dev/hda1   /mnt/win   ntfs   nls=utf8,umask=0222   0   0
```
Please use the sudo, not su.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
gksudo gedit /etc/fstab
```

---

### Post by highneko on 2007-02-13
There is no root account by default on ubuntu for security. Try this if you want to temporarily mount windows:
```
sudo mkdir /windows; sudo mount /dev/hda1 /windows; sudo nautilus /windows || sudo konqueror /windows
```I don't know how to edit the fstab. Good luck.

---

### Post by geovino on 2007-02-13
> **taurus said:**
> ```
/dev/hda1   /mnt/win   ntfs   nls=utf8,umask=0222   0   0
```
Please use the sudo, not su.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
gksudo gedit /etc/fstab
```

OK, I did that and was able to add the line to fstab. 

Where do I go to see the drive? in the file manager I presume.... I found it under Network server. 

Now, if I want to see my hdb drive with PCLOS on it, would I add a line like this:
/dev/hdb   /mnt/pclos   ext3   nls=utf8,umask=0222   0   0

does that look right?
Thanks

---

### Post by taurus on 2007-02-13
Browse to /mnt/win with nautilus.

---

### Post by geovino on 2007-02-13
isn't nautilus the file manager?

How do I show the hdb drive which is pclos?

The /mnt directory is empty. How could that be. I now see the winxp partiton in Places > Network servers.

---

