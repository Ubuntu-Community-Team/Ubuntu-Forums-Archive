---
title: "dual boot osx + Ubuntu and file sharing."
date: 2008-01-29
forum: Apple PPC Users
---

### Post by jrharvey on 2008-01-29
I now have a dual boot setup on my PowerBook G4. 50G of the HD is devoted to OSX leopard and 10G is ubuntu 7.10. I put all my songs, pics and videos on the leopard part of the HD thinking I could view them from ubuntu but this is not the case. Ubuntu can see volumes and all the files but when I click on my home folder, it says I do not have permision to view the contents. How can I get permision. In Leopard I did set my home folder to be shared. Im not sure what else to do here.

---

### Post by jrharvey on 2008-01-29
bump

---

### Post by jrharvey on 2008-01-29
bump :(

---

### Post by jrharvey on 2008-01-29
wow, somebody has to know this. I do know most of you are x86/windows users but there has to be someone rocking OSX and ubuntu.

---

### Post by frog_pilot on 2008-01-29
on OSX you have to clicl on your home folder. press command+i. at  the bottom of the appearing window you find the permissions-section. alter the value for "others" to 'read' and press the button 'apply to recursive folders' (or similar). now you can access the files in your osx home folder from inside ubuntu.

---

### Post by VidiotGeek on 2008-01-29
If you use the computer out of the house alot, in coffee shops, airports, etc. I might not recommend sharing your entire home folder. Just keep in mind that it might also make it easier for someone snooping about on your wireless or at a hot-spot to get their hands on personal information. Maybe just change the permissions for the Music folder. I wouldn't mind so much someone gaining access to my music folder, my documents folder would be another story.

Of course this applies mostly if you're running OS X when you're out. If you're settings are fairly secure in Ubuntu, you should be fine. Maybe install the Firestarter firewall from the repos too.

**EDIT**
I assumed that you were using a laptop, if this is not the case, then that eliminates alot of the worry. But if you have a wireless network at home, it's still a concern, just not as much.

---

### Post by jrharvey on 2008-01-29
> **frog_pilot said:**
> on OSX you have to clicl on your home folder. press command+i. at  the bottom of the appearing window you find the permissions-section. alter the value for "others" to 'read' and press the button 'apply to recursive folders' (or similar). now you can access the files in your osx home folder from inside ubuntu.

Ok i tried this for my movies, music and pictures folder. I still cannont access it from ubuntu. I can see all kinds of other files but only my home folder tells me that I do not have permision. Ubuntu can read the files fine but for some reason I just do not have permision. Is it OSX or ubutnu that is keeping me from viewing these?

---

### Post by jrharvey on 2008-01-29
> **VidiotGeek said:**
> If you use the computer out of the house alot, in coffee shops, airports, etc. I might not recommend sharing your entire home folder. Just keep in mind that it might also make it easier for someone snooping about on your wireless or at a hot-spot to get their hands on personal information. Maybe just change the permissions for the Music folder. I wouldn't mind so much someone gaining access to my music folder, my documents folder would be another story.

Of course this applies mostly if you're running OS X when you're out. If you're settings are fairly secure in Ubuntu, you should be fine. Maybe install the Firestarter firewall from the repos too.

**EDIT**
I assumed that you were using a laptop, if this is not the case, then that eliminates alot of the worry. But if you have a wireless network at home, it's still a concern, just not as much.

I am using a laptop and I will aslo take your advise. As stated above I will only share my movies, music and pictures folder. Can ubuntu write to the OSX file system???? I know it can read it but not sure if i can put things in the folder from ubuntu.

---

### Post by oswaldkelso on 2008-01-29
> **jrharvey said:**
> I am using a laptop and I will aslo take your advise. As stated above I will only share my movies, music and pictures folder. Can ubuntu write to the OSX file system???? I know it can read it but not sure if i can put things in the folder from ubuntu.

enjoy :lolflag:

[http://ubuntuforums.org/showthread.php?t=657225](http://ubuntuforums.org/showthread.php?t=657225)

I just noticed an Error in my notes the command is df -h not du -h I 'll go change my notes!!!

g5@debian1333:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda17            6.5G  4.8G  1.4G  79% /
tmpfs                 505M     0  505M   0% /lib/init/rw
udev                   10M  176K  9.9M   2% /dev
tmpfs                 505M     0  505M   0% /dev/shm
/dev/hda19             20G   11G  7.9G  58% /home
/dev/sda1             110M  110M     0 100% /media/sda1
/dev/hda9             101G   85G   16G  85% /media/emac1
/dev/hda10             30G   29G  1.1G  97% /media/emac2
g5@debian1333:~$

---

### Post by jrharvey on 2008-01-29
ok so i finally figured something out that works for me. I simply put all my folders inside my shared folder from OSX. Now ubuntu can access the files with no problem. Now I can kinda use the same home folder for both OS's. This may be a crude method but I guess it works.

---

### Post by oswaldkelso on 2008-01-30
> **jrharvey said:**
> ok so i finally figured something out that works for me. I simply put all my folders inside my shared folder from OSX. Now ubuntu can access the files with no problem. Now I can kinda use the same home folder for both OS's. This may be a crude method but I guess it works.

That shows  its an  permissions problem nothing else. Most likely on the osx side, an easy way to prove it, is in osx create a new user with the same user name and password as on Linux. change the permissions in osx  and see what access you get I get complete access to all my osx users directory's apart from "Library"   due to it containing roots system files I suspect. There is nothing worse seeing a file you need but needing to reboot due to forgetting to  place it in shared.

---

### Post by jrharvey on 2008-01-31
Yes I know what you mean. The problem is that in OSX and linux i have the exact same user name and password. All  my the files i wanted were set to share. I set permisions to read and write but ubuntu is still not allowed to read it. Maybe its a Leopard thing, I dont know. When I had panther I didnt even have to change permisions.  Its ok thought I guess. I moved all my media stuff completely to my shared folder. I dont really care if anyone can see that stuff because I dont keep any personal info on those files.

---

