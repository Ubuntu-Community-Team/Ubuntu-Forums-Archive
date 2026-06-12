---
title: "nonserver edition serving or server guied"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-04-29
what i would like to do:
have a file server for music files.  it would work between windows and ubuntu machines.

i felt like i was rocking out ubuntu and nothing could slow me down, so i got myself a 933mhz computer and decided to make it into the server.  i installed feisty i386 server edition.

hmm. there is no gui.  so with the good Lord and some good ole fashioned sudo apt-get install. i downloaded xfce.  but startx complained about fonts.  i googled and found someone who had this problem.  yay - fonts.  but x still did not want to start.  i have gotten so many errors and i have tried changing so many things.  i am not exactly certain what my videocard was so i thought if it was being so fussy ill just give it vga 800x600.  i downloaded gnome and still nothing.

am i going about this the wrong way?  i want samba and ssh, but can't i just use xubuntu and get those applications to make a server? what are the advantages/disadvantages?  is the server edition just the same desktop ubuntu -gui +server programs?

---

### Post by nonewmsgs on 2007-04-29
the live feisty gives me a GUI (of course) and sysinfo says 1024x768 vga compable intel graphics card.

---

### Post by octoberdan on 2007-04-29
Generally installing X on a server is considered bad form. Not only does it present a security risk, but it also takes a hit to performance. With servers, less is more and more is dangerous. That is why the server install of ubuntu is streamlined. However, where this is just going to be a local server, you probably don't have to worry too much about security and those issues. My suggestion would be to reinstall ubuntu server and learn to set up things by hand (the command prompt can be scary, but mastering it is worth the time). We will help! A simple **apt-get install ssh**, for example, is all you need to install the ssh server. For samba, take a look at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) is a fantastic resource.

---

### Post by nonewmsgs on 2007-04-29
yeah just a local server.  well if you say it is bad form, then i would rather do it the "right way".  another stupid question:  what forum should i post my questions in?  should i go for a LAMP or DNS, and indepedant or the other one?

---

### Post by octoberdan on 2007-04-29
Probably either 
[http://ubuntuforums.org/forumdisplay.php?f=131](http://ubuntuforums.org/forumdisplay.php?f=131) (General Help, mention you're using server)
or
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7) (Servers and Security)

---

