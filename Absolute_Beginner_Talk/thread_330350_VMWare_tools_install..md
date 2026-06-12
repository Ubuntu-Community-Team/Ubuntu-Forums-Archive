---
title: "VMWare tools install."
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Wall86 on 2007-01-03
hello, after fighting relentlessly with a full ubuntu install, i had to resort to a macrohard install under VMWare, and now, ubuntu seems to not want to install VMWare tools, so i have some very very laggy hardware support? and help on installing these tools.

what usually happens? i click on the "run in terminal" and it usually does nothing. no error messages. nothing at all. 

any help?

---

### Post by jordanmthomas on 2007-01-03
I may be mistaken, and if I am please disregard this, but is it a .deb file?

If so, here is how you need to install it:
Applications --> Accessories --> Terminal
once it opens,
```
cd ~/Desktop
sudo dpkg -i *.deb

```


If it is not a deb, then it is probably an sh script.  If this is the case:
Applications --> Accessorries --> Terminal
```

cd ~/Desktop
sudo chmod +x *filename.sh*    #  sudo may not be needed, but it won't hurt
sudo ./filename.sh

```

If neither of these work, just let us know what kind of file it is and we can see if we can get things rolling

---

### Post by Lod on 2007-01-11
Which version of VMWare (and tools) are you using? Try updating to the latest one.

I had a similar, perhaps even the same problem.
I'm using VMWare on Windows XP and made an Ubuntu virtual machine. The installation went fine. In one of the menus of vmware there is an option called Install vmwaretools.
This mounts a (virtual) cdrom with two packages: a rpm file and a tar file. I unpacked the tarfile to a temporary directory and ran the vmware-install.pl file. To all questions I answered the default values.
After the install he said something about problems with the Xorg version. So I updated my vmware from 5.5.1 to 5.5.3 and now it's working nicely.

---

