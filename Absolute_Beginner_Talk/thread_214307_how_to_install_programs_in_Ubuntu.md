---
title: "how to install programs in Ubuntu ?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by mco on 2006-07-12
Hi, im trying to install some programs in ubuntu but dont know how to do so.
These programs are not availabre from Synaptic :( 

Winrar For Linux 3.1.0 Tar.gz
CrossOver.Office.Professional.v4.0.Linux.sh.tar.bz2
GoogleEarthLinux.bin

I think I need to use a terminal but I dont know how this stuff works, I cant even change the directory I am in.

Would anybody be so kind as to help me :) 

Thanks in advance.

---

### Post by Kilz on 2006-07-12
> **mco said:**
> Hi, im trying to install some programs in ubuntu but dont know how to do so.
These programs are not availabre from Synaptic :( 

Winrar For Linux 3.1.0 Tar.gz
CrossOver.Office.Professional.v4.0.Linux.sh.tar.bz2
GoogleEarthLinux.bin

I think I need to use a terminal but I dont know how this stuff works, I cant even change the directory I am in.

Would anybody be so kind as to help me :) 

Thanks in advance.

[Take a look here for more info]("http://www.monkeyblog.org/ubuntu/installing/")

---

### Post by mco on 2006-07-12
Thaks, that guide seems to be usefull but I'm afraid i'm still have problems

what have I done wrong?

alan@evo:/$ cd ..
alan@evo:/$ cd /home/alan/alan/programas/rar
alan@evo:~/alan/programas/rar$ ./configure
bash: ./configure: No such file or directory
alan@evo:~/alan/programas/rar$ make
make: *** No targets specified and no makefile found.  Stop.
alan@evo:~/alan/programas/rar$

---

### Post by autocrosser on 2006-07-12
Take a look at some of the other threads on building software--you need about 12/15 different libraries & helper apps--g++, gcc, auto-conf & some others to set-up your enviroment. Start with this---
"To proceed you must have the compiler tools installed. They all come with the package *build-essential*, available in Synaptic."
 
Once these are in place, you can build anything you want.....

---

### Post by Kilz on 2006-07-12
> **mco said:**
> Thaks, that guide seems to be usefull but I'm afraid i'm still have problems

what have I done wrong?

alan@evo:/$ cd ..
alan@evo:/$ cd /home/alan/alan/programas/rar
alan@evo:~/alan/programas/rar$ ./configure
bash: ./configure: No such file or directory
alan@evo:~/alan/programas/rar$ make
make: *** No targets specified and no makefile found.  Stop.
alan@evo:~/alan/programas/rar$

When you extracted that archive, what files were inside it?

---

### Post by mco on 2006-07-12
Files inside are;

default.sfx  Makefile   rar_faq.txt   rar_static  register.txt  unrar
file_id.diz  order.txt  rarfiles.lst  rar.txt     rereg.txt     whatsnew.txt
license.txt  rar        rar_site.txt  readme.txt  technote.txt

This is what i've been up to so far:

alan@evo:~/alan/programas/rar/rar$ su root
Password:
root@evo:/home/alan/alan/programas/rar/rar# cd /home/alan/alan/programas/rar/rar
root@evo:/home/alan/alan/programas/rar/rar# ./configure
bash: ./configure: No such file or directory
root@evo:/home/alan/alan/programas/rar/rar# make
cp rar unrar /usr/local/bin
cp rarfiles.lst /etc
cp default.sfx /usr/local/lib
root@evo:/home/alan/alan/programas/rar/rar# sudo make install
cp rar unrar /usr/local/bin
cp rarfiles.lst /etc
cp default.sfx /usr/local/lib
root@evo:/home/alan/alan/programas/rar/rar#

---

### Post by cbudden on 2006-07-12
'You shouldn't need to install winrar, as support for rar archives are provided.

```

sudo apt-get install unrar

```

This will let you extract RAR archives in Ubuntu.

With the crossover file, right click the file and click "Extract Here".  You should have a file ending in .sh, double click it and click "run".  Do the same with the google earth file.  Just double click it and it should run.

---

### Post by mco on 2006-07-12
Thanks again but;


root@evo:/# sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

---

### Post by mco on 2006-07-12
Oh, I've just installed crossover perfectly, thank you ever so much!!!

However I cant do the same with google earth;


Could not open the file /home/alan/alan/programas/GoogleEarthLinux.bin.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

...hum... GoogleEarthLinux.bin sounds like a binary file so... im doing something wrong right?

---

### Post by Brunellus on 2006-07-12
> **mco said:**
> Oh, I've just installed crossover perfectly, thank you ever so much!!!

However I cant do the same with google earth;


Could not open the file /home/alan/alan/programas/GoogleEarthLinux.bin.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

...hum... GoogleEarthLinux.bin sounds like a binary file so... im doing something wrong right?
you need to execute it.  first make it executable:

```
chmod +x GoogleEarthLinux.bin
```

then execute it

```
sh GoogleEarthLinux.bin
```

---

### Post by mco on 2006-07-12
Oh I actually made it executable (in graphic mode) and it seemed it was going to work because I was offered to select run, but when I pressed it in less than a second something opened and then got close... (??)

However I'm more worried about how to open rar files as I said, let me quote:

 	'You shouldn't need to install winrar, as support for rar archives are provided.
Code:
sudo apt-get install unrar

mco  	Thanks again but;


root@evo:/# sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

---

### Post by aysiu on 2006-07-12
[http://www.codeweavers.com/support/docs/crossover-pro/install](http://www.codeweavers.com/support/docs/crossover-pro/install)
may help for Crossover Office

[http://www.ubuntuforums.org/showpost.php?p=1138374&postcount=24](http://www.ubuntuforums.org/showpost.php?p=1138374&postcount=24)
may help for Google Earth

For unrar or rar, you need extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

