---
title: "Wireless internet"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by bngn on 2007-03-04
First off, I am a complete newb to linux.
I am trying to connect wirelessly to the internet.  I have a WMP54G wireless card, and would like to connect.  I read that the card is compatible, but am having trouble connecting.  When I look under the network settings it gives me a wan0 and a wan1 connection.  I have tried to connect with both of those, but cannot.  I have entered correct SSID and WEP information, but still cannot connect.  Can someone walk me through the process from the beginning, keeping in mind I am a newb to the process.  Thanks.

---

### Post by Kobalt on 2007-03-04
When you click on the network icon in the notification area (top right) of your screen, is the signal power jauge active ?
I guess it is, Lynksys cards are very linux friendly so it should be working. My guess is it's just a matter of settings : you should install a package named network-manager. This will manage your wifi very easily and very well. (Once you've installed it with Synaptic, reboot so that it's launched and added to your panel)

---

### Post by bngn on 2007-03-04
Thanks but where do i get network-manager?

---

### Post by RomeReactor on 2007-03-04
Hi. You can find Network-Manager in Synaptic; i recommend you also install it's graphical interface (Network-Manager-Gnome). Or, to do it from the command line:

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by bngn on 2007-03-05
ok I have gone to terminal and at the matthew@matthew-desktop:~$ prompt i typed in the command,after that it said                reading package lists...done     building dependency tree     reading state information...done    E: couldn't find package

---

### Post by bngn on 2007-03-05
any help?

---

### Post by RomeReactor on 2007-03-05
Do you have wired internet on your computer? Otherwise you won't be able to download Network-Manager for installation. If you **do** have wired internet in your Ubuntu system, then perhaps you must enable Universe and Multiverse repositories, in which case you open Synaptic (System-->Administration-->Snaptic Package Manager), click on Settings-->Repositories and check all the boxes there; next press the Reload button, and search for the program there, or try it again from the terminal.

If you **don't** have internet on your Ubuntu, check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=375546").

---

