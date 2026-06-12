---
title: "Permissions for beginners"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by cmw000 on 2005-11-02
I just started using Linux on my desktop and I like it, but one of the major hurdles I've found is this whole permissions/logging in as root concept. I understand that to do some things in the terminal, you need to log in as root. What I don't understand is how to gain permissions in the GUI. When I try to empty the recycle bin, *AHEM*, excuse me, TRASH CAN...I get a permissions error. This is annoying. Is it a good idea to be logged in as root all the time so I don't have to deal with this? Or what would an expert recommend to a newb?

---

### Post by Kyral on 2005-11-02
*hears sirens going off*

No no no, logging in as root is NOT a good idea. In fact some apps like XChat will yell at you if run them as root.

Ubuntu uses the sudo command to gain root power for the command only, which is why you see things like

```
sudo apt-get update
``` 

A classic tale in Unix mythos that warns about being root all the time is what happens if you run

```
rm -rf /
```

as root. It completely deletes your HD. If you try to run that command as a user, you won't ;P

For better info on the subject

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by towsonu2003 on 2005-11-02
never log in as root, this will make linux' security maybe worse than windows. File permissions are one of the basic security layers in linux...

here you can find a brief info on permissions: 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml) (don't worry about setting user id and stuff, just read it quickly)

here you can find info on permissions and a little bit of security:

[http://www.faqs.org/docs/linux_intro/sect_03_04.html](http://www.faqs.org/docs/linux_intro/sect_03_04.html)

basically, as you are logged in as yourself but not root, any malicious code you execute will be executed with your permissions (hopefully....) and will not damage the system as a whole. it will only damage your files in your home directory. it also is useful to protect configuration files from newbies like me. 

welcome to linux :)

---

### Post by LHZ on 2005-11-02
An easy way to set permissions with a GUI is to type 
> 
gksudo nautilus

This will give you a file browser with root privileges. You can now set any permissions you want for the files on your harddrive by right-clicking the file and going to the 'permissions' tab.

WARNING: As has been said above, running anything as root means that if you mess up, you mess up. It's best to use this root file browser ONLY to set the permissions you want, and immediately close it afterwards. Also, please stay clear of changing the permissions in the system folders (anything that isn't /home or /media) unless you're very sure you know what you're doing.

---

### Post by waimang on 2005-11-02
Hi cmwooo. 
I like this:

A classic tale in Unix mythos that warns about being root all the time is what happens if you run

Code:

rm -rf /


as root. It completely deletes your HD. If you try to run that command as a user, you won't ;P

For me it would be like taking a "panadol" for a head ache. I am finding this Ubuntu to be a BIG head ache. 
To many things need tweaking or are broken for this kid so back to bliss with Kanotix and Puppy.
I have Kanotix on my laptop and apart from the installation giving you more bulk than herd of Elephants..all works a treat.
Cheers,
Tim.

---

### Post by Kyral on 2005-11-02
Thats the great thing about Linux. So many choices. Some people like Slack, others Gentoo, others Ubuntu, and still more Kanotix. I'm sorry Ubuntu didn't work out for you, but the fact that you still use Linux is awesome :D

---

### Post by pasmith on 2005-11-02
I'm stumped on a permissions problem.

I have a directory that is owned by a group other than my 'primary' group:

drwxrws---  3 oracle oinstall 4096 2005-10-31 17:48 product

So I added my user ID to the oinstall group:

uid=1000(pasmith) gid=1000(pasmith) groups=1000(pasmith),1002(oinstall)

But I still can't get into the directory. What am I missing?

I know I could just chmod it to 777 or something, but I'm trying to do things the 'right' way.  Can anyone help?

---

### Post by cmw000 on 2005-11-04
Someone correct me if I'm wrong, but I think you should just chmod it. That's what it's there for.

And thanks to everyone who replied to my question. I don't have time to read any of the resources right now, but I'll read them later when I feel adventureous and log into Linux instead of XP.

---

