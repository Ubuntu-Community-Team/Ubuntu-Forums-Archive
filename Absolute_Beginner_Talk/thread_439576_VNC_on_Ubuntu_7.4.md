---
title: "VNC on Ubuntu 7.4"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ati on 2007-05-10
I have reinstalled Ubuntu server a few times over the last couple of days. The one problem i have right now is that i cant set up vnc to work. I followed few different approaches discussed in the forums but the best i could get is that I could log in but see only a command line box and not the desktop.

Could someone please tell me the steps i have to take to get it working. Since i plan to have the box running as a headless server it is no point to set up further unless i can sort out this issue. 

The setup is following:
Fresh install of Ubuntu 7.4 server + installed gnome desktop environment, and updated everything.

Any help appreciated.

Thank you.

---

### Post by fakie_flip on 2007-05-10
You haven't told us what you did exactly, so I dont know what you've tried already, and what you did wrong. You haven't provided enough information, so all I can do is guess the problem. I would use x11vnc. Then "man x11vnc" Servers should have GUIs. Maybe what you really should have downloaded was ubuntu desktop for a desktop computer. That would be a lot easier for someone new to Linux to setup vnc because it is included already and all you have to do is enable it. The one included in Ubuntu desktop is called vino, and it comes with Gnome.

---

### Post by ati on 2007-05-10
I was following [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc") thread.

Otherwise i think i made it clear that i have a fresh install of ubuntu, and I was hoping that someone would be able to gave me a step by step instruction how to do the setup. 

I just checked and vino is installed but to my knowledge wino is only capable of showing the actual session, and someone has to accept the connection on the server. That is definitely not what I was looking for.


Thank you.

---

### Post by fakie_flip on 2007-05-11
Did you create a ~/.vnc/xstartup? I believe that file tells the vnc server what desktop environment to you. In your case it would be Gnome. If not, do a search for xstartup on this forum or Google and create one. Let me know how that goes.

---

### Post by fakie_flip on 2007-05-11
[http://www.realvnc.com/faq.html#grey](http://www.realvnc.com/faq.html#grey)

---

### Post by ati on 2007-05-12
This is what i did so fahr:
> 
Edit /etc/X11/gdm/gdm.conf

sudo vi /etc/X11/gdm/gdm.conf (or gksudo gedit ... if you prefer)

(While writing this, I notice that the file has a warning that it may be overwritten on upgrade and recommends using another .conf file. Should really look in to that…)

    * Find the [xdmcp] section in the file, set: Enable=True (One place suggested rebooting after editing.)
    *

      Find:

      # The greeter for xdmcp logins, usually you want a less graphically intensive
      # greeter here so it's better to leave this with gdmlogin
      # RemoteGreeter=/usr/lib/gdm/gdmlogin
And uncomment the RemoteGreeter line



sudo apt-get install vnc4server xinetd
sudo vncpasswd /root/.vncpasswd
sudo vi /etc/xinetd.d/Xvnc
```
service Xvnc
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
    port = 5901
}
```
sudo /etc/init.d/xinetd stop

sudo /etc/init.d/xinetd start
vncviewer localhost:1

Now if i try to connect i got the password promt and can log in but i only get a gray screen and cant do anything in it.

As for [COLOR="DarkOrange"]~/.vnc/xstartup[/COLOR] I dont have the folder nor the file on my box.

And Xvnc doesnt seem to run because when i do "sudo killall Xvnc" I get the massage  "no process killed"

I hope that this information can help sort this issue out.

Thank you.

---

### Post by fakie_flip on 2007-05-13
> **ati said:**
> This is what i did so fahr:

As for [COLOR="DarkOrange"]~/.vnc/xstartup[/COLOR] I dont have the folder nor the file on my box.

And Xvnc doesnt seem to run because when i do "sudo killall Xvnc" I get the massage  "no process killed"

I hope that this information can help sort this issue out.

Thank you.

So create a ~/.vnc/xstartup. Google on how to do it. That is why you see a xterm window only. You don't have to kill a process to see if it is running. Try this instead.

```
ps -ef | grep -i vnc
```

Since you told it to run on port 5901, you need to connect like this.

```
vncviewer 127.0.0.1:5901
```

---

### Post by ati on 2007-05-13
It is finaly working! :lolflag: 

Thank you very much!

---

### Post by gio68 on 2007-05-14
> **ati said:**
> It is finaly working! :lolflag: 

Thank you very much!

Hi, I'm new on Ubuntu, can you explain me how have you resolved?
Thanks

---

### Post by fakie_flip on 2007-05-14
The instructions are already there. Read the posts.

---

