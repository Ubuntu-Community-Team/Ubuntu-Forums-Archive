---
title: "Cant install tarball ..."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by aachen on 2008-03-20
I am a newbie in linux and dont know how to install tarball.. I tried like following and I could go into the directory but when I try to configure it says no such file or directory. The extracted setup folder is in my home directory. and i get this same error while installing all tarball setups. please help me.


patelgopesh@patelgopesh-laptop:~$ cd '/home/patelgopesh/realplay-10.0.9'
patelgopesh@patelgopesh-laptop:~/realplay-10.0.9 $ ./configure
bash: ./configure: No such file or directory
patelgopesh@patelgopesh-laptop:~/realplay-10.0.9 $ make
cd common/runtime && make  SUBMAKEFLAGS="" -f Makefile
make[1]: Entering directory `/home/patelgopesh/realplay-10.0.9/common/runtime'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/home/patelgopesh/realplay-10.0.9/common/runtime'
make: *** [all] Error 2

---

### Post by bumanie on 2008-03-20
have you installed buil-essential. If not 
> sudo apt-get install build-essential
That's at least the first step

---

### Post by forestpixie on 2008-03-20
```
cd Desktop
``` first then have another go - and have you installed build essential - if not

```
sudo apt-get install build-essential
```

---

### Post by aachen on 2008-03-20
I tried but it says build essential is already installed...

---

### Post by Oldsoldier2003 on 2008-03-20
> **aachen said:**
> I am a newbie in linux and dont know how to install tarball.. I tried like following and I could go into the directory but when I try to configure it says no such file or directory. The extracted setup folder is in my home directory. and i get this same error while installing all tarball setups. please help me.


patelgopesh@patelgopesh-laptop:~$ cd '/home/patelgopesh/realplay-10.0.9'
patelgopesh@patelgopesh-laptop:~/realplay-10.0.9 $ ./configure
bash: ./configure: No such file or directory
patelgopesh@patelgopesh-laptop:~/realplay-10.0.9 $ make
cd common/runtime && make  SUBMAKEFLAGS="" -f Makefile
make[1]: Entering directory `/home/patelgopesh/realplay-10.0.9/common/runtime'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/home/patelgopesh/realplay-10.0.9/common/runtime'
make: *** [all] Error 2

is this actually a source package? check to see if you can just install it (look for an install script) or see if the config script is called something else. Sometimes it pays to take a moment and scan the readme and Install files in a tarball.

---

### Post by spiderbatdad on 2008-03-20
you need to look for a readme and/or install file in the extracted folder. it may run as an installer script like sudo ./realplay(whatever) from within the proper directory. There should be some instructions for installing it somewhere in the folder or on the download site.

---

### Post by Nepherte on 2008-03-20
You probably won't have to install it that way. Perhaps there's an install script or a .run or .bin file.
In any case, you have to read the readme and/or install file that is most likely included in the archive file.

---

### Post by forestpixie on 2008-03-20
you need to change directory to where it's been downloaded - if it's as standard for ff it'll be desktop - so do the command I gave and try from there

cd Desktop

---

### Post by bumanie on 2008-03-20
As the extracted file is in /home (I'm going from memory), in terminal
> cd ~/home 
> cd <filename> ./configure
> make
> make install
Hope my memory is good.

---

### Post by forestpixie on 2008-03-20
> make[1]: Entering directory `/home/patelgopesh/realplay-10.0.9/common/runtime'
make[1]: Makefile: No such file or directory
it's not in /home is it?

check what's in there

ls /home/patelgopesh

---

### Post by aachen on 2008-03-20
I want to install 5 programs. real player, firefox 3 beta 4, divx codecs, win rar and quick time player..
there are no instructions written for any program in read me file. and all are giving the same kind of error. I tried it from my desktop also and home directory also. but that doesnt help. firefox has a bin file but i dont know how to install it. and also run-mozilla.sh file. any suggestion ?

---

### Post by forestpixie on 2008-03-20
where exactly are the files downloaded to? you're going to need to give people more information here if you want help - 

firefox4 - where did you get that - ff3 is still in beta, I know in my ff3 folder there is a firefox.bin and firefox file - dbl click the firefox file it should run.

have you looked into linux equivalents for these - are you sure you have linux versions?

---

### Post by bumanie on 2008-03-20
To install rar (and unrar so you can unpack rar files)
> sudo  apt-get install rar unrar 

---

### Post by aachen on 2008-03-20
ok the firefox runs as you told and i installed it. I am sure all the setup files are correct and for linux. 
I am saving all the setup files on my desktop. Now I have a bin file for real player called 'RealPlayer10GOLD.bin' on my desktop. please guide me how to install .bin files.

---

### Post by tad1073 on 2008-03-20
where ever you havr the tar file downloaded to right-click on it and select extract here, (~ =  /home/your_user_name)
```
cd ~/wherever_the_file_is/filename
./configure
make
sudo make install
```

---

### Post by aachen on 2008-03-20
I downloaded the divx codec from this website :

[http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec) 

and extracted it on my desktop. then tried to install it in a usual way but still it gives this error:

patelgopesh@patelgopesh-laptop:~$ cd '/home/patelgopesh/Desktop/divx611-20060201-gcc4.0.1'
patelgopesh@patelgopesh-laptop:~/Desktop/divx611-20060201-gcc4.0.1$ ./configure
bash: ./configure: No such file or directory
patelgopesh@patelgopesh-laptop:~/Desktop/divx611-20060201-gcc4.0.1$

---

### Post by forestpixie on 2008-03-20
[http://ubuntuforums.org/showthread.php?t=621133](http://ubuntuforums.org/showthread.php?t=621133) 

for realplayergold

if you have downloaded files to your desktop and then can't find them in a terminal make sure you are using the correct command - case means something in linux


re the divx thing

do this please - if you're not in Desktop but are at home

```
cd Desktop
ls divx611-20060201-gcc4.0.1
```

why do you need the divx codec - do the restricted extras not work for you

---

### Post by forestpixie on 2008-03-20
for the divx it should be once youve naviagted to the correct folder

sudo ./install.sh

---

### Post by aachen on 2008-03-20
thanks a lot all the people for replying.. now i got all the softwares installed..
just one question. I installed avast antivirus from .deb file. double clicked it and simply installed it. 
But I cant see the avast icon anywhere on my panel or even in Applications or Sytem menu. Then I checked in add/remove and it shows that I have avast installed already but then why cant i see its icon anywhere ?

---

### Post by forestpixie on 2008-03-20
perhaps it doesn't have one - I don't know the command but try avast in a terminal - if not open synaptic instead of add/remove - search for avast - highlight and click the properties tab - look in the installed files - ther will likely be an entry that starts /usr - use whatever comes after that in a terminal.

You do know that you probably won't get any viruses - likley the onley use will be checking stuff before it gets sent to a win machine.

---

