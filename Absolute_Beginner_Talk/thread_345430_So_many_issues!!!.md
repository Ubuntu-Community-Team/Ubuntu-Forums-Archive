---
title: "So many issues!!!"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Twain on 2007-01-24
I am not completly new to Linux but new enough that this is probably where I should post.  This is probably the first of many posts.

Problem 1:

I am not able to share folders on my Linux box to my windows box.  On the Linux box I can view and access the shared folders on the windows box, but I can't write to them, even though I have allowed write privledges on the windows box.  The windows box can't even see the linux box on the network.  I turned on an option on the linux box to "broadcast services" on the network, but still nothing. Any suggestions?

Problem 2:
I'm am well versed with windows networking, and very familiar with logging in remotely, but I don't even know where to start on the Linux box.  I would love to have the ability to login remotely and utilize a GUI interface, but I'm not even sure if such an application exists.  

These are simple problems I'm sure but I feel stupid because I can't figure it out.  I am somewhat comfortable in using terminal, I was well versed with DOS way back in the day, the commands are just different.  Any suggestions on good books I should read about Linux/Ubuntu would be much appreciated.

---

### Post by oilchangeguy on 2007-01-24
sorry i don't have the answers for your questions. i'm sure there are many people in here who can help you. what i'm going to suggest is getting a book on ubuntu, one i've found very helpful is ubuntu unleashed.

---

### Post by lamego on 2007-01-24
Problem 1:
The Linux default NTFS driver does not support write access, there is a new driver called ntfs-3g but is still under development. I would recommend to install a driver on windows to access to the linux partition and access the way around.
Ext2/Ext2 driver for Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)
To share your data over the network you will need to install samba on the linux box, do some research on the forum about using samba.

Problem 2:
You can install a vnc service on your linux box and use an vnc client on the windows box or you can install a X client like xming and setup your graphical server to accept remote connections.

---

### Post by stijn_pol on 2007-01-24
Talking about remote login? use ssh!
Make sure on your linux machine, you install ssh and openssh-server
```
 sudo apt-get install ssh openssh-server 
```
ssh uses port 22 as default port.

Running an X11 application: 
The X11 application is installed on the server but the x11 windows will be shown on the host client.
Do this on your linux(server) machine
    * Allow X11 applications to connect : 
```

xhost +

```

    * Now you can connect to the server using : 
```

ssh -Y user@server

```
You're ready to start any X11 application you want. 
So now, if you ssh to your linux machine and you type: firefox in terminal, firefox wil be opened on your client machine.
OK?!

---

