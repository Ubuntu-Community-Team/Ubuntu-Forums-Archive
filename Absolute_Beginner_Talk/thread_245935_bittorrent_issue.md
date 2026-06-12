---
title: "bittorrent issue"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-28
Hey, im getting fed up with azuerus and when i try to boot up bittorrent it says that it cant find a twisted.python module. When i can get it started up i get a 111 error or something, i cant get it to open up right now.

---

### Post by Lord Landis on 2006-08-28
Installing Azureus can be a bit of a pain through synaptec.  If you use Automatix to install it, however, it seems to work quite well.

As for your issue with Bittorrent itself, have you tried checking for updates and/or searching for the module you need in Synaptec?  

I wish I could be more helpful, but I've only just started using Ubuntu myself, and as of my install, the Bittorrent client was installed and working.

---

### Post by ezek on 2006-08-28
i installed azureus manually, it just doesnt want to download my torrents. Mabye i should uninstall bit torrent (im not 100% sure where it is) and re install it? I downloaded bit torrent and then converted it into a deb folder and tryed this command to install it sudo dpkg -i <filename> it loads and then just gives me the standard command line to put in other commands. It ends in ....... and never installs.

---

### Post by Lord Landis on 2006-08-28
Is Azureus giving you a specific error, or is it just not working with the torrent files at all?  There's a chance it may also be wanting you to update a component, but I think you need to be running as root to make said changes (it tries to install updates to a directory that you, as a normal user, cannot write to).

---

