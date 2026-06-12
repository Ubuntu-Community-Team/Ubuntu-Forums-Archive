---
title: "Upgrading to edgy with the alternate CD"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by thelinux_guy on 2006-10-29
Im currently downloading the Ubuntu 6.10 Alternate CD to update my system (I heard it could be done)So how? I heard that you configure the "update Channels" tool to include the CD-ROM and others said you run a command in terminal,But which one and if none of the ones that I listed,then what?

P.S. :I heard that upgrading to edgy was like hell (X would not start,Could not see the new"Usplash,ect)Is this true,I just want to know,my system is working properly now and do not want to screw things up....

---

### Post by Dual Cortex on 2006-10-29
There have been so many questions on this, the search function should help you a lot.
ANyway, instructions are here hope you understand them because they are not THAT newbie friendly:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

EDIT:

Just in case you don't understand (Assuming you are using Gnome Desktop Environment):

1) Issue the following command in the terminal
```
sudo apt-get install ubuntu-desktop ubuntu-minimal ubuntu-standard 
```

2) Another command:
```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

3)Another command
```
sudo apt-cdrom add
```

4)And more:
```
 sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade 
```

5) And lastly, "Just to be totally sure that everything is installed properly, run these commands":
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a 
```

6) Reboot

---

### Post by jd65pl on 2006-10-29
Edgy is NOT an upgrade from dapper it should be taken in to consideration as a different system used for running cutting edge software which may contain bugs!

---

### Post by thelinux_guy on 2006-10-29
So,if I do decide to upgrade,I will lose everything,like a reformat?

---

### Post by jd65pl on 2006-10-29
No you shouldn't loose everything however you so keep in mind that you will be using an environment which may be prone to bugs. Be prepare to resolve problems on your system. There is a sticky post regarding this in the begginer forums.

---

### Post by Dual Cortex on 2006-10-29
I also suggest you not to 'upgrade.' It was hell but I got it working the after many despairing hours.

---

### Post by thelinux_guy on 2006-10-29
So what you are saying is if there are bugs in this new release,there is no way to fix them because they are not known yet?

P.S. Im using the regular Ubuntu OS with Gnome...

---

### Post by jd65pl on 2006-10-29
You should be willing to fix your own issues with the system and find out way of fixing problems read the[ sticky thread ]("http://ubuntuforums.org/showthread.php?t=286209")on the subject in these forums

---

