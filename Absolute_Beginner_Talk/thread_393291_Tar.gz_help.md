---
title: "Tar.gz help"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-25
So I just downloaded network manager which was in a tar.gz file.  I extracted into a folder.  What do I do now? How do I actually install it?

---

### Post by r4ik on 2007-03-25
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

good luck !

---

### Post by shof2k on 2007-03-25
> **zeroo said:**
> So I just downloaded network manager which was in a tar.gz file.  I extracted into a folder.  What do I do now? How do I actually install it?

You will need to open a terminal using Applications-Terminal and open the package using "sudo tar -xvzf  *package name*".  Then you need to go into the resulting folder using "cd *folder name*".  Then you need to type the commands "make" and "make install".

This is a bit heavy for a newbie, so a much easier way is to open the terminal and type ```
sudo apt-get install automatix
```.  This installs the automatix tool.  You can then select it from the Applications menu and use that to install network manager.

Hope that helps.

---

### Post by aysiu on 2007-03-25
**shof2k**
Isn't installing Automatix to install Network Manager a bit like (calling then) hiring a personal assistant to make one phone call for you?

If you're going to bother to *sudo apt-get install automatix*, which won't work unless you have the proper repositories enabled, anyway, you might as well do ```
sudo apt-get update
sudo apt-get install network-manager
```

**zeroo**
Do you have Ubuntu connected to the internet right now (via a wired connection), but you're installing *network-manager* to make wireless configuration a bit easier? Or are you unable to connect at all?

The methods outlined by me (earlier in this very post) and by r4ik (earlier in this thread) require you to be connected to the internet.

---

### Post by lamalex on 2007-03-25
fyi before you install automatix: automatix can b0rk your system hard. network-manager is installable trough the repos, you should be able to apt-get install network-manager-gnome. you will probably need to enable the universe repository.

---

### Post by aysiu on 2007-03-25
> **Iamalex said:**
> fyi before you install automatix: automatix can b0rk your system hard. network-manager is installable trough the repos, you should be able to apt-get install network-manager-gnome. you will probably need to enable the universe repository.
Actually, [network-manager-gnome is in the Main repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=network-manager-gnome&searchon=names&subword=1&version=all&release=all). No need to enable extra ones.

---

### Post by zeroo on 2007-03-25
I have my computer wired. I want my wirless to work, but someone told me that if I have a static ip I should go with network-manager.  Is this true, because the other one is not working for me.

---

### Post by aysiu on 2007-03-25
> **zeroo said:**
> I have my computer wired. I want my wirless to work, but someone told me that if I have a static ip I should go with network-manager.  Is this true, because the other one is not working for me.
I don't know if the second part is true, but if you have a wired connection, pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) will install *network-manager*: ```
sudo apt-get update && sudo apt-get install network-manager
``` For more info on software installation in general:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by zeroo on 2007-03-25
After I install it, how do I open it?

---

### Post by aysiu on 2007-03-25
> **zeroo said:**
> After I install it, how do I open it?
Go to System > Preferences > Sessions and add a new command: ```
nm-applet --sm-disable &
```

---

### Post by zeroo on 2007-03-25
> **aysiu said:**
> Go to System > Preferences > Sessions and add a new command: ```
nm-applet --sm-disable &
```

I dont have anything under system that says preferences.

---

### Post by aysiu on 2007-03-25
> **zeroo said:**
> I dont have anything under system that says preferences.
Are you not using Ubuntu?

Kubuntu or Xubuntu, perhaps?

Well, just paste that into the terminal, then: ```
nm-applet --sm-disable &
```

---

### Post by Frak on 2007-03-25
Umm... I'm going to guess your using Kubuntu?

---

### Post by zeroo on 2007-03-25
Its kubuntu but this is what I get when I try.

zero@snuggles:~$ nm-applet --sm-disable &
[1] 11695
zero@snuggles:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: not found

---

### Post by Frak on 2007-03-25
As I recall, both of those "Error: BadDevice" messages are just saying you don't have a Toshiba Tablet PC, so just ignore those.

---

### Post by zeroo on 2007-03-25
So what's supposed to happen with this command?

---

### Post by aysiu on 2007-03-25
> **zeroo said:**
> So what's supposed to happen with this command?
It's supposed to launch the Network Manager, and it should appear as an icon in your notification area.

---

### Post by Frak on 2007-03-25
Did you originally try going to K->Internet->Wireless Assistant Wireless LAN Manager ?

---

