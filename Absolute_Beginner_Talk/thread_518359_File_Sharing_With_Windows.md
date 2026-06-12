---
title: "File Sharing With Windows"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by boomcat on 2007-08-05
I just started using Ubuntu 7.04 on an old T20 laptop at home. I have a Win 2K Pro network using static IPs and a Linksys WRT54G router. Some of the Windows PCs are wired and some are wireless with WEP. There is an HP 2510 Wireless printer, too. The T20 is wired to the router. 
As soon as Ubuntu booted for the first time it found the network and got on the Internet - I had to enter the static IPs during installation, of course, but it was simple.
Then I installed my wireless printer - Ubuntu found THAT, too, and it was amazingly easy.
The problem is that Ubuntu can't retrieve any files from any of the Windows computers. One computer, called dave, has text documents and another, called timmy, has MP3s.
Ubuntu can see the other computers in Places/Network. But the Windows computers can't see the Ubuntu computer in "Computers Near Me".
I read the instructions on using Samba and my eyes rolled back into my head! That looks too much like editing the Windows Registry! There must be an easier way to share text and music files over a mixed network.

---

### Post by jimrz on 2007-08-05
think that at a minimum you will need to edit /etc/samba/smb.conf and change the name of your workgroup to be exactly the same as the name of your windows workgroup / domain. then install something like linneighborhood (a gui SMB browser, kinda like "MyNetworkPlaces" in win) and see if that provides all that you need. you may, though, need to learn how to and mount your network shares in order to play media across the network. if so, check out [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") HOWTO, but be aware it will require some work in the terminal. the good news is that you can mostly (you need to edit some to match your stuff)  cut and paste the instructions.

---

