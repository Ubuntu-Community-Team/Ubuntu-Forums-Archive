---
title: "How to install these files?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-08-05
I have modem drivers for linux supplied by my manufacturer. I dont know how to install these files. I dont have an internet connection in kubuntu and I am dual booting my PC. Is there a way to install these files and I am not that great in the terminal. Please help me. :(

Thanks In Advance...

---

### Post by hc2995 on 2007-08-05
Well, most likely you will need to use the terminal. Extract the files to the desktop and then type this into the terminal:

```

sudo -i
<ENTER PASSWORD>
cd /home/USERNAME/Desktop/FOLDER_OF_FILES_NAME
./configure
make
make install

```

That should do it, however, you may not have the right compilers to install it. If you get errors like "No c compiler" then you MUST execute this command first

```

sudo apt-get install build-essential

```


Lemme now if you need more help

---

### Post by Rabindranath on 2007-08-05
There are not any .configure files in it. I think they are for red hat. Only 3 files in it.

---

### Post by ticklecricket on 2007-08-05
Unzip the files. Then execute the installer.

to execute it just type './programname' in the terminal.

That *should* do it, but I'm just guessing.

---

### Post by jvc26 on 2007-08-05
If you make the installed file executable (right click, permissions, make executable) Then go to terminal, change to the directory of the file, then type sudo ./filename - does that work?
Il

---

### Post by AlexenderReez on 2007-08-05
> **Illuvator said:**
> If you make the installed file executable (right click, permissions, make executable) Then go to terminal, change to the directory of the file, then type sudo ./filename - does that work?
Il

hm..it suppose to work.....actually the easiest way is to install **nautilus-open-terminal**....you can open terminal in any nautilus folder and just run any executable file:)

---

### Post by kirios on 2007-08-05
> I dont have an internet connection in kubuntu
[COLOR="DarkRed"]Did you try changing the location in kppp? [/COLOR]
[http://ubuntuforums.org/showpost.php?p=2960122&postcount=11]("http://ubuntuforums.org/showpost.php?p=2960122&postcount=11")

---

### Post by Rabindranath on 2007-08-05
I have tried ./filename but for the files it says

Cannot install binary file.

If I tried opening "install_Binary_RH90_oasis_beta", it says the following in the terminal.



rabindranath@rabindranath-desktop:/media/sda5/Linux 9.0$ ./install_Binary_RH90_oasis_beta
-e
-e ***** MAKE NODE FOR MODEM DRIVER *****
ERROR: Module ptserial does not exist in /proc/modules
ERROR: Module pctel does not exist in /proc/modules
rm: cannot remove `/dev/modem': Permission denied
mknod: `/dev/ttyS15': Permission denied
chgrp: cannot access `/dev/ttyS15': No such file or directory
chmod: cannot access `/dev/ttyS15': No such file or directory
ln: creating symbolic link `/dev/modem' to `/dev/ttyS15': File exists
rm: cannot remove `/dev/ttyS1': Permission denied
ln: creating symbolic link `/dev/ttyS1' to `/dev/ttyS15': File exists
-e
-e ***** LOADING BINARY pctel_RH90_oasis_beta.o MODULE *****
insmod: error inserting 'pctel_RH90_oasis_beta.o': -1 Operation not permitted
-e
-e ***** LOADING BINARY ptserial_RH90_oasis_beta.o MODULE *****
insmod: error inserting 'ptserial_RH90_oasis_beta.o': -1 Operation not permitted
-e
-e ***** DONE *****
rabindranath@rabindranath-desktop:/media/sda5/Linux 9.0$
rabindranath@rabindranath-desktop:/media/sda5/Linux 9.0$

---

### Post by Rabindranath on 2007-08-05
What should I do to install those files if I have the error? Please help me:confused:

---

### Post by kirios on 2007-08-05
[COLOR="Red"]This post in your other thread suggests that your modem is supported. If so, you don't need to install Red Hat drivers. Why not try kppp first?[/COLOR]
[http://ubuntuforums.org/showpost.php...2&postcount=11]("http://ubuntuforums.org/showpost.php...2&postcount=11")

---

