---
title: "Unable to lookup calvin-laptop by gethostbyname()"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-10-05
In my haste to try and fix my internet problem, I tried deleting things out of networking and started getting this error and also being unable to use sudo or kdesu, I can use gksu for some reason though. I then uninstalled postfix (I can't remember why, it seemed a good idea at the time, I think it was moaning at me about it) forgetting I wouldn't be able to reinstall it without the internet, can I fix the above WITHOUT internet? Can I fix internet WITHOUT these?

Please help :o(

Calv

---

### Post by calvinthomas on 2006-10-05
Got postfix reinstalled and thats stopped postfix moaning errors but I still have the error from the title, any ideas?

Calv

---

### Post by arkangel on 2006-10-05
you have to check  the consistency of 2 files 
/etc/hosts  and /etc/hostname , this most probably your problem

[http://ubuntuforums.org/showthread.php?p=1584412#post1584412](http://ubuntuforums.org/showthread.php?p=1584412#post1584412)

 
for example my hosts file is like these 
  > 
127.0.0.1 localhost **greybox**
127.0.1.1 **greybox**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and my hostname file is
> **greybox**

---

### Post by calvinthomas on 2006-10-05
Thankyou, that is the problem but how do I fix it, my /etc/hosts file only says:

# The following lines are desirable for IPv6 capable host.

How can I find out what my ip number thing at the start should be? Will it be the same as yours? Can I simply copy yours an change the name to the correct one? Also i'm taking it, I won't need anything else here for my wireless connection? (I ask because of my broken internet!)

Calv

---

### Post by arkangel on 2006-10-05
reboot  and use the live cd    then  mount your drive 
when the live cd is loaded, open a terminal
 
**sudo mount /dev/hda1  /mnt**    

if hda1 is not your drive/partition try with [hda2 hda3 ..]    whatever your drive/partition is 
to unmount a drive:  
**sudo umount /dev/hda1**  (before mounting another partition  , unmount the previosly mounted )
 

then use the same teminal to edit the files

**sudo gedit /mnt/etc/hostname  /mnt/etc/hosts**

save an reboot

---

### Post by calvinthomas on 2006-10-05
I can edit the files already but I am not sure what to put in them. Are you saying if I do this it'll give me the correct settings?

I have tried just copying yours exactly as it is (with the name changed) and I no longer get the error, does that mean its right or could it still be wrong?

Calv

---

### Post by arkangel on 2006-10-05
ok so  most probably  is solved 
type in a console 
**hostname **
if appears the name you just entered is ok 
or type , ofr example 

**sudo synaptic **

and it should open with no problem

---

### Post by calvinthomas on 2006-10-05
no errors at all, what i'm most worried about is the second line, the second ip address that is, should that be the ip address of my network connection? or my router? Or doesn't it really matter?

Sorry to be such a pain, thankyou so much for your help

Calv

---

### Post by arkangel on 2006-10-05
the 127.0.0.1  and 127.0.1.1 are reserved ip adresses and represent you local host (in fact  127.0.0.1=mycomputername),   must be ok , i dont know what is the meaning of  127.0.1.1.
at this point doesnt matter.  Try to google for 127.0.1.1  for sure there is a wiki somewhere

---

### Post by calvinthomas on 2006-10-05
I've changed it to my ip address and it hasn't changed anything so i'll just not worry about it unless i'm told otherwise, I did this because the link you gave me previously had the second line as 192.168.0.5 (or something similar) which looked like i was probably there ip address.

Thankyou for your help, just the internet problem now and i'll be all fixed!

Calv

---

### Post by arkangel on 2006-10-05
i am curios :)   what was your internet problem ?

---

### Post by arkangel on 2006-10-05
[http://www.faqs.org/docs/securing/chap9sec95.html](http://www.faqs.org/docs/securing/chap9sec95.html)

now it's clear  :)

---

### Post by calvinthomas on 2006-10-05
This i my internet problem caused by my own stupidity:

[http://www.ubuntuforums.org/showthread.php?t=271872]("http://www.ubuntuforums.org/showthread.php?t=271872")

Thanks for the link, how would I go about finding out if I needed any of these? i.e. mail, web etc and what they were (just wondering if thats my internet problem)

Calv

---

### Post by arkangel on 2006-10-05
:S no idea sorry ,

---

### Post by calvinthomas on 2006-10-05
Never mind, thankyou for all your help, hopefully someone else will be able to help with my internet problem. Oddly I thought fixing that would of been easier (i'd of thought it'd of happened to others before) but it seems i've really screwed it up!

Calv

---

