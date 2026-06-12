---
title: "Help with conversion from Win to Ubuntu"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Richardinel on 2007-10-22
I have a seven machine network office, I am determined one piece at a time to convert the whole office to Ubuntu but am not an IT administrator rather just an experienced windows user. 

Open Office and Mozilla Browsers are no problem cause we have used them for ever. I have installed 7.1 to a new machine but am struggling with a few things. I will need for the interim, to access from the Linux machine to the Win XP Pro Data Server  to get OO files only and from the Linux machine allow access by other Windoze machines of my Photographs only.

I have installed 7.1 on my machine, and somehow have found the other networked xp machines, Ubuntu immdiatly found my Gateway, internet immediately was up and running.

1. I have a directory on the XP data server called "Reports" I have found this on the Linux machine but how do I create a shortcut on the Linux desktop ?  
2. I have assigned IP address to all network machines, how do I do this on the Linux machine.
3. I am old school in respect of viewing files, I like to have a directory tree, to access and create folders etc., like Windows Explorer, can this be done ? showing the networked machines as well ?.

I am sure I will need more help in the future, please assist me in making this work, I am very keen to get this pilot machine working.

---

### Post by hyper_ch on 2007-10-22
(2) if you assign static IPs then I assume you know the details needed for each computer.

The config files for entworking are:

/etc/network/interfaces

Make an entry sort of like this:
```

iface eth0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        gateway 192.168.0.1

```
It is important, that adress, netmask and gateway are indented! Just replace it with your box's static IP and the correct gateway.

The /etc/resolv.conf file contains your nameservers:
```

nameserver 192.168.0.1

```
In that case your router would be the nameserver. You can add more e.g.:

```

nameserver 192.168.0.1
nameserver 208.67.222.222
nameserver 208.67.220.220

```

And finally you have your /etc/hosts file
```

127.0.0.1       localhost.localdomain   localhost
192.168.0.5 mydomain.com myhostname

::1     ip6-localhost   ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Once you setup the right stuff there, restart the eth0 interface:

```

sudo ifdown eth0 && sudo ifup eth0

```

(1) Regarding the reports folder. Where on the linux box have you found that? The simplest way to add it to the desktop would be creating a symlink (it can also be done using the gui somehow but I don't have a ubuntu box right now available here):

Go to the desktop (or whereever you want it to be):
```

cd /home/USER/Desktop
[code]

Now make the symlink:
[code]
ln -s /path/to/where/the/reports/folder/is/ REPORTS

```

(3) I consider the tree-thingy new school and not old school ;) That didn't come until Win 95 or so... I rather prefer multi-pane viewings. Not sure how Nautilius can do that but Konqueror kan easily do that (and it's also a multi-pane browser). However Konqueror is a KDE application so it will load additional libraries (but I like it too much so I use it anyway)

---

### Post by realvz on 2007-10-22
about you directory vew question
in Ubuntu when you open Nautilius (the file browser), on the right hand side...you should see something like
Desktop
My Computer.
....
....

just above that should be a drop down button called Places...you can drop in down and it will present you the option of choosing a tree view just like Explorer.

---

### Post by Samhain13 on 2007-10-22
Addition to realvz's post on #3,

In Nautilus, toggling between Icon View and List View can be done in the View Menu, where you will find the options: View as Icons and View as List (this gives you a tree view). To set either as default, go to Edit->Preferences. Select your preferred default view in the View tab. :)

---

### Post by Richardinel on 2007-10-22
Guys, I dint know what the hell your talking about, yes I know the IP address for all machines and assigning these address in windows I can do blind folded, creating shortcuts is a drag and drop in windows, whats a symlink and where is this ?. Gee... clearly this is not going to be as easy as I thought it would be. My next problem is accessing the shared printers on the xp network !.

---

### Post by hyper_ch on 2007-10-22
Calm down and have a read here:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

After the "D'oh" experience [IMG]http://content.answers.com/main/content/wp/en/thumb/1/19/250px-D_oh.jpg[/IMG] have some coffee ;)

If you don't know what a symlink is, you can google for it. Drag'n'Drop is nice but for solving problems it's more an obstacle than a help. You have to say: Go there, do this, select that, check this box.... and then you have also the problems of language barriers. You say translate from your language into english, the other translates from english back in their language and in the end you don't know what the other is talking about. Furthermore you have different Desktop Environments - each of them handles things differently ;)

So using the cli (command line interface) can give you just a straight solution. Not much explanation is needed there, but if you want to know more about what you're doing, you can find out what that all means - and hence you learn something ;)

P.S.: Not sure about the printer. never done that ;) my printer has it's own IP in the net and printing is done through tcp/ip

---

