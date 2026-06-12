---
title: "avg antivirus for ubuntu?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by crakkajakka15 on 2006-04-03
ok when i was using windows i was using avg anti virus which i thought did an excelent job. i see they have 3 versions for linux, but they are for mandrake,red hat, and suse will any of these work for ubuntu?

---

### Post by jason.b.c on 2006-04-03
[QUOTE=crakkajakka15]ok when i was using windows i was using avg anti virus which i thought did an excelent job. i see they have 3 versions for linux, but they are for mandrake,red hat, and suse will any of these work for ubuntu?[/QUOTE]


I don't see why not, Try it and find out for yourself..;)

---

### Post by jason.b.c on 2006-04-03
[QUOTE=crakkajakka15]ok when i was using windows i was using avg anti virus which i thought did an excelent job. i see they have 3 versions for linux, but they are for mandrake,red hat, and suse will any of these work for ubuntu?[/QUOTE]


I don't see why not, Try it and find out for yourself..;)



**EDIT** **I don't know how this got here twice..!!!**

---

### Post by az on 2006-04-03
[QUOTE=crakkajakka15]ok when i was using windows i was using avg anti virus which i thought did an excelent job. i see they have 3 versions for linux, but they are for mandrake,red hat, and suse will any of these work for ubuntu?[/QUOTE]
Is there a source version?  If not, then what's the point of a linux version?  If I wanted to run closed-source, proprietary applications, I would use windows.  Come to think of it, if I wanted to run an antivirus, I would be running windows!

---

### Post by jason.b.c on 2006-04-03
> If not, then what's the point of a linux version? 

Yea, thats true too isn't it.

> Come to think of it, if I wanted to run an antivirus, I would be running windows!

Somehow this sounds familiar..

---

### Post by Papa-san on 2006-04-03
[QUOTE=azz]Is there a source version?  If not, then what's the point of a linux version?  If I wanted to run closed-source, proprietary applications, I would use windows.  Come to think of it, if I wanted to run an antivirus, I would be running windows![/QUOTE]

azz... How long have you been using linux, and how many viruses (virii?) have you had infect your systems?

---

### Post by stuporglue on 2006-04-03
If you're ok with it not being AVG, you can use clamAV. There's a GUI for it too, just search for it in Synaptic. clamAV is OSS and is a great program.

---

### Post by tikal26 on 2006-04-04
You can try alien
AS you probably know there are distros on linux and they use differnet package systems the most common ones are rpm and deb. ubuntu is base on debian and uses .deb packages. Most of the time you want to use packages offered by the ubuntu repos only, but sometimes I understand the use of commercial closed source applications. I have tried Suse and red hat packages before and alien them so you might try either one.
You want to go to synaptic and install alien
the you want to open a console and type the following

you:~$ cd /yourlocation/yourfile  for example if I dowloaded to my desktop it would be cd /home/sara/desktop

alien avglinux-7.1-24_free_rh_avi0720.i386.rpm (notice that is the red hat package you substitute it for the one you dowload)
 
 this will create a .deb file, install it:
 
 sudo dpkg -i "the-name-of-the-file".deb

Hope this helps. off course you might want to try a truly free and open antivirus provided on the ubuntu repos.  They have aegis, clamav,  and many more, but some of them are command line tools so you might want to stick with either aegis or clamav. One more thing viruses are not a big problem on unix systems. They do 'exist' but it is hard for them to affect your system, but you might still want to get rid of them so that you don't spread them.

---

### Post by crakkajakka15 on 2006-04-04
im running aegis now should i be fine with that and firestarter? or is ubuntu like my MAC where anti virus programs are not needed?

---

### Post by stuporglue on 2006-04-04
> or is ubuntu like my MAC where anti virus programs are not needed?

Yup. Both Linux and Mac (due to it's Unix roots) have a more secure design. I'd rate making backups and running system updates as more important than having anti-virus. 

I wouldn't go so far as to say "don't use AV on Linux/Mac", because you never know what could happen[*], but I don't use AV on my Linux/Mac boxes. 


[*] I read of someone who had Wine configured to launch exe files by double clicking, and they got a virus from a forward...

---

### Post by meborc on 2006-04-04
howto avg for ubuntu - [http://www.ubuntuforums.org/showthread.php?t=136064](http://www.ubuntuforums.org/showthread.php?t=136064)

just to show the power of ubuntuforumsearch :mrgreen: 

and by the way, the point of using antivirus in linux is to protect your windows partition (if you have one) and your unlucky friends who still run windows and who might get affected by one of the files coming from your box... it is highly unlikely that you yourself can get infected as there are very few linux viruses roaming around, but better be safe than sorry...

---

### Post by florizs on 2006-04-04
I'm particulary fond of AVG antivirus for windows. However I don't know how it works for Linux. 
for Linux I use Clam AV to ensure all the documents on my windows partition and SMB Shares stay virusFree. 
however I'm curious how Grisoft works. maybe you should download the RPM and convert it to a DEB with Alien.
goodluck

---

### Post by localzuk on 2006-04-04
I would recommend working with clamAV also. Nice and customisable. Personally, I always grisoft AVG for windows boxes but don't have an RPM based machine with which to try their linux offering... And I haven't really looked at alien yet.

---

### Post by meborc on 2006-04-04
the link i posted in few posts up is a how-to setup avg in ubuntu... ;)

---

### Post by RavenOfOdin on 2006-06-08
[QUOTE=meborc]howto avg for ubuntu - [http://www.ubuntuforums.org/showthread.php?t=136064](http://www.ubuntuforums.org/showthread.php?t=136064)

just to show the power of ubuntuforumsearch :mrgreen: 

and by the way, the point of using antivirus in linux is to protect your windows partition (if you have one) and your unlucky friends who still run windows and who might get affected by one of the files coming from your box... it is highly unlikely that you yourself can get infected as there are very few linux viruses roaming around, but better be safe than sorry...[/QUOTE]

That would be a great thing for me, I'm running a XP/Linux dual boot and I've been moving files over from my Windows to Linux partition via CD ever since I first installed Ubuntu.

As well, I switch files back and forth via disks.

Grisoft is a great company and I've used their software since XP SP1.  But I'm somewhat leery of this "Dazuko" kernel module that they want me to install for AVG.  Does it have a chance of screwing my system up?

---

### Post by u.b.u.n.t.u on 2006-06-08
[QUOTE=crakkajakka15]ok when i was using windows i was using avg anti virus which i thought did an excelent job. i see they have 3 versions for linux, but they are for mandrake,red hat, and suse will any of these work for ubuntu?[/QUOTE]

Hi, I too used avg free for a long time. I use nothing on ubuntu. One of the benefits of linux. That and there is no need for "perfect disk' etc as defrag isn't an issue.

I do use firestarter and it is excellent. As good as sygate free for windows.

---

### Post by u.b.u.n.t.u on 2006-06-08
Firestarter
[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by ram0071989 on 2006-10-25
> **crakkajakka15 said:**
> ok when i was using windows i was using avg anti virus which i thought did an excelent job. i see they have 3 versions for linux, but they are for mandrake,red hat, and suse will any of these work for ubuntu?

yup buddy....i have installed avg antivirus for ubuntu.in the downloads section of avg antivirus download the first file link for linux workstations(.._flm...).

---

