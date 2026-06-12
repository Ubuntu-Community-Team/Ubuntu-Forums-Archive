---
title: "Borked home folder move"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by rBGH on 2007-12-17
In the process of using this [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
howto, I managed to make my computer unbootable. I'm using the live CD right now and am unable to use it to perform the recovery that the howto refers to. The error I get when I try to log on is, paraphrasing here, I have no home folder, would I like to use the root as a home folder? If I click yes, it goes to another error saying it can't read or write to folder. 

In the process of the how to, my computer wouldn't let me continue. It didn't freeze altogether, just the app I was using. So, I rebooted. That was the last time it worked. 


I can hit F6 at the log in page but that's it.

A better list of errors that I found from another thread
This is the message I get when I try to log in:

"Your home directory is listed as 'home/mfrac' but it does not appear to exist. Do you want to long in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."

If I change the session to GNOME failsafe and accept the above message, I get:

"Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users."

After I hit OK, I get another error message stating that my GNOME session lasted less than 10 seconds.

Any ideas?

---

### Post by spiderbatdad on 2007-12-17
er...yep I think following that guide would definitely "bork" your system. You may have to reinstall from scratch.
Do not sudo rm -rf anything

---

### Post by rBGH on 2007-12-17
> **spiderbatdad said:**
> er...yep I think following that guide would definitely "bork" your system. You may have to reinstall from scratch.
Do not sudo rm -rf anything


I'm not feeling the love here:confused:J/k


Did I not follow the guide correctly, or is the guide incorrect?

Edit-I hadn't gotten to that command yet so I still have all the files and folders, I just screwed up the permissions I think.

---

### Post by JillSwift on 2007-12-17
This is less immediately helpful, but here's a better guide for that:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)


Do you still have your backup of /home?

---

### Post by rBGH on 2007-12-17
> **JillSwift said:**
> This is less immediately helpful, but here's a better guide for that:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)


Do you still have your backup of /home?

Yes, but I can't access it with the live CD, and thanks for the link btw.

A better explanation would be that I can see it but can't copy or move it.

---

### Post by spiderbatdad on 2007-12-17
I'm not sure you can change file permissions in single user mode (live cd) never tried. But at boot up if you hit ctrl-alt- F1 i believe you'll get a terminal

---

### Post by rBGH on 2007-12-18
> **spiderbatdad said:**
> I'm not sure you can change file permissions in single user mode (live cd) never tried. But at boot up if you hit ctrl-alt- F1 i believe you'll get a terminal

I'm still a long way from having this sorted out. Anyone else want to comment? I'm okay with a reinstall but would like to avoid it if I can.

---

### Post by JillSwift on 2007-12-18
You *might* be able to copy your backup into /home like so, once the disk is mounted:```
sudo cp -a /path_to_home_backup/* /path_to_home
```

---

### Post by rBGH on 2007-12-18
> **JillSwift said:**
> You *might* be able to copy your backup into /home like so, once the disk is mounted:```
sudo cp -a /path_to_home_backup/* /path_to_home
```

No luck, I don't have the right permission.
If I try it with the live CD, I get ubuntu@ubuntu:~$ sudo cp -a /path_to_home_backup/* /path_to_home
cp: cannot stat `/path_to_home_backup/*': No such file or directory

---

### Post by philinux on 2007-12-18
The guide works fine but you can get minor problems.

Use the live cd to navigate to your home folder, show hidden files. 

Delete any .gnome files and .dmrc

they will be recreated when you  log back in.

---

### Post by spiderbatdad on 2007-12-18
> **rBGH said:**
> No luck, I don't have the right permission.
If I try it with the live CD, I get ubuntu@ubuntu:~$ sudo cp -a /path_to_home_backup/* /path_to_home
cp: cannot stat `/path_to_home_backup/*': No such file or directory


Hopefully you didn't type "path_to_home_backup/*   that was only intended as an example, but i seriously doubt your backed-up directory is going to be on the live cd:)

---

### Post by The Cog on 2007-12-18
Can you boot into recovery mode? If so, try making a new home directory with these commands:
[B]mkdir /home/mfrac
chown mfrac:mfrac /home/mfrac[/B]
which should allow you to log in again.

Where did your original home directory go?
Are you getting the new /home partition mounted yet? (maybe this is what's hiding your old home?)

---

### Post by Bölvaður on 2007-12-18
I'd like to get the home folder in a separate partition, The only thing that is wrong is su has stopped working for no apparant reason at all!
Worked fine last month.:confused:

user@computer:~$ su
Password: 
su: Authentication failure
Sorry.

---

### Post by rBGH on 2007-12-18
> **philinux said:**
> The guide works fine but you can get minor problems.

Use the live cd to navigate to your home folder, show hidden files. 

Delete any .gnome files and .dmrc

they will be recreated when you  log back in.

I don't see and .gome or .dmrc files.

>   Can you boot into recovery mode? If so, try making a new home directory with these commands:
mkdir /home/mfrac
chown mfrac:mfrac /home/mfrac
which should allow you to log in again.

I get a permission denied error

Thank you everyone that has tried to help me. You'll all be getting a Christmas card in the mail.
I think I'm going to do a fresh install. I've made sooo many attempts to fix this problem that I've probably changed the system beyond what I would want even if I could log back in.

---

### Post by rBGH on 2008-04-13
I just bought and assembled my new computer so here I am faced with this problem again. I tried to move the folder after the install but kept getting the error, "home folder can not be found on this partition". Since I only just installed the OS and since it's so easy with Ubuntu, I decided to do it again. Only this time, I was able to specify the home folder during the partition editor stage. 

The good news is that after 5 installs I'm getting pretty good at installing Linux. I'm still having trouble though since I can't seem to install windows and not bork the Ubuntu install every time I try. I'm thinking of trying Wine since reinstalling Ubuntu is getting tiresome.

---

