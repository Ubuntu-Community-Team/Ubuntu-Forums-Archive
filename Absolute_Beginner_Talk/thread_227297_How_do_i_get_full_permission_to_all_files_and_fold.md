---
title: "How do i get full permission to all files and folders?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Mennoz on 2006-08-01
I'm a Linux/Ubuntu newbie, so i think this is the right place to drop this question;)  

How come i can not place files in certain maps or modify certain files?

For example i need to change etc/apt/sources.list.

When i try to save the modified sources.list, gedit says:
'You do not have the permissions necessary to save the file' 

I think it's because i am just a user, and not an 'admin' or 'superuser'.
But how can i login like that? I only filled in my useraccount during the install.

---

### Post by jrjr on 2006-08-01
.

---

### Post by cheway on 2006-08-01
Try typing...

"sudo gedit /etc/apt/sources.list"

...into the console. This is what I do when I want to edit the source list.

When I want to add/edit other things (installing plugins for XMMS or aMSN for example) I type...

"gksudo nautilus"

...and then I add the files that I require through the window that pops up.

I can't be much more specific/helpful than that I'm afraid, I'm a n00b myself!

---

### Post by Tomosaur on 2006-08-01
Try learning how to use the terminal for things like this. To gain the privileges you want, you should use the 'sudo' command. To edit that file in the terminal for example, you'd open it (the terminal) up and type:

```

sudo nano /etc/apt/sources.list

```

nano is a terminal based editor. If you wanted to use a GRAPHICAL editor, you'd use gksudo, like this:

```

gksudo gedit /etc/apt/sources.list

```

The password both sudo commands will ask you for is just your normal login password.

---

### Post by orb9220 on 2006-08-01
or to be able to copy and move files in nautilus. Drag a places like home or computer icon onto panel. then right click properties. and on command line insert gksudo nautilus and close you now can sudo browse.

Good for copy and moving files around, But beware that any sudo operation is a danger.

---

### Post by shotomonk on 2006-08-01
Alternatively If you are super-sure of what your doing you can re-enable the root user by following this guide:

[http://https://help.ubuntu.com/community/RootSudo]("http://https://help.ubuntu.com/community/RootSudo")

From then on you can 'su' to root user and have full permissions.

---

### Post by Mennoz on 2006-08-01
Thanks for your replies, i've changed sources.list now.

But isn't it a bit weird that this is the only way to do things like editing files?
I mean, it doesn't makes a lot of sense to me? When i installed RedHat (long ago) i got an admin-account. Why not with Ubuntu?

I'm the only user on this computer, thus why can't i be able to just do with the files what ever i want( without the 'sudo' command)? 

I'm sure there is an explanation, but i just entered the World of the Penguin, so i'm just curious.;)

---

### Post by Tomosaur on 2006-08-01
Well, if you're connected to the internet and you're constantly logged in as the root user, it's only a matter of time before someone hacks you, or you download a program with malicious code on the offchance that you're logged in as root.

---

### Post by stupidkid on 2006-08-01
> **Mennoz said:**
> Thanks for your replies, i've changed sources.list now.

But isn't it a bit weird that this is the only way to do things like editing files?
I mean, it doesn't makes a lot of sense to me? When i installed RedHat (long ago) i got an admin-account. Why not with Ubuntu?

I'm the only user on this computer, thus why can't i be able to just do with the files what ever i want( without the 'sudo' command)? 

I'm sure there is an explanation, but i just entered the World of the Penguin, so i'm just curious.;)

You do have a root account. Run:
```

sudo su (you will be in the root account)
passwd (to set a root password)

```

I hope that's what you mean...

---

### Post by jrjr on 2006-08-01
.

---

### Post by FenrisAbraxas on 2006-08-01
> **Mennoz said:**
> Thanks for your replies, i've changed sources.list now.

But isn't it a bit weird that this is the only way to do things like editing files?
I mean, it doesn't makes a lot of sense to me? When i installed RedHat (long ago) i got an admin-account. Why not with Ubuntu?

I'm the only user on this computer, thus why can't i be able to just do with the files what ever i want( without the 'sudo' command)? 

I'm sure there is an explanation, but i just entered the World of the Penguin, so i'm just curious.;)

Well, if you KNOW WHAT YOU ARE DOING, and want to suffer the same xploits windows have just because you are the only user and want to edit whatever you want with your normal user account try this:

```

sudo - s -H
chmod -R 777 /

```

Then EVERY user on the box will be able to edit anything. Just be carefull if that's what you want.

And yeah, there's an explanation.

If you are a user you only have permission to install things within your /home/user directory. why? well let's say you are surfing a site with spyware, and this site have some script that if you have a root account (like in windows 99% of the people uses admin accounts for everyday work) this site will install "spy_and_spam.sh" will load it at startup and probably will change your users settings.  But if you use the user account as it is, the spyware will not change a thing because the system will not allow it. (hope i made my point here)

Now if you want your user to edit important files that's what you will get, also if you get your box compromised by some cracker, he will whatever he want without trying to crack your root password :S. 

The root account is just for maintainance and users accounts are for everyday work. 

If you don't like the idea of typing sudo command use sudo -s -H and you will stay as root.

Have fun and welcome to the penguin world!

---

### Post by Mennoz on 2006-08-01
Ok, I understand. It all makes a lot of sense now. Thanks for your replies!

---

