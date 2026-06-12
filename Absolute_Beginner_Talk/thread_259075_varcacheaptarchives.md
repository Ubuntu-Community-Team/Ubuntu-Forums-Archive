---
title: "/var/cache/apt/archives"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-09-16
Is it safe to delete files within this folder?

Thanks

---

### Post by towsonu2003 on 2006-09-16
yes, it's safe to delete them. use either synaptic or apt-get. apt-get way is: ```
sudo apt-get clean
```
synaptic way is: 
1. launch synaptic
2. under settings -> preferences -> files -> temporary files, click on "delete cached package files"
3. done

note that you can also set your preferences about the apt cache in that same menu. I prefer to leave all the downloaded files in the cache indefinitely, because it makes life much easier if an upgrade breaks something. than you go to the cache (cd /var/cache/apt/archives), install a previous version (sudo dpkg -i ./package_name), and live your life until the break is fixed at which point I do the upgrade again (sudo apt-get update && sudo apt-get upgrade).

---

### Post by Dinerty on 2006-09-16
> **towsonu2003 said:**
> yes, it's safe to delete them. use either synaptic or apt-get. apt-get way is: ```
sudo apt-get clean
```
synaptic way is: 
1. launch synaptic
2. under settings -> preferences -> files -> temporary files, click on "delete cached package files"
3. done

note that you can also set your preferences about the apt cache in that same menu. I prefer to leave all the downloaded files in the cache indefinitely, because it makes life much easier if an upgrade breaks something. than you go to the cache (cd /var/cache/apt/archives), install a previous version (sudo dpkg -i ./package_name), and live your life until the break is fixed at which point I do the upgrade again (sudo apt-get update && sudo apt-get upgrade).

Thank you for the quick reply and advice !

---

### Post by k@y@ on 2006-10-23
I would like to know if i can change this folder to another partition. Because i think it's nice to backup these files.

With this way, apt-get downloads to another partition and when a formatting is needed, all the files downloaded before aren't lost...

---

### Post by Ben Sprinkle on 2006-10-23
```

sudo apt-get clean
```
Is good for it, else {
```
sudo rm -r '/var/cache/apt/archives/*.deb'
```
} :)

---

### Post by CatKiller on 2006-10-23
> **k@y@ said:**
> I would like to know if i can change this folder to another partition. Because i think it's nice to backup these files.

With this way, apt-get downloads to another partition and when a formatting is needed, all the files downloaded before aren't lost...

You need to learn the power of symbolic links: copy the contents of a directory somewhere else, delete the original directory and then make a symbolic link from the old place (called the same as the old directory) to the new place.

---

### Post by k@y@ on 2006-10-23
Thank you very much CatKiller. Now i have a backup of those files and it's safe to format root partition :)

---

### Post by az on 2006-10-23
> **CatKiller said:**
> You need to learn the power of symbolic links: copy the contents of a directory somewhere else, delete the original directory and then make a symbolic link from the old place (called the same as the old directory) to the new place.

You can also put them on cd

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
or the simple version:

[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

---

### Post by newrhyme on 2006-10-23
Hey all! ](*,) <---Here I am!

I am trying to open /var/cache/apt/archives, using the Synaptic Package Manager, but, when I go into "Root" ( sudo -i, or, sudo su, or, just su), the password I enter (have tried My own) ...won't open anything!!!!
And, every program is "closed" by error message ("wrong password")

Plus  ---  trying to open w/o root and going into "ROOT" console shell, in login screen doesn't work , either!

HELP!!!! HELP!!!!  ](*,) <---Look, here I am again!!!!

Signed me...

Newrhyme

---

### Post by ghoran on 2008-02-12
This was very helpful THANKS!!!!!

---

