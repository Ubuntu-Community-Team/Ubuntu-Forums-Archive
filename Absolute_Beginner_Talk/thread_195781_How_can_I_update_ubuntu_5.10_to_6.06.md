---
title: "How can I update ubuntu 5.10 to 6.06?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by jeanvial on 2006-06-13
Hello.

How can I update ubuntu 5.10 to 6.06?

---

### Post by rbalfour on 2006-06-13
[QUOTE=jeanvial]Hello.

How can I update ubuntu 5.10 to 6.06?[/QUOTE]

This AIN'T for the faint-hearted...

[http://www.cyberciti.biz/tips/howto-upgrade-from-ubuntu-linux-breezy-to-dapper.html](http://www.cyberciti.biz/tips/howto-upgrade-from-ubuntu-linux-breezy-to-dapper.html)

---

### Post by bruce89 on 2006-06-13
[QUOTE=jeanvial]How can I update ubuntu 5.10 to 6.06?[/QUOTE]
Just use update manager - there should be a button to upgrade.  Make a backup of anything you want to keep on the Breezy install if it goes wrong.  It is probably best just to reinstall.

---

### Post by barisurum on 2006-06-13
The best way is:
  get the ubuntu dapper 6.06 "alternate install" cd image from ubuntu.com
  burn the iso on a disk
  edit the etc/apt/sources.list
  change every word "breezy" to "dapper" in the file
  enter synaptic
  select include CD (I dont know where exactly it is) and include the CD you downloaded
  refresh metadata
  select every update possible and click on apply

  and wait :)

---

### Post by JanVH on 2006-06-13
There are several ways to do this. This is one of them that worked for me:

in /etc/apt/sources.list change every occurence of 'breezy' to 'dapper'. Then:

```

apt-get update
apt-get dist-upgrade

```

And wait...

---

### Post by jeanvial on 2006-06-13
OK

now I'm updating.

Thanks.

---

### Post by impakt on 2006-06-13
I just clicked up my update manager. It gave me the general update and also had a link " update to 6.06".I clicked on that and everything worked great for me

---

### Post by djb21212 on 2006-06-13
One way that's always worked for me is this:

(Bear in mind that as of now this is my third time installing Ubuntu)

1: Boot into the recovery console when GRUB comes up

2: nano -w /etc/apt/sources.list (Nano is pretty much the best text editor for this little experiment in my case)

3: Edit every instance of "breezy" to "dapper", uncommenting certian repositories as you go

3a: You might also want to add the section "multiverse" to the universe repositories so you be able to upgrade as cleanly as possible and comment out the CD-ROM source as well

4: CTRL+X to save it. Hit Enter to save it under the original name.

5: Back at the shell prompt, run "apt-get update" and wait a few seconds.

6: When it's done, run "aptitude"

7: Hit F10 and select "Mark Upgradable Packages"

8: Hit "g" twice and, if you're running broadband, prepare to wait about two hours for it to finish.

9: After it's finished, hit F10+q to quit. Type reboot to reboot your PC.

10: At the GRUB menu, a new kernel version will be listed. Select the new kernel from the list and wait.

11: Welcome to Ubuntu 6.06 LTS! Enjoy!

---

### Post by uzi09 on 2006-06-13
yet again it's the same method:
[http://easylinux.info/wiki/Ubuntu#How_to_upgrade_from_Breezy_Badger_to_Dapper_Drake_.28experimental.29](http://easylinux.info/wiki/Ubuntu#How_to_upgrade_from_Breezy_Badger_to_Dapper_Drake_.28experimental.29)

but the only reason i post is because you should really use this wiki. it's ***very*** helpful in a lot of stuff. if you scroll up it'll provide you with the link to the dapper one as well....(or if you can't find it, it's [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper))

---

### Post by ububaba on 2006-06-13
[QUOTE=JanVH]There are several ways to do this. This is one of them that worked for me:

in /etc/apt/sources.list change every occurence of 'breezy' to 'dapper'. Then:

```

apt-get update
apt-get dist-upgrade

```

And wait...[/QUOTE]

I tried to replace "breezy" with "dapper". I could not save the changed file.:?: 
Suggestions?

Thanks

---

### Post by uzi09 on 2006-06-13
did you open using sudo?? you should have admin permissions.

try this, copy all of that, then close the file without saving. then open it this way (from terminal):
```
sudo gedit /etc/apt/sources.list
```

now paste everything in there again and save.

---

### Post by ububaba on 2006-06-13
[QUOTE=uzi09]yet again it's the same method:
[http://easylinux.info/wiki/Ubuntu#How_to_upgrade_from_Breezy_Badger_to_Dapper_Drake_.28experimental.29](http://easylinux.info/wiki/Ubuntu#How_to_upgrade_from_Breezy_Badger_to_Dapper_Drake_.28experimental.29)

but the only reason i post is because you should really use this wiki. it's ***very*** helpful in a lot of stuff. if you scroll up it'll provide you with the link to the dapper one as well....(or if you can't find it, it's [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper))[/QUOTE]

I used this link to "wiki". Everything went fine.:D 

Thanks

---

### Post by az on 2006-06-13
[QUOTE=jeanvial]Hello.

How can I update ubuntu 5.10 to 6.06?[/QUOTE]
Use the update manager.

If you don't have broadband, get the new Dapper alternate install cd.  Boot into your breezy install and then pop the cd in the drive.  Follow instructions.

If you have broadband, just click on the upgrade box, as mentioned.

The update-manager takes care of any problems that could result in ubuntu-desktop getting removed.

---

### Post by webster on 2006-07-03
I have broadband.   A T-1 network in fact.  I am on a network with windows machines.  I have Ubuntu 5.10.  I want to upgrade to 6.06.  When I try I get the following,  it begins to upgrade but stops saying it can't load a list of files and that it must be a network problem. 

So what what to do?

---

### Post by Apple 101 on 2006-07-04
You could download the CD/DVD.  You have a T-1 connection (way faster then my connection), unless you are limited by an ISP download limit.  Try again though, before resorting to downloading an ISO.

---

