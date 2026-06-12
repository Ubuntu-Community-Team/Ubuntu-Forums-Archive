---
title: "Smb problems in ubuntu 8 beta"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Troca on 2008-04-14
Hi there iam a compete newb to ubuntu just started using it used ubuntu 7 for 1 day that upgraded to the beta verison 8. 

My problem now is that in version 7 i could select 1 folder right click it select share. it would then give me 2 options linux share or Smb i chose witch one i wanted and clicked apply and all worked.

in ubuntu version 8 i dont have the same options eaven tho i installed both system when asked and when i try to share something i get this error (see screen shoot)

[http://www.mediahump.com/gallery/2335/](http://www.mediahump.com/gallery/2335/)

---

### Post by AndrewTheArt on 2008-04-14
Try this - 

(1) Open a terminal and type

```
sudo gedit /etc/samba/smb.conf
```
(When prompted, type in your password.)

(2) Find the section entitled "Global" and anywhere under that word, add the line

```
usershare owner only = False
```

(3) Save, quit. In a terminal,

```
sudo /etc/init.d/samba restart
```

(4) Try sharing the folder again

---

### Post by Troca on 2008-04-15
Works like a charm thank you very very much :)

---

### Post by Troca on 2008-04-15
I spoke to early its not working 100%. Cuz every time i reboot i have to re share every folder again. Witch is anoying sens its alot of folders and its all for my XBMC (Xbox Media Center) 
also in Ubuntu 7 when i set everything up it was SO fast when i streamed a movie it was MUCH faster then in windows. But in Ubuntu 8 that iam using now its MUCH MUCH slower


If anyone could help me figure out a way where i dont have to re share every time i reboot

---

### Post by JediYodaNT on 2008-04-27
I too am having a hard time enabling sharing on Ubuntu 8.  Any help would be wonderful.  I have all my media set up to share with my XBMC, but where all the instruction I read online make it seem easy to share with Ubuntu 7, this is not quite the case with 8.  I've even tried uninstalling Samba so that I can reinstall it, however each time I try to remove Samba, the Add/Remove system just hangs.

---

