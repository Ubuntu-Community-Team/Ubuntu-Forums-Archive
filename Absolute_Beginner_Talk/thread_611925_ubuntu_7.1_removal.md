---
title: "ubuntu 7.1 removal"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by wsx123 on 2007-11-13
I have another linux distro installed with ubuntu 7.10, how do I remove Ubuntu?

---

### Post by wsx123 on 2007-11-13
Do I enter that into a terminal while booted into ubuntu?

---

### Post by eldepeche on 2007-11-13
Don't enter that anywhere.

It's a troll, and that command will delete all the files in your home directory.

EDIT: Although, since you want to remove Ubuntu, I guess it wouldn't make much difference...

Does your computer boot into the other Linux distribution by default?

---

### Post by WebSiteGuru on 2007-11-13
It will delete you home dir

---

### Post by schorsch on 2007-11-13
This command will remove your home folder under ubuntu but not ubuntu so just forget it!!!!

---

### Post by santiagoward2000 on 2007-11-13
> **eldepeche said:**
> Don't enter that anywhere.

It's a troll, and that command will delete all the files in your home directory.

EDIT: Although, since you want to remove Ubuntu, I guess it wouldn't make much difference...

Does your computer boot into the other Linux distribution by default?

Well, I know this guy's an idiot and is telling everyone to erase the home folder, but isn't that exactly what the person who wrote this thread wanted?

---

### Post by wsx123 on 2007-11-13
I installed ubuntu after open suse. When it powers up Ubuntu is listed at the top of the boot list.

---

### Post by RTrev on 2007-11-13
> **wsx123 said:**
> I installed ubuntu after open suse. When it powers up Ubuntu is listed at the top of the boot list.

You could edit the /boot/grub/menu.lst file to remove the Suse entries, which would avoid you having to deal with the GRUB menu on each boot.  Or are you trying to recover the disk space that Suse is using also?

Bob

---

### Post by Inxsible on 2007-11-13
> **RTrev said:**
> You could edit the /boot/grub/menu.lst file to remove the Suse entries, which would avoid you having to deal with the GRUB menu on each boot.  Or are you trying to recover the disk space that Suse is using also?

BobI think he/she wants to keep Suse and remove ubuntu.

Log into your Suse OS and then you can simply use a partition utility to remove Ubuntu. you will also have to change the grub entries accordingly.

---

### Post by RTrev on 2007-11-13
> **Inxsible said:**
> I think he/she wants to keep Suse and remove ubuntu.

Log into your Suse OS and then you can simply use a partition utility to remove Ubuntu. you will also have to change the grub entries accordingly.

Whoops, you're right.. I mis-read the original post.  Sorry.

---

### Post by eldepeche on 2007-11-13
Does SuSE use GRUB by default? If so, log in to SuSE, then use the grub command to allow SuSE to take over the bootloader. Something like:
```
$ sudo grub
> root (hd0,0)
> setup (hd0)
> quit
$
```
This will tell GRUB to look on the first hard drive's first partition for configuration information, install itself in the master boot record of the first hard drive, then quit. Modify the (hd0,0) and (hd0) to suit your needs. If you aren't exactly sure what to do, then come back.

Once you've fixed your bootloader (boot first to make sure it behaves correctly, and the menu corresponds to what SuSE thinks it should say), then you can go about removing the Ubuntu partition and recovering the space.

---

### Post by RTrev on 2007-11-13
Can't help but ask, though.. what do you like better in Suse than Ubuntu?

---

### Post by wsx123 on 2007-11-14
Thanks. I like the KDE desktop better and I like Yast for adding software.And I like being asked for a root password, not just a user password.

---

### Post by Inxsible on 2007-11-14
> **wsx123 said:**
> Thanks. I like the KDE desktop better and I like Yast for adding software.And I like being asked for a root password, not just a user password.
There is also KDE in Ubuntu. Its called Kubuntu :)
KDE has Adept and of course the terminal commands to install stuff (apt-get and aptitude) The first user that you create is the root user. You can, if you want create additional users and simply use them to do your daily activities and use the root account and password only when you install stuff etc.

---

### Post by Incense on 2007-11-14
To fix grub in openSUSE, open up YaST2, select System, Boot Loader, and you'll see your grub list. You can delete Ubuntu from the list there. Then to delete the Ubuntu partition, you can access the partitioner from the System area as well, and reformat the ubuntu partition  (make sure you select the correct one!) so you can use it for data, or another distro. You have to love YaST in openSUSE.

---

### Post by RTrev on 2007-11-14
> **Incense said:**
> To fix grub in openSUSE, open up YaST2, select System, Boot Loader, and you'll see your grub list. You can delete Ubuntu from the list there. Then to delete the Ubuntu partition, you can access the partitioner from the System area as well, and reformat the ubuntu partition  (make sure you select the correct one!) so you can use it for data, or another distro. You have to love YaST in openSUSE.

Okay, I'm thinking of doing some distro hopping again.  Could one of you Suse folks tell me what you like most, and what you like least, about the distro?  

Thanks,
Bob

---

### Post by Incense on 2007-11-14
> **RTrev said:**
> Okay, I'm thinking of doing some distro hopping again.  Could one of you Suse folks tell me what you like most, and what you like least, about the distro?  

Thanks,
Bob

Pros:

Great KDE 
One Click Install
Mature stable distro
KDE4 Games
Great OpenOffice 
Fast
Good Community repos
YaST
Kickoff KDE menu

Cons:

Community is not what it is here
YaST package management can be slow (though it's better in 10.3)
Some people do not like the Novell/Microsoft deal

Overall though, I really like openSUSE. Of all the KDE distros I have tried, it has worked out the best for me.

---

### Post by RTrev on 2007-11-14
> **Incense said:**
> Pros:

Great KDE 
One Click Install
Mature stable distro
KDE4 Games
Great OpenOffice 
Fast
Good Community repos
YaST
Kickoff KDE menu

Cons:

Community is not what it is here
YaST package management can be slow (though it's better in 10.3)
Some people do not like the Novell/Microsoft deal

Overall though, I really like openSUSE. Of all the KDE distros I have tried, it has worked out the best for me.

Sounds like a good, fair assessment.. thanks!  I'll give it a try.

Bob

---

### Post by wsx123 on 2007-11-15
I will try Ubuntu again on a fresh install. These forums are much better and I"m not much for Microsoft agreements.
1-How do I change the boot sound?

---

### Post by RTrev on 2007-11-17
> **Incense said:**
> Pros:

Great KDE 
One Click Install
Mature stable distro
KDE4 Games
Great OpenOffice 
Fast
Good Community repos
YaST
Kickoff KDE menu

Cons:

Community is not what it is here
YaST package management can be slow (though it's better in 10.3)
Some people do not like the Novell/Microsoft deal

Overall though, I really like openSUSE. Of all the KDE distros I have tried, it has worked out the best for me.

I'm downloading the 64-bit Gnome version right now.  Any "gotchas" to be aware of in the install?  I have Ubuntu on my sdb, and will put Suse on my sda.  Will the GRUB install (assuming Suse uses GRUB) handle this okay and give me both options on boot?

Thanks,
Bob

---

### Post by chips24 on 2007-12-21
ok, insert the live cd and you cant delete the partion, than install whatever you need, i did thet while dual booting and absolutely no effect . i dont know exactly if thats what you want to do though.

---

