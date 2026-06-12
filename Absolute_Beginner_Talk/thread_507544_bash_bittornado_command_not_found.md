---
title: "bash: bittornado: command not found"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by vector on 2007-07-23
ok im new, i dont understand im very frustrated. I have read dozens of posts..man this is a real mess people!!

however lets see what dosent work.
bittorrant and gnome-btdownload are already installed in my ubuntu 2.6.15 machine.
I saved a meta file using firefox into a folder.
I used applications/internet/bittorrent to run the meta file
but its real slow. From what I read it needs to be told things and set up.. fine how?
How on earth do you configure it????
I installed  bitornado, bittorent-gui and all i get is 
bash: bittornado: command not found
bash: bittorent command not found
etc etc addnausem

what gives?? i even tired man bittorent ...same deal
its there but I cant run it or even man it.
I even removed em them put em back

---

### Post by Mornedhel on 2007-07-23
I don't know if you typoed only in your post, but there are two 'r' in bittorrent. And I think the command is actually gnome-btdownload .

---

### Post by RomeReactor on 2007-07-23
Hi. You could double-click on the **.torrent** file you downloaded to open it with BitTorrent, or right-click on it and select which application you want to open it with.

---

### Post by Mornedhel on 2007-07-23
Afterthought :

If you need something configurable, Azureus is a (very heavy) torrent manager. Be warned : Azureus is Java, and as such, resource-hungry (don't look at me like that Java fans, Azureus used at least 100 MB RAM on my machine, I run rtorrent now).

---

### Post by spd106 on 2007-07-23
There aren't many options to the standard gnome bt client, that's on purpose. Bittornado has more options that are accessible through the gui menus. It's sounds like you need to enable port forwarding in your router, to get that magic green light in bittornado.

If you want to start either bt gui client from a terminal run
```
btdownloadgui.bittorrent
```
or
```
btdownloadgui.bittornado
```

You can also have curses and headless versions by changing the gui part.

---

### Post by vector on 2007-07-23
ok im gettting link 10kbs woefull.
I did a port fwd thingo ... i think
torrent1 	Always On 	tcp 	6881 - 6881 	6881 - 6881 	192.<machine IP>
but itmade no diff

---

### Post by vector on 2007-07-23
```
 btdownloadgui.bittorrent
Could not load wxPython. In order to use this script,
you must have wxPython installed.  It is available in
the package libwxgtk2.4-python.

```
right ill play its game

```
sudo apt-get install libwxgtk2.4-python
Password:
Reading package lists... Done
Building dependency tree... Done
Package libwxgtk2.4-python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-wxtools python-wxgtk2.4
E: Package libwxgtk2.4-python has no installation candidate

```

oo yeah the great run around

---

### Post by RomeReactor on 2007-07-23
> **vector said:**
> From what I read it needs to be told things and set up.. fine how?
How on earth do you configure it????

There's not much to configure in the default BitTorrent client; the only option that is missing in the graphical interface is the ability to change ports, which is achieved through **Gconf**. You can open it by opening a terminal and entering:
```
gconf-editor
```
or by editing the menus (right-click on the menubar at the top, select "Edit Menus"), and checking the "System Tools" submenu just below "Sound & Video"); now you can find Gconf in "Applications->System Tools->Configuration Editor").

Once Gconf is open, go to "apps->gnome-btdownload->settings"

By the way, did you try my earlier suggestion?

---

### Post by vector on 2007-07-23
yeah right click on the file and it just starts the same thing that was running from the applications/internet menu

i gave up on the gui's as things look broken or not installed or dependent on things that arnt there..
so i tried to focue on the port fwd thing

im unsure as to wheather I have that right.

Is there a way to test if things are set right.. i mean the other end could be a slow link?

I also capped the users to 3 and upload capped to 5

---

### Post by Mornedhel on 2007-07-23
The python-related packages were renamed not too long ago (think not too many releases ago). The new naming convention appears to be python-something (the old convention was better if you ask me). You should install python-wxgtk2.4 .

---

### Post by vector on 2007-07-23
ok i got gconf running but the "Once Gconf is open, go to "apps->gnome-btdownload->settings""
only gives me cap settings tho, which i have already played with. 
nothing to change  ports.
is the 6881 not a good one to use or do i have the port fwd stuff right.. its just a slow link?

---

### Post by vector on 2007-07-23
> **Mornedhel said:**
> The python-related packages were renamed not too long ago (think not too many releases ago). The new naming convention appears to be python-something (the old convention was better if you ask me). You should install python-wxgtk2.4 .

ok did that.. not a great help a big grey window which extends past the top of my screen and below the bottom , ie no way of closeing. I killed it tho ;)
it displays switch command like youd find in a man page.
defaults to 6881 so it should all be kewl

---

### Post by RomeReactor on 2007-07-23
When you are in the gnome-btdownload settings in Gconf, double click on the ports if you want to change them; usually you only need **min_port 6881** and **max_port 6889**.

To help you set up port forwarding in your router, you can go to [PortForward]("http://portforward.com/").

---

### Post by vector on 2007-07-23
ok  under gconf. gnome-btdownload there is the path value and a settigns folder
in the settings folder there are 5 names?
cap this cap that .
There is nomention of no port.

anyway point is i have redirected external port 6881- to internal port 6881 I also looked at the port forward link thanks, and it looks like what I have.

so I guess i just assume this one is slow. Murphy would agree with that it being my first attempt and all.
im getting 13 out of my possible 50 ish

---

### Post by RomeReactor on 2007-07-23
You have to double-click on **min_port** and **max_port** to change the settings.

---

### Post by vector on 2007-07-23
yep i read you right.. those are just not there!!

---

### Post by vector on 2007-07-23
hopefully it attached a snapshot

---

### Post by vector on 2007-07-23
this time

---

### Post by RomeReactor on 2007-07-23
Oh, sorry; thought you overlooked it. That's very odd.

If you're not averse to run KDE applications in Gnome, I suggest you try Ktorrent; it's the best client I've used, and undoubtedly one of the very best in Linux. It's really fast and very configurable, in my opinion.

---

### Post by vector on 2007-07-23
ok ill just give up for tonight seems a rather waste of time and brokenness

thanks for your help

---

### Post by vector on 2007-07-23
i add this in case this thread is seen by others.

It seems that it was a misunderstanding of what and how bittorrent works.

    *d ont get all bent up over your speed being real slow.. I found out that unless your supplying others with guff (ie uploading to them, then your download sucks. For eg, I was torrenting at 6kb/s then someone else joined in on this side of the world and it jumped to 30kb/s, being adsl 50 ish would be best bet anyway. Fastest I have seen was 41kb/s and it was defiantly connected with who was leeching off of me..
    * So dont get bent over your setup it might simply be that there are no suckers in your area creating demand 

checks and balances
I used this below to see if my port was open.
    * [http://www.utorrent.com:16000/testport2.php?port=28357](http://www.utorrent.com:16000/testport2.php?port=28357) where 28357 is the port your torrent software has chosen

---

