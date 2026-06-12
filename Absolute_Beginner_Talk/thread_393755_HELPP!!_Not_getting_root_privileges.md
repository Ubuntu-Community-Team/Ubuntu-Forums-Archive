---
title: "HELPP!! Not getting root privileges"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by gravz84 on 2007-03-26
I have a similar problem and I need help pls!!

what i wanted to do was give myself complete root privileges since nautilus shows a lot of folders as locked.. and i can't change the permissions cos it says only root has permission to do that?? 

So i did something with visudo and commented one of the lines.. i think its purpose was to enable the root account so I don't have to type in the pwd repeatedly!

Now I can't execute anything as root with sudo command!!!
when I type "sudo command" it doesn't prmpt for pwd but doesnt do anything either!!!
I can't even edit sudo now with visudo!! nor any program that requires root..eg synaptic!!

and also how does sudo work with nautilus or any other graphical browser?? i mean the locked folders? u might be able to access them in terminal with sudo but wat about thru nautilus!!!!

HELPPPP!!!!!!!!!
I am really getting frustrated with ubuntu now..

---

### Post by Penguin Power on 2007-03-26
grav84, I'm not entirely sure what you mean by your problem, perhaps because I'm not familiar with Visudo... but you gotta just live with entering your root password every now and again, make it something you can type quickly and remember because the root password is the key to your system. don't run the root account just because you don't have to type password, you'll get all sorts of problems.

When you start nautilus, as far as i know, it will start with the permissions of the current user -so if you press [alt]+[f2] to start an application the command "gksu nautilus" will start nautilus as root graphically. I use it sometimes if i can't remember the path to a file... still clinging to my Windows GUI dependance here ;)

---

### Post by wj32 on 2007-03-26
DON'T give yourself root privileges. It is a stupid idea that defeats the whole purpose of security. This is **not** Windows.

When you boot up in GRUB, press Esc and choose a "recovery" mode. Then, it will ask for your root password. Hopefully you have one. If you don't, try pressing Ctrl+D. Then, type visudo and uncomment that stuff you commented.

To use nautilus in root, do:

<code>gksudo "nautilus --no-desktop"</code>

Don't change ANY permissions in /. Please.

---

### Post by seshomaru samma on 2007-03-26
Well what you should do is retrace your steps
Did you follow a wiki or maybe a post on the forum?
You can check the history tab in firefox if you dont remeber what you were following

please post the output to :
```
sudo cat /etc/sudoers
```

btw - you can easily run nautilus as root by issuing the command:
```
sudo nautilus
```
this will give you graphic access to alll files

---

### Post by Penguin Power on 2007-03-26
i concur. be very careful with your root priveleges. 

follow the thinkgeek "Got Root?" t-shirt motto:
"if you don't know what it is, you shouldn't have it."

i find gksu nautilus useful at times, however it's easy to make mistakes with it so make sure you know what you're doing before you do it :)

---

### Post by wj32 on 2007-03-26
Um, he can't USE sudo. That's the thing with visudo; it checks your file because if you stuff up... there's no going back (easily).

---

### Post by Tomosaur on 2007-03-26
Download the 'nautilus-gksu' package, and other nautilus scripts, or look for other '<command> as root' scripts for nautilus.

You should really get used to not messing around though - you shouldn't ever need to mess with anything outside of your home directory really. The programs which ask you for your password do so for a very good reason - they change important settings, files etc. By granting yourself system-wide root permissions by default, you're opening yourself up to problems, not least security problems.

If the locked folders are INSIDE your home directory - then you're doing something wrong.

In any case - the command to change permissions and ownership of root folders/files is:
```

sudo chown -R <username>\: <files/directories>

```

So if your username is mike, and you want to change everything on your system to be owned by you (which is a VERY, VERY, VERY bad idea):
```

sudo chown -R mike\: /

```
Under no cirumstances should you actually run that command. To change specific permissions on files you already own (such as readable, writable, executable), the most common command is:
```

chmod 755 <file>

```

You should only really do this on files inside your home directory - everything outside of your home directory is normally set up with the right permissions and ownership automatically.

So - if you want to open yourself up to errors and security problems - then go ahead and mess with permissions. If, however, you don't actually know what you're doing (which I assume is the case), then do not.

---

### Post by gravz84 on 2007-03-26
Thx fr all thehelp guys. I should have paid attention to all the warnings I got when I was editing the sudo file..I followed the "man sudo_root" and thought what I was doing would equate the user to root..
and yes rite now only root would be listed in /etc/sudoers
1. I will follow your advice and go to recovery mode and undo the change
2. I still don't get the whole permissions scenario and its really bothering me. I previously installed zope/plone and couldn't get access to the text file that contained the admin usr/pwd. Eventually I had to change the permissions for that particular file to read it. maybe it was only nautilus but **this seemed absolutely ridiculous to me that a user cant get access into something that he himself installs.**
3. how exactly do u run/read all programs files as root in nautilus like u do thru the terminal! 
**seshomaru samma** says **sudo nautilus** 
others say **code>gksudo "nautilus --no-desktop"</code> or gksu nautilus**
It is intuitive and i will check these out.
4. Nothing inside home is locked. 

Well I am a newbie..and this is how we learn :) by screwing up!!:lolflag:

---

### Post by STREETURCHINE on 2007-03-26
to popen nautilus with root permissions you open terminal and type


```
gksudo nautilus
```

that will open nautilus with root permissions

or you could just create a launcher so you can click and drag files to so they open with root permissions ,save time 

click on desktop ,click creat launcher

                     type =  application
                     name = open in root
                    command = gksudo "gnome-open %u"  (exactly as written)
                    comment = anything you like

find your self an icon and stick it on your desktop for later use

---

### Post by wj32 on 2007-03-27
Sorry about my screwed up <code> section...

1. OK. Do that.
2. File permissions are for your own safety. If any user could read passwords, they could **crack your passwords**. BTW, you didn't install the software. root did.
3. do gksudo nautilus or sudo nautilus or gksudo "nautilus --no-desktop". You can't use sudo nautilus outside of a terminal.
4. That's because you have permissions to your home directory. It's a your-own-stuff folder. That means, you can delete it, a virus can delete it, whatever. Nobody cares. However, you can't delete system files/folders. Everybody cares about *them*!

---

### Post by zvacet on 2007-03-27
If you are realy want that 
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

### Post by gravz84 on 2007-03-27
gksudo Nautilus is working fine for me. Thank you. Now I don't need to change permissions anymore.
Thanx

---

### Post by Arby on 2007-03-27
If you're struggling to get your head around the permissions system try this article [http://www.linux.org/lessons/beginner/l14/lesson14a.html](http://www.linux.org/lessons/beginner/l14/lesson14a.html) There's some good stuff on the next few pages as well

---

