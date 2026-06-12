---
title: "how can i install pidgin ???"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Aamir Aziz on 2007-08-05
i have the setup of pidgin (debian pakage) i'm trying to install it but it does not work and errors are produced during installation i.e:

uncertainty@IBM:~$ sudo dpkg -i pidgin_2.1.0-1_i386.deb
(Reading database ... 110276 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on tcl8.4 (>= 8.4.5); however:
  Package tcl8.4 is not installed.
 pidgin depends on tk8.4 (>= 8.4.5); however:
  Package tk8.4 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
uncertainty@IBM:~$ 



how should i install it ????

---

### Post by kleo skywalker on 2007-08-05
This is a very simple way to install Pidgin, and it worked for me:
1) Go to **System**-->**Administration**-->**Synaptic Package Manager**. Search for **tcl8.4** and **tk8.4** and install them.
2) The latest version of Pidgin is split in 2 packages. Click [here]("http://www.getdeb.net/download.php?release=1045&fpos=1") for the first one. (I opted to **Open with  GDebi Package Installer**, but I guess you can save to disk and install from there as well.)
3) Click [here]("http://www.getdeb.net/download.php?release=1045&fpos=0") for the second part of the package.
4) To access, **Applications**-->**Internet**-->**Pidgin**.
5) If you want to remove Gaim, click [here]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb").

P.S.: Can't get gtalk to work, but with the gtalk gadget and the option to chat from inside gmail, I suppose that's not a big problem.

---

### Post by AlexenderReez on 2007-08-05
> **Aamir Aziz said:**
> i have the setup of pidgin (debian pakage) i'm trying to install it but it does not work and errors are produced during installation i.e:

uncertainty@IBM:~$ sudo dpkg -i pidgin_2.1.0-1_i386.deb
(Reading database ... 110276 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on tcl8.4 (>= 8.4.5); however:
  Package tcl8.4 is not installed.
 pidgin depends on tk8.4 (>= 8.4.5); however:
  Package tk8.4 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
uncertainty@IBM:~$ 



how should i install it ????


please do installation using deb package installer....which just double click the pidgin deb package....dpkg is really dangerous ..unless you can confirm you have all dependencies installed.....

---

### Post by kleo skywalker on 2007-08-07
> **kleo skywalker said:**
> This is a very simple way to install Pidgin, and it worked for me:
1) Go to **System**-->**Administration**-->**Synaptic Package Manager**. Search for **tcl8.4** and **tk8.4** and install them.
2) The latest version of Pidgin is split in 2 packages. Click [here]("http://www.getdeb.net/download.php?release=1045&fpos=1") for the first one. (I opted to **Open with  GDebi Package Installer**, but I guess you can save to disk and install from there as well.)
3) Click [here]("http://www.getdeb.net/download.php?release=1045&fpos=0") for the second part of the package.
4) To access, **Applications**-->**Internet**-->**Pidgin**.
5) If you want to remove Gaim, click [here]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb").

P.S.: Can't get gtalk to work, but with the gtalk gadget and the option to chat from inside gmail, I suppose that's not a big problem.

Or, as your problem is missing dependencies, you could simply do step 1 above, and then try to install the debian package you have.

---

### Post by basketballer on 2007-08-08
when i mark tcl8.4 and tk8.4 in Synaptic, it tells me that it's NOT AUTHENTICATED..
Shall i continue in installing these dependencies!??

---

### Post by kevin11951 on 2007-08-08
let me help "all" of you! go [here]("http://www.getdeb.net/app.php?name=Pidgin"), download, instal, be happy! :)

---

### Post by ivesjd on 2007-08-08
And when this happens (see attachment)?

---

### Post by Dark Star on 2007-08-08
> **ivesjd said:**
> And when this happens (see attachment)?
Might be repo problem :p Check this repo .. download and instal it easily ;)

[http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/](http://www.kalpiknigam.com/blog/2007/05/12/install-pidgin-200-on-ubuntu-feisty-with-all-plugins/)

---

### Post by kleo skywalker on 2007-08-09
> **basketballer said:**
> when i mark tcl8.4 and tk8.4 in Synaptic, it tells me that it's NOT AUTHENTICATED..
Shall i continue in installing these dependencies!??

Yes, go ahead. It's been a while since I did this, and there hasn't been a problem so far.
Good luck.

---

### Post by ivesjd on 2007-08-09
Nope, I'm still getting the same thing. And I'm saving everything to my desktop so I do have permission to open the file.

---

### Post by AlexenderReez on 2007-08-09
> **ivesjd said:**
> Nope, I'm still getting the same thing. And I'm saving everything to my desktop so I do have permission to open the file.

that is because installer corrupted....install using synaptic is even easier ....


> [http://ubuntuforums.org/showthread.php?t=482859&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=482859&highlight=pidgin)

---

### Post by kleo skywalker on 2007-08-11
To the person who started this thread,
If and when your problem is solved, could you please mark this thread as "solved"? That makes it easier for other people looking for a solution to the same problem.
Thanks.

---

### Post by jeremy1138 on 2007-08-11
I have a problem with pidgin as well...  I got it installed fine and it will start and all that but it won't connect to any of my aim or yahoo accounts...  Any ideas?

---

### Post by ubermenschx on 2007-08-11
thankx...this worked perfectly on 7.04 /Dell 1420n

---

### Post by Old Pink on 2007-08-12
> **kleo skywalker said:**
> 5) If you want to remove Gaim, click [here]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb").Source of part 5: [http://www.mbhoy.com](http://www.mbhoy.com)

Really appreciate it if you put that somewhere in the original post. 

Thanks for visiting my site :)

---

### Post by kleo skywalker on 2007-08-13
> **Old Pink said:**
> Source of part 5: [http://www.mbhoy.com](http://www.mbhoy.com)

Really appreciate it if you put that somewhere in the original post. 

Thanks for visiting my site :)

I'm so sorry, I didn't realize I hadn't mentioned it.
I got this working using the instructions [here]("http://ubuntuforums.org/showthread.php?t=506791&page=2") and [here]("http://ubuntuforums.org/showthread.php?t=474071&highlight=pidgin+how+to"), added something put it into baby steps for clueless newbies such as myself.
Thanks for pointing it out, and for the how-to.

---

