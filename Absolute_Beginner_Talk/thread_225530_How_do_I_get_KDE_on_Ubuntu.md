---
title: "How do I get KDE on Ubuntu?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-07-29
Hi all, I've been experimenting with various linux distros on and off for the past 2 years but I've never really gotten anywhere. I've decided to give Ubuntu a go, and now I'm wondering if KDE comes with Ubuntu or will I need to download it?
Thanks!

---

### Post by 5-HT on 2006-07-29
If you only want KDE, you could install Kubuntu ( [http://www.kubuntu.org/](http://www.kubuntu.org/) ) which is Ubuntu with KDE instead of GNOME.

Alternatively, if you happen to have already downloaded the alternate Ubuntu install CD you could do a barebones server install and then install the *kubuntu-desktop* metapackage to bring your system up to that of a default kubuntu installalation.

Furthermore, instead of installing the full-blown kubuntu-desktop package, you could opt for a more minimal KDE experience by installing either the *kde* or *kde-core* packages.

To get a feel for the differences between kubuntu-desktop, kde, and kde-core, you can look at the package discriptions and dependencies by browsing [http://packages.ubuntu.com](http://packages.ubuntu.com).

Hope that helps.

---

### Post by wsun on 2006-07-29
I'm sorry, how do I do the server install? I am using Ubuntu right now already. Thanks

---

### Post by SpawnSC on 2006-07-29
I would just download the kubuntu iso and burn it and then try the live cd :) what I plan on doing :P

---

### Post by aysiu on 2006-07-29
> **wsun said:**
> I'm sorry, how do I do the server install? I am using Ubuntu right now already. Thanks
If you're already using Ubuntu now, try this:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by 5-HT on 2006-07-29
> **wsun said:**
> I'm sorry, how do I do the server install? I am using Ubuntu right now already. Thanks

Sorry, I assumed you had yet to install Ubuntu.
You have a few options available.

If you are not too familiar with Linux in general, and Ubuntu specifically, I would suggest option i) If you would like to keep your Ubuntu install (and all your data) and install KDE alongside it.
If you don't mind loosing your current Ubuntu install (and any data), downloading the Kubuntu CD and installing via option ii) would be the easiest.
[B]
 i) Add KDE to your existing Ubuntu installation.

*****EDIT: If you would like to install KDE using this method, please refer to Aysiu's excellent guide posted above. It is a much more detailed walkthrough and also suggests using Aptitude which will make uninstalling KDE much easier down the road if you so choose (though you may want to override the default 'treat recommends as dependencies').*
[/B]   
This can take the form of installing either kubuntu-desktop, kde, kde-core, or you could manually install the bits and pieces of kde that you would like. I'd suggest opting for one of the first three, as that last one will require some knowledge of which packages you need to  have a  functional  KDE  environment.

If you are not familiar with apt or aptitude for package management, I'd suggest using Synaptic (System -> Administration -> Synaptic Package Manager) to search for, read about, and finally install one of kubuntu-desktop, kde, or kde-core.

Kubuntu-desktop would be the *recommended* way of getting KDE, the other two KDE packages will yield more minimal kde installations



** ii) Install Kubuntu using the kubuntu install CD**
[SIZE=3][B]
If you install Kubuntu to existing partitions using this method  ALL of the data on those partitions will be deleted[/B].

[/SIZE] This method would basically wipe out your Ubuntu install (if you install onto the Ubuntu partitions) and give you Kubuntu.
Just download the install CD (link provided in my first post) and install from that.



[B] iii) Install a bare-bones server using the alternate Ubuntu CD and download and install kubuntu-desktop

[/B] This method will only work using the alternate Ubuntu install CD, not the live/install CD. I would only recommend this method if you already have the alternate install CD and don't mind installing kubuntu-desktop  from the net (it's a big package).
**[SIZE=3]   If you install to existing partitions using this method  ALL of the data on those partitions will be deleted.[/SIZE]**

To do a server install, it should be an option from the menu. Alternatively you could get to a prompt by pressing 'Esc' and enter 'server'.
Going this route, I'd suggest installing kubuntu-desktop to get the fully featured Kubuntu experience (this will be the same as installing from the Kubuntu CD).
To install kubuntu-desktop you'll need Internet access. The command to install the package using apt is:
```
sudo apt-get install kubuntu-desktop
``` 

Instead of apt, you could use aptitude to install kubuntu-desktop. There are plenty of threads around comparing apt ang aptitude.
By default, aptitude will install all packages recommended by kubuntu-desktop. While these packages may not be necessary, they can be handy at a cost of potentially greatly increasing download size and needed disk space.

Using aptitude without installing recommended packages:
```
sudo aptitude -R install kubuntu-desktop 
``` 
Using aptitude with installing recommended packages:
```
sudo aptitude install kubuntu-desktop
``` 


Hope that helps, post again if this wasn't clear or you have other questions.

---

### Post by wsun on 2006-07-29
Thanks for the help, I am using apt get to install kubuntu-desktop right now,I'll tell you guys how it goes later. :)

---

