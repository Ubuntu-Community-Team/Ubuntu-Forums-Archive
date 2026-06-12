---
title: "gxine not working"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-28
For some reason, gxine refuses to play any file. It either looks as if it plays the entire file in 5 seconds or gives out an error. It can't even play FLAC or MP3, even if these work on Totem Movie Player. What is happening? How can I completely reinstall gxine to make it work? Thanks.

PROBLEM SOLVED:

I decided to completely remove gxine and reinstall using this method in the terminal:

sudo apt-get autoremove gxine
sudo aptitude install gxine

I am not sure why this worked or what was going on. But this solution fixed my problem. Can anyone explain what happened here and how it worked? Thanks.

---

### Post by amitroy5 on 2007-08-28
I just realized that I have a different problem with gxine. How can I play a media file accross a samba share. I have a shared folder via samba from another comptuer. However, it will not play unless I copy the file over to this computer.

---

### Post by constrictor on 2007-08-28
> **amitroy5 said:**
> I just realized that I have a different problem with gxine. How can I play a media file accross a samba share. I have a shared folder via samba from another comptuer. However, it will not play unless I copy the file over to this computer.
I have found that by mounting the network share as a local folder you should get it to work. i think the command is smbmount <source> <destination> username=yourusername. I think it works with root only so you'll have to prepend sudo to it. 
Not sure if this might help but i used this for my mythTV install and it worked fine.

---

### Post by amitroy5 on 2007-08-28
How do I mount a samba share as a virtual disk? Thanks.

---

### Post by amitroy5 on 2007-08-28
I figured out how to do such a mount. Follow the following excellent guide:

[http://ubuntuforums.org/showthread.php?t=280473&highlight=mount+samba](http://ubuntuforums.org/showthread.php?t=280473&highlight=mount+samba)

I wish Samba was more easier to use, since file sharing is very commonly used in Windows.

This is a great workaround to mount Samba shares and make samba shares act like a virtual drive. Thus, virtually any program should now be able to load files on another computer.

---

