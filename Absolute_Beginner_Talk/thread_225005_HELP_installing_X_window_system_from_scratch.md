---
title: "HELP: installing X window system from scratch"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-07-28
hello,

just wondering... i've installed ubuntu for a friend, its an old machine i had the breezy and dapper cds in hand. i chose server install with the breezy cause the gnome desktop enviro would be really slow... anyway

now everything is text based. i wish to install the x windows system then install XFCE desktop enviro with ICEWM window manager or maybe something lighter... what packages do i need to install with aptitude?

very urgent many thanks :D

---

### Post by az on 2006-07-28
Dist-upgrade to Dapper first.  Then, enable the universe repository and install xubuntu-desktop and icewm.

sudo apt-get install xubuntu-desktop icewm menu
or 
sudo aptitude install xubuntu-desktop icewm menu

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by ProjectGod on 2006-07-28
do i need to upgrade to dapper first? is this a must?

cheers.

---

### Post by ProjectGod on 2006-07-28
bump. nudge.

---

### Post by az on 2006-07-29
Xubuntu-desktop in Dapper is much better.  But, no, you can stick with breezy....

---

### Post by confused57 on 2006-07-29
> **azz said:**
> Xubuntu-desktop in Dapper is much better.  But, no, you can stick with breezy....

I agree, I've tried both...upgrading a server install from Breezy to Dapper is a "breeze", also.  

Not that you needed my endorsement, maybe just a second opinion.

---

### Post by c24ck32 on 2007-12-20
Thanks guys, this thread really useful... Thanks alot :)

---

### Post by louieb on 2007-12-20
Really nice guide to installing  one piece at a time 
[LIST=1]
[*]install a command line system
[*]install xorg
[*]install a window manager
[*]install a login manager.[/LIST][Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

I've used this guide a couple of times. Its nice and straight forward. And with Ubuntu and apt-get its pretty quick and easy.

---

