---
title: "Tired of permissions.  Getting annoyed"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by waste301 on 2008-03-09
I've been using ubuntu on my home PC for a few months now, and I've consistently run into permission problems.

I download a program written  for debian - can't write to .usr

I get a new phone - can't put music on it because I'm not "owner"

I try to fix it with various commands - sometimes certain directories will be allowed.

Then I have to run the commands all over again if I re-start my computer.

Is there any way to skip this crap and be the owner of my own computer where I can read or write to any directory I please? Permanently? Do I need to be logging in as Owner with some hidden password?

I don't have any sensitive data I need protected from other people who might access my PC at home.  I am a newb at linux but enough already with protecting me from myself - thats why I switched to ubuntu.

---

### Post by Jimmyfj on 2008-03-09
I don't know what commands you are refering to. But -

```
sudo chown -R user:user /dev/device
``` 
 or

```
sudo chown -R user:user /media/device
``` 

should be enough to keep the ownership of that device, even after 100 reboots.

---

### Post by handydan918 on 2008-03-09
Just a little note on permissions....
The unix permissions model employed by virtually all Linux distros is the main reason that virus writers target Windows. 
If the market shifted tomorrow and Linux had 75% market share, there STILL wouldn't be the vast number of "cracks" against Linux that exist on the lesser O/S's.
Permissions don't just protect you from yourself. They protect you from everybody else, too.

---

### Post by waste301 on 2008-03-09
> **Jimmyfj said:**
> I don't know what commands you are refering to. But -

```
sudo chown -R user:user /dev/device
``` 
 or

```
sudo chown -R user:user /media/device
``` 

should be enough to keep the ownership of that device, even after 100 reboots.

Thanks for the response. Sorry but I am a newb - does this mean type "sudo chown -R (my login at startup):(my login again) /home(?)/(where do I do this?)

Does "device" mean my computer's name?  or root? or owner? or home? Where would I find that?

---

### Post by waste301 on 2008-03-09
sorry :( = : (

---

### Post by Jimmyfj on 2008-03-09
If your username is hugo, then the command will look as follows:

```
sudo chown -R hugo:hugo /media/name of device(i.e. sda1)
```

You'll need to go to Programs>Accessories>Terminal window and type in the command in the terminal.

I know you're tired of permissions but give it a shot. Click your way into /dev or /media through Nautilus file browser. Try this:

```
gksu nautilus
``` 

Also from withinb the terminal window - This will start up nautilus with root-permissions making it easier for you to surfe the disk.

And for your questions about the command: 

sudo = Run task as root
chown -R: ChangeOwner, -R means recursive, including forlders and subfolders
User:user - The name of the user and group who shall own the device
/dev or /media - both are a path to the device. Both forlders are stored under / (root)

---

### Post by waste301 on 2008-03-09
> **Jimmyfj said:**
> If your username is hugo, then the command will look as follows:

```
sudo chown -R hugo:hugo /media/name of device(i.e. sda1)
```

You'll need to go to Programs>Accessories>Terminal window and type in the command in the terminal.

I know you're tired of permissions but give it a shot. Click your way into /dev or /media through Nautilus file browser. Try this:

```
gksu nautilus
``` 

Also from withinb the terminal window - This will start up nautilus with root-permissions making it easier for you to surfe the disk.

And for your questions about the command: 

sudo = Run task as root
chown -R: ChangeOwner, -R means recursive, including forlders and subfolders
User:user - The name of the user and group who shall own the device
/dev or /media - both are a path to the device. Both forlders are stored under / (root)

thanks - will try

cat has decided to sleep on my chest - will try later

---

