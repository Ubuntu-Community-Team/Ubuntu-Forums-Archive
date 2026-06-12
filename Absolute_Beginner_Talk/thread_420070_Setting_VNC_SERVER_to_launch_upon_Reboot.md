---
title: "Setting VNC SERVER to launch upon Reboot"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-23
When I remotely reboot my Fiesty box, it doesn't launch the VNC Server when it comes back up.  I have to login locally and then the VNC server starts.  How can I make this start automatically upon reboot?

---

### Post by dannyboy79 on 2007-04-23
how have you configured your vnc server? if you're running it thru xinetd than you need to make sure xinetd is being started at bootup. if you're running it as a daemon, than you need to make sure you enable it for yoru main run level. i think this will do it if you're running it as a daemon.

sudo update-rc.d x11vnc defaults

(NOTE: x11nvc should be replaced by whatever vnc server you're using)

---

### Post by kc5hwb on 2007-04-23
I didn't configure it really at all, I installed it thru Synaptic then enabled it in the Administration menu.

---

### Post by dannyboy79 on 2007-04-23
are you using dapper, edgy, or feisty? are you just saying that you enabled the XDMCP thru the login screen? tell me what these commands return

netstat -pant

sudo find / -name *vnc*

---

### Post by kc5hwb on 2007-04-23
Fiesty AMD 64 version

netstat -pant

```
jason@samson:~$ netstat -pant
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     -                   
tcp6       0      0 :::5900                 :::*                    LISTEN     8298/vino-server    
tcp6       0     79 ::ffff:10.10.10.86:5900 ::ffff:208.54.14.:20200 ESTABLISHED8298/vino-server  
```


sudo find / name *vnc*


```
  
jason@samson:~$ sudo find / -name *vnc*
Password:
/etc/alternatives/Xvnc
/etc/alternatives/x0vncserver.1.gz
/etc/alternatives/vncviewer
/etc/alternatives/vncconfig.1.gz
/etc/alternatives/Xvnc.1.gz
/etc/alternatives/xvncviewer
/etc/alternatives/vncviewer.1.gz
/etc/alternatives/x0vncserver
/etc/alternatives/vncconfig
/etc/alternatives/vncserver.1.gz
/etc/alternatives/vncpasswd.1.gz
/etc/alternatives/xvncviewer.1.gz
/etc/alternatives/vncserver
/etc/alternatives/vncpasswd
/etc/X11/app-defaults/Xvncviewer
/etc/vnc.conf
/usr/bin/Xvnc
/usr/bin/vnc4passwd
/usr/bin/xrealvncviewer
/usr/bin/vncviewer
/usr/bin/realvncpasswd
/usr/bin/xvncviewer
/usr/bin/realvncpasswd.real
/usr/bin/x0vncserver
/usr/bin/vncconfig
/usr/bin/x0vnc4server
/usr/bin/vnc4server
/usr/bin/vncserver
/usr/bin/vnc4config
/usr/bin/vncpasswd
/usr/bin/Xvnc4
/usr/lib/xorg/modules/extensions/libvnc.so
/usr/share/man/man1/vnc4passwd.1.gz
/usr/share/man/man1/Xvnc4.1.gz
/usr/share/man/man1/x0vncserver.1.gz
/usr/share/man/man1/vncconfig.1.gz
/usr/share/man/man1/vnc4config.1.gz
/usr/share/man/man1/Xvnc.1.gz
/usr/share/man/man1/vncviewer.1.gz
/usr/share/man/man1/realvncpasswd.1.gz
/usr/share/man/man1/vncserver.1.gz
/usr/share/man/man1/vncpasswd.1.gz
/usr/share/man/man1/xrealvncviewer.1.gz
/usr/share/man/man1/realvncpasswd.real.1.gz
/usr/share/man/man1/xvncviewer.1.gz
/usr/share/man/man1/x0vnc4server.1.gz
/usr/share/man/man1/vnc4server.1.gz
/usr/share/man/man5/vnc.conf.5x.gz
/usr/share/doc-base/vnc
/usr/share/doc/vnc4-common
/usr/share/doc/vnc4-common/examples/vnc.conf.gz
/usr/share/doc/xvncviewer
/usr/share/doc/xvncviewer/examples/vncviewer
/usr/share/doc/vnc-common
/usr/share/doc/vnc4server
/usr/share/menu/xvncviewer
/usr/share/omf/vnc
/usr/share/omf/vnc/vnc-C.omf
/var/lib/doc-base/info/vnc.status
/var/lib/doc-base/info/vnc.list
/var/lib/dpkg/alternatives/Xvnc
/var/lib/dpkg/alternatives/vncviewer
/var/lib/dpkg/alternatives/x0vncserver
/var/lib/dpkg/alternatives/vncconfig
/var/lib/dpkg/alternatives/vncserver
/var/lib/dpkg/alternatives/vncpasswd
/var/lib/dpkg/info/vnc-common.list
/var/lib/dpkg/info/vnc4-common.prerm
/var/lib/dpkg/info/vnc4-common.md5sums
/var/lib/dpkg/info/xvncviewer.prerm
/var/lib/dpkg/info/vnc-common.prerm
/var/lib/dpkg/info/vnc-common.postinst
/var/lib/dpkg/info/xvncviewer.preinst
/var/lib/dpkg/info/vnc4-common.postinst
/var/lib/dpkg/info/xvncviewer.conffiles
/var/lib/dpkg/info/vnc-common.md5sums
/var/lib/dpkg/info/vnc-common.conffiles
/var/lib/dpkg/info/vnc4server.list
/var/lib/dpkg/info/vnc4-common.list
/var/lib/dpkg/info/vnc4server.postinst
/var/lib/dpkg/info/vnc4server.prerm
/var/lib/dpkg/info/xvncviewer.postinst
/var/lib/dpkg/info/xvncviewer.md5sums
/var/lib/dpkg/info/xvncviewer.list
/var/lib/dpkg/info/xvncviewer.postrm
/var/lib/dpkg/info/vnc4server.md5sums
/var/cache/apt/archives/vnc4server_4.1.1+xorg1.0.2-0ubuntu4_amd64.deb
/var/cache/apt/archives/vnc4-common_4.1.1+xorg1.0.2-0ubuntu4_amd64.deb

```

---

### Post by dannyboy79 on 2007-04-23
i meant that I wanted you to show me netstat immediately after you bootup. so what command are you using to envoke your vncserver?

---

### Post by kc5hwb on 2007-04-23
I am not at home right now, I am doing all of this remotely.  But I do not use a command to invoke the VNC Server.  It launches automatically when I login to X

---

### Post by dannyboy79 on 2007-04-23
ok then I am obviously not understanding what the problem is here? you stated that your vnc server wasn't starting at bootup, now you're saying that it does start when you login? so are you saying that you'd like to be able to have your machine sitting at home with no one logged in and you'd like to be able to login remotely? if that's the case than you need to enable XDMCP. that's under the login options under remote desktop. otherwise I have no idea what you're trying to accomplish. please explain better.

---

### Post by kc5hwb on 2007-04-23
ok.......... VNC server runs automatically when I login to X on the LOCAL machine while sitting in front of it at home.  I can then go to work, VNC into the machine from my laptop here and all is well.  However, if there is ever a need for a REBOOT, the box shuts down and restarts like it normally should.  It ends up back at the Gnome login screen after launching X automatically on bootup.  I cannot SEE this screen remotely because it doesn't LAUNCH VNC SERVER until I physically sit down at the machine and login locally.  THEN I can VNC into it again.  Obviously, this is a problem if I am at work all day, using the box, and ever need to reboot because I can't login locally from work.

---

### Post by dannyboy79 on 2007-04-23
it sounds like you want to be able to login remotely. just do as I said or setup the box to login automatically.

Ok, this is going to be very long. This article is posted at Linux Magazine and I can't just link to it because you need to register. It's free so if you want to register it's here: [http://www.linux-mag.com/id/1311/](http://www.linux-mag.com/id/1311/)
otherwise here ya go.

To use XDMCP with VNC, your XDMCP server must accept connection attempts from the local computer. Ordinarily, the XDMCP server doesn't accept such connections. It just manages the local X display. Precisely how you do this depends upon the XDMCP server your system runs. If you're not sure which XDMCP server your system uses, type ps ax | grep dm and examine the output for one of the XDMCP server names. Of course, the XDMCP server must be running for this to work, and that's only likely to be true if your system is configured for GUI logins. On most distributions, setting the system to use runlevel 5 will do this. Type telinit 5 to enter runlevel 5 until you reboot or change it manually. You can also edit /etc/inittab and change the number in the id line to 5 to change the runlevel permanently.

The simplest XDMCP server to reconfigure is GDM, which is the default for Red Hat and some other distributions. Open /etc/X11/gdm/gdm.conf in your favorite editor and locate the [xdmcp] section. Change the line that reads enable=false to enable=true. This line reconfigures GDM to function as a network-enabled XDMCP server and to accept remote login requests. If you prefer, you can use the gdmsetup program to edit gdm.conf. Click the "XDMCP" tab and check the "Enable XDMCP" box.

XDM's configuration files usually reside in /etc/X11/xdm, and some versions of KDM use those files as well. More recent versions of KDM use similar files in another directory, typically /etc/kde2/kdm, /opt/kde/share/config/kdm, or something similar. 

For both KDM and XDM, one critical file is Xaccess. The Xaccess file controls who can access the XDMCP server. For the configuration described here, a line that reads localhost should do the job. To open the XDMCP server to any remote system, * works. (Note that the XDMCP server program doesn't need to accept remote connections for remote, VNC-mediated logins to work -- it's only the VNC server program that needs to accept such access.)

XDM's main server options are set in a file called xdm-config. To have the server listen for connection requests from a VNC X server or other computers, you must tell it to listen to port 177 with a line like this:

DisplayManager.requestPort: 177
The default configuration on most systems substitutes 0 for 177, which keeps the server from listening for connection requests. In recent versions of KDM, the same task is accomplished through a line that reads Enable=true in the kdmrc file. 

Whatever XDMCP server you use, it's a good idea to implement firewall rules to keep unwanted individuals out. This is particularly true of GDM, which doesn't include any access control tools akin to XDM or KDM's Xaccess file.

For instance, to let only localhost access the XDMCP port, you could use rules like this:

# iptables -A INPUT -s 127.0.0.1 -p udp \ --dport 177 -j ACCEPT
# iptables -A INPUT -p udp --dport 177 -j DROP
To make these changes permanent, enter these rules in an appropriate startup or firewall script. 

After you've created the firewall rules and reconfigured the XDMCP server, you must restart the server, or at least pass it a USR1 signal to tell it to reread its configuration file. In either case, you must log out of any active X sessions, so the simplest way to do it is to log out and then restart the XDMCP server. You can do this by typing killall xdm (or whatever the server executable name is). Chances are that X will shut down, and you may need to restart your XDMCP server manually.

At this point, the XDMCP server should be up and running, but you won't be able to make a VNC connection yet. If, after completing the VNC configuration (described in the next section), you can't get it to work, you can try another XDMCP server -- sometimes one will work when another obstinately refuses to function with VNC. 

For instance, KDM doesn't work with VNC under SuSE, although GDM works under SuSE, and KDM works with other distributions. To change the XDMCP server, install a second one and then dig around in your configuration files to change the default. In Red Hat or Mandrake, edit /etc/sysconfig/desktop and add a line that sets the DISPLAYMANAGER variable to GNOME for GDM, to KDE for KDM, or to XDM for XDM. In SuSE, change the DISPLAYMANAGER variable in /etc/sysconfig/displaymanager to gdm, kdm, or xdm. In Debian, place the complete path to the XDMCP server's binary in /etc/X11/default-display-manager.

Launching VNC From a Super Server

Once XDMCP is configured to run, you need to set up VNC. The simplest way to do this is to launch VNC from a super server such as inetd or xinetd). To do that, you must first specify one or more VNC ports in /etc/services:

vnc-800x600    5900/tcp
vnc-1024x768   5901/tcp
If you want to enable multiple VNC logins using multiple virtual resolutions, specify more than one VNC port, as shown immediately above. Port 5900 (the default VNC port) accepts 800x600 logins, while 5901 accepts 1024x786 logins. 

If you only want to support one virtual resolution, you need only one entry. The entry for port 5900 should correspond to whatever you want the default resolution to be. Note that you're not restricted to traditional resolutions, and in fact, using resolutions slightly lower than is normal, such as 950x700 instead of 1024x768, can be useful. Such resolutions leave room for window borders around the VNC client window.

If your system uses xinetd, as Red Hat and Mandrake do, you need to create a file in /etc/xinetd.d corresponding to the new VNC server. You can call this file vnc, and it should include entries like this:

service vnc-800x600
{
  disable     = no
  socket_type = stream
  protocol    = tcp
  wait        = no
  user        = nobody
  server      = /usr/X11R6/bin/Xvnc
  server_args = :1 -inetd -query localhost \
    -geometry 800x600 -depth 24 -once \
    -fp unix/:7100
}
The server_args line is very important, and must be customized for your system. In particular, you should set the -geometry value to whatever resolution you want to use, and -depth to the bit depth. The -fp option is very important: this sets the VNC X server's font path. This example sets the font path to unix/:7100, which is appropriate for a Red Hat system. Consult the FontPath entries in your /etc/X11/XF86Config file and enter all the directories referenced there on this line, separated by commas, such as -fp /usr/fonts,/opt/fonts.

If your system uses inetd, the procedure is similar, but inetd uses a single-line for each of its entries. The inetd equivalent to the preceding xinetd example is:

vnc-800x600 stream tcp nowait nobody \
/usr/sbin/tcpd /usr/X11R6/bin/Xvnc :1 \
-inetd -query localhost -geometry 800x600 \
-depth 24 -once -fp unix/:7100
The line shown above has been split across several lines due to column width constraints -- it should be entered on just one line in /etc/inetd.conf, even if it's longer than 80 columns.

Of course, if you want to support multiple resolutions, you need to create multiple inetd or xinetd entries, one for each resolution. Each entry needs a unique port number reference -- one for vnc-800x600, one for vnc-1024x768 (or whatever names you specified in /etc/services). You should also change the :1 server argument for subsequent entries. This argument sets the local X server display number, which must be unique for each call. You can also implement firewall rules to accomplish the same goal.

If you want to implement restrictions on who may access the VNC server, you can do so using the usual access control tools for your super server -- TCP Wrappers for inetd or xinetd's built-in access control tools. Implementing such restrictions is a very good idea. Without them, anybody who can reach your computer and who has a username and password can log in.

After you've created the super server configuration, you need to restart the super server, or at least pass it a SIGHUP to have it reload its configuration file. Typing killall -HUP inetd or killall -HUP xinetd should do the trick.

---

### Post by dannyboy79 on 2007-04-23
or this thread:

[http://ubuntuforums.org/showthread.php?t=191564&page=2&highlight=xdmcp+vnc](http://ubuntuforums.org/showthread.php?t=191564&page=2&highlight=xdmcp+vnc)

you can just use the "search" function within the ubuntu forums, this is how I found the answer although I'm familar with it, it's a lot of explaining so I'd rather link to it.

---

### Post by Pobega on 2007-04-23
If you want the VNC server to automatically start at boot time, put a symbolic link in the /etc/rcS.d/ folder to the executable: Be sure to start it off with S and then the number you want it to boot up at (The lower numbers are booted first).

So if the executable is /usr/bin/vnc-server, do this:

cd /etc/rcS.d/
sudo ln -s /usr/bin/vnc-server S50vnc-server

Or something similar to that. Make sure to change the number following the S to apply to your system, at whichever point in boot you want it (Preferably after networking)

---

### Post by dannyboy79 on 2007-04-23
i don't think this will work for him. he isn't even logged into the machine so how will his vnc session have all his user's settings and what not. this is not the way to do this. either things that I wrote about are the correct way to enable remote login capablities. plus, how does he pass all the appropriate options thru the command you listed. if his vnc-server normally starts thru the super daemon (xinetd) than he needs to review that and see what options it's being passed thru that file.

I mean Pobega could be right but I don't believe so. why would there be so many write ups about remote desktop login if it was as simple as Pobega is saying?

---

### Post by Pobega on 2007-04-23
> **dannyboy79 said:**
> i don't think this will work for him. he isn't even logged into the machine so how will his vnc session have all his user's settings and what not. this is not the way to do this. either things that I wrote about are the correct way to enable remote login capablities. plus, how does he pass all the appropriate options thru the command you listed. if his vnc-server normally starts thru the super daemon (xinetd) than he needs to review that and see what options it's being passed thru that file.

I mean Pobega could be right but I don't believe so. why would there be so many write ups about remote desktop login if it was as simple as Pobega is saying?

I've never used VNC before, but I just assumed that he wanted to start it at boot time so I told him how to. If he wants to pass arguments to it he'll have to set up a bash script and create a symbolic link to the script instead of directly to the binary.

If you have to pass the "start" parameter to the server at boot time, just create a symbolic link to the /etc/init.d/ script. But don't forget to set up the K script (K50vnc-server) for when it comes time to shutdown.

If he wants to take my advice sure, if not then that's alright too. I'm just telling him how to start something at boot time.

---

### Post by dannyboy79 on 2007-04-23
ok, why give advice when you don't know what you're even telling someone? Are you aware of what exactly he's trying to accomplish? Are you aware of how vnc works? or are you simply taking your knowledge of init and applying without any understanding of the program that he wants started at boot? 

Say someone wanted a terminal window to open upon boot, are you going to tell them to add it to init? No.

---

### Post by kc5hwb on 2007-04-23
I appreciate both of your attempts to help, but does anyone have a PROVEN fix for this?  I did a search and didn't see anything, before I posted this thread.

---

### Post by dannyboy79 on 2007-04-23
i have already provided you the solution. it's not a fix, it's not even a problem. when you tell your machine to restart, it's going to come to gdm since I am assuming you don't have auto-login set. so the only way to actually login to your session thru vnc is to do what I said in either of my solutions. OR change your setup so it auto logs in. the vnc server can't start until you start an x-session otherwise what in the world is it going to show you if you're not logged in??????????

---

### Post by kc5hwb on 2007-04-23
Ok, I just now looked at that link and thats what I was looking for (assuming that it will work with Fiesty, as that link is for Dapper)

---

### Post by dannyboy79 on 2007-04-23
the link is also what I posted referring to the linux magazine article. it deals with allowing remote desktop login thru XDMCP and VNC.

---

### Post by rmfought on 2007-04-24
Here's what I do to get my VNC servers up automatically after boot:

Add lines such as the following to /etc/rc.local

```
su - -c "vncserver :1 -geometry 1680x1050"
su - username -c "vncserver :2 -geometry 1680x1050"
```

The first one starts a vncserver using the root login.  The second one start a vncserver using the "username" login.

This works in Fedora, haven't tried it in Ubuntu though.

---

### Post by Calash on 2007-04-24
I am probably thinking to simple here, but why not just enable automatic login of the account you use?  It is under the Administration menu....login screen I think.  I am at work so my menu names may be a bit off.

---

### Post by dannyboy79 on 2007-04-24
> **Calash said:**
> I am probably thinking to simple here, but why not just enable automatic login of the account you use?  It is under the Administration menu....login screen I think.  I am at work so my menu names may be a bit off.

not to be rude, but if you would have read the previous posts, I have already suggested that,       repeatedly.

---

### Post by etank on 2007-04-24
If I am not mistaken, it looks like the user is trying to use the built in vino-server. I am not aware of a way to start that unless the user is logged in locally.

---

### Post by Calash on 2007-04-24
> **dannyboy79 said:**
> not to be rude, but if you would have read the previous posts, I have already suggested that,       repeatedly.



Twice by my count, but yes you did and I apologize for missing it.

---

### Post by c.dric on 2007-07-19
> **rmfought said:**
> 
```
su - username -c "vncserver :2 -geometry 1680x1050"
```


thanks!

i'm glad i've found this ... exactly what i needed. 
i put it in a script after a sleep 20 to be sure X is already started by then...

---

### Post by MetalMusicAddict on 2007-07-19
I personally put **x11vnc -forever** in my Session manager. Works perfect for me.

---

### Post by c.dric on 2007-07-20
> **MetalMusicAddict said:**
> I personally put **x11vnc -forever** in my Session manager. Works perfect for me.

that's another way ... but in that case you need to start a session for the vnc server to start.
i'm using vnc to use a linux app that's not available on osx so it has to work even when noone has started a session on the server.

---

### Post by MetalMusicAddict on 2007-07-20
> **c.dric said:**
> that's another way ... but in that case you need to start a session for the vnc server to start.

Yes. My box auto-logs in. So the session starts once the user is logged in.

---

### Post by kc5hwb on 2007-07-20
My original question was how to make VNC server launch WITHOUT logging in remotely.  I see the answer to that on the first page, but it seems like a long, drawn-out process just to get a server to launch before login.

No, I don't want to have it login automatically

---

