---
title: "Unable to delete .odt files in Trash"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by garthcrocker on 2007-06-18
I've got two .odt files I deleted stuck in my Trash and can't delete them because the owner is root. I've tried following the advice given to similar questions such as use gksudo nautilus etc but got nowhere. It's not vital but annoying!

---

### Post by testube_babies on 2007-06-18
This will change the permissions on all files in the trash can so that you can delete them:
```
sudo chmod -R 777 ~/.Trash
```

---

### Post by garthcrocker on 2007-06-18
Many thanks but tried that and still no deal! Still says root is the owner I fear.

---

### Post by coffeecat on 2007-06-18
Try:

```
sudo rm /home/yourusername/.Trash/*.odt
```

---

### Post by garthcrocker on 2007-06-18
Many thanks. I tried that too but it just said no such file or directory. The mystery deepens.:-k

---

### Post by Golyadkin on 2007-06-18
please do a 
> 
sudo ls -la ~/.Trash/ 

and post the results here.

---

### Post by wormser on 2007-06-18
Here is another thing to try.

```
 gksudo nautilus
```

Then navigate to your home folder and into the trash.  You might have to go to View then Show Hidden Files.

---

### Post by garthcrocker on 2007-06-18
Herewith the data you asked for.


garth@garth-desktop:~$ sudo ls -la ~/.Trash/
Password:
total 8
drwxrwxrwx  2 garth garth 4096 2007-06-18 15:38 .
drwx--x--x 45 garth garth 4096 2007-06-18 19:03 ..
garth@garth-desktop:~$

---

### Post by garthcrocker on 2007-06-18
Just remembered where these files came from. I deleted them in Nautilus.

---

### Post by garthcrocker on 2007-06-18
OK guys. The heats off. I managed to trace them and got rid of them! Phew! Many thanks to all.:popcorn:

---

### Post by Golyadkin on 2007-06-19
Alright, glad to hear you got it fixed!

---

