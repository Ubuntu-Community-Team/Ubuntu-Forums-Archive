---
title: "Xchat with XUbuntu or any IRC client"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by emkuf on 2008-03-18
I would like to know how to install Xchat on XUbun,tu or any IRC client besides Pidgin. I have read some how to's on installing software and so far they have not worked at all. If I can get Xchat to work I will be happy but I refuse to use Pidgin.

---

### Post by TenPlus1 on 2008-03-18
Pidgin is a fine IRC client, but you can find xchat and th gnome-gui for it in the repos and it works perfectly...

---

### Post by bigfootnmd on 2008-03-18
Since you are probably using FIREFOX why go get another program?  I use the Chatzilla plugin.  I am at work now where we use WINDOZE so I can't take you step by step.  However, if you click on Tools in Firefox you should see the option to add plugins and stuff.

Since Chatzilla was released I do not use any other IRC client.

---

### Post by Wobedraggled on 2008-03-18
Use synaptic or type "sudo apt-get install xchat" in a terminal.

and whala, Xchat.

---

### Post by emkuf on 2008-03-18
> **Wobedraggled said:**
> Use synaptic or type "sudo apt-get install xchat" in a terminal.

and whala, Xchat.

```
****@M****:~$ sudo apt-get install xchat
[sudo] password for maru-chan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xchat
```
nope no good :(

---

### Post by emkuf on 2008-03-18
> **bigfootnmd said:**
> Since you are probably using FIREFOX why go get another program?  I use the Chatzilla plugin.  I am at work now where we use WINDOZE so I can't take you step by step.  However, if you click on Tools in Firefox you should see the option to add plugins and stuff.

Since Chatzilla was released I do not use any other IRC client.
I like to keep my IRC clients as IRC clients and nothing more.

---

### Post by Xiong Chiamiov on 2008-03-18
I'm not sure why xchat isn't showing up in your repos.  Do you understand how to use Synaptic and manage repositories?  If so, then make sure that the first 3 at least sources are checked and then click reload.  You can also always go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and find the .deb package, though then of course it won't update automagically.

---

### Post by tlink on 2008-03-18
You might check out ircii, its a terminal based client, but will get you by till you can get your xchat working.

---

### Post by Oldsoldier2003 on 2008-03-18
> **emkuf said:**
> ```
****@M****:~$ sudo apt-get install xchat
[sudo] password for maru-chan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xchat
```
nope no good :(
turn on the repos in software sources (don't remember which repo xchat is in... multiverse?)

then
```

sudo apt-get update
sudo apt-get install xchat
```

---

### Post by emkuf on 2008-03-18
> **Xiong Chiamiov said:**
> I'm not sure why xchat isn't showing up in your repos.  Do you understand how to use Synaptic and manage repositories?  If so, then make sure that the first 3 at least sources are checked and then click reload.  You can also always go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and find the .deb package, though then of course it won't update automagically.

Is Synapatic the add remove thingy

---

### Post by emkuf on 2008-03-18
> **Oldsoldier2003 said:**
> turn on the repos in software sources (don't remember which repo xchat is in... multiverse?)

then
```

sudo apt-get update
sudo apt-get install xchat
```
How do I go about turning on the repos?

---

### Post by dr3ad on 2008-03-19
**EASY-graphical method**

go to system in top menu bar
go to administration
select synaptic package manager


once in synaptic go to the settings tab and select repositories

select the repositories you want to add.

I personally select canonical, community and source code atm

then you will need to select reload.

you can then run code in your post in console or just download the package through synaptic

---

### Post by undertakingyou on 2008-03-19
I use Pidgin for jabber and msn, but for IRC the one that I like the best is irssi.  It is all terminal based but easy, straight forward and well documented.  Plus, it can be wrapped in screen and then used anywhere if you use SSH.

---

### Post by emkuf on 2008-03-20
> **dr3ad said:**
> **EASY-graphical method**

go to system in top menu bar
go to administration
select synaptic package manager


once in synaptic go to the settings tab and select repositories

select the repositories you want to add.

I personally select canonical, community and source code atm

then you will need to select reload.

you can then run code in your post in console or just download the package through synapticWorked thank you :KS

---

### Post by bhavi on 2008-03-20
Well I use IRSSI now... and its working great.......

---

### Post by SorenK on 2008-03-22
Which of these would be best for receiving files from other IRC users (and no, I don't mean all the piracy that goes on using IRC channels-- my brother's a mega geek and wants to share stuff via IRC, but he doesn't know linux well enough to recommend me a good client)?

---

