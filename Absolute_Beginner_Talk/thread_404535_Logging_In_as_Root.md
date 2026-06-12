---
title: "Logging In as Root"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Shichao on 2007-04-08
I was wondering how you log in as root. Could someone please tell me as soon as possible. :confused:

---

### Post by mac.ryan on 2007-04-08
From a terminal:

```
sudo -i
```

---

### Post by trent dillman on 2007-04-08
...

---

### Post by ograbah on 2007-04-08
> **trent dillman said:**
> or
```
sudo su -
```
or
```
sudo -s -H
```

once root, you can use 'passwd' to set a root password, then use
```
su -
```
to become root

or

```
sudo passwd
```
then enter the password you want root to have.  After that, you just log out and then log back in as root with the password you setup.

You shouldn't need it though.  The user you created during the install can run commands as root if you type command ```
sudo
``` in front of whatever command you are running.

---

### Post by infoseeker on 2007-04-08
I prefer ```
sudo -s
``` as all my aliases are as when I am user but with root privileges :).

---

### Post by ardchoille42 on 2007-04-08
You don't log in as root, it's not necessary. the root account is locked by default in Ubuntu and we use the [sudo]("https://help.ubuntu.com/community/RootSudo") command to perform admin tasks.

I have been running Ubuntu on 11 machines (5 of which are servers) since Warty and I have never seen an instance when logging in as root is needed.

You can get a root shell with:
```

sudo -i

```

When someone tries to break into your computer, they know you have a root account so they can sit there and try to brute force that. But, if the root account is disabled, they can't do that. And they can't break into your user accounts because they don't know the user names.

Having the root account locked and using sudo just makes the system that much more secure.

---

### Post by steevk on 2007-04-08
Everyone has already told you how. However, I'm wondering why this is neccesary? You should never really need to log in as root, and in fact, it's a poor idea. 

If you don't mind me asking, why do you need to know? Maybe there's a better way to accomplish what you're trying to achieve.

---

### Post by mac.ryan on 2007-04-08
> **ardchoille42 said:**
> I have been running Ubuntu on 11 machines (5 of which are servers) since Warty and I have never seen an instance when logging in as root is needed.

Hi, I agree with your statement, yet, at times (when piping various commands all of them needing root priviledges) the system seems to mess up if i run the commandline with "sudo"... how did you work around that? I only managed opening a root shell with "sudo -i"... any advice welcome.

---

### Post by aysiu on 2007-04-08
Can you be more specific than "the system seems to mess up"? What happens when you run a command like ```
sudo apt-get update
```?

---

### Post by Shichao on 2007-04-08
Well.. I was trying to log in as root because when I tried moving a file to a folder it said I don't have permission to change this archive(or something like that) even though I'm admin of my laptop. I was thinking that logging in as root would allow me to move that file. Is there an alternate solution? :confused:

---

### Post by happymellon on 2007-04-08
> **Shichao said:**
> Well.. I was trying to log in as root because when I tried moving a file to a folder it said I don't have permission to change this archive(or something like that) even though I'm admin of my laptop. I was thinking that logging in as root would allow me to move that file. Is there an alternate solution? :confused:

Automatix has some nice right click scripts that will give you:

Open in GEdit as root and
Open this directory in Nautilus as root

It's only Nautilus as root that your hitting a wall against, or you could change permissions on the file. It would be simpler than creating a root account too.

---

### Post by steevk on 2007-04-08
> **Shichao said:**
> Well.. I was trying to log in as root because when I tried moving a file to a folder it said I don't have permission to change this archive(or something like that) even though I'm admin of my laptop. I was thinking that logging in as root would allow me to move that file. Is there an alternate solution? :confused:

The above post gave a good way to do it with the GUI. If you're not scared of the terminal, you can try this:

```
% sudo mv /path/to/the/file /path/to/the/destination
```

---

### Post by Freakazilla on 2007-04-08
do you have to set a UNIX password or not?

---

### Post by LaurelLynn on 2007-04-08
No,

You could edit   /etc/shadow  and remove the passwords for

root and your usernames directly ( nothing between the first two colons = no password ).

BUT please reconcider.  It would make your computer Windows XP home complient, but comes with all the inherent risks that in tails. And I don´t know how Gnome or some other apps would react.

Laurel Lynn

---

### Post by happymellon on 2007-04-08
> **Freakazilla said:**
> do you have to set a UNIX password or not?

Ubuntu will set up so that if you run sudo in a terminal and it asks for a password, it is referring to the password for the first created user, if it is your machine then it is more than likely your own password you used to log in. You don't need to do any additional password set ups unless your trying to create a root account which isn't advised since as my previous post mentioned you can set it up as a right click option in Nautilus or use the sudo command in the terminal and it will prompt your for your password, no harder than that.

---

### Post by Punker on 2007-04-08
ok I have a question 

I have a unix password 
and sudo password
what is the differences  because bolth are different

---

### Post by 23meg on 2007-04-08
"UNIX password" corresponds to just any user password. The reason you see the term at all is almost certainly that you set up a root password with ```
sudo passwd root
```

That is root's password, the password you use to log in as the UNIX (super)user "root". Your "sudo password" (bad term), the password you enter to use sudo, is the actual password of your own user.

---

### Post by aysiu on 2007-04-08
> **Shichao said:**
> Is there an alternate solution? :confused: There are much better alternatives. Read about them here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by trent dillman on 2007-04-08
...

---

### Post by aysiu on 2007-04-08
> **trent dillman said:**
> you could take a page from apple and make everything world-writable :-)

(ducks)
Actually, they don't. When my wife's widgets were acting up, we had to use the terminal and *sudo nano* to edit a system library on her Mac.

---

### Post by trent dillman on 2007-04-08
...

---

### Post by mac.ryan on 2007-04-08
> **aysiu said:**
> Can you be more specific than "the system seems to mess up"?

As you quoted me, I assume the question was to my issue with piping commands, rather than to the OP (sorry to hijack the thread...)

Well, as I get used to use "sudo -i", I can't really recall what was the situation I incurred in. I suppose it was something down the line of what also explained in the official documentation (section "downsides of using sudo"): basically if you give on a single command line different "steps" (piping or redirecting) there are situations in which the "root permission" given by *sudo* doesn't apply to all the steps, thus the command will fail to work.

I honestly can't recall the exact situation I was in, but I solved issuing the same commandline in a root shell...

---

### Post by aysiu on 2007-04-08
Yeah, you end up having to repeat the *sudo* command somewhere along the way for piping, but it does work. If you want to use *sudo -i*, that's cool, but you should also know you don't have to.

---

