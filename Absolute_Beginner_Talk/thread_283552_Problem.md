---
title: "Problem"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by stake on 2006-10-24
i want to extract something in here /usr/share/.... (after i open and some subfiles) but it says me "You don't have the right permissions to extract archives in the folder <folder i want to extract in it> " ... why ? what can i do ?

---

### Post by bulldog on 2006-10-24
You must use sudo because you need root acces to write to system folders.

---

### Post by stake on 2006-10-24
and how can i do it from the terminal ? and then that i will have to edit the .conf i am going to be able to edit it ?

---

### Post by Bachstelze on 2006-10-24
To edit a file from command line

```
gksudo gedit /path/to/file
```

will open it in Gedit with root access to it. OTOH, this ;

```
sudo nano /path/to/file
```

will open it in nano (command-line text editor) which is IMHO a better option. I don't like running GUI stuff as root when I can avoid it. Good opportunity to learn how to use vi :)

---

### Post by PriceChild on 2006-10-24
You may want to read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) to learn about sudo

---

### Post by stake on 2006-10-24
i get this now:

> gksudo gedit /usr/share/doc/eggdrop-data/examples/eggdrop.conf.gz

(gedit:15218): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

i have this problem because it is .gz ? what can i do ?

---

### Post by Bachstelze on 2006-10-24
AFAIK, pretty much everyone gets such messages when running GUI apps from the CLI. However, yout problem is thaz the file is GZIPped, you have to uncompress it first, the Archive Manager should do it fine.

---

