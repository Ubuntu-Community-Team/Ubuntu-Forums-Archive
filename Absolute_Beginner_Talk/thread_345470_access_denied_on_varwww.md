---
title: "access denied on var/www"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Stevie007 on 2007-01-24
I have just moved from windows to ubuntu and am making good progress, but am stumped and can't see this problem posted elsewhere.

On installing the Ubuntu 6.06 LAMP server, I was asked only once for a username and password.

I have since used this to install the gnome desktop (sorry old windows habits - a fear of command line!) and webmin successfully. 

The apache server works ok as can be seen at [http://212.159.46.65/apache2-default/](http://212.159.46.65/apache2-default/)
I want to put my own index.html in the ver/www folder, but am getting access denied. I haven't created more than one user, so what am I doing wrong?

I have got this far, I am determined not to give up and resort to IIS! 
Please help.

Steve

---

### Post by kidders on 2007-01-24
Hi there,

There are a few basic things you should check first, like whether you have permission to modify /var/www or index.html. If not, you can always use sudo to grant yourself access.

---

### Post by Stevie007 on 2007-01-24
Many thanks for this,

so SUDO is like the default super user?

I typed SUDO chown <whatevermyusernameis> /var/www

and it prompted me for a password. I put in my user password and the promp just moved down a line, no errors.

How do I know if it was successfull?

many thanks for you help.

---

### Post by annda on 2007-01-24
you didn't get any errors, so the command was successful - otherwise you would get complaints / error messages.

by the way, you might want to change the ownership of directories recursively with the -R option.

---

### Post by ComplexNumber on 2007-01-24
> **Stevie007 said:**
> Many thanks for this,

so SUDO is like the default super user?

I typed SUDO chown <whatevermyusernameis> /var/www

and it prompted me for a password. I put in my user password and the promp just moved down a line, no errors.

How do I know if it was successfull?

many thanks for you help.
thats not a good idea. to edit a file in that directory, you were best off using 'gksudo gedit <filename>'. to move a file to or from there, you were best off using 'gksudo nautilus'. 
don't go round changing the directory permissions or ownership outside of your home directory unless you know what you're doing.

---

### Post by Stevie007 on 2007-01-24
thanks for this, and you are right. I don't know what im doing, as I have just proved, as now I am getting 

Forbidden, you do not have permission to access index.html.

so my apache placeholder is missing! Is there anyone who can spoon feed me exactly what I should be typing?

Thanks in advance.

---

### Post by kidders on 2007-01-25
Hey again,

What ComplexNumber said in criticism of my & annda's advice on solving your problem is true. Linux depends very heavily on filesystem permissions to prevent unauthorised fiddling with your system ... in some cases, one single permissions bit out of place can have devastating consequences, were your system to become the subject of an attack.

Thankfully, permissions & ownership are easy to understand, so you should read about them. In a way, using Linux without learning about filesystem permissions is a bit like using Windows without learning about firewalls!

How to work your website permissions is a matter of taste, really. One possibility might be to enable per-user web directories, and create your own personal www directory inside your home. That way, you would only ever be editing files in your own home directory. In the traditional Linux security model, the file access permissions at /home/username/www are relatively unimportant, and you could just forget about the whole issue. The usual URL for per-user websites is [http://hostname/~username](http://hostname/~username).

Then again, you might like to set up a group of users with explicit permission to modify the contents of /var/www. You could add yourself (and anyone else you liked) to that group, and **chgrp** your entire /var/www.

In general terms, you should _never_ alter the permissions/ownership of anything outside your home directory (no matter how inoccuous the change might seem), unless you know what you're doing. Having said that, you could equally argue: Hell, my PC is a personal desktop box ... what do I care if I'm a bit loose with my /var/www?!

Anyhow, the point is that Linux is designed to behave the way your posts describe. In the case of your /var/www, feel free to make any permissions changes you like, provided you understand the effect your changes will have.

I hope that helps!

---

### Post by Pobega on 2007-01-25
Wow, it seems a lot of people have been having trouble lately with accessing /var/www. Just an observation (And probably a pointless post) but this has to be the 10th thread I've seen on it in two days.

---

### Post by kidders on 2007-01-25
> **Pobega said:**
> Wow, it seems a lot of people have been having trouble lately with accessing /var/www. Just an observation (And probably a pointless post) but this has to be the 10th thread I've seen on it in two days.

Lol yep! Although I can easily imagine how a Windoze -> Linux switcher could get frustrated by how difficult Linux makes it to make apparently inconsequential little changes to system files. I guess the answer is only obvious when you already know it, hehe.

---

### Post by az on 2007-01-25
> **Pobega said:**
> Wow, it seems a lot of people have been having trouble lately with accessing /var/www. Just an observation (And probably a pointless post) but this has to be the 10th thread I've seen on it in two days.

I guess it's not intuitive.  Apache runs as the www-data user and needs that user to have priviledges to the files it serves.  

You run as a different user.  You can add your user to the www-data group and write files to its folders or make everyting owned by whomever and world-readable (in some cases world-writeable and executable - not recommended!)

---

