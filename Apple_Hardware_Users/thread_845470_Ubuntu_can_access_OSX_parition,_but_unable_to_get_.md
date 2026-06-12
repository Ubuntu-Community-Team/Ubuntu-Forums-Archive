---
title: "Ubuntu can access OSX parition, but unable to get into iTunes music?"
date: 2008-06-30
forum: Apple Hardware Users
---

### Post by Quipacorn on 2008-06-30
Hello all
I have a macbook pro, revision 3 (santarosa) and have a triple boot setup (XP, Hardy, 10.5), I'm most likely going to be using hardy the most, but i don't want to migrate everything over, nor do i wish cease use with mac os (I find i like the itunes interface among other things, as well as the organization. Anyways, I used the wiki instructions to make it possible to access the OS X partition and also write to it.
I can access the parition, and go to a certain extent, however when i get into my oSX user folder, i cannot access the iTunes music directory due to incorrect permissions, as far as i know there is no simple way to change permissions, nor is it possible to login as root and change them. can anyone offer any solutions or ideas? 

Regards

---

### Post by Dacobi on 2008-06-30
There is one way to do it which is to change the id number of your linux user to match the id of your OSX user.

If you mount your OSX partition and log in as root in a terminal then go to /media/OSX/Users and type ls -l you will se the id number of your OSX user before the folder name.

ex.
drwxr-xr-x 1 502 dialout 85 2008-06-30 16:16 username

502 is the number you want.

Now reboot Ubuntu in recovery mode and drop to root shell.
open /etc/passwd and find your user.
the line will look like: username:x:#:#:name,,,etc...
change the first number to your OSX user id.

Just to be safe reboot again into recovery mode and drop to root shell.
Now all thats left is to change owner ship of your homefolder to match the new user id.

cd /home and type 
chown -R <username> <home folder>

now reboot and you should be able to access your OSX home folder.

One problem with this solution is if you have files owned by your ubuntu user outside your home folder, these will have to be manually changed to your new user id.

/Dacobi

---

### Post by Oscar Pradilla on 2008-07-07
there's an easy way... start up in mac, go to itunes>properties (cmd + i) then in permissions unlock and change everyone to Read and Write, do the same to itunes music. Now shut it down and enter in ubuntu.

In ubuntu you can now navigate to you mac drive: users/your user name/itunes/itunes musics/

That's all that you need....it works for me perfect

---

### Post by DonnieP on 2008-07-07
> **Quipacorn said:**
> nor is it possible to login as root and change them. can anyone offer any solutions or ideas?
I really like Pradilla's suggestion, but why do you say it is not possible to login as root?  This is exactly how I've been accessing iTunes files from Ubuntu (until now).

---

### Post by Oscar Pradilla on 2008-07-07
i've done that also, but this is simple and you can access that folder from every app in ubuntu

---

### Post by cyberdork33 on 2008-07-08
> **Oscar Pradilla said:**
> i've done that also, but this is simple and you can access that folder from every app in ubuntu
In fact, you should just change the permissions in OSX for all the files in your Home folder you would like to access in Ubuntu...

---

### Post by spencercarran on 2008-07-10
> **Oscar Pradilla said:**
> there's an easy way... start up in mac, go to itunes>properties (cmd + i) then in permissions unlock and change everyone to Read and Write, do the same to itunes music. Now shut it down and enter in ubuntu.

In ubuntu you can now navigate to you mac drive: users/your user name/itunes/itunes musics/

That's all that you need....it works for me perfect

I tried that, and for some reason Ubuntu still tells me I don't have permission to access those files. I'm thinking of just syncing the music from my iPod up to my computer with one of the iTunes knock-offs. Is there any reason changing the permissions from the Mac side to allow everyone to read and write wouldn't enable access to them in Ubuntu?:confused:

---

### Post by cyberdork33 on 2008-07-10
> **spencercarran said:**
> Is there any reason changing the permissions from the Mac side to allow everyone to read and write wouldn't enable access to them in Ubuntu?:confused:nope that should work.

---

### Post by spencercarran on 2008-07-10
> **cyberdork33 said:**
> nope that should work.

It should but somehow doesn't. Ubuntu knows, when I click on "Properties," that "everyone" can "read and write" in the folders I selected, but when I try to open them I get a warning about not having the permissions to access them.

---

