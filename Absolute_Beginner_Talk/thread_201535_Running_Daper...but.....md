---
title: "Running Daper...but...."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-06-21
I had to do a complete new install.  Thar's okay, because I'm learning a lot about Linux.

For instance, I figure out how to enable my extra internal hard drives. dapper still did not find and mount these.   a small pain this time around.  Folks up here helped me out last time and I marked the thread.:)  

The next challenge is changing screen rez.  I can't get it over 1024 x 768. I tried doing this with the command sudo dpkg-reconfigure xserver-xorg and really messed it up so much that I had to do an install all over again.
now, I'm going to manually edit the xorg file and add resolutions and reboot. I'm hoping this works.

So far, Dpper has a really easy install routine.  Six steps and you're installing Ubuntu. Nice!

The downside is the hard drives not being recognized and the screen rez not being fully available.  but, I'll give the xorg edit a shot now and see if it works.:)

---

### Post by Dr. Nick on 2006-06-22
yes you can edit your xorg.conf to add the resoulitions you need. And if you good it up using the dkpg-reconfigure then just re-run it and take the defaults and you should be fine, shouldnt require a reinstall

---

### Post by georgetoon on 2006-06-22
Nope.   the xorg edit did not work.  and i sure as heck won't do that whole routine sudo dpkg-reconfigure xserver-xorg!  Too many steps to go through just to get to the screen rez.  And it messed me up to the point of shutting down the GUI. 

Anyone else have another solution?

---

### Post by Dr. Nick on 2006-06-22
Ive posted instructions on how to do the edit before, Ill dig them up and repost it here, can you post a copy of your xorg.conf as it stands now so I can check over it?

---

### Post by Dr. Nick on 2006-06-22
here is the link to the instructions I used in a similar thread

[http://ubuntuforums.org/showthread.php?t=193556](http://ubuntuforums.org/showthread.php?t=193556)

It could just be your monitor refresh rate isnt set properly if following them instructions doesnt work

---

### Post by codejunkie on 2006-06-22
try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` this will configure the xorg.conf file automaticly, then reboot by entering ```
sudo init 6
``` or restart the login manager with ```
sudo /etc/init/gdm restart
``` hope this helps..

---

### Post by georgetoon on 2006-06-22
[QUOTE=Dr. Nick]Ive posted instructions on how to do the edit before, Ill dig them up and repost it here, can you post a copy of your xorg.conf as it stands now so I can check over it?[/QUOTE]

Dr. Nick,

I sincerely appreciate this help.:) 

However, I took the plunge.:)  

I ran "sudo dpkg-reconfigure xserver-xorg" and it worked!:)  I've got all my screen rez's!:) Nice!:)

I guess this time around, I actually paid attention to what i was doing instead of being lazy.:)

My next question, however, has to do with the way I enabled my hard drives. 

I made directories for these and I accidentally created a directory twice for one of the drives. So, "fat1" appears twice in the  storage listing. Should I correct this? And how would i correct this?

Dapper is really nice! Really, really nice!:)

---

### Post by Dr. Nick on 2006-06-22
glad you got it.

I dont think that having it appear 2 times is bad, but if you want to correct it you can. Im not sure exactly what you are describing but the fstab file control mounting and mount points, Look at the file /etc/fstab and see if the entry is in their 2 times

---

### Post by georgetoon on 2006-06-22
[QUOTE=Dr. Nick]glad you got it.

I dont think that having it appear 2 times is bad, but if you want to correct it you can. Im not sure exactly what you are describing but the fstab file control mounting and mount points, Look at the file /etc/fstab and see if the entry is in their 2 times[/QUOTE]

Okay.:)  I'll take a look at the file this evening.:)

Thanks again to all on this board for their help and patience with me.:)

---

