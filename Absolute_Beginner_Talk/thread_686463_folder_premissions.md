---
title: "folder premissions"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by tet3828 on 2008-02-03
I have a Ubuntu Lamp server running with SMB file sharing enabled. My windows machines have all premissions to the WWW folder. This is what I need.[COLOR="Red"] however when I create a folder in the WWW directory the windows machines do not have write or delete access[/COLOR]. this is not good because one of the scripts I run on the server creates dynamic folders intended for the windows users to write files to. [COLOR="Red"]how can I give them permission?[/COLOR]

---

### Post by Dr Small on 2008-02-03
Try:
```
sudo chmod rwx /path/to/www
```

---

### Post by tet3828 on 2008-02-03
seems like were on the right track here, however that command returns an INVALID MODE error.

---

### Post by jan quark on 2008-02-03
try 
```

sudo chmod 777 /path/to/www
```

---

### Post by tet3828 on 2008-02-03
I typed:

sudo chmod 777 /var/www

and I still have no write access to the www SUB-FOLDERS.

---

### Post by iansane on 2008-02-03
Isn't the question how to make subfolders inherit permissions from the parent so you don't have to set each one individually? And doesn't mod 777 give full access to everyone and everything?

---

### Post by Dr Small on 2008-02-03
Sorry, it should have been:
```
sudo chmod +rwx -R /path/to/www
```

---

### Post by jan quark on 2008-02-03
```
sudo chown -R usr:usr /path/to/directory
sudo chmod -R 755 /path/to/directory
ls -la
```

change usr:usr to your username

---

### Post by tet3828 on 2008-02-03
:( I tried:
```
catuser@cats:~$ sudo chown -r catuser:catuser /var/www
```
and:
```
catuser@cats:~$ sudo chown -R catuser:admin /var/www
catuser@cats:~$ sudo chmod -R 755 /var/www
catuser@cats:~$ ls -la
```

I didnt get any errors but my XP stations still cannot write to the sub-folders of /var/www
my XP stations have now even lost write access to the www folder its self.
which sorta stinks because I am using a xp based web devloping program to create scripts on the server

---

### Post by jan quark on 2008-02-03
hmmmm

didi you try to set the permission from the other side I mean from XP

just guessing

---

### Post by tet3828 on 2008-02-03
I just tried. but xp says I dont have premission to set premission on the www folder.:mad:

note: my xp stations are all logged on with different usernames. if that makes a difference. not the same user name that I logon to ubuntu with.

---

### Post by tet3828 on 2008-02-03
this seems to have done it:
sudo chmod -R 777  /var/www

:guitar:

---

### Post by jan quark on 2008-02-03
great to hear

please mark this thread as solved so others find their answer more quickly 
thank you

---

### Post by tet3828 on 2008-02-03
hey I am back
so using:

sudo chmod -R 777 /var/www

works great to allow my xp users to access folders on my server.

but it seems every time a new folder is created the command has to ran again... which will be often considering the purpose this server...serves.

is there a way to avoid this??

---

### Post by tet3828 on 2008-02-03
sorry about the accidental double post
hey I am back
so using:

sudo chmod -R 777 /var/www

works great to allow my xp users to access folders on my server.

but it seems every time a new folder is created the command has to ran again... which will be often considering the purpose this server...serves.

is there a way to avoid this??

---

