---
title: "how make backup ,restore by command line"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by msn4us on 2006-12-08
...now i broke my system and also my CD drive not working..and i cant enter 

coz i had (Segmentation fault) ](*,) so cant boot

i remember i had befor backup in my system..

so how i make restore by commond line

:confused:

---

### Post by msn4us on 2006-12-08
> **msn4us said:**
> ...now i broke my system and also my CD drive not working..and i cant enter 

coz i had (Segmentation fault) ](*,) so cant boot

i remember i had befor backup in my system..

so how i make restore by commond line

:confused:

no body know](*,) ](*,)

---

### Post by devnulljp on 2006-12-08
Depends what you mean by backup. 
How did you do backup? If it's a tar all you need to do is tar xvf <name of tarfile>
How did you break the system?
What sort of problem do you have?
Can you boot at all?
Can you enter repair mode (from the grub prompt).

I suspect you may have killed X so you can still get in on the command line? If so, easiest fix is:
sudo dpkg-reconfigure -phigh xserver-xorg
That will reset your xorg.conf
But without more information it's impossible to be more helpful.

---

### Post by msn4us on 2006-12-08
> How did you break the system?

i dont remmember but the main problme i cant boot at all and i think file 
```
/sbin/init
```
was broke


 and take loog time like freeze and stop ](*,) ](*,) 

so what i do now:-k

---

### Post by devnulljp on 2006-12-12
Not much info to go on. It's impossible to tell what your problem is, or how to fix it.
My suggestion would be boot from the live cd/dvd, back up your data (you can mount your drive with sudo mount -t ext3 /dev/hda1 /media/somemountpoint) and then reinstall. 
(Take off and nuke it from space, it's the only way to be sure).

---

### Post by xyz on 2006-12-12
> ...now i broke my system and also my CD drive not working..and i cant enter

Well that doesn't sound good! System is broke; so is your CD-ROM...if I understood you correctly?
Do you have a floppy on your computer?

---

### Post by SpearZ on 2007-10-19
I'm relatively new to Ubuntu (my background is in Windows), but this line:
sudo dpkg-reconfigure -phigh xserver-xorg

...just saved me from a failed Feisty Kubuntu (+Beryl) upgrade to Gutsy.
After running the upgrade everything locked up - I suspect this was somehow a result of Beryl being removed.
Running the above xserver reconfigure from a shell, allowed me to copy all my data off and at least start again with my upgrade :-)
Thanks a lot - life saver.

---

