---
title: "Getting around permissions..."
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Will5639 on 2006-10-13
First and foremost, I'm at the boiling point because I can't even work in /var/www/ for apache.

But Ok.. i respect the idea of permissions, keeps people like me who are inexperienced with the linux file system from really screwing something up.

But enough is enough, I wanna do the utmost simple tasks, like creating files and folders... and cannot becuase I don't have 'root' permissions.

How can I on startup (aka not have to do something over and over ...) have the right permissions?  Either globally or by designating one folder at a time?

---

### Post by willca on 2006-10-13
Theoretically, if you work only within your home folder, you can pretty much do anything you want in that environment. Nothing really needed to play around permissions here.

Where are you trying to create files/folders?

Cheers-
-W ;)

---

### Post by jordanmthomas on 2006-10-13
```
gksu nautilus
```
Navigate to /var
Right click on www.
Change its permissions to have it owned by your user.

If you have Konqueror installed, use it instead of nautilus because it will recursively change all the files within to be yours.

---

### Post by skymt on 2006-10-13
You should do what I do: make a launcher on the panel that runs "gksudo nautilus". Then one click and one password entry will give you a root file browser that you can do whatever you want with.

If you want something similar in the shell, use "sudo -s". You can even run graphical programs from this root shell, and they will, of course, run as root.

You can even take it a step further: enable the root account. It's easy, just run "sudo passwd". Once you do this (and maybe set "Allow Root Login" in GDM, I don't remember the default) you can log in to Gnome as root.

---

### Post by steve.horsley on 2006-10-13
OK, you've had a couple of suggestions to use **gksudo nautilus**. While in a root nautilus, I set the background red to remind me that I'm in dangerous mode.

If you need a root command prompt, use **sudo su**. This command prompt retains root priviledge until you exit.

---

### Post by thornomad on 2006-10-13
What I did was create a symbolic link to a www directory in my home folder -- this made it easy for me to login remotely and access the files as well.  Details: 

[http://www.damontimm.com/blog/how-to-redirect-apaches-default-www-or-public_html-folder-to-a-directory-in-your-home-folder/](http://www.damontimm.com/blog/how-to-redirect-apaches-default-www-or-public_html-folder-to-a-directory-in-your-home-folder/)

Am not sure if that is the most "secure" way, but it works well for me.

---

### Post by TheWizzard on 2006-10-13
> OK, you've had a couple of suggestions to use gksudo nautilus. While in a root nautilus, I set the background red to remind me that I'm in dangerous mode.

get familiar with the command line. it is some efford in the beginning, but in the end the command-line is your best friend.

> If you need a root command prompt, use sudo su. This command prompt retains root priviledge until you exit.

or **sudo -i**

---

### Post by fatsheep on 2006-10-13
or you could use this command to make /var/www your own folder (so you don't need root permissions to work in it):

sudo chown -R $USER:users /var/www

---

### Post by Will5639 on 2006-10-14
Thank's all for the suggestions.. 

What fatsheep suggested is percicely what I was looking to hear.

---

### Post by Will5639 on 2006-10-15
Side note... > **jordanmthomas said:**
> ```
gksu nautilus
```

I find myself using this (Simply made a link on my Panel) often, I'm just curious is there any way to add a parameter to this?

In such that, when I launch the shortcut (or link.. *whatever*), it automaticly completes the password authorization screen for me?

*and please disregard the 'oh bad idea' responses.. I understand the "risks" I'm taking.*

---

### Post by TheWizzard on 2006-10-15
> *and please disregard the 'oh bad idea' responses.. I understand the "risks" I'm taking.*
obviously you don't.

---

### Post by Will5639 on 2006-10-15
> **TheWizzard said:**
> obviously you don't.

Thank's for a waste of a post.

I posted here because I'm new to Ubuntu, not to computers.

Try not to confuse the two again.

---

### Post by triplep on 2006-10-15
I personally like a combonation of ideas,

make a /var/www/blah and chown it, then symlink it back to your home directory.

I know you already have a solution, but it's always nice to have options.

---

### Post by capn_hector on 2006-10-15
back on topic you could also set up a group web (users that can edit the website pages, i have a webserver setup this way) then add users to this group and do a group own on the folder.  heres a good tutorial on users and groups.  [http://www.opensourcetutorials.com/tutorials/Server-Side-Coding/Administration/user-administration/page1.html](http://www.opensourcetutorials.com/tutorials/Server-Side-Coding/Administration/user-administration/page1.html)

---

### Post by TheWizzard on 2006-10-16
> Thank's for a waste of a post.

I posted here because I'm new to Ubuntu, not to computers.

Try not to confuse the two again.
i don't. 

surry dude, but: 
> I find myself using this (Simply made a link on my Panel) often, I'm just curious is there any way to add a parameter to this?

In such that, when I launch the shortcut (or link.. *whatever*), it automaticly completes the password authorization screen for me?
is just plain stupid. on every computer. it's just asking for trouble... (although it can be easily done). 

especially if you want to run an apache server i would advice you to obey security do's and dont't's. ubuntu is already rather relaxed on the security side because it is meant for desktops (not ubuntu server of course). 

please try to get familiar with the way stuff is organised in linux. it is differten, but also quite logical. and try to get use the command line for root's tasks. it saves you when you run into real trouble.

---

### Post by PriceChild on 2006-10-16
I would reccomend adding you to the "www-data" group instead of changing any permissions.

---

