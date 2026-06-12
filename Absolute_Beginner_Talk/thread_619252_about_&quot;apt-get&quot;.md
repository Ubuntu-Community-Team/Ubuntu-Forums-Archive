---
title: "about &quot;apt-get&quot;"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by determinedblkman1 on 2007-11-21
do you have to be online to use the apt-get command? and if so where can i get the "ubutu desktop" for  ubutu server?

---

### Post by Inxsible on 2007-11-21
> **determinedblkman1 said:**
> do you have to be online to use the apt-get command? and if so where can i get the "ubutu desktop" for  ubutu server?yes you have to be online.

If however, you cannot be online on the same machine, you can burn a CD with all the repositories and then use that.

[AptOnCD]("http://aptoncd.sourceforge.net/")

---

### Post by determinedblkman1 on 2007-11-21
so with these repositories i'll beable to install the ubuntu desktop, or do i still have to get the package[s]

---

### Post by aysiu on 2007-11-21
If you do not want to install *ubuntu-desktop* directly from the internet, download and burn a Ubuntu Alternate CD (as opposed to the Desktop CD or Server CD). Then put the Alternate CD in your CD-ROM drive and type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by determinedblkman1 on 2007-11-21
pardon me for asking so many questions, but where do i put the packages (in what file) once i downloaded them so that i can use the "apt-get" command? and what is the ubuntu alternate cd for?

---

### Post by Inxsible on 2007-11-21
> **determinedblkman1 said:**
> pardon me for asking so many questions, but where do i put the packages (in what file) once i downloaded them so that i can use the "apt-get" command? and what is the ubuntu alternate cd for?you put all those files on CD. You can get the alternate CD [here]("http://www.ubuntu.com/getubuntu/download"). Don't forget to click the checkbox which asks you if you want an alternate CD

Actually the alternate CD is an install CD except that it is text based. It has ubuntu-desktop package on it. So get the alternate CD, burn it, then use the commands aysiu gave to install ubuntu-desktop on your machine.

---

### Post by determinedblkman1 on 2007-11-21
i appreciate all the help, however what i'm trying to do is put a gui on "ubuntu server" (which is text based)this website told me to use the "apt-get command  to install it.  ---  and thats my mission([http://www.dharwadkar.com/technology/linux/ubuntu03/view](http://www.dharwadkar.com/technology/linux/ubuntu03/view))

---

### Post by aysiu on 2007-11-21
Oh, you don't want *ubuntu-desktop*. You just want a GUI for your server?

Well, that's a lot easier (and since it is a server, I'm assuming you do have an internet connection but just didn't want to wait for 700 MB of packages to download):
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Inxsible on 2007-11-21
> **determinedblkman1 said:**
> i appreciate all the help, however what i'm trying to do is put a gui on "ubuntu server" (which is text based)this website told me to use the "apt-get command  to install it.  ---  and thats my mission([http://www.dharwadkar.com/technology/linux/ubuntu03/view](http://www.dharwadkar.com/technology/linux/ubuntu03/view))Whatever aysiu said, WILL put a GUI on your server.

---

### Post by smartbei on 2007-11-21
That is exactly what the commands aysiu gave you would do. It uses the alternate CD since it already has those packages on it.

EDIT: Sorry, others beat me to it.

---

### Post by Inxsible on 2007-11-21
> **aysiu said:**
> Oh, you don't want *ubuntu-desktop*. You just want a GUI for your server?

Well, that's a lot easier (and since it is a server, I'm assuming you do have an internet connection but just didn't want to wait for 700 MB of packages to download):
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)In his first post he asked whether he has to be online to install it, So I am not sure if he has internet connection on his machine, aysiu

---

### Post by determinedblkman1 on 2007-11-21
i dont have an internet connection, but i want to set up my computer as a server to network my laptop (also install an os on a laptop that doesnt have a cd drive - which i'll probebly need help on that too -- so stay tuned PLEASE) so will the instuctions youn gave me work w/o me being online? also i have the ubuntu server on cd - i'm just trying to add a gui to it

---

### Post by aysiu on 2007-11-21
> **Inxsible said:**
> In his first post he asked whether he has to be online to install it, So I am not sure if he has internet connection on his machine, aysiu
Well that's what I thought too, but if it really is a GUI for a server, as opposed to a desktop, then *ubuntu-desktop* is a little excessive.

---

### Post by aysiu on 2007-11-21
> **determinedblkman1 said:**
> i dont have an internet connection, but i want to set up my computer as a server to network my laptop (also install an os on a laptop that doesnt have a cd drive - which i'll probebly need help on that too -- so stay tuned PLEASE) so will the instuctions youn gave me work w/o me being online?
The first instructions will work, but you need the Alternate CD.

---

