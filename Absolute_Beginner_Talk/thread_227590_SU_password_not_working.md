---
title: "SU password not working"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by philefluxx on 2006-08-01
Im a little new to the linux enviorment but when I open the terminal and try to log in the SU it says my password is wrong. Well I know its right since I use the same pass to log in to the computer. I can SUDO something and the password works. Im not sure what Im doing wrong, oh and I did try "root" knowing that from my previous attempts at Fedora and that doesnt work either. Any one have any ideas?

---

### Post by Kilz on 2006-08-01
> **philefluxx said:**
> Im a little new to the linux enviorment but when I open the terminal and try to log in the SU it says my password is wrong. Well I know its right since I use the same pass to log in to the computer. I can SUDO something and the password works. Im not sure what Im doing wrong, oh and I did try "root" knowing that from my previous attempts at Fedora and that doesnt work either. Any one have any ideas?

On Ubuntu use sudo instead of su. Root is disabled in Ubuntu. If you need a gui to work with files as root, open a terminal and type in
```
gksudo nautilus
```
then hit enter.

---

### Post by philefluxx on 2006-08-01
actually I did also try SUDO and its requireing another command. Sorry Im a newb but shouldnt SUDO come up with something else?

---

### Post by 5-HT on 2006-08-01
As Kilz mentioned, the root account is locked by default in Ubuntu.
The following wiki page may be of help: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

EDIT: 
			 		 		 		[quote=philefluxx]
actually I did also try SUDO and its requireing another command. Sorry Im a newb but shouldnt SUDO come up with something else? [/quote]

  	 		 		 		 		 		 	 		 Are you looking for a root shell?
If so:

 ```
 sudo -s 
``` 
Alternatively, the following should work as well:
```
 sudo su 
``` 
For both of the above, to exit the root shell:
```
 exit 
```

---

### Post by cstudent on 2006-08-01
sudo should be followed by a command to execute as root.

For example:
```

sudo chmod +x mybashscript.sh

```

---

### Post by jineesh on 2006-08-31
try
     sudo -i

---

