---
title: "How to set up remote Access?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by plr2 on 2007-03-10
I´ve just started using Ubuntu today,  and I have it loaded on my old PC which is connected to my Router/modem, as is my new PC (which still runs windows - so far).

I would like to access my old PC remotely using my new screen on my new PC.

I´ve found Remote Desktop but I don´t think that´s what I need.

How can I set this up?

---

### Post by spin2cool on 2007-03-10
If you want to log in and use a GUI, look on this forum for one of the tutorials on setting up VNC. 

If you just need shell access, you'll need to install ssh on the Ubuntu box (sudo apt-get install ssh) and then use something like putty to ssh in from your windows box.

---

### Post by Gerard Barberi on 2007-03-10
So you want to access the Ubuntu remotely?

You could use VNC, but you need to enable it first in the Ubuntu install.
System -> Preferences -> Remote Desktop 
select allow users to contorl, deselect ask for confirmation and set a password.
VNC uses port 5900
If you're comfortable with command line you can ssh into the box.

There's also XDMCP, which I have never used
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Login_via_XDMCP](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Login_via_XDMCP)

---

### Post by plr2 on 2007-03-10
> **spin2cool said:**
> If you want to log in and use a GUI, look on this forum for one of the tutorials on setting up VNC. 

If you just need shell access, you'll need to install ssh on the Ubuntu box (sudo apt-get install ssh) and then use something like putty to ssh in from your windows box.
Thanks for that....I´m not very computer literate yet, so command line is out at the moment, till I know more.

What do I need to do at the other end (my new PC). Just enter a URL into my browser?

---

### Post by kelbizzle on 2007-03-10
Well both ways are probably simple. If your "New PC" is running windows. Just do what spin2cool said.  Just head over to [here ]("http://sourceforge.net/project/showfiles.php?group_id=63887&package_id=60914&release_id=428901") download the standalone viewer (it's only one file and has an auto scale feature). Type 192.168.1.whatever your ip is.  and your in. 

or if your other pc is linux open a terminal window
```
vncviewer 192.168.1.whatever
```

---

### Post by plr2 on 2007-03-10
> **kelbizzle said:**
> Well both ways are probably simple. If your "New PC" is running windows. Just do what spin2cool said.  Just head over to [here ]("http://sourceforge.net/project/showfiles.php?group_id=63887&package_id=60914&release_id=428901") download the standalone viewer (it's only one file and has an auto scale feature). Type 192.168.1.whatever your ip is.  and your in. 

or if your other pc is linux open a terminal window
```
vncviewer 192.168.1.whatever
```

Thanks everyone for your help. I've now got UltraVNC on my new PC, I've set up remote desktop in Ubuntu on my old computer, and can access my old PC from my new PC's screen - as long as I'm logged on to Ubuntu on my old PC.

As I really want to be able to do away with my old crt screen on my old computer - which means I couldn't log on when I power it up - I need to work out the more complicated method of being able to log on remotely without being already logged on to my old PC.

This is a fast learning curve for me - some of the terms used I just don't understand yet, and I realise my descriptions are very basic - but I'll get there. I'm really stoked at being able to get this far with it. I'm almost tempted to load it onto my new PC now!

My thanks to everyone all over the world involved in open source - how wonderful and fabulous it is.

---

### Post by Gerard Barberi on 2007-03-10
> **plr2 said:**
> 
As I really want to be able to do away with my old crt screen on my old computer - which means I couldn't log on when I power it up - I need to work out the more complicated method of being able to log on remotely without being already logged on to my old PC.


You can try setting up [FreeNX]("http://www.nomachine.com/products.php").  It's like an RDP for linux.  Plus it can be accessed from a windows client.  I've set it up on Dapper by following these [directions]("http://ubuntuguide.org/wiki/Dapper#Remote_Desktop_Access_via_NX").

You do not need to login, just get to the login screen which your pc should do just by being turned on.  It operates off the ssh port.

---

