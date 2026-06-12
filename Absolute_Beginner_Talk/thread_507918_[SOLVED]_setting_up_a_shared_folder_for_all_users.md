---
title: "[SOLVED] setting up a shared folder for all users"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by NeillHog on 2007-07-23
After only 4 days I have Kubuntu up and running and am now getting down to the details.

At the moment each user has there own directory which they can reach from "home Folder"
Via "Storage Media" we can all see the USB stick that I have plugged in.

My question: Is there a directory that everyone can see for shared data?

And another question. I have "shared" the folder /home/neill/data/Bilder (the symbol now has a two pin electric plug attached to it) but how do others now see this folder.

Thanks!

Neill

---

### Post by bodhi.zazen on 2007-07-23
sudo mkdir /media/data
sudo chown root.users /media/data
sudo chmod 770 /media/data
sudo chmod g+s /media/data

ln -s /media/data ~/data #run this for each user

---

### Post by NeillHog on 2007-07-23
Sorry!

It worked up to
neill@NeillsPC:/media/data$ ln -s /media/data ~data
ln: accessing `~data': Permission denied

so I then tried
neill@NeillsPC:/media/data$ sudo ln -s /media/data ~data
and now I have the folder data in /media but it now belongs to root and is locked.

I did mention that I am VERY new didn't I.

Maybe you could give me another tip.

Thanks!

neill

---

### Post by bodhi.zazen on 2007-07-23
You missed a /

~ = short hand for /home/<username> (each users will have to run that command after the log in)

ln -2 /media/data ~/data 

#see the / in front of data ?

Post the output of :

```
sudo ls -l /media | grep data
```

*you can copy and paste that command to the terminal, highlight it with the mouse, move to the terminal, push down on the scroll wheel ...

---

### Post by NeillHog on 2007-07-23
I ran
sudo ls -l /media | grep data
as you said and received the following
drwxrws--- 2 root  users  4096 2007-07-23 22:22 data

Thanks for any and all help

Neill

---

### Post by bodhi.zazen on 2007-07-23
That looks good. Are you still having problems ?

If so, are you a member of the group "users" ?

If not, add yourself to the users group, log out, log back in (you need to log out/in for the changes in group membership to take).

---

### Post by NeillHog on 2007-07-23
Thank you!

That did it. I wasn'zt in the group "users" but now I am am it works.
Thank you!

---

### Post by NeillHog on 2007-07-24
Thanks again bodhi.zazen
Kubuntu is as clear as mud but with your (and others) help here in the forum it is slowly starting to make sense.

sudo mkdir /media/data - We created the directory.
sudo chown root.users /media/data - we changed the owner to root ??
sudo chmod 770 /media/data - We gave everyone all rights ??
sudo chmod g+s /media/data - What did we do here?

ln -s /media/data ~/data - we linked this directory to a directory in my home directory.


And now - without wanting to appear to be greedy - can some one help me with the second part of my original question.

Thanks again

Neill!

---

### Post by bodhi.zazen on 2007-07-24
> **NeillHog said:**
> Thanks again bodhi.zazen
Kubuntu is as clear as mud but with your (and others) help here in the forum it is slowly starting to make sense.

When it all makes sense, let me know :twisted:

sudo mkdir /media/data - We created the directory. 
# yep

sudo chown root.users /media/data - we changed the owner to root ??
# Well, with the sudo command the directory belonged to root.root (that is owner.group) ...\
#So we changed the group ownership from root to users

sudo chmod 770 /media/data - We gave everyone all rights ??
# We gave rights to the owner (root) and group (users)
# We removed rights from everyone else
# Format is user(owner):group:other(everyone_else)
# Take a peak at permissions ...

sudo chmod g+s /media/data - What did we do here?
# He he he ... we set the gid on the directory. When you create a file, you will be the owner and your primary group will ge the group and permsisions are set with umask ...
# by setting the gid any file created in the shared directory will have a group ownership of the directory, in this case users ...

ln -s /media/data ~/data - we linked this directory to a directory in my home directory.
# yep

> And now - without wanting to appear to be greedy - can some one help me with the second part of my original question.

Thanks again

Neill!

Same way ...

this time no sudo ;)

chown neill.users /home/neill/data/Bilder
chmod 770 /home/neill/data/Bilder

You can also set permissions via the gui (nautilus)

Open home, navigate to /home/neill/data

Select the directory Bilder -> select the permissions tab -> set permissions via pull down menu.

---

### Post by NeillHog on 2007-07-26
It worked!
 Once again bodhi.zazen - thank you.

Maybe I could even get to enjoy all this Ubuntu stuff :-)

Neill

---

