---
title: "Permissions for web dev?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by eDRoaCH on 2007-11-15
Not sure I quite belong here, but this seems like a very simple one. My first introduction to ubuntu was to set up a mediawiki server to consolidate tech support information for my job. I used linux because I knew it was the right tool for the job and I have been so very impressed with ubuntu since. 

I have spent the last few days getting ubuntu 7.10 on my laptop to do everything i want it to do. Bluetooth headset with skype, avg menu, beryl, etc. Mostly thanks to these forums.

So this one just has to be simple. I want to do some amateur web developing on this system, and therefore I just want to edit the var/www directly. However I do not have permissions to save. I made a group called webdev, added root and my user to it, and I thought I gave it the right group permissions by using the gui (rclick on dir and hit properties) I clicked the 'apply to contained files' button but it didnt seem to do anything. I still have no ability to delete files, even though I can create them.

What am I missing? What is the "proper" way to do this?

Help much appreciated!

---

### Post by p_quarles on 2007-11-15
To edit the permissions on files that don't belong to your user, you need root privileges. To do this with the GUI file manager, you can run this command:
```
gksudo nautilus
```
now, when you click on "apply" the settings will stick.

The command line equivalent is also pretty easy:
```
sudo chmod -R 774 /var/www
```
That will give the user and and group owners full access to those files.

---

### Post by eDRoaCH on 2007-11-15
I should have mentioned i used gksu nautilus. I added a link in the administration menu to it because I can never spell nautilus right... ^^;

I ran the command you mentioned, and now it says I can delete the files, but never does. It also tells me they cant be put in the trash. In the 'details' view the octal permissions, and owner are 'unknown'

I also should probably mention I made a separate 8gb partition for my /var/www at install

---

### Post by p_quarles on 2007-11-15
Nah, you haven't broken anything (yet). :) Nautilus just isn't the best file manager in the world (you might try Thunar or Konqueror -- both much better imho)

Anyway, you can set "webdev" as the owner by typing this:
```
sudo chown -R webdev /var/www
```
If that gives you an error, it's likely because you only created the group webdev, and not the user. You can fix this by doing the following:
```
sudo adduser webdev webdev
```
run the previous command again, and you should be set.

---

### Post by eDRoaCH on 2007-11-15
still confused...

edroach@eDToP:~$ sudo adduser webdev webdev
[sudo] password for edroach:
adduser: The user `webdev' does not exist.

I found that quite funny actually. No kidding they don't exist, you're supposed to be creating them!

So I went back to the gui and was going to add the user, but is this really what I want to do? As I never plan on logging in as this user, I will probably forget the password when I need it >.>

I know I could probably just take ownership of the directory, but is that safe? This is just a dev system, but I want to do it the "right" way. I don't want to learn bad security practices.

---

### Post by p_quarles on 2007-11-15
You can create a new user via the gui, that'll work fine. 

For the CLI, I guess you have to create the user first:
```
sudo adduser webdev
```
and *then* add it to the group:
```
sudo addgroup webdev webdev
```
Then, make it webdev the owner of /var/www.

---

### Post by eDRoaCH on 2007-11-15
Ok, after that failed (i ended up with 2 webdev groups and no user) I started to create a user in the gui and gave them 'no access'

I decided against this. Instead I got rid of the user and both groups (prob bad I know but to my knowlege these groups and user never did anything) and remade the webdev group, 

I added myself and root to it, then used the gui to make me the owner and the group webdev. The octal is 774. 

Is there anything wrong with this setup?

---

### Post by p_quarles on 2007-11-15
Sounds good to me. The only thing I'd add is that you don't need to add root to any groups, since it already has the ability to do whatever it wants. 

Anyway, if the current setup *works*, that's the important part. Since, as you say, the octal permissions are 774, it's completely safe against the scriptkiddies.

---

### Post by eDRoaCH on 2007-11-15
thanks much!

---

