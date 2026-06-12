---
title: "Loging in as the &quot;root&quot; user?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Rasorial on 2006-11-17
Hi all, new user here using 6.10. I need to do a few changes that requires root user permissions. How do you log in as "Root"?

thanks

Rod

---

### Post by scrooge_74 on 2006-11-17
Use the sudo command

---

### Post by Rasorial on 2006-11-17
> **scrooge_74 said:**
> Use the sudo command

Hi there, how do you use the sudo command and where do you find it?

Thanks.

Rod

---

### Post by aysiu on 2006-11-17
You never need to log in as root (except when you boot into recovery mode, and even then you're not logging in, you just *are* root).

Command-line info:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

GUI info:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by tribaal on 2006-11-17
Logging in as root is probably the top one security hazard on linux, and should be absolutely avoided (even if you root account is enabled - use su).

"Sudo" lets you borrow root access rights. To use it, just add "sudo" before the command you want to use as root, and when prompted, enter *your* password (not root's).

Additional information can be found [here]("https://help.ubuntu.com/community/RootSudo").

Hope this helps :)

- trib'

---

### Post by wpshooter on 2006-11-17
> **Rasorial said:**
> Hi all, new user here using 6.10. I need to do a few changes that requires root user permissions. How do you log in as "Root"?

thanks

Rod

You really don't need to do that, although it is possible.  I thought that I needed that capability when I first started using Ubuntu, but I found out that I did NOT.  Use the advice given to you in the other replies to your post.

Good luck.

---

### Post by Rasorial on 2006-11-17
> **tribaal said:**
> Logging in as root is probably the top one security hazard on linux, and should be absolutely avoided (even if you root account is enabled - use su).

"Sudo" lets you borrow root access rights. To use it, just add "sudo" before the command you want to use as root, and when prompted, enter *your* password (not root's).

Additional information can be found [here]("https://help.ubuntu.com/community/RootSudo").

Hope this helps :)

- trib'

Hi there, thanks for your help, maybe I should explain more about what I am trying to do. 

I've installed Mozilla Thunderbird via "Add/Remove" but the default icon is just an envelope. I have a copy of the correct icon which I am trying tp paste into the thunderbird folder in usr/share/thunderbird/icons.

The message is that I do not have permission to write to this folder.

Some really simple instructions would be appreciated.

Cheers

Rod

---

### Post by tribaal on 2006-11-17
Alright I get it. You should still use sudo, something like the following command (ran from the directory where your new icon is):

```
sudo cp <iconfilename> /usr/share/thunderbird/icons
```

At the prompt, put in your password.

This should do the trick... You might want to check that it worked by navigating to /usr/share/thunderbird/icons with nautilus (the ctrl-l shortcut is useful for quickness).
cp is the command for copying files. So the command starts by "sudo" (borrowing root rights), then copies the icon file to the destination folder.

Hope this helps :)

- trib'

---

### Post by Rasorial on 2006-11-17
> **tribaal said:**
> Alright I get it. You should still use sudo, something like the following command (ran from the directory where your new icon is):

```
sudo cp <iconfilename> /usr/share/thunderbird/icons
```

This should do the trick... You might want to check that it worked by navigating to /usr/share/thunderbird/icons with nautilus (the ctrl-l shortcut is useful for quickness).

Hope this helps :)

- trib'

Thanks for your reply, I get the general idea. The icon is just sitting in my home folder. How do I run the command from my home folder?

Rod

---

### Post by Henry Rayker on 2006-11-17
cd /home/<username>
sudo cp <iconfilename> /usr/share/thunderbird/icons

---

### Post by tribaal on 2006-11-17
Easy enough: when you open a terminal window, you are in your home folder (just like when you open nautilus). 

If you move around (using the "cd" command - "change directory"), just issuing the "cd" command without arguments will get you back to your home folder.

So just open a terminal window, and paste in the command line I mentionned in my previous post, and it should work. Of course, replace <iconfilename> by the actual icon name (including the extention if any) :)

I know the terminal can be quite intimidating at first, but it is really worth learning how to use it (at least at a very basic level), since it's the easiest way for people to give tips to each other (graphical user interfaces change and depend on many factors - terminals are always terminals :) )

I'm sure you can find a few good introductions to the linux terminal online. It's really a powerful tool! I used to hate it, now I love it :)

Hope this helps :)

- trib'

---

### Post by CujoQuarrel on 2006-11-17
If you want a shell to do a few 'root' operations you can always just type "sudo bash" in a bash shell to get a shell with root privs.

Prob not the correct way to do it but I like it.

---

