---
title: "Sharing the /home directory - what did I do wrong?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by theonlyrealperson on 2007-04-08
All right, Ubuntu is fantastic, and it made me realize the error of my ways. I nuked WinXP as soon as I could. 

Then, I decided to install a second 'nix distro on that now empty space, just to flex my knowledge and get a feel for what else is out there.

I recently did the right thing, and put my /home directory on a separate partition from my /root directory as well. (Well, not exactly, I remade my home partition, because I screwed up my fstab, I swear I followed all the psychocats' page directions for moving you home to a new partition.)

I did some forum searching, and I figured that if I didn't use the same username/password, I could use the same partition for home as my Edgy. So, I installed Mepis (Beryl "just works" for my ATI Mobility Radeon 9000 in Mepis, although I still prefer Gnome).

When I went to go log into my Ubuntu Edgy again though, I was confronted by a series of errors, telling me my home directory was in use or I didn't have write permissions to it. After signing in, it gave me a popup that said I was logged in for less than 10 seconds.

I'm sorry I don't have any logs - I reinstalled (again!) and remade my home partition. 

My question is: How do you safely use a /home partition between two distros? I'd really like to try out more Linux flavors while using Edgy as my base, and my laptop only has so much room. 

Thanks!

---

### Post by LaurelLynn on 2007-04-08
Dear theonlyrealperson,

It is OK to share the /home partition between two different distributions.  Just be sure to use different login names on each.  Both Ubuntu and Gnome put user configuration information in you user directory.  Trick is those files are hidden (any filename that starts with a period is hidden).

The config files are not always compatible between different distributions. Even different releases of Gnome can cause problems.  Even more to the point, the two distributions can use different user numbers even if the usernames match. That means you may no longer have permission to access your files.

You do NOT need to reinstall!!!!

The solution is to add two new user accounts. one for each flavor of Linux. Then you can use sudo to copy over you old files with ¨cp¨ and change the owner with ¨chown¨ from any terminal window.

Laurel Lynn

---

### Post by theonlyrealperson on 2007-04-08
Thanks! That's what I thought I did (well, I know I used two different usernames and passwords). I wonder if I 'ticked' a box I shouldn't have when I installed Mepis. 

But, in the future, as long as I don't use the same user id's and passwords, I should be ok. Cool.

But, if something like that were to happen again, can I just reinstall Ubuntu root - and direct it to use the existing username and password? Something of a "recovery"?

So what's the proper way to "recover" your /home directory? You'd reinstall Ubuntu root, and then would you enter your same username and password - or would you create a new account and copy the files over - then delete the old account?

Thanks!

---

