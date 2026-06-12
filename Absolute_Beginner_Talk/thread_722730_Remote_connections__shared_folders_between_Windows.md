---
title: "Remote connections / shared folders between Windows Vista and Ubuntu 7.10"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by burnt_sky on 2008-03-12
Hey,

This is going to be a reasonable-sized post as I'm new to Linux and want to make sure I explain my problem properly :). Because of this I'm going to start with my issues:

1.  I can remote onto my linux machine from a laptop runing vista, but not vica versa.

2. I can access shared files on the vista machine from ubuntu, but can't access shared files on the linux machine from vista.

:confused::confused::confused::confused:

So, to fill you in: 

I installed Ubuntu 7.10 about three days ago to try it out since I was lucky enough to have a machine available. Very impressed so far! My wife has a laptop running windows vista home premium, and I have some experience with windows desktops and servers but no experience with any linux distro. What I want to be able to do is (from Ubuntu) access shared folders on windows and remote onto the windows desktop. I also want to be able to do this the other way around. What I've done is this:

I have enabled remote connections on both ubuntu and vista.

I have installed TightVNC on both machines.

I have shared folders on the windows machine (and set the relevant permissions), and I *think* I've done the same for the folders on ubuntu.

Looking in the network folders on both machines, they can see each other. 

I have not installed Samba (as I don't think it's needed?), but the relevant service is running.

One thing that is confusing me is that I installed TightVNC using Synaptic, but now can't seem to find it in any menu (even using alacarte). Do I need to run something on the terminal?

Also, does anyone know of a useful comparison of windows command line and linux terminal commands?


Sorry for the long post, thanks for reading if you got this far!

---

### Post by SpaceTeddy on 2008-03-12
first off, i must mention that i have been wrong on things before, and that i am very much a command line fan - therefore my answers might not be what you are looking for :)

> **burnt_sky said:**
> 1.  I can remote onto my linux machine from a laptop runing vista, but not vica versa.
what programm are you trying to use when accessing the ubuntu via remote desktop ? (which one are you running on the vista to connect). Also, can you please open a terminal in ubuntu and post the output of the following command
```
netstat -lnp |grep LISTEN
```
this will list all services that are listening on the network. It will show if your vnc server is running and what port it is listening on.

> **burnt_sky said:**
> 2. I can access shared files on the vista machine from ubuntu, but can't access shared files on the linux machine from vista.
Accessing Windos shares from ubuntu to vista is done via smbclient and smbfs. This is a standard part of ubuntu and is automaticially installed. If you want your ubuntu computer to also have shares that the vista can access, you will need the full grown samba server  on your ubuntu machine, since that one is acctually handling the shares. If you want to know how to configure it, [this]("http://ubuntuforums.org/showthread.php?t=708002") thread is describing it (there is a sample configuration in there too) - that ought to get you started. 
I know of no other way to create windows shares than installing samba.

hopefully this helps to get you started
PS: nice that you explained what you want - most people do not do that :)

---

### Post by burnt_sky on 2008-03-12
SpaceTeddy:

Thanks for the heads up regarding Samba - I thought running the service would be enough, but obviously not!!!

With the remote desktop connections, I'm using TightVNC on the vista machine to access ubuntu (which works, although vista's native Remote Desktop Connection doesn't!). I've also installed TightVNC on ubuntu.

Running netstat -lnp |grep LISTEN (not as root user) gives me this output (really sorry, but since I'm not sure what's relevant and what's not, it's all here!):

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:58144           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:36194           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:6543            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:6544            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:35635           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     -                   
tcp6       0      0 :::5900                 :::*                    LISTEN     5614/vino-server    
unix  2      [ ACC ]     STREAM     LISTENING     14051    -                   @/tmp/dbus-s8msymUUY2
unix  2      [ ACC ]     STREAM     LISTENING     14068    -                   @/var/run/hald/dbus-1UmEjXaZSV
unix  2      [ ACC ]     STREAM     LISTENING     16231    -                   /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     16823    5587/dbus-daemon    @/tmp/dbus-zSFZeht5Dy
unix  2      [ ACC ]     STREAM     LISTENING     13992    -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     13739    -                   /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     16050    -                   /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     14071    -                   @/var/run/hald/dbus-W0lmtX6kLZ
unix  2      [ ACC ]     STREAM     LISTENING     16292    -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     16731    5543/gnome-keyring- /tmp/keyring-qUx0T9/socket
unix  2      [ ACC ]     STREAM     LISTENING     16812    -                   /tmp/ssh-SyqnUD5546/agent.5546
unix  2      [ ACC ]     STREAM     LISTENING     16842    5589/gconfd-2       /tmp/orbit-chris/linc-15d5-0-77242dea4d431
unix  2      [ ACC ]     STREAM     LISTENING     16852    5546/x-session-mana /tmp/orbit-chris/linc-15aa-0-31ee1b3e62171
unix  2      [ ACC ]     STREAM     LISTENING     17110    5546/x-session-mana /tmp/.ICE-unix/5546
unix  2      [ ACC ]     STREAM     LISTENING     17133    5593/gnome-settings /tmp/orbit-chris/linc-15d9-0-19c959586a1f2
unix  2      [ ACC ]     STREAM     LISTENING     17222    5618/gnome-screensa /tmp/orbit-chris/linc-15e5-0-38e59a96120f5
unix  2      [ ACC ]     STREAM     LISTENING     17226    5600/bonobo-activat /tmp/orbit-chris/linc-15e0-0-1bc54768151c3
unix  2      [ ACC ]     STREAM     LISTENING     17306    5614/vino-server    /tmp/orbit-chris/linc-15ee-0-111561337eb29
unix  2      [ ACC ]     STREAM     LISTENING     17318    5626/gnome-volume-m /tmp/orbit-chris/linc-15f4-0-7dad4faf82897
unix  2      [ ACC ]     STREAM     LISTENING     17342    5616/gnome-panel    /tmp/orbit-chris/linc-15f0-0-7dad4fafa00ac
unix  2      [ ACC ]     STREAM     LISTENING     15326    -                   /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     17357    5619/nautilus       /tmp/orbit-chris/linc-15f3-0-7dad4fafb9a7e
unix  2      [ ACC ]     STREAM     LISTENING     17417    5638/trashapplet    /tmp/orbit-chris/linc-1606-0-6f8175f05b1fb
unix  2      [ ACC ]     STREAM     LISTENING     17383    5628/gnome-vfs-daem /tmp/orbit-chris/linc-15fc-0-130c1a63ea067
unix  2      [ ACC ]     STREAM     LISTENING     17522    5704/mapping-daemon /tmp/mapping-chris
unix  2      [ ACC ]     STREAM     LISTENING     17576    5735/bluetooth-appl /tmp/orbit-chris/linc-1667-0-43aa59834d3b3
unix  2      [ ACC ]     STREAM     LISTENING     17658    5732/gtk-window-dec /tmp/orbit-chris/linc-1664-0-5dc686b4f25d8
unix  2      [ ACC ]     STREAM     LISTENING     17717    5734/vino-session   /tmp/orbit-chris/linc-1666-0-3664e5dec5e38
unix  2      [ ACC ]     STREAM     LISTENING     17722    5753/gnome-power-ma /tmp/orbit-chris/linc-166e-0-18197edfcad53
unix  2      [ ACC ]     STREAM     LISTENING     17724    5739/update-notifie /tmp/orbit-chris/linc-166b-0-3664e5decaffb
unix  2      [ ACC ]     STREAM     LISTENING     17743    5750/nm-applet      /tmp/orbit-chris/linc-1676-0-4a5f818ee863f
unix  2      [ ACC ]     STREAM     LISTENING     17771    5733/compiz.real    /tmp/orbit-chris/linc-1665-0-139fd41457936
unix  2      [ ACC ]     STREAM     LISTENING     17790    5741/evolution-alar /tmp/orbit-chris/linc-166d-0-6e0604f72ec2f
unix  2      [ ACC ]     STREAM     LISTENING     17832    5764/evolution-data /tmp/orbit-chris/linc-1684-0-315089465d2f
unix  2      [ ACC ]     STREAM     LISTENING     17881    5769/evolution-exch /tmp/orbit-chris/linc-1689-0-756f0216d899e
unix  2      [ ACC ]     STREAM     LISTENING     17936    5799/mixer_applet2  /tmp/orbit-chris/linc-16a7-0-1fa5ef6014056
unix  2      [ ACC ]     STREAM     LISTENING     17963    5795/fast-user-swit /tmp/orbit-chris/linc-16a3-0-1fa5ef6054a1f
unix  2      [ ACC ]     STREAM     LISTENING     18106    5797/python         /tmp/orbit-chris/linc-16a5-0-4d95ddb94b68d
unix  2      [ ACC ]     STREAM     LISTENING     19025    5812/gnome-terminal /tmp/orbit-chris/linc-16b4-0-1030642ed9ac4


(I realise this probably wasn't what you wanted - I'm using the excuse that I'm new to linux!)

Thanks again for the link to the samba thread - looks like just what I need!

---

### Post by SpaceTeddy on 2008-03-12
the listing looks ok - altought there are a lot of open ports. The standard port for vnc is 5900, the standard port for rdp (remote desktop protocol) is 3389. neither of them are open on your ubuntu machine, which would indicate that the acctual vnc server is not running.

also, please run the command netstat again, this time like this 
```
sudo netstat -lnp |grep "LISTEN "
```

it should now print the appropriate processes along with the ports. and it should be way less :)

As a sidenote, the netstat indicates that the samba server is already runnning on your computer. so you might only need to configure it (ports 137,139 and 445 are samba)

---

### Post by burnt_sky on 2008-03-12
Thanks for this -

There may be a lot of open ports because I was originally installing Mythbuntu, but thought I'd have a look at the desktop environment and got hooked!

The output I get from that command is:

tcp        0      0 0.0.0.0:58144           0.0.0.0:*               LISTEN     3819/rpc.statd      
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:36194           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4607/mysqld         
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4982/smbd           
tcp        0      0 0.0.0.0:6543            0.0.0.0:*               LISTEN     5215/mythbackend    
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3800/portmap        
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     5450/apache2        
tcp        0      0 0.0.0.0:6544            0.0.0.0:*               LISTEN     5215/mythbackend    
tcp        0      0 0.0.0.0:35635           0.0.0.0:*               LISTEN     4894/rpc.mountd     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4982/smbd           
tcp6       0      0 :::5900                 :::*                    LISTEN     5614/vino-server 


From what you mentioned about the default ports, it does look like they aren't open! Would I open them using the terminal?

I know the samba service is running, which is why (I think) I can access windows shared folders - I think you're right, I just need to either configure it or install the rest.

---

### Post by SpaceTeddy on 2008-03-12
i was wrong, the vino server is there - but listeing on the wrong protocol 

tcp6 0 0 :::5900 :::* LISTEN 5614/vino-server

that is the vnc server - but why it is bount to tcp6 (which would be tcp over ipv6) i have no idea. i'll try to do some research later on and get back to you.

as for samba, you should be able to take my config from the other thread and create a share with minimal changed to it.

---

### Post by burnt_sky on 2008-03-12
Many thanks for that SpaceTeddy, I'll definitely be able to configure the samba service with the info in that thread - but I must go to bed now as I have to get up for work in 6 hours!

If you do have the time/inclination and generosity to post again regarding the port that vino is running on then it would be much appreciated, but if not then fully understood!

I shall check back tomorrow and post an update as and when I reach some conclusion!


Thanks again  :)

---

### Post by Windy George on 2008-03-31
Hello Burnt Sky:

I did have the same difficulty.  My Vista system could not see the Ubuntu system but Ubuntu could see the Vista system.  The solution for me came from someone here at this forum.  From the command line in the Vista system enter \\192.168.0.nnn   -   nnn being the IP address of your Ubuntu system.  I am able to share and see either system from the other.  This will not work while a terminal emulator is running on the Vista system. On the Ubuntu system I have an icon for the Vista shared drives on the desktop that returns every time I start Ubuntu.    I have had no luck with a remote Ubuntu desktop running on the Vista system

George

---

