---
title: "windows network"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by fleaboss on 2005-08-08
hey, complete noob here. first time on the forums. i currently hav a home nework in my house of windows comps, and i just installed ubuntu on mine. i went to network servers and i found i could access the other computers on my network, but when i tried to it asked me for a username, domain and password. i tried my ubuntu acout info, and root, both didnt work. none of the windows comps hav passwords, so im not really sure wat to do. any help appreciated.

---

### Post by RastaMahata on 2005-08-08
[QUOTE=fleaboss]hey, complete noob here. first time on the forums. i currently hav a home nework in my house of windows comps, and i just installed ubuntu on mine. i went to network servers and i found i could access the other computers on my network, but when i tried to it asked me for a username, domain and password. i tried my ubuntu acout info, and root, both didnt work. none of the windows comps hav passwords, so im not really sure wat to do. any help appreciated.[/QUOTE]
 sudo apt-get install samba
sudo gedit /etc/samba/smb.conf

look for this (line 76): ```
; security = user
```
change it for ```
security = share
``` (notice that the **;** is gone)

sudo /etc/init.d/samba restart

now go to System->Administration->Shared Folders
Share a folder (your home folder should be ok)
In that same window, go on the BIG button below (general configuration thing), and edit correctly the domain/workgroup.

wait a few minutes, and you should be able to browse and be browsed.

---

### Post by lonetree on 2005-08-09
Wonder any of you have this problem. I have a mixture of linux (ubuntu, novell suse) and windows machines in my home network, have a simple NAS call a LANDISK ([http://www.vgear.com)](http://www.vgear.com)), acting as a file server.

My problem:

I have problem in date and time when copying folders and files from :
      i) linux to linux (i.e ubuntu to suse, suse to ubuntu) - time and date of files 
         always get changed to 1980 01 01 Tues 0800am GMT despite the original 
         date as something else.

      ii) linux to windows (i.e suse to windows or ubuntu to windows) - time and date 
          always get changed to a few hours ahead of the current time of the copying 
          process, despite the original date as something else.

      iii) linux to NAS - the time and date always get changed to 1980 01 01 Tues 
           0800am GMT (when the network folder is not mounted) and time and date 
           get changed to current time and date of the copying process (when it is 
           being mounted as a share folder, ie /media/share-folder)

Wierd isn't it? Am I doing anything wrong here or what?

Have been posted in quite a number of threads and still no one has reply. Hopefully someone can see this and reply, a yes or no will be at least an answer to me.

Thanks in advance.

Regards,

---

