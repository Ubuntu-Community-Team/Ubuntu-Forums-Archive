---
title: "Some definite beginner questions..."
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by klainmeister on 2006-11-13
I've been interested in installing Ubuntu for the last couple of weeks and now have a live cd in my hand with the intention of complete installation. I first have to say i am completely new to Linux and am excited to check it out. But i have some questions that i cant seem to get resolved on my own.

I have a dell 700m and the res is wrong. I've read about how to change it in the terminal but still cannot get it to work and was wondering if this was because i am running a live cd? If not, so quick help on that would be fantastic so i can have a feeling for how this OS would actually look on my laptop. 

The other question i had is that i have a texas instruments card SD card reader and it currently not working, is there a driver i can find for this. My searching has left me empty. Thanks guys, and i hope i can join the community soon!

---

### Post by bulldog on 2006-11-13
Hi,
Well the resolution,you can try to reconfigure X-server by typing this in your terminal and see if you can get it right.```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

But no guarantees it works.

About your SD card I have no clough,but you can wait if someone else have some ideas.

---

### Post by Anonii on 2006-11-13
Try this:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
its basicaly what bulldog said, but with detailed instructions, more info, explanations etc.

---

### Post by nickpaton on 2006-11-13
Could you post the make and model of the card reader, and the TI chip if you know it.

Also which CD version of Ubuntu you are using and whether it's 32 or 64bit.

---

### Post by klainmeister on 2006-11-14
OK, so i tried the process with the xorg. and can select the resolution but it never actually gets applied, nor does it show up in the the systerm-screen resolution.

I've read about the 915resolution but i even ran into a problem installing that because no package installed can find it, and then there is a command "# su" that i need to sign in, and even then it won't allow me to. I am beginning to think i am too stupid to run this OS. 

SO, resolution...

And just out of curiousity, i accidentally made a /root folder on my desktop. How do i delete this and my unneeded partitions from my desktop when they cant be moved?

Thanks a ton guys, i realize this is a lot of quetions. I really want to switch...well i already have, now i just need to to work for me and not me for it. Thanks again!

---

### Post by IYY on 2006-11-14
OK, so i tried the process with the xorg. and can select the resolution but it never actually gets applied, nor does it show up in the the systerm-screen resolution.

> I've read about the 915resolution but i even ran into a problem installing that because no package installed can find it, and then there is a command "# su" that i need to sign in, and even then it won't allow me to. I am beginning to think i am too stupid to run this OS.

This is just a difference between Ubuntu and some other distributions. 'su' will give you a root account asking for the root password. In Ubuntu, the root password is hidden from you, but you can still execute root commands with an admin account using your user password. So, instead of su, type **sudo su**. This means, run 'su' as root.


> And just out of curiousity, i accidentally made a /root folder on my desktop. How do i delete this and my unneeded partitions from my desktop when they cant be moved?

Have you mounted something on this partition? If so, you will need to first unmount whatever you mounted on it (**umount ~/Desktop/root** might work, depending on how you mounted it). If it's just an empty directory with nothing in it, **rm -r ~/Desktop/root **

---

### Post by infidel on 2006-11-14
As to the resolution issue, I ran into something similar when I tried to install Dapper from the standard live CD on a brand-new machine with integrated ATI graphics. Nothing I did helped until someone suggested that I try the Alternate Install CD image. If I recall (it's been months), the installation process was completely text-based yet everything flowed smoothly, my graphics were auto-detected, and I ended up with a flawless installation that Just Worked. 

I don't know where you are in the world, or if Edgy's alternate install  is as fruitful as Dapper's was for me, but the Alternate Install image is available (as "Alternate install CD" under "Other installation options") from all of the North American download locations, at least. I hate for you to have to wait for another lengthy download, but it might be worth it it nothing else helps.

Veterans, please jump in here and smack me down if I'm steering him wrong.

---

### Post by klainmeister on 2006-11-14
Ok, so how exactly do i add the Multiverse and Universe repositories? From what i gathered, i can download the 915resolution package directly through commandline if i have this setup. But the help section on this goes in circles. Any quick way to do this? If i can get this done and get 915resolution installed i should be set, but as of right now when i dl the 915resolution zipped file and extract it, i cant use it in synamptics. What's going on?! haha, this is awesome. I am almost beginning to enjoy this installation stuff, maybe if i can understand exactly whats going on. Thanks guys.

---

### Post by Obor on 2006-11-14
> **klainmeister said:**
> Ok, so how exactly do i add the Multiverse and Universe repositories?

To add repos using graphical interface follow [this]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

To add repos using command line (terminal) follow [this]("http://psychocats.net/ubuntu/sources")

Find many other useful links in [this thread]("http://www.ubuntuforums.org/showthread.php?t=232059").

---

### Post by klainmeister on 2006-11-14
Thanks guys, i got my resolution fixed and also got my mp3's going, and even my card reader. But i am still lacking the most basic skills to delete this folder i made on my desktop. I was using Synaptics package manager when i created a folder using that software on my desktop and i dont have permission to delete it?

Location: /home/klain/Desktop
File Owner: Root
File Group: Root

It says i am not the owner and therefore cant delete. any help would be great, thanks!

---

### Post by nickpaton on 2006-11-15
Hey Klainmeister (what does that mean BTW!) congratulations on all that.

How did you solve the card reader problem?  it would be useful for others to know since some of them can be a problem.

About getting rid of your file on the desktop, first of all I'm slightly worried about what this file contains, since if you delete it, it may mess up your OS.

So with this in mind, the way to remove it is via Nautilus:

Nautilus is a VERY powerful program which gives you root rights to do anything you want to any program, so make 100% sure you don't accidently delete the wrong file

In a terminal:

```
gksudo nautilus
```

Ignore any error messages you may get.

Password.

You should now see Desktop, or if you don't navigate to it.

Simply delete the folder.

Are you OK on all the rest of the stuff like the repositories etc?

---

