---
title: "can't delete vmware file"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by dcalvani on 2007-06-20
hi, I'm trying to delete the following file (located at   /etc/rc0.d)
 /etc/init.d/vmware-player 

This is a broken link leftover from a (failed) attempt to install Vmware server. It supposedly prevents me from re-installing Vmware server (every time I try I can't complete the installation process because I get a message that says I should "purge" any trace of Vmware first). According to Synaptic, there's no trace of Vmware on my machine. 

If I type the following through Terminal:

~$ sudo apt-get remove  /etc/init.d/vmware-player

I get the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 

I also tried 

~$ sudo rm -R /etc/vmware

and got the following:

rm: cannot remove `/etc/vmware': No such file or directory
daniele@Adab:~$ sudo sudo rm -R /etc/init.d/vmware-player
rm: cannot remove `/etc/init.d/vmware-player': No such file or directory


Any idea? Thanks.

---

### Post by atria on 2007-06-20
If you want to remove configuration files too, use aptitude purge or apt-get erase.

It seems that your repositories aren't updated correctly since the package does exist.

Make sure that the universe repository is added and do a 
```
sudo aptitude update
```

After that try uninstalling again.

---

### Post by wormser on 2007-06-20
> sudo apt-get remove  /etc/init.d/vmware-player

You are not suppose to use the path when removing via apt-get.  Try this.

```
sudo apt-get remove vmware-player
```

---

