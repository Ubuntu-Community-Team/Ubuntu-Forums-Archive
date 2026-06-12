---
title: "Another Small Question"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Glass Casket on 2006-05-18
So I tried Googling this, but couldnt find the answer because I don't think I was searching for the right thing, lol.

I'm trying to find a site or something that will explain what each partition type does and the benefits of each. (ie. /usr, /home and all the other ones)

Thanks!

---

### Post by joshrobinson on 2006-05-18
[QUOTE=Glass Casket]So I tried Googling this, but couldnt find the answer because I don't think I was searching for the right thing, lol.

I'm trying to find a site or something that will explain what each partition type does and the benefits of each. (ie. /usr, /home and all the other ones)

Thanks![/QUOTE]

give me a few minutes ill type it up for you

---

### Post by skinnygmg on 2006-05-18
these are directories you speak of.  look here

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

g

---

### Post by aysiu on 2006-05-18
This may not be exactly what you're looking for, but try this.
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by joshrobinson on 2006-05-18
/bin   -   vital tools to get system up and running, for use in repairing system and diagnosing problems

/boot - boot loader and its config files

/cdrom aka /media/cdrom - cdrom mount point

/dev - symbolic links to your hardware

/etc - central repository of config files

/home - your userspace and personal data

/lib - shared system files

/lost+found - salvaged scraps and files

/media - directory for mounted drives

/mnt - where discks are temp. mounted

/opt - software that is optional and not vital to the system

/proc - vital info about your system and its status

/root - root users personal space (his /home really)

/sbin - administrasion programs

/srv - network server config files

/sys - mountpoint for the sysfs filesystem used by the kernel

/tmp - temp. files

/usr - shared programs and data

/var - space used to store data that is constantly updated such as printer spooling

and vmlinuz and initrd.img are files used to boot linux

---

### Post by Glass Casket on 2006-05-18
Thanks everyone!

So then it makes sense to do the following:

/boot => 32MB
/home => 15GB (For personal files)
/usr => 10GB (For programs and such)

So if I don't have a /usr partition, does that mean all my programs get installed in /root. But if I do have a /usr partition, all the applications get installed in there?

---

### Post by joshrobinson on 2006-05-18
[QUOTE=Glass Casket]Thanks everyone!

So then it makes sense to do the following:

/boot => 32MB
/home => 15GB (For personal files)
/usr => 10GB (For programs and such)

So if I don't have a /usr partition, does that mean all my programs get installed in /root. But if I do have a /usr partition, all the applications get installed in there?[/QUOTE]

you dont really need paritions for all of those, you can create one parition as / (which includes /boot and /usr)
one parition for /home
and then your swap parition

or you can do one parition as / (including home)
and one for swap

but if you chose to reinstall you will lose your /home directory if you dont back it up.. so /home on its own parition is nice to have since you can just mount it as /home on your next install and your personal files are there

---

### Post by aysiu on 2006-05-18
[QUOTE=joshrobinson]you dont really need paritions for all of those, you can create one parition as / (which includes /boot and /usr)
one parition for /home
and then your swap parition[/QUOTE] I agree with Josh. No need to have a separate /usr and /boot partition.

/home is what matters most.

---

### Post by Klaidas on 2006-05-18
Wow, joshrobinson, that's some detailed list! :)
I'll copy-paste it into a text file. It will be uselful ;)

---

### Post by joshrobinson on 2006-05-18
[QUOTE=Klaidas]Wow, joshrobinson, that's some detailed list! :)
I'll copy-paste it into a text file. It will be uselful ;)[/QUOTE]

haha thanks.. hopefully i included all of them in there ](*,)

---

### Post by matthew on 2006-05-18
[http://www.debian.org/doc/packaging-manuals/fhs/]("http://www.debian.org/doc/packaging-manuals/fhs/")

EDIT: I go to look for a link and 80 people post! :) I love this place.

---

### Post by joshrobinson on 2006-05-18
[QUOTE=matthew][http://www.debian.org/doc/packaging-manuals/fhs/]("http://www.debian.org/doc/packaging-manuals/fhs/")

EDIT: I go to look for a link and 80 people post! :) I love this place.[/QUOTE]

theres a good amount of us here that just stalk the forums waiting for questions.. sadly im one of them haha:-D

---

### Post by skinnygmg on 2006-05-18
[QUOTE=matthew]I go to look for a link and 80 people post! :) I love this place.[/QUOTE]

i hate when people beat me to it :mad:

---

### Post by Klaidas on 2006-05-18
I keep ubuntuforums opened in my browser almost all the time.
I'm addicted! \\:D/

---

### Post by it.henrik on 2006-05-18
thnx heaps joshrobinson .. that list is something I always wanted

---

### Post by joshrobinson on 2006-05-18
[QUOTE=it.henrik]thnx heaps joshrobinson .. that list is something I always wanted[/QUOTE]

glad i could help :D

---

### Post by matthew on 2006-05-18
[quote=joshrobinson]theres a good amount of us here that just stalk the forums waiting for questions.. sadly im one of them haha:-D[/quote]Just the kind of person we love...glad you're here.

---

### Post by joshrobinson on 2006-05-18
[QUOTE=matthew]Just the kind of person we love...glad you're here.[/QUOTE]

its a great place to be, i say to myself i have to help everyone that has a problem i can fix, so that way someone will be nice enough to help me when i have problems.. and help sure does come fast on these forums

---

### Post by Klaidas on 2006-05-18
Same here. People on these forums help me, so I want to help them too.

About the speed of replying:
On a MSDN forum, I had to wait ~3 days to get an answer (programming at my computer school).
Here, my questions are answered in like 3-5 minutes :)

---

### Post by joshrobinson on 2006-05-18
[QUOTE=Klaidas]Same here. People on these forums help me, so I want to help them too.

About the speed of replying:
On a MSDN forum, I had to wait ~3 days to get an answer (programming at my computer school).
Here, my questions are answered in like 3-5 minutes :)[/QUOTE]

sometimes even 1 minute.. alot of people on here are quick to post

but im off to work guys, take it easy

hold the forums down for me Kladids :cool:

---

### Post by Klaidas on 2006-05-18
Trying, trying... 
But teachers still give me much homework to do. I should show them these forums and make posting here an excuse for no doing some homework! :mrgreen:
Just kidding :) I always do them ;)

---

