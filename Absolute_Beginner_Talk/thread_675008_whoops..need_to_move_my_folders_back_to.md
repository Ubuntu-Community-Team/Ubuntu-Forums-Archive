---
title: "whoops..need to move my folders back to /"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by mikecicc on 2008-01-22
While i was trying to move some gimp brushes I downloaded to '/usr/share/gimp/2.0/brushes' using this command:

sudo mv /* /usr/share/gimp/2.0/brushes/


it ended up moving the majority of the directories in my / to that brushes directory, now i can't get them folders back to /

i figured since i was in the directory with the brushes when i did a 'dir' that my '/*' would be relative, not the root of my file system .. =(

and of course drag n drop doesnt work because of permissions, which i feel should be a feature available to turn off and on. 

what can i do here?

---

### Post by philinux on 2008-01-22
If you want to drag and drop to sort it out use 

gksudo nautilus

with care.

---

### Post by emarkd on 2008-01-22
For future reference, your current working directory is always .  (as in period), so youcould have done:

```
mv ./* /usr/share/brushes
```

or whatever, but it is always understood that you're working from your current working directory, so don't need to have the slash at all.  This would do the exact same thing:

```
mv * /usr/share/brushes
```

---

### Post by mikecicc on 2008-01-22
> **philinux said:**
> If you want to drag and drop to sort it out use 

gksudo nautilus

with care.

god damnitt, i totalled messed something up, on the command prompt that i already have open, i receive 'bash: /usr/bin/gksudo: no such file of directory'

and if i try to open another command line i get error "failed to change to directory '/home/mike' (No such file or directory)"

i imagine i moved the command line application/utility out of / now i cant use it ?

wow amazinh how easy you can damage things in linux

i feel like i totally ruined this system with one line, and i have a good feeling if i reboot it wont ever turn back on because all those directories that were once in my / like "boot" are now in gimp's brushes directory

---

### Post by p_quarles on 2008-01-22
> **mikecicc said:**
> god damnitt, i totalled messed something up, on the command prompt that i already have open, i receive 'bash: /usr/bin/gksudo: no such file of directory'

and if i try to open another command line i get error "failed to change to directory '/home/mike' (No such file or directory)"

i imagine i moved the command line application/utility out of / now i cant use it ?

wow amazinh how easy you can damage things in linux

i feel like i totally ruined this system with one line, and i have a good feeling if i reboot it wont ever turn back on because all those directories that were once in my / like "boot" are now in gimp's brushes directory
Yes, everything is now in your brushes directory. The only way you'll be able to repair the system is to boot up into System Rescue Mode with your live CD.

---

### Post by arsenic23 on 2008-01-22
Can you ```
sudo mv /usr/share/gimp/2.0/brushes/* /
``` with your open terminal ?

I've never done anything like this, so I'm not sure how it'll work, but that might help you out.

---

### Post by mikecicc on 2008-01-22
> **arsenic23 said:**
> Can you ```
sudo mv /usr/share/gimp/2.0/brushes/* /
``` with your open terminal ?

I've never done anything like this, so I'm not sure how it'll work, but that might help you out.

Nope, it won't accept any commands i get:

"bash: /usr/bin/sudo: No such file of directory"

when i try that command, man i wish i could somehow give permissions to drag and drop folders back into / without using the command line...

i lost my live CD too, lol what a drag.

thanks for all the help tho guys.

---

### Post by smurphy_it on 2008-01-22
Quote:              sudo mv /* /usr/share/gimp/2.0/brushes/
wow amazinh how easy you can damage things in linux

That move command could of been catastrophic in a windows environment as well because you referenced the root with your first slash.

---

### Post by hyper_ch on 2008-01-22
it's not easily damaged.

you're using "sudo" for that command... that's why it got damaged...

---

### Post by mikecicc on 2008-01-22
> **hyper_ch said:**
> it's not easily damaged.

you're using "sudo" for that command... that's why it got damaged...


i figured sudo was the same as " su root " in ubuntu 

which i figured was necessary to move files/folders...

i booted from the live CD and moved all the folders back to root...everythings fine now..

now that i know that i need the "./" to reference the directory im browsing i wont use '/' again

haha

---

### Post by emarkd on 2008-01-22
Since it's looking for sudo where it isn't, have you tried telling it where it is?  Like this:

```
/usr/share/gimp/2.0/brushes/usr/bin/sudo /usr/share/gimp/2.0/brushes/usr/bin/nautilus
```

That may or may not work...

---

### Post by mikecicc on 2008-01-22
> **emarkd said:**
> Since it's looking for sudo where it isn't, have you tried telling it where it is?  Like this:

```
/usr/share/gimp/2.0/brushes/usr/bin/sudo /usr/share/gimp/2.0/brushes/usr/bin/nautilus
```

That may or may not work...

I suppose i could have done that, but i booted with the Live CD and restored all my directories to /

now everything is back up and running smoothly.

thanks anyways

---

### Post by hyper_ch on 2008-01-23
> **mikecicc said:**
> i figured sudo was the same as " su root " in ubuntu 

which i figured was necessary to move files/folders...

i booted from the live CD and moved all the folders back to root...everythings fine now..

now that i know that i need the "./" to reference the directory im browsing i wont use '/' again

haha

well, sudo means "do as super user". However there is a reason that the normal system user needs to run sudo on certain things... if you can't do a a normal

```

mv /* /path/to/somewhere

```

then there's a pretty good reason for that and you really should think whether you want to run that as sudo.

---

