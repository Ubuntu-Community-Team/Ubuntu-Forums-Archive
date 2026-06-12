---
title: "need help with copying files to ///usr/bin in root folder"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by linuxmann on 2007-10-06
I am trying to copy a ipodvidenc shell script to the root usr/bin directory to transfer videos to my ipod i was in the middle of [http://ubuntuforums.org/showthread.php?t=114946]("http://ubuntuforums.org/showthread.php?t=114946")trying to follow the steps but it is saying there is no file or directory when i try to copy the file.. I need help. I am in the teminal to do this but it seems not to be working. I have tried sudo, su, and cp. Nothing seems to be working so far.

---

### Post by Majorix on 2007-10-06
Hi linuxmann,
Have you tried
```
sudo cp /file/location /usr/bin/filename
```
?

---

### Post by linuxmann on 2007-10-06
it keeps saying this. if you can provide me with steps that would be fine.

justin@jolly:~$ sudo cp /file/justin/ipodvidenc /usr/bin/ipodvidenc
Password:
Sorry, try again.
Password:
cp: cannot stat `/file/justin/ipodvidenc': No such file or directory
justin@jolly:~$ su
Password:
root@jolly:/home/justin# cp /ipodvidenc/home/justin usr/bin/ipodvidenc
cp: cannot stat `/ipodvidenc/home/justin': No such file or directory
root@jolly:/home/justin#

EDIT: NVM It worked. Thanks.

---

### Post by ryanVickers on 2007-10-06
> The youngest kubuntu user... maybeCheck my profile ;) (and then some of the stuff I've made (signature (specifically the rar maker :p)))

To get to the point :), It looks like you've got the wrong name or something.  Are you sure it's mounted (correct path name) and everything is typed correctly?  It just doesn't look like anything on that page could wreck it...

---

### Post by jcorbeil on 2008-01-24
> **linuxmann said:**
> it keeps saying this. if you can provide me with steps that would be fine.

justin@jolly:~$ sudo cp /file/justin/ipodvidenc /usr/bin/ipodvidenc
Password:
Sorry, try again.
Password:
cp: cannot stat `/file/justin/ipodvidenc': No such file or directory
justin@jolly:~$ su
Password:
root@jolly:/home/justin# cp /ipodvidenc/home/justin usr/bin/ipodvidenc
cp: cannot stat `/ipodvidenc/home/justin': No such file or directory
root@jolly:/home/justin#

EDIT: NVM It worked. Thanks.

Not working for me.  it's sudo cp /name of the file or folder/username/directory file is in /usr/bin/name of copied file ?

I'm getting all sorts of  'no such file or directory' messages... And I'm a command-line dolt. :confused:

Thanks.

---

### Post by mr_ed on 2008-01-24
You have to make sure your locations are correct.  For example, 

```
root@jolly:/home/justin# cp /ipodvidenc/home/justin usr/bin/ipodvidenc
```
You probably just want ```
cp ipodvidenc /usr/bin/
``` if you're located in /home/justin.

In your command, you're telling it to copy the file "justin" from the location /ipodvidenc/home/, so that's wrong, and you're telling it to copy to a bad place.  (You missed the first "/" in front of "usr," so that would try and copy it to /home/justin/usr/bin/ipodvidenc

---

