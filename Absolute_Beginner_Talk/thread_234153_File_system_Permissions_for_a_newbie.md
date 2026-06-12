---
title: "File system Permissions for a newbie"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by soutSA on 2006-08-11
To start this off I am just going to try and explain what I have done, I am fairly new with this so please bare with me.

OK...I am trying to copy a Folder from my Home directory to the /opt directory. I have installed LAMP and are trying to configure a normal website at first, so I am trying to copy a folder containing HTML files to the following folder called /opt/www. 

My problem I have now is that my the /opt folder is locked for my user to do anything and a bit dum still using the proper command lines. I was abble to do this about 2 days ago.

I have recently updated my kernel from i386 to the i686(do not know if this matters at all).

---

### Post by macca87 on 2006-08-11
I'm assuming ur /opt/ directory needs root privileges, you can check this by 'ls -l' in your '/' directory. (It should be)

You will need to make sure your user has sudo privileges.
Try sudo cp FILENAME /opt/www/FILENAME
It will ask for a password, use your normal login password.

If you already know that, go to System > Admin > Users and Groups, and then make sure your user has sudo priveliges.

---

### Post by soutSA on 2006-08-11
I think I am just being a bit close minded today. I am trying to copy a folder and not just one file. Is there a different way to do this.

Why do my administrative account show that It have proper permissions but can not perform any su tasks? It still shows that the filesystem is locked and I am unable to do any task at filesystem level with this account. This is only in the desktop enviroment and not when I do it through the terminal.

All help appreciated.

Thanks in advance

---

### Post by nomb on 2006-08-11
by default in ubuntu there isn't a root account so su doesn't work everything is done with sudo altho I'm not sure how this is more secure.  if you want to get your root account working do this

sudo passwd root
*type your regular password*
type the password you want for root
re-type

you should then be good to go
now you can su
--------------------------------------

you could just do the sudo command to 
copy the folder over where you want it

---

### Post by sirlancelot on 2006-08-11
You'll want to use cp with the -r option (r for recursive)```
sudo cp -r /home/ /opt/www/
```Hope this helps. the -r option will copy everything in the folder as well as all folders within. you can add -v (for verbose) to see what it's copying.```
sudo cp -rv ... ...
```

Welcome to the world of Linux!

---

### Post by soutSA on 2006-08-11
It works:D 

Thanks for all the input, but still got an question. I was able to copy paste into the /opt directory with my normal user account just 2 days ago and now I am unable to do so.

Anybody got an idea?

Thanks

---

### Post by orb9220 on 2006-08-11
where you running a gksudo nautilus that is what I do when I want to browse to a root file system and copy and paste or modify a config.

But be careful
If you do a right click copy for a config file as an example then do a right  click psste then you will have a copy of the file there next to the one your going to modify for backup.

Good luck

---

