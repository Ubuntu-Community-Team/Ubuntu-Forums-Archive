---
title: "Trying to share files"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by sarsippius on 2007-05-16
I'm having a lot of trouble sharing files between my computer and my Wife's Windows XP computer.  What would be the easiest way to fix this?

Also our printer is attached to her computer, and shared.  But I cannot see the printer.

Any thoughts?

---

### Post by MoxJet on 2007-05-16
There are various ways to solve this, the recommended one is probably samba, which allows your Ubuntu computer use the windows network. Samba also allows you to share printers. Read on:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

The pure way would be to install Linux on the other computer and use SSH. It's really fascinating! Read more:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

If you only need to share data from your Linux computer to the Windows one, you could set up a server... But that's a bit out of this post.

Good luck!

---

### Post by esoterica on 2007-05-16
I've used Samba for years and it works perfectly for doing this. Setting it up and getting it to work flawlessly is possible but requires a lot of reading through all the documentation to do so. 

Your going to want 

Samba:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?action=fullsearch&context=180&value=Samba&titlesearch=Titles](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?action=fullsearch&context=180&value=Samba&titlesearch=Titles)

and probably also this to let you access the NTFS drive on the XP computer

NTFS3G:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

If you have additional problems still with printing you may want to search the Ubuntu community documentation for "Cups" as well.

A simple but effective fool proof work around is to install an FTP server on your Linux computer and just use FTP for file transfers between the 2. It won't help with your printer problem, but does make for a quick and easy way to share files between different computers that doesn't require a lot of complicated setting up and configuring. Just make sure you properly protect it so you don't have Anonymous users across the internet connecting into your FTP server and filling your hard drive with garbage.

---

