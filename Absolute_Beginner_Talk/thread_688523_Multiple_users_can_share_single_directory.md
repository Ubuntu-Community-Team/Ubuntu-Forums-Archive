---
title: "Multiple users can share single directory?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by MadCatX on 2008-02-05
Hi folks,

I've recently decided to switch from Windows to Linux and have been very happy with Ubuntu since.

There's one thing I haven't been able to figure out yet, I was hoping someone on this forum could help me:

I want to share a single directory with multiple users where, within that directory, any user has full read/write/execute/delete/etc permission on every file or directory once it is created. So we wouldn't need to set full permissions on every file/directory we create, everyone has full permission no matter who created/owns the file/directory. 

Can someone tell me if this is possible and if so, how would I go about doing it?

Thanks,
Madcat

---

### Post by kernel tom on 2008-02-05
Whoever owns the partition this directory is on is going to be the main permissions holder.  Usually the permissions will be 755 or rwxr-wr-w owner:group:global

The easiest and most dangerous way to change this is to change the directory to 777
however, this isn't dangerous if you control who is on your machine, and that they are not malicious


sudo chmod -R 777 directory 

this will give global rwx permissions

however, the only one who will be able to have write permissions to newly created files will be the user who has root permissions and the user who created the file.

-kt

---

### Post by jrothwell97 on 2008-02-05
I doubt it is possible. In Linux, every file has its own set of permissions. I'm not sure if there's a way to get it to abandon that whenever file *x* is copied into folder *y*.

You may be able to use chmod at the command line to bomb all of them to 777, but that would have to be done manually, unless you set it as a cron job in the background to execute every minute or so.

---

### Post by kernel tom on 2008-02-05
yeah ur almost undermining one of linux's great security measures...

btw dont do 777 to all folders... instead to this

for each user

sudo usermod -g <group> <username>

where <group> is the group that you want everyone to be in

then do 
sudo chown -R <username>:<group> directory

where <username> is you and you are in <group> with everyone else.

then do
sudo chmod -R 775 directory

you should never give global write permissions, its dangerous

-kt

---

### Post by Cypher on 2008-02-05
Find a common place to share, if you want to this to be a seperate partition all-together, then you can mount it using the option "umask=002" in the /etc/fstab file.

Then you will want to go into each user's .bashrc or the global bash profile file and set the command "umask 002" which will make every file/directory have 775 permission and thus both the owner and everyone in the same group can do anything to those files/directories.

This has the unfortunate side-effect of making every file in your own home directory come up with 775 as well..if that is not a consequence, then this will work fine.

But it looks like you are essentially migrating from a Windows environment where multiple people used a PC that booted right into Windows without different profiles, so you might want to mimic that in Ubuntu as well and login to a default profile for every user rather than having multiple profiles and trying to share a single directory..

---

### Post by Nythain on 2008-02-05
aye, was totally gonna be my advice till pc overheated...
just create a group for you and the other users
create the directory
add you and other users to the group
chown the directory to you:group
then chmod it to 775

much more secure than a 777

---

### Post by MadCatX on 2008-02-05
Thanks for the great advice all. I got the group-thing to work so I think that's how I'll go about it!

---

