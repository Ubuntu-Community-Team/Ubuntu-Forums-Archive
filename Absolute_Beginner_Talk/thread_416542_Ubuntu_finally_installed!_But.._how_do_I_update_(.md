---
title: "Ubuntu finally installed! But.. how do I update :( ?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-21
Hi there ^_^ The las two days I've had problems with installing Ubuntu. I'm a complete noob with Linux HOWEVER! I was dedicated on not stopping until I get to try out Ubuntu and now I Have. I've had Ubuntu only about 30 minutes and I LOVE IT. It simpleness of it and everything I can't wait to learn more about it. Though I'm using a outdated version of Ubuntu. I'm using version 6.06. The version you get in mail when you order free ones. I want to upgrade to 7.04 but I Can't do that until I get version 6.10 ( correct me if I'm wrong ). How do I upgrade from 6.06 to 6.10? It would be obvious to go download it > burn it > reinstall, but honestly I really don't want to do that unless need be. Can you guys please inform me where I go to upgrade from 6.06 to 6.10 so I can then update to 7.04! And be up to date with everyone else. 

Thank you in advance for all your answers :]

---

### Post by mikewhatever on 2007-04-21
[https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29)
and thea
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Good luck with that.

---

### Post by Zaosyn on 2007-04-21
Your a god! Installing now!!!!

---

### Post by spin2cool on 2007-04-21
You have two options:
upgrade to edgy, then upgrade to feisty
OR
download and burn a feisty disk and install from scratch.  

If you're on a new install already, and haven't tweaked your settings too much, I'd *really* recommend installing from scratch.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
It's typically a lot easier than upgrading, which sometimes fails for odd reasons and leaves your system in something of a mess.

If you're really set on the upgrade route, I would still burn a feisty disc first.  That way, if something goes wrong during the upgrade, you can always forget the upgrade and install the newest version from scratch.

To upgrade, go into a terminal and run this:
gksu &#8220;update-manager -c &#8221;

Once you've upgraded to edgy, you'll do the same thing to get up to feisty. More detailed instructions here:
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html)

---

### Post by DougieFresh4U on 2007-04-21
> **Zaosyn said:**
> Hi there ^_^ The las two days I've had problems with installing Ubuntu. I'm a complete noob with Linux HOWEVER! I was dedicated on not stopping until I get to try out Ubuntu and now I Have. I've had Ubuntu only about 30 minutes and I LOVE IT. It simpleness of it and everything I can't wait to learn more about it. Though I'm using a outdated version of Ubuntu. I'm using version 6.06. The version you get in mail when you order free ones. I want to upgrade to 7.04 but I Can't do that until I get version 6.10 ( correct me if I'm wrong ). How do I upgrade from 6.06 to 6.10? It would be obvious to go download it > burn it > reinstall, but honestly I really don't want to do that unless need be. Can you guys please inform me where I go to upgrade from 6.06 to 6.10 so I can then update to 7.04! And be up to date with everyone else. 

Thank you in advance for all your answers :]

To help you and to be sure you get ALL,make sure you have all your repositories enabled. Go to System>Administration>Synaptic Package Manager, then under Settings>Repositories check all the repo's for universe etc. then close the little window and click Reload. This way as you move on to Edgy and then maybe Feisty you will have all the packages. Good luck and any problems please post here.

---

### Post by mikewhatever on 2007-04-21
Take it easy buddy. No need to finish it all in one day. :)

---

### Post by Ekin on 2007-04-21
> **DougieFresh4U said:**
> To help you and to be sure you get ALL,make sure you have all your repositories enabled. Go to System>Administration>Synaptic Package Manager, then under Settings>Repositories check all the repo's for universe etc. then close the little window and click Reload. This way as you move on to Edgy and then maybe Feisty you will have all the packages. Good luck and any problems please post here.

But Beware. There should be a little problem with selecting all repos if you experimented with them like me. It means if you added some repos before (3rd party repos) they maybe dont exist anymore so when system starts to update it fails to gel all packages. You just unklick those (way said before) and it will work...

---

### Post by Zaosyn on 2007-04-21
Thank you all for your great replys. I will use them ^_^. 6.10 installed, and running perfectly. Now time to get 7.04 and get some sleep o_o

---

