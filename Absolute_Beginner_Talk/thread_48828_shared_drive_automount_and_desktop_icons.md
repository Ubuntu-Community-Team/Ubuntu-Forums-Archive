---
title: "shared drive automount and desktop icons"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by akechi on 2005-07-14
hi all!
im pretty new to linux.  i've got the basics down, but still dont know much.  i've been through a couple of distros until i landed here.

anyway, i was wondering,  when i use mepis, if i created shared windows drives, they would automount and show up on the desktop.  can anyone tell me how to do this with ubuntu?  also if possible, how to select the icons it will use.   oh yeah, one more thing.  if i am install a program from a tar file, where would be a good place to install to?  kinda like how windows has program files dir, is there something similar in linux?  i kinda dont like putting everything in my home folder, gets too cluttered for me.  i like things simple and in order, and to have a purposefull place too.
well thanks in advanced for any help.  after i finish my last year of computer networking and network security i plan on having fun with linux. they will be teaching us how to support it, use it, and compile our own versions of gentoo and slack.  
ok im done, i babble too much,  cheers!

---

### Post by adwait on 2005-07-14
Hey!

Well, first off for the automounting thing, you can make entries in the /etc/fstab file for mounting the drives automatically at start up. To edit the file use
sudo gedit /etc/fstab.

In the file you should add,
<replace x with whichever drive u want to mount, if you don't know which one, first use sudo fdisk -l to find out>

/dev/hdaX <TAB> /mnt/<location> <TAB> auto <TAB> rw,user,uid=1000,gid=1000

/mnt/location should be the folder where you want to mount that drive (basically, any empty folder will do).

Now, to make icons on the Desktop, right click on the desktop and click create launcher. In the space for command, type nautilus /mnt/location (replay /mnt/location with the location you mounted your drive to).

Phew! ;)

Ok... now about installing tar files. It is advisable that you install mostly from deb files. But if you have to, install to /opt.

---

### Post by akechi on 2005-07-14
WOW! thanks for the detailed info :)
one more question, if i want to mount windows shared drives will they be located in my fstab?  if not, where would i point fstab to to automatically mount them?
sorry.  one more.  can i somehow, network ubuntu and win together using ubuntu as the server (i think thats what i mean).  basically,  i set up samba to give my win machine access, but the only way in win i can view the ubutu machine is if i create a network connection using the same workgroup, but, when i view the machine in ubuntu, i get the actual pc's icon, then, i get a windows workgroup or network icon which leads me to the same area as the pc icon would if i clicked on it?!?  i assume its because of the network i created with windows but that was the only way to get ubuntu to show up.   i dunno.  i really didnt see anything pertaining to this in the ubuntuguides or in any searches here.   i'll stop now, im at work and need to.......... work!
thanks again for the help

akechi

---

### Post by adwait on 2005-07-15
Hey,

Yes, windows drives (infact any type of drives) can be mounted in the fstab file.

Sorry, dunno much about networking.........You'd be better of starting a new thread for that : ).

---

