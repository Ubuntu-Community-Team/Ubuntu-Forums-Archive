---
title: "Remote Desktop"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by lauch on 2006-06-09
At work, we use Exceed to remotely connect to Unix/Linux servers.   We log into the terminal and then use "export DISPLAY="...   Is this how it can be done with VNC viewers?  I tried tightVNC, but it just seems to be like netmeeting for Windows.   

I guess what I'm looking for is to be able to access ubuntu programs on my windows PC and have all the output (sound, display..etc) go to the windows box.   

1. Can I use TightVNC in coordination with the "export DISPLAY" command to bring up X windows like I do at work with Exceed?

2. Can you output sound to the local box when connected remotely via tightVNC or another viewer?

---

### Post by steve.horsley on 2006-06-09
VNC is really for exporting entire desktops - the applications open windows on the desktop (which runs on the server) and VNC transmits the desktop bitmap image back to the remote user. The remote user only sees one window with multiple application windows inside it.

On the other hand, X (as you are probably used to with exceed) exports a separate window for each application to the remote user (where they all get shown inside the Exceed window).

It looks like vino is the package Ubuntu supply for the server. Look for the setup wizard in System->Preferences->Remote Desktop. The VNC server will let other computers connect and see your current desktop, move your mouse and type on your keyboard.  This is very-much a remote-control way of doing things as you might use to help out users who aren't sure what to do.

There is also a vnc4server package. This runs a vnc server that creates a new login and invisible desktop session for you when you connect to it. A user sitting in front of the server wouldn't see anything happening on their screen. The remote user would see an entire desktop with its own icons and application windows inside it.

So you see, VNC is very different to remote X as you would do it with Exceed. You can of course use Exceed to display remote X apps running on Linux, but you need to install an ssh server or (ugh - security?) telnet server on Ubuntu so that the Exceed user can log into a command prompt and launch the applications. The command **ssh -X hostname** has the advantage of automatically setting up an encrypted tunnel back to the caller for the X traffic so that you don't have to fanny around with manual **export DISPLAY...** commands. But I don't know if Exceed can automatically log in using ssh from an icon click - it's been years since I used Exceed.

---

### Post by dglock on 2006-06-10
Where in ubuntu is the remote desktop viewer?

  I want to be able to view and control the other computers on my lan. In kubuntu it is in the internet menu, I can not find it in ubuntu!

  thanks
don

---

### Post by itbkmjs on 2006-06-14
hello there!!

i hope that this time i can get help that i have been trying to get for the past month without any luck.:confused: 

the scenario:

i am working at a IT helpdesk in the university and we always use netmeeting to fix other client's pc's through remote desktop sharing.  and our network is 95% windows and 5% linux and based on novell.  so i want to use a linux pc at the office to netmeet with windows pc's and do remote desktop sharing.

is this possible?? if so.. how?

last time i was told to install :rolleyes:  speex codec on a windows pc and it will work, but i have downloaded the codec and i can't install it because it has a *.patch extension and i do not know which program to use to open it.

please help as this will "maybe" increase linux usage on the network and we can get more linux geeks.

thanx

kagiso sephiphi- potchefstroom
[email]itbkmjs@puk.ac.za[/email]
+27731923629 / +27182992145:D

---

### Post by killernurd on 2006-06-14
There *is* a Windows Remote Desktop-compatible client available for Ubuntu, as part of the standard GNOME desktop (at least, it was there last I checked). It ought to be in the Internet submenu, and it will likely be labelled as 'Terminal Server Client' or something similar.

As for Speex, there are Windows binaries available direct from the project; here's a link to the page:
[http://speex.org/download.html](http://speex.org/download.html)

and here's a direct link to the codec for Windows:
[http://downloads.us.xiph.org/releases/speex/speex_win32_1.0.4_setup.exe](http://downloads.us.xiph.org/releases/speex/speex_win32_1.0.4_setup.exe)

I don't know about the Speex codec business, but I do know that RDP has support in the Ubuntu world.

---

### Post by killernurd on 2006-06-14
Slight shift in direction... I actually want to go the other way.

I'm not interested in VNC because it's ridiculously slow over the network I need to use, so I was looking into the world of RDP *from* Windows *to* Ubuntu. I know that it's possible to connect remotely to a Fedora machine using the Windows Remote Desktop Client (having done this in the past), but I've never set it up myself, and so far I haven't found a useful resource to go by.

Cheers!

---

### Post by killernurd on 2006-06-14
itbkmjs: just remembered that if you can't find it in the main menu, you can always enter rdesktop on a command line.

---

### Post by johnthejack on 2006-06-14
I want to have the Ubuntu as server and view it on a windows machine. I have UltraVnc on the Windows machine. I have gone system/preferences/remote desktop and ticked for sharing. I open the UltraVnc viewer in Windows and get "failed to get server address". Does anyone know what I need to do please?

---

### Post by Triad773 on 2006-06-14
That sounds like something I would like to know too. My Ubuntu machine is in a place where I do not like spending a lot of time (namely, my basement). If there were a way to administrate that from the comfort of other areas that'd be ideal. Is there a client available somewherre for Ubuntu?

Good thread :)

---

### Post by masinger53 on 2006-06-14
I just got vpn functioning and launched remote desktop to view my desktop at work -- wuwu, finally!   Using pptp-linux & pptpconfig tool for the tunnel and the remote desktop client on a recent install of Xubuntu Dapper on my laptop to drive my WinXP Pro workstation remotely.

Have 1 problem to resolve -- can't resize the window that the remote desktop client runs in and it is a tiny one, which turns my 21" desktop at work into a really humorous little square.

I've done both VNC and FreeNX both ways in the past, but the Ops folken frown on too many customizations at work, so I needed to get to it from my Linux box with no changes on the work end.  

For what it's worth, I had some trouble initially getting the pptp stuff installed and configured properly for the vpn.  I ended up removing vpnc completely and removing and reinstalling pptp-linux and pptpconfig and for whatever reason, it worked this time.

Sorry for the long-windedness, but if anyone has any tips for the rdesktop windows resize issue, I'd appreciate it.

Thanks,
M.A.

---

### Post by Soarer on 2006-06-15
I use rdesktop to an XP (work) machine on my LAN all the time. The second tab (display) lets you set the size of the window. Also, ctrl-alt-enter will toggle  full screen on & off. 

I can't get sound to stay at the XP machine, though, depite following M$'s instructions. It just shows the RDP drivers, not the XP machine's one's. rdesktop works fine though, and seems rock solid.

---

### Post by johnthejack on 2006-06-15
Any chance you could give me some ideas, please? I can't get it to work. Under Remote Desktop Preferences I have enabled sharing. I try to connect using UltraVnc from my Windows machine and it says failed to get server address. I pinged and that worked fine so there is a possible connection. I also typed netstat in a terminal and the Ubuntu is listening on 5900. I can't think of anything else to try. It may be something really simple, as I'm a complete starter. Any ideas would be welcome, thanks.

---

### Post by Soarer on 2006-06-15
Hi johnthejack - I think there are two threads in one here  - connecting to and from Windows. They are different because Windows has the RDP server built-in, so as long as its enabled, you can connect TO a Windows machine from another Windows or Ubuntu machine (using rdesktop from Ubuntu).

To connect FROM windows TO Ubuntu you have to be running the server component of VNC on the Ubuntu box. It is not installed by default. You will need to install vnc4server through Synaptic on the Ubuntu box & make sure its started.

UltraVNC is a Windows-only implementation of VNC - it MAY work as a client to Ubuntu vnc4server, but I haven't tried it.

Finally, if your DNS/NIS is not properly set-up, you may need to use the IP address of the server machine for connection, rather than the machine name.

Hope this helps - it took me ages to get FreeNX working so I know how frustrating it can be. For me, though, VNC 'just worked' :).

---

### Post by johnthejack on 2006-06-15
Fantastic. Thanks. I was pretty sure I had installed vcn4server, but I ran a search for vcn in synaptic, downloaded and installed everything I could see which looked possibly connected. I still couldn't connect, but then I typed in the IP address and that worked a treat. Thank you.

---

### Post by Soarer on 2006-06-16
You're welcome. Glad it works for you :).

You could put the server name & IP address in your Windows 'HOSTS' file if its a static IP - if not you'll have to get DNS working properly as I am struggling to do :(

---

### Post by nightofnih on 2006-06-16
[QUOTE=masinger53]I just got vpn functioning and launched remote desktop to view my desktop at work -- wuwu, finally!   Using pptp-linux & pptpconfig tool for the tunnel and the remote desktop client on a recent install of Xubuntu Dapper on my laptop to drive my WinXP Pro workstation remotely.

Have 1 problem to resolve -- can't resize the window that the remote desktop client runs in and it is a tiny one, which turns my 21" desktop at work into a really humorous little square.

...
[/QUOTE]

I have the same setup and it works great. I am using Gnome-RDP which is the GUI front end for configuring different remote destop configurations. In  it you can specify the "Remote Desktop Size" in the RDP tab when you are editing the properties of a profile. You can install Gnome RDP by installing the "gnome-rdp" package through synaptic or apt-get. Then it should be available through the "Internet" menu.

---

### Post by enyaw on 2006-06-16
[QUOTE=steve.horsley]VNC is really for exporting entire desktops - the applications open windows on the desktop (which runs on the server) and VNC transmits the desktop bitmap image back to the remote user. The remote user only sees one window with multiple application windows inside it.

On the other hand, X (as you are probably used to with exceed) exports a separate window for each application to the remote user (where they all get shown inside the Exceed window).

It looks like vino is the package Ubuntu supply for the server. Look for the setup wizard in System->Preferences->Remote Desktop. The VNC server will let other computers connect and see your current desktop, move your mouse and type on your keyboard.  This is very-much a remote-control way of doing things as you might use to help out users who aren't sure what to do.

There is also a vnc4server package. This runs a vnc server that creates a new login and invisible desktop session for you when you connect to it. A user sitting in front of the server wouldn't see anything happening on their screen. The remote user would see an entire desktop with its own icons and application windows inside it.

So you see, VNC is very different to remote X as you would do it with Exceed. You can of course use Exceed to display remote X apps running on Linux, but you need to install an ssh server or (ugh - security?) telnet server on Ubuntu so that the Exceed user can log into a command prompt and launch the applications. The command **ssh -X hostname** has the advantage of automatically setting up an encrypted tunnel back to the caller for the X traffic so that you don't have to fanny around with manual **export DISPLAY...** commands. But I don't know if Exceed can automatically log in using ssh from an icon click - it's been years since I used Exceed.[/QUOTE]

Steve it always reassures me whenever I read such intellegent input as you have presented here.  I always enjoy hearing from our British cousins.  Thank you;  I needed this info.:D

---

