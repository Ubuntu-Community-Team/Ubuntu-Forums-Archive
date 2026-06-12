---
title: "My first Bash Script"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by prodonjs on 2007-01-15
Well as I was told, once I began operating in a command-line based environment I was going to realize how convenient and cool scripts can be. I finally have my first real usage for a custom script.

What I want to do is have a script so that when I connect to my college via a VPN, I can run the script to automatically mount the three network drives I need into my homespace.

I'm not exactly sure how to do it though because I know I have to use my school username and password to access the drives through Samba and I'm really starting blind with this. I figured it would be a good exercise to familiarize myself with shell scripts.

I'm pretty fluent in the C based languages and I'm a computer science major so I pick things up pretty quickly, but the only way to learn things is to do it so I was hoping someone could give me some pointers on how to get started with this one. Thanks everyone.

---

### Post by rccharles on 2007-01-15
This page has the info you requested:

[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

Robert
:cool: 
;) and don't forget google.com

---

### Post by prodonjs on 2007-01-16
Hey thanks for the link. I've edited my fstab file before when I originally set up Kubuntu on my machine. I edited it so that my Windows FAT32 partition would get automatically mounted at startup but for these three network drives, I don't want them to always get mounted, I just want to be able to mount them quickly whenever I connect to my VPN and this unmount them after I disconnect. That's why I thought it would be convenient to have a script to mount them and another one to unmount, or just one script with a paramater to signify whether I wanted to mount or unmount.

---

### Post by rccharles on 2007-01-17
> **prodonjs said:**
> Hey thanks for the link. I've edited my fstab file before when I originally set up Kubuntu on my machine. I edited it so that my Windows FAT32 partition would get automatically mounted at startup but for these three network drives, I don't want them to always get mounted, I just want to be able to mount them quickly whenever I connect to my VPN and this unmount them after I disconnect. That's why I thought it would be convenient to have a script to mount them and another one to unmount, or just one script with a paramater to signify whether I wanted to mount or unmount.

Here is an example script:
#!/bin/bash

echo "testing... $*"

if [ "$1" = "abc" ]
then
  echo "first eq test worked"
fi

function debug()
{
  echo "debug... $*"
  set $*
  for arg
  do
     #echo "echo -n \ $arg=\$$arg \ "
     eval "echo -n \ $arg=\$$arg \ "
  done
  echo ""
}
declare -i lines=24
declare -i columns=80

debug "lines columns"

call it sample.  Do the following command to mark it runable.

chmod +x sample

to run:

. ./sample "abc"


Bash scripts get a bit cryptic.  

A better scripting language, in my view, is Python.  

...

You can specify the noauto option in fstab to prevent the filesystem from automatically mounting at boot time.  You will have to manually mount this file system.  See:
man fstab 
for details.

With an fstab entery, you can use a shortened mount command like:
mount /media/common




Robert

---

### Post by prodonjs on 2007-01-18
Ok well I'm working on just getting the three drives to mount first before I do any editing of the fstab file. Unfortunately, I cannot get any of them to mount although I can view the files when I go to Konqueror and type in smb://xxx.xxx.xxx.xxx/shared$ and then it prompts me for my campus domain and login name and password. When I do that it works and I can view the folder structure in Konqueror.

However when I try something like this in the terminal

sudo smbmount //172.16.100.250/shared$ /home/jason/mapped_Drives/homeSpace -o username=CAMPUS\<username>,password=<password>

I get a message saying I cannot access the file. What could I be doing wrong because as I said, it works in Konqueror but I would really prefer to mount these network drives to my home folder.

---

### Post by prodonjs on 2007-01-19
Ok now I have gotten it to work. I created a credentials file with my username and password for the share and also added three mount points to my fstab file and set them to noauto. The only things that I need to do now are make it so that any user can mount (not just root) and also I would like to shorten the command so that I could just say something like mount SHARED instead of having to say mount /home/jason/mapped_Drives/campusPub ...etc for the other two. Thanks so much for all the help so far though.

---

### Post by rccharles on 2007-01-19
> **prodonjs said:**
> Ok now I have gotten it to work. I created a credentials file with my username and password for the share and also added three mount points to my fstab file and set them to noauto. The only things that I need to do now are make it so that any user can mount (not just root)

Try the user option.  I've also seen a users option, but I do not see it in the man fstab documentation.
>  and also I would like to shorten the command so that I could just say something like mount SHARED instead of having to say mount /home/jason/mapped_Drives/campusPub ...etc for the other two. Thanks so much for all the help so far though.

One way would be to create a local variable. Put your local variable in .bashrc.

abc="/home/jason/mapped_Drives/campusPub"
mount $abc

You could write a script to do this too.

Also, try the ln -s command.  I think if you put the symbolic link fstab it might work. And I can't remember the format of the ln -s command.


Robert
:guitar:

---

### Post by Buck2348 on 2007-01-20
In the option field of the fstab line, "user" allows an ordinary user to mount the filesystem, and only that user can unmount it.  "users" allows every user to mount and unmount the filesystem.  (From man mount).

Buck

---

### Post by rccharles on 2007-01-20
> **prodonjs said:**
> mount /home/jason/mapped_Drives/campusPub ...etc for the other two. 
Why don't you put the drive in /media/myname?  The /media directory is defined for user mounted drives.

sudo mkdir /media/myname

ls -ld /media/myname
sudo chmod o+w /media/myname
ls -ld /media/myname

Not sure you need the chmod command.

change fstab and you can mount
mount /media/myname
You can add a symbolic link ( ln -s ... )  for your existing directory.

> Thanks so much for all the help so far though.
Glad to be of assistance.

---

