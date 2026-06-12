---
title: "Upgrade Desktop to Desktop/Server."
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by M374llic4 on 2006-09-13
I had a friend burn me the desktop version toady. Where can I download all the addon utilities I would need to make it a full featured server edition?

I am on 56k at home for the time being, so I will need to download it here at work, is there a package I can download and install that will add all server abilities to my deaktop version?

Thanks :)

---

### Post by M374llic4 on 2006-09-13
Also, what all does the server package include that the Desktop dose not. Is it just LAMP? If I were to download that, would it have everything the server has? Or could I download both and combine them somehow?

---

### Post by Kilz on 2006-09-13
> **M374llic4 said:**
> Also, what all does the server package include that the Desktop dose not. Is it just LAMP? If I were to download that, would it have everything the server has? Or could I download both and combine them somehow?

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
That link will show you what to install to make your desktop into a server. With the server CD or setup, its more like what it doesnt add, a desktop. Desktops use a lot of resources most people running servers would rather have go to running the server. A lot of people that do ad a desktop to a server either use lightweight ones like fluxbox or icewm. Xubuntu is a good choice to.

---

### Post by M374llic4 on 2006-09-13
> **Kilz said:**
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
That link will show you what to install to make your desktop into a server. With the server CD or setup, its more like what it doesnt add, a desktop. Desktops use a lot of resources most people running servers would rather have go to running the server. A lot of people that do ad a desktop to a server either use lightweight ones like fluxbox or icewm. Xubuntu is a good choice to.

I checked that page out not long ago, but did not see a link to download the package.

The reason I want both, is I am new to linux and would like to learn the ins and outs of everything. I will be going back to school soon for network admin / engineering soon, and would like to have a few skills under my belt for linux, and servers. :)

---

### Post by bodhi.zazen on 2006-09-13
> **M374llic4 said:**
> Also, what all does the server package include that the Desktop dose not. Is it just LAMP? If I were to download that, would it have everything the server has? Or could I download both and combine them somehow?

The server install is a minimal install. CLI interface only. You can add what you want (Window manager included) including LAMP (well AMP....). There is an option to do a LAMP install, but again CLI, add what you want.

FYI: I do a server install an add fluxbox = Desktop without bloat. More secure (less apps & daemons= more secure).

---

### Post by Kilz on 2006-09-13
> **M374llic4 said:**
> I checked that page out not long ago, but did not see a link to download the package.

The reason I want both, is I am new to linux and would like to learn the ins and outs of everything. I will be going back to school soon for network admin / engineering soon, and would like to have a few skills under my belt for linux, and servers. :)

That page will walk you through the setting up of a lamp server. Apache server, mysql database and php. Apache could be conciderd the server alone. But all it will do is serve static web pages.
Another option for a lamp package it to get the server install disk. But that is a complete Ubuntu operating system install and will remove the already existing Ubuntu. It will also not add a desktop. Unless you are good with the cli or command line interface this is not what you want.

---

### Post by M374llic4 on 2006-09-13
> **Kilz said:**
> That page will walk you through the setting up of a lamp server. Apache server, mysql database and php. Apache could be conciderd the server alone. But all it will do is serve static web pages.
Another option for a lamp package it to get the server install disk. But that is a complete Ubuntu operating system install and will remove the already existing Ubuntu. It will also not add a desktop. Unless you are good with the cli or command line interface this is not what you want.

Thats why I want all the fucntions of both, so I can get better at it. :) So to sum it all up, the desktop version with LAMP (AMP) Would basicly be the desktop and server versions mixed? Thats all the missing software that I should get to learn about the server administration, and also the basic linux functions and tools that the dsektop provides?

---

