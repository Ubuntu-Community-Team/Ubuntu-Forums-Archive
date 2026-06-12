---
title: "File permission problem"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2005-10-18
I created the directory /osshare to share files between windows and linux. At first I found I could not put any files into the directory and so I looked at the permissions for the directory, The root user had full permission but me as an ordinary user only had read permission

I being new to linux went on the internet to learn how to change permissions through the command line so i could write into the directory too. 

I found the chmod command and tried to change permissions both using sudo and (very carefully) with su but with no success. Using the ls -l command showed that the permissions were still set to drw- r-- r--.

Any help is appreciated.

---

### Post by LHZ on 2005-10-18
What exact syntax did you use? Keep in mind that if you are logged in as root setting u+rwx just gives those permissions to root. To make the directory read/write/executeable by everyone, just set:

> sudo chmod go+rwx /osshare

This gives all memebrs of the root group and all other users full privileges on the file. An added benefit is that you can now change the file permissions as a normal users.

Just to be sure, are you sharing /osshare between different Linuxes? Otherwise, you have to find a way to make it Fat32, or Windows won't be able to read/write to it. I don't know wether that's possible without making a new partition.

---

### Post by blueoyster on 2005-10-18
I used sudo chmod go=rwx osshare, I see now I left out the slash. 
However I did remember to make it FAT32

Thank you very much for your help.

---

### Post by blueoyster on 2005-10-18
alright now there is a new problem....

Using the new and imporived syntax i managed to give everyone read and browse permissions but I cannot give anyone outside root write privileges.

I tried both sudo chmod go=rwx /osshare and
sudo chmod go+w /osshare, but it wont allow me to do so.

---

### Post by Murgle on 2005-10-18
I would reccomend just changing the ownership to your local user then if you are more comfortable you can change the permissions in the properties window.  

sudo chown username:\ /directorygoeshere -R

will make /dierctorygoeshere and all of it's sub folders be owned by username

---

### Post by blueoyster on 2005-10-18
Sorry to bother yet again.

I tried to change owner ship of /osshare but I was unable to.
After running "sudo chmod alex /osshare -R" i was prompted for the password and then an error mesage said:

chown: changing ownership of `/osshare': Operation not permitted

Is there any reason why it would not be permitted even when using sudo?

---

### Post by LHZ on 2005-10-19
chmod is for changing permissions. If you want to change the owner or group  file belongs to, use chown (CHange OWNer):

> sudo chown -R alex /osshare

Also, you usually set the command line options (such as -R) before the users or file.

---

### Post by blueoyster on 2005-10-19
Sorry, my mistake.
There is typo in the my previous post, 'chmod' should read 'chown.' 
I actually DID use the chown command. 

I apologize about the misunderstanding

---

### Post by Murgle on 2005-10-19
who owns the file?  that might have bearing on changing the ownership, also is the file used for a seperate partition?  if so I think you need to add something to your /etc/fstab to allow for access to others.

---

### Post by blueoyster on 2005-10-19
The root user own the file, and since it had to be FAT32 I created it on a separate partition. Do you know what I'll have to change in /etc/fstab?

---

### Post by Murgle on 2005-10-19
I think that it is uid=000 and you put that after defaults in the options column you seperate them with a comma

---

### Post by blueoyster on 2005-10-20
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
           /dev/hda9       /osshare            vfat   defaults,uid=000      0            0

Alright, so this is what the /osshare part of fstab look like now. After editing I went back and tried chmod again but still with no luck. Then I tried to chown and that didnt work at all. So I am still unable to write to /osshare.
I am not sure what else to do.

---

### Post by blueoyster on 2005-10-21
Sorry for double post but doesnt anyone know what else I could do?

---

