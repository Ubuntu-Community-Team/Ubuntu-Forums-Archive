---
title: "ATI video driver installation"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by noezoom on 2005-12-17
first of all, i'm not sure that the drivers i downloaded will work with my card (X300 SE).  i downloaded drivers for radeon 8500 and better, which seemed like the best bet.

second, i can't figure out how to run the installation, mostly because i don't know how to do anything in command line beyond copy things i see on the internet.  the istallation instructions told me to type "./ati-drivers-blah-blah.run" which told me permission was denied.  i'm 90% sure i'm in super user mode, but it still tells me that permission is denied.

any clue what i'm doing wrong?  if the drivers aren't a good match am i going to do any serious damage?  thanks

---

### Post by drummer on 2005-12-17
Are you doing "sudo ./ati-drivers.run" ? If that's not working, try "sudo su" then "./ati-drivers.run" to get into a full root shell before installing. Installing them shouldn't mess anything up, just make sure you have a backup of your xorg.conf file so you can go back if something goes wrong. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by noezoom on 2005-12-17
here's an account of what happened:
```
$ ./ati-driver-installer-8.20.8-i386.run
bash: ./ati-driver-installer-8.20.8-i386.run: Permission denied
$ sudo su ./ati-driver-installer-8.20.8-i386.run
Unknown id: ./ati-driver-installer-8.20.8-i386.run
```

---

### Post by Rackerz on 2005-12-17
Ok, i had this problem earlier today. ATI fails to specify that you should also try using the 'sh' command. Try this;

> sh ./ati-driver-installer-8.20.8-i386.run

If you get permission denied, try putting 'sudo' before the sh.

---

### Post by drummer on 2005-12-17
[QUOTE=noezoom]here's an account of what happened:
```
$ ./ati-driver-installer-8.20.8-i386.run
bash: ./ati-driver-installer-8.20.8-i386.run: Permission denied
$ sudo su ./ati-driver-installer-8.20.8-i386.run
Unknown id: ./ati-driver-installer-8.20.8-i386.run
```[/QUOTE]
Sorry noezoom, I meant "sudo su" then <enter> and "./ati-driver.run" on the next line (executed as a separate command). I should be more clear :rolleyes:
```
user@computer$  sudo su
password:
root@computer#  ./ati-driver.run
```

---

