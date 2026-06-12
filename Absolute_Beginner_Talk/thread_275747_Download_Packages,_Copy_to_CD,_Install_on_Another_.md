---
title: "Download Packages, Copy to CD, Install on Another Ubuntu"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-11
Hi,

Am working to install Xubuntu on an old Mac that doesn't have an internet connection; how do I install packages (educational programs from my younger brother) from a CD ?  I want to download them on this system (Ubuntu with internet), copy to CD, and then move them to the system without the internet.

Thanks,
DAmon

---

### Post by catlett on 2006-10-11
You can go here and get the deb files for the applications. [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/) Just download to your system, copy to cd and then double click the file when you open the cd on your brother's system. gdebi package installer will install the deb file for you.
The MAIN problem is dependencies. When you install an application with synaptic package manager and you have an internet connectin, synaptic will automatically download and install any dependencies. Your brother's system will not be able to do that. A dependency will stop the installation. YTou will then have to record the dependencies and download them as well.
Your other option is to get the repositories on cd. There are 2 ways. 1 is free and the other costs $35 
[http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1113&zenid=7afmkrsvtgfugshugbocoigj15](http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=1113&zenid=7afmkrsvtgfugshugbocoigj15)
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

---

### Post by guysmiley25 on 2006-10-11
You might be able to do so, download the debs burn to CD and then add the CD to your sources.list. Not that I have tryed this but if it does work you would also have to consider the dependices of the debs. unless you do the whole resporite for ubuntu but I think you would need a few cd's to do that.

Sorry that I dont have a real solution. But while I am here (Sorry to intrude) fi what you want to be done can be done, what about if you have 100+ computers in a network and they all need to be upgraded? that would use up alot of bandwidth? is there a better way?

---

### Post by thornomad on 2006-10-11
Hi thanks!  Downloading the .deb packages seems reasonable ... I will have to play with it I guess.  I really don't need five DVDs worth of packages ... just educational games and material for my brother.  That's it.

On the Ubuntu site it does list dependencies ... so ... maybe I can be sure to pick those up at the same time.

Thanks!

---

### Post by Beernut on 2006-11-22
Take a look at aptonCD.  It will create a backup of all the packages you have installed.

[URL="http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html"]
Here is a quick little HowTo[/URL]

---

