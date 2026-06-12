---
title: "Remote GUI from Windows?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Bios___ on 2006-07-15
Is it possible?

Is it possible to have a windows Xp machine, display the GUI of Ubuntu, that which is interactive? Like a sort of remote access from Windows to Ubunutu (5.10).

I have heard of programs like Putty and Telnet, which do similar, but as far as I can tell only display a 'MS-Dos' version of the Ubuntu, if ofcourse that is the version in use (I am assuming thats the server version). 

I am using a Desktop version of Ubuntu as a server (reason being is im an absolute newb at this and require a GUI, but hey atleast im honest)and want to be able to acces the Ubuntu Server from my Windows XP machine with GUI.

Is it possible?

If so, can I ask for the help of the experts who know what im babbling on about please, to direct me on, how to set this 'Remote GUI' up.

Thank you in advance, with regards Bios___.

---

### Post by jimmygoon on 2006-07-15
You want to use Windows to control Ubuntu?

Inside Ubuntu goto
System -> Prefernces -> Remote Desktop

Enable "Allow other users to control desktop" and change whatever settings you want.

Then download UltraVNC Client for windows and connect to the IP address of your Ubuntu PC. (These have to be two different computers obviously)

---

### Post by dtfinch on 2006-07-15
For running single apps I just enable X11 forwarding in Putty and run a windows X server like Xming. Then any GUI apps I run appear in their own windows as though they were running locally. You can also run a full remote desktop, but I haven't felt the urge to do it more than once. It looks like there's XDMCP instructions on the Xming page, or I'm pretty sure you can just run gnome-session manually with Xming in full screen mode. I've heard good things about freenx as well, but I've never looked into it much.

Some good remote server administration tools I'd recommend are webmin for general administration and swat for samba administration.

---

### Post by Lord Illidan on 2006-07-15
VNC or TightVnc are pretty cool. Try them out.

---

### Post by Bios___ on 2006-07-15
errr, im trying out that Ultra VNC, a little help please? So far ive got it installed and am having trouble with trying to connect t the Ubuntu machine, um, help, please :S

---

### Post by Bios___ on 2006-07-15
Also, ive only installed Ultra VNc on the Windows machine, and am unsure as to what UltraVNC-102-bin.zip and UltraVNC-102-src.zip are for. As I said little help please, I know I must sound like a rigth whiney pain in the rectum, but im very much used to Windows, and using Ubuntu and attempting to do remote GUI etc, seems like learning an entirley new language, I do apologize.

---

### Post by jimmygoon on 2006-07-15
On the Ubuntu machine do these steps:

Alt+F2
Type "gnome-terminal"
Type "ifconfig"

Paste results here. Thanks.

---

### Post by Bios___ on 2006-07-15
> user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:FC:A0:0C:8E
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fea0:c8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66035 (64.4 KiB)  TX bytes:12191 (11.9 KiB)
          Interrupt:9 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1893722 (1.8 MiB)  TX bytes:1893722 (1.8 MiB)

user@ubuntu:~$



Hope that helps. Thanks.

---

### Post by x64Jimbo on 2006-07-15
Don't you think Bios would be better off running x11vnc? It's the closest thing you can get to the Windows version of VNC that connects you to whatever desktop is running, not a new session like tightvnc and realvnc do.

---

### Post by jimmygoon on 2006-07-15
> **x64Jimbo said:**
> Don't you think Bios would be better off running x11vnc? It's the closest thing you can get to the Windows version of VNC that connects you to whatever desktop is running, not a new session like tightvnc and realvnc do.

x11vnc is a (vnc) server right? If so why would he use that when Ubuntu has a VNC server built in ... (that I had him enable)

Bios: goto your windows pc and open up the UltraVNC client and where it says host, type in 192.168.0.10

Tell me what happens!

---

### Post by Oler1s on 2006-07-15
> **Bios___ said:**
> Also, ive only installed Ultra VNc on the Windows machine, and am unsure as to what UltraVNC-102-bin.zip and UltraVNC-102-src.zip are for.

The -src.zip file is the source code of the VNC program. You don't want it.

The -bin.zip is the source compiled into a binary, meaning ready to use by your computer. You want that.

---

### Post by jrleighton on 2006-07-17
JimmyGoon says that Ubuntu has a vnc server built in.  Great...but sorry for being a dimwit....how do I access it ?   A friend of mine  who helped me set up my Ubuntu box uninstalled a lot of the default apps on Ubuntu as I was getting confused with so much choice (you can tell that I am a windows user making the transfer).

So, given that I may have the appropriate vnc server software uninstalled, what should I install (with synaptic package manager) ?

Thanks vm for the help.

PS I have also installed another couple of vnc server programs, but I really am looking for something with a GUI if poss (I am an old man, and getting this far with this new stuff really saps my limited brain power)  Thanks !!!

---

### Post by Bios___ on 2006-07-17
> **jimmygoon said:**
> You want to use Windows to control Ubuntu?

Inside Ubuntu goto
System -> Prefernces -> Remote Desktop

Enable "Allow other users to control desktop" and change whatever settings you want.

Then download UltraVNC Client for windows and connect to the IP address of your Ubuntu PC. (These have to be two different computers obviously)

That is the VNC server, allow that and the server is setup, all you need is the ip of the machine of which to connect to.

And the link for Ultra VNC, which I recommend using as it is excellent is below.

[I am a link, click me]("http://sourceforge.net/project/showfiles.php?group_id=63887&package_id=60914&release_id=428901")

---

### Post by x64Jimbo on 2006-07-17
> **jimmygoon said:**
> x11vnc is a (vnc) server right? If so why would he use that when Ubuntu has a VNC server built in ... (that I had him enable)

Bios: goto your windows pc and open up the UltraVNC client and where it says host, type in 192.168.0.10

Tell me what happens!
Yes, but doesn't regular-old VNC have you start a new desktop session when you log in? I have been using x11vnc so that I can see whatever is on the desktop. It allows me to share the session with whoever is sitting at the physical terminal. If the built-in VNC is capable of doing this now, there are still other nice reasons to use x11vnc - 
> 
It has built-in [SSL]("http://www.karlrunge.com/x11vnc/#faq-ssl-tunnel-int") encryption and authentication, UNIX [account and password]("http://www.karlrunge.com/x11vnc/#faq-userlogin") support, server-side [scaling]("http://www.karlrunge.com/x11vnc/#faq-scaling"), [single port]("http://www.karlrunge.com/x11vnc/#faq-ssl-tunnel-viewers") HTTPS and VNC, and TightVNC and UltraVNC [file-transfer]("http://www.karlrunge.com/x11vnc/#faq-filexfer"). It has also been extended to work with [webcams and TV tuner]("http://www.karlrunge.com/x11vnc/#faq-video") capture devices.


---

### Post by mayamaniac on 2006-07-18
x64Jimbo,

I just did a sudo apt-get install x11-vnc, now how do I use it? Is there a GUI?

---

### Post by jrleighton on 2006-07-18
x11vnc works perfectly for me. Just need to add an appropriate menu item with the relevant command, and it's one click to start up the vnc server (having set my password as per the terminal instructions beforehand).  Thanks guys for all the help.

---

### Post by x64Jimbo on 2006-07-18
> **mayamaniac said:**
> x64Jimbo,

I just did a sudo apt-get install x11-vnc, now how do I use it? Is there a GUI?
If you visit the x11vnc site, there are some pretty detailed instructions about how to configure it.
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

---

### Post by Sgurd on 2006-10-04
X11vnc has been suggested, but that's the server side, correct?

Second, I just tried UltraVNC got "screen loading" forever.  I disconencted and tried again and all I get is "Password Accepted", 0 bytes sent, 0 received, no screen. 

Update:
Tried TightVNC - similar situation: Password accepted, then nothing. 

Pardon the newbishness; had "Ask you for confirmation" checked on the host. I'm guessin' it'll work fine now. - JD

---

### Post by x64Jimbo on 2006-10-04
Yep, that'll do it ;)

---

