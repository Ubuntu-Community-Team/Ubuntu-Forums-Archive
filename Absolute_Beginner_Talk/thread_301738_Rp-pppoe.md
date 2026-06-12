---
title: "Rp-pppoe"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Harry_Callahan on 2006-11-17
Hello folks,

I never got RP-PPPOE working under 6.06 & 6.10. I used this ubuntuguide.org:

--------------------------------------------------------

    * Read #General Notes
    * Read #How to install Basic Compilers (build-essential) 

wget -c [http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz](http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz)
sudo tar zxvf rp-pppoe-3.6.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.6/
gksudo gedit /usr/share/applications/RP-PPPoE.desktop

    * Insert the following lines into the new file 

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;

    * Save the edited file
    * Applications -> Internet -> RP-PPPoE 

------------------------------------------------------

Nothing happens when I click RP-PPPOE from Applications-> Internet

I tried typing: gksudo /opt/rp-pppoe-3.6/go-gui which should start everything up, but it stops with these last lines:

Running GUI configuration tool...
exec: 24: wish: not found



I know I can use pppoeconf as alternative, but I was hoping to get RP-PPPOE to do the job. Sometimes I need a PPPoE connection for testing.


Any help would be great!

---

### Post by justin whitaker on 2006-11-17
I haven't gotten pppoe to run on 6.10, but on 6.06.1, it's as simple as running the pppoeconf dialogue. 

There is no function difference between the rp-pppoe Gui and that, so why do you specifically need roaring penguin?

---

### Post by Harry_Callahan on 2006-11-17
Thanks for the reply Justin,

I'm little confused, your saying that rp-pppoe and pppoeconf are similiar? Is that right? I'm looking for a PPPoE dailer with GUI, let's say like WinXP's PPPoE dailer(mini-port WAN dailer) or RASPPPOE(also for MS systems). Instead of typing "pon adslprovider" from terminal, I simply want a PPPoE dailer with GUI. Anyway, RP-PPPOE isn't starting up, I followed the guide correctly

Thanks

---

### Post by justin whitaker on 2006-11-17
> **Harry_Callahan said:**
> Thanks for the reply Justin,

I'm little confused, your saying that rp-pppoe and pppoeconf are similiar? Is that right? I'm looking for a PPPoE dailer with GUI, let's say like WinXP's PPPoE dailer(mini-port WAN dailer) or RASPPPOE(also for MS systems). Instead of typing "pon adslprovider" from terminal, I simply want a PPPoE dailer with GUI. Anyway, RP-PPPOE isn't starting up, I followed the guide correctly

Thanks

As I understand it, rp-pppoe puts a GUI around the whole process, but the core process is similar. Then again, I'm not an expert. 

Whenever I used RPPPPOE, it wasn't exactly a dialer: you set up a connection, and when you wanted it to run, you started the connection. PPPOECONF does the same thing, only via a terminal. 

I suppose you could add more than once provider to pppoeconf and then manually select them via command line.

As for getting rp-pppoe running, every time I have something exit like that, I am missing a gui library. Do you have TK and tkpppoe installed?

---

### Post by Basu on 2006-11-30
I had sort of the same problem. Only, whenver I ran go-ui, it would compile the whole thing and then do absolutely nothing. I fixed it by going into the GUI folder and making the file tkppoe executable as root and chaning the menu entry to point there. Check it out. Might work.

---

### Post by justin whitaker on 2006-11-30
FYI, I just installed 6.10 Edgy last night, and had pppoe up and running within 5 mintues. Very odd.:-k

---

### Post by Harry_Callahan on 2006-11-30
@Basu

the file tkpppoe is in /usr/bin and is already executable by root

if I run tkpppoe(even as root) I get exec: 24: wish: not found

You said "and chaning the menu entry to point there. "
Do you mean writing /usr/bin/tkpppoe in the script:

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.6/go-gui   <<<--------- at this point????????
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;



Thanks!

---

### Post by funk19 on 2006-12-02
Harry there is a problem with rp-pppoe in general and that problem is there is no GUI to use for this. I was experiencing all the same problems as you and then I realised i needed to install g++ via the synaptic package manager.

Once g++ was installed I could then compile this app without any problems and get it to connect to the pppoe connection. The only problem was that this was all done in the terminal and not using any GUI.

I then decided that your execute in the RP-PPPoE.desktop file should probably be executed via terminal to see what it does. When running 
gksudo /opt/rp-pppoe-3.6/go-gui with g++ installed all that happens is it simply tries to recompile the application.

In reading the readme and connection docs in the tar ball I noticed that compiling this script from source requires either ./go or ./go-gui as the initial command to compile.

I could also not find any reference to an actual GUI interface to use with this script.

So, I have come to the conclusion that this app does work once g++ is installed and but it provides no additional value as you still need to connect via terminal so it's probably better to use the native pppoe in Ubuntu.

I, like you, would ideally like to have some kind of GUI interface to work with with pppoe but I'm running out of ideas. Anyone?

---

### Post by funk19 on 2006-12-02
Ahh... I stand to be corrected. I finally did manage to find the GUI and in so doing I found out what is wrong with your RP-PPPoE.desktop file.

Change the Exec line in the desktop file from this:

```
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
```

To this:

```
Exec=sudo tkpppoe
```

This will now bring up the GUI when clicking on the icon in Applications > Internet

I still think though that your main problem is going to be that you need to compile this script before you can really use it. I may be wrong but here is what I did.

1. Install g++ from Synaptic Package Manger
2. cd /opt/rp-pppoe-3.6/src
3. sudo ./configure
4. sudo make
5. sudo make install

Assuming you have changed your RP-PPPoE.desktop file as mentioned above you should be able to now click on your icon in Applications > Internet and you can then setup your pppoe connection using the GUI.

If you want to know how to use the GUI then go here:
file:///opt/rp-pppoe-3.6/gui/html/tkpppoe.html

---

### Post by Merlintrix on 2006-12-03
> **funk19 said:**
> Ahh... I stand to be corrected. I finally did manage to find the GUI and in so doing I found out what is wrong with your RP-PPPoE.desktop file.

Change the Exec line in the desktop file from this:

```
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
```

To this:

```
Exec=sudo tkpppoe
```

This will now bring up the GUI when clicking on the icon in Applications > Internet

I still think though that your main problem is going to be that you need to compile this script before you can really use it. I may be wrong but here is what I did.

1. Install g++ from Synaptic Package Manger
2. cd /opt/rp-pppoe-3.6/src
3. sudo ./configure
4. sudo make
5. sudo make install

Assuming you have changed your RP-PPPoE.desktop file as mentioned above you should be able to now click on your icon in Applications > Internet and you can then setup your pppoe connection using the GUI.

If you want to know how to use the GUI then go here:
file:///opt/rp-pppoe-3.6/gui/html/tkpppoe.html

It still gives the same error i.e exec: 24: wish: not found
and isn't running the go file equivalent to compiling it? At least, that was the impression I got from the readme.
Am I missing a library somewhere? Because I've got it to work on both breezy and dapper.

---

### Post by Harry_Callahan on 2006-12-08
Hello to all,

same problem here too, exec: 24: wish: not found
g++ already installed
tried to ricompile from cd /opt/rp-pppoe-3.6/src, but no luck

---

### Post by aseembehl on 2007-02-19
> **funk19 said:**
> Ahh... I stand to be corrected. I finally did manage to find the GUI and in so doing I found out what is wrong with your RP-PPPoE.desktop file.

Change the Exec line in the desktop file from this:

```
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
```

To this:

```
Exec=sudo tkpppoe
```

This will now bring up the GUI when clicking on the icon in Applications > Internet

I still think though that your main problem is going to be that you need to compile this script before you can really use it. I may be wrong but here is what I did.

1. Install g++ from Synaptic Package Manger
2. cd /opt/rp-pppoe-3.6/src
3. sudo ./configure
4. sudo make
5. sudo make install

Assuming you have changed your RP-PPPoE.desktop file as mentioned above you should be able to now click on your icon in Applications > Internet and you can then setup your pppoe connection using the GUI.

If you want to know how to use the GUI then go here:
file:///opt/rp-pppoe-3.6/gui/html/tkpppoe.html

I had the same problem, tried the above but still RP-PPPOe is not working.

---

### Post by netstv on 2007-10-29
Just in case anyone wants to know the answer....

You need the tk8.* package.
System >> administration >> Synaptic Package Manager
Install the package tk8.4

Once I did that everything work... ahhh GUI's.. gotta luv em.

:guitar:

---

