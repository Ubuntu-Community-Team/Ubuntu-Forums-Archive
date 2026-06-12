---
title: "Quick Easy Question That I Need An Answer To Fast!"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by VolvoPunch on 2007-07-20
Sorry i hate to make a post like this but i need to get this system going quickly. Here this the thread i posted, no one seems to go into that section of the forum so i decried to post here.

[http://ubuntuforums.org/showthread.php?t=505156](http://ubuntuforums.org/showthread.php?t=505156)

---

### Post by dhruva023 on 2007-07-20
just use the synaptic.

it does the same thing.

---

### Post by ubanchaos on 2007-07-20
yea u need to use synaptic

---

### Post by kittyhawk63 on 2007-07-20
Synaptic uses apt-get to install programs.

---

### Post by VolvoPunch on 2007-07-20
This is a server, i can only connect to it using ssh (Putty to connect). Not all the packages i want are in the sources.list file but i do find the packages on this site [http://packages.ubuntu.com/](http://packages.ubuntu.com/). So is there a repositories list for that site? 

My original question. 
I am using Xubuntu and i want to know how i can tie apt-get into the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) site. Don't ever want to have to install software by visiting a site i just want to use apt-get because it keeps everything clean. How can i do this. :)

---

### Post by ARandomKid on 2007-07-20
So, you want the repositories (things to add into your sources.list) that are connected to those?

I can't help you there, but just to clarify for somebody who might...

---

### Post by VolvoPunch on 2007-07-20
> **ARandomKid said:**
> So, you want the repositories (things to add into your sources.list) that are connected to those?

I can't help you there, but just to clarify for somebody who might...

Exactly. Many of the software programs i need come up in the search on that site. So if i can tie apt-get into the  site by adding it to the sources.list file that would be great. Now i need someone to tell me how to do it. :)

---

### Post by spur on 2007-07-20
Thats a cononical site and the repositories listed in apt should have it. You may need to enable it. If you have a gui running go to System->Administration->Software sources put in your passwor when asked, then go to third party software (the second tab) and make sure the canonical entries have ticks in then close.
On the first page you should have the boxes ticked as well for official sources.

---

### Post by kvonb on 2007-07-20
By the looks of it, packages.ubuntu.com is simply a human readable list of all the packages that are available form apt-get.

Edit your /etc/apt/sources.list, it should have universe and multiverse commented out.

```
sudo vi /etc/apt/sources.list
```

Uncomment those, save and exit, then do an update:

```
sudo apt-get update
```

You should now find that all the packages listed on packages.ubuntu.com are available via apt-get

---

### Post by VolvoPunch on 2007-07-20
I have gone into my sources.list file and removed all the # in front of the addresses and run apt-get update. Yet i still cannot download zabbix-server-mysql using apt-get althrought  its on the site.

---

### Post by VolvoPunch on 2007-07-20
I found the package [http://packages.ubuntu.com/feisty/net/zabbix-server-mysql](http://packages.ubuntu.com/feisty/net/zabbix-server-mysql) but when i do sudo apt-get install zabbix-server-mysql i get the package not found. Whats going on?

---

### Post by grishenko2000 on 2007-07-20
zabbix-server-mysql is only available for edgy and above if your trying to install it on xubuntu 6.06 you wont be able to get it.

---

### Post by VolvoPunch on 2007-07-20
> **grishenko2000 said:**
> zabbix-server-mysql is only available for edgy and above if your trying to install it on xubuntu 6.06 you wont be able to get it.

No way of tricking it? Is there any other way i can install zabbix-server-mysql using apt-get?

---

### Post by grishenko2000 on 2007-07-20
there may be but I cant think of a way and Im sure if there was it wouldnt be recommened.
The only thing I can think of is try install it from source (though im not sure of all the dependancies it requires)
OR you may have to upgrade to edgy / feisty.

---

### Post by VolvoPunch on 2007-07-20
> **grishenko2000 said:**
> there may be but I cant think of a way and Im sure if there was it wouldnt be recommened.
The only thing I can think of is try install it from source (though im not sure of all the dependancies it requires)
OR you may have to upgrade to edgy / feisty.

Thats the problem question and one of the reasons why i have stayed away from Linux for such along time. DEPENDENCIES! So if anyone has the solution for this problem please by all means post up. :mad:

---

### Post by VolvoPunch on 2007-07-20
Ubuntu is just Debian so is there a Debian server i could connect to for the package.

---

### Post by VolvoPunch on 2007-07-20
Bump for a solution.

---

### Post by kittyhawk63 on 2007-07-20
> **VolvoPunch said:**
> Bump for a solution.

Yes, and it has been offered. [COLOR=Red]Upgrade[/COLOR]. That will resolve your issue immediately. By the way, I'm fairly certain about this, DEPENDENCIES, which seem to be a problem with you, are in every OS program application. They are just included. If you will notice when using the repositories, there are times when you select an application to install that it will include dependencies. Notice that also sometimes it will automatically mark other dependencies to uninstall. It does this because of suspected conflicts. 

In conclusion, I hope someone will be able to offer the "under-the-table solution that you want.

Have a gid day, mate.
kh

---

