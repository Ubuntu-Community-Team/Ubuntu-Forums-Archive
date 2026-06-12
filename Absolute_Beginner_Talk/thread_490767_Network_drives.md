---
title: "Network drives"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by swordfixx on 2007-07-02
Is there any way to mount ntfs network drives in ubuntu v7.04 so that they can be viewed in any application when browsing for folders (within the application itself - such as VLC , and realplayer)

10x

---

### Post by KCMOStealthRT on 2007-07-02
try out this guide on Ubuntu Guide [Link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read")

---

### Post by p_quarles on 2007-07-02
My solution to that problem isn't particularly sophisticated, but it's very simple. I just log into the disk via Nautilus first, then use whatever other needs to access the disk. This works in my case because Nautilus is capable of calling up the keychain password dialogue, whereas VLC, Gnome Commander and OOo aren't. Dunno if that's what you were asking, but I hope you get it working.

---

### Post by swordfixx on 2007-07-02
> **KCMOStealthRT said:**
> try out this guide on Ubuntu Guide [Link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read")

i tried this method a few times but it didnt work.

i am trying to mount using the pc name not IP and i am trying to mount the hidden shares on windows, i did this already through the connect to server option and i can browse them however i still cant view them in players.
i tried this command

sudo mkdir /media/PCNAME-C
sudo mount //PCNAME/C$ /media/PCNAME-C/ -o username=USERNAME,password=PASSWORD

the letters in capital being the ones i changed for my specific setup

---

### Post by swordfixx on 2007-07-02
> **p_quarles said:**
> My solution to that problem isn't particularly sophisticated, but it's very simple. I just log into the disk via Nautilus first, then use whatever other needs to access the disk. This works in my case because Nautilus is capable of calling up the keychain password dialogue, whereas VLC, Gnome Commander and OOo aren't. Dunno if that's what you were asking, but I hope you get it working.



I didnt understand what u ment by

>I just log into the disk via Nautilus first, then use whatever other needs to access the disk<

---

### Post by p_quarles on 2007-07-02
> **swordfixx said:**
> I didnt understand what u ment by

>I just log into the disk via Nautilus first, then use whatever other needs to access the disk<
Nautilus is the window manager for the GNOME desktop. If you're using KDE or Xfce, that won't apply. Use the equivalent window manager.

In any case, after you log-in to the network shared subdirectory, you'll be able to access all the files located there.

---

### Post by swordfixx on 2007-07-04
my problem is not that i am not able to access the files. my problem is that realplayer , helixplayer , vlc and other applications cannot view the network drives when i browse through the applications for specific folders.

---

### Post by DerridaIsDead on 2007-07-13
p_quarles,
I'm afraid  what you're saying here terminates my little quest. 

> **p_quarles said:**
> My solution to that problem isn't particularly sophisticated, but it's very simple. I just log into the disk via Nautilus first, then use whatever other needs to access the disk. This works in my case because Nautilus is capable of calling up the keychain password dialogue, whereas VLC, Gnome Commander and OOo aren't. Dunno if that's what you were asking, but I hope you get it working.

I was hoping there is a way to authenticate within Gnome Commander as I try to access a directory on a Windows Network (as is the case at my office) on which authentication is required.

When I try to access such a directory through Gnome commander, I receive an error message:
"List failed: operation not permitted." But when I authenticate first via Nautilus, I can access it afterwards in Gnome commander. Not user-friendly, I say, in comparison with Total commander.

Sure there's not a way within Gnome commander? :???:

(Very new at this stuff.)

---

