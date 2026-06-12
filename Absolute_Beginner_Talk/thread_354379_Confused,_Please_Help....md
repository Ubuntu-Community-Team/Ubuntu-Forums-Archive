---
title: "Confused, Please Help..."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by orcalover on 2007-02-05
Okay, I've been at this for the last 48 hours and I'm no closer to getting Ubuntu setup than I was when I started, I'm just more confused. 

I've managed to get Ubuntu desktop installed, but I'm unable to get a web server or home network setup. I don't understand the DHCP settings or the network connections configuration. 

My Internet provider only provides me with a dynamic ip address, so I use DynDns.org to get around this. I have two nic cards in my computer, one goes to a router "linksys WRT54GP2" and the other goes to a switch. I have the router setup to act as a local DHCP server. From everything that I've read so far, it seems that I'm supposed to disable the DHCP server in the router and install DHCP3-Server on the Ubuntu server. However, when I try to disable the DHCP in the router, I lose my connection to the internet and nothing I do in Ubuntu seems to remedy this. 

On a related matter, I have a Samsung laser printer that I need to setup, but it only has an ethernet connection (it's connected to the switch). The CD has a linux driver, but it won't seem to run in Ubuntu. I've been told that I need to assign the printer an IP address in order to install it, but I can't do that unless I have the DHCP3-Server setup in Ubuntu - which now gives me two DHCP servers. 

And, of course, I can't setup Ubuntu as the LAN network server without it having DHCP, so I'm at a complete loss here. Am I misunderstanding something here? 

Should I have two DHCP servers running (though, I've tried this as well to no avail) or do I need to configure something so that I can turn off the DHCP in the router and still have internet. 

Please help me, I'm nearly pulling out my hair. 

Sean

---

### Post by shareMenaPeace on 2007-02-05
For each diffrent problem run a search on the forum like


"nvidia 1313" look for how to/guides. If you cant find something search on google.com - maybe add a "ubuntu" or "debian" to the search query.

If this dindt help start a topic single for 1 problem at a time. This makes it easyer to help you.

---

### Post by banditti on 2007-02-05
I am really confused why you would do that.  Most people go:  Internet ==> Router ==> Switch ==> Computers.  Router handles DHCP.  What am I missing?

---

### Post by orcalover on 2007-02-06
> **banditti said:**
> I am really confused why you would do that.  Most people go:  Internet ==> Router ==> Switch ==> Computers.  Router handles DHCP.  What am I missing?

Well, perhaps your are correct. I'm still in the "windows" mindset, so this may be the problem, but it just doesn't seem like it would work. With the Windows server, we had to have the server setup this way (router -> server -> switch). 

If all the computers, server included, were on the router, how would the server act as the, um, server? Make sense? I'm not really sure how to explain what I'm thinking... Doesn't the server need to control the internet connection, or am I totally confused on all this. 

Like I said, I've tried several different tutorials, etc, nothing has worked at this point. I can't get the network running, can't get a web server up, and I have no printer, lol. 

Hopefully I can get this figured out soon. 

I'm willing to pay someone to help walk me though this, I'm getting desperate :)

Sean

---

### Post by kvonb on 2007-02-06
I would suggest the following:

1) Do you REALLY need all the other computers on your LAN to go "through" the Ubuntu "server"?  I'm guessing that the router is already/permanently connected to the net, so you shouldn't need to touch that!

2) You can still setup a web server/samba/squid on the Ubuntu machine without having 2 netcards in it, remove the 2nd netcard, keep the remaining card as a fixed IP address, ie set it to DHCP, then look at the address that is assigned to it.

It would be something like 192.168.0.116, copy this down, now set the remaining netcard to be a fixed IP, something like 192.168.0.x (x being any number between 200 and 254 as a safe bet), and your gateway would be the address of the router, ie 192.168.0.1 (usually!).

3) You can change the DHCP info that the router dishes out, you need to read the docs that came with it, or search on-line for info on it, I can't help you as I don't own one!

4) The printer is the easiest as it has a network interface, look in it's inbuilt menus (or search online for info), it should have a way of setting it's IP, set it to somewhere in your assigned DHCP range, ie if you're range is the 192.168.x.x as in my example above, assign it something like 192.168.x.199, then on the Ubunti box, goto Menu->System->Administration->Printing and do the "add Printer" helper, if your printer is not listed there, it MIGHT allow you to install the Linux driver from the CD, again you might have to search on-line or ring the manufacturer for info/help.

If none of this makes sense, simply open a terminal (on the Ubuntu machine) and type the following as a start for someone here to help you:

```
ifconfig -a
```

...then copy and paste the results here.

And remember, Don't Panic!  Someone here WILL help you.

Regards, KEv :)

---

### Post by orcalover on 2007-02-06
Okay, let me try to understand...

Am I going to actually remove (deactivate) the second nic from the server? Will having the server on the router along with the other computers prevent other users from storing their files/documents on the server? I'm sorry, I think I'm just brain dead this evening, been up straight for the past 48 hours. 

I think I can live with everything just going through the router, but I am wondering if the DynDns.org issue will allow this? Of course, I still haven't gotten it to work yet the way I have it, so I suppose it couldn't make it any worst. 

I'll admit that I am starting to freak out a bit. I really need to get this all sorted out before Thursday when my associates will be returning from Costa Rica. I pretty much decided to ditch the Microsoft Server while they were gone and managed to convince them that Ubuntu is the better way to go (and I still believe that, without a doubt). The last thing I want is for them to return to see me having problems. 

Once again, I REALLY appreciate the help and feedback. I'm still more than willing to pay someone to help walk me through this, via chat, etc. I think my problem right now is that my brain is still wrapped around the window's way of doing things. 

Sean

---

### Post by orcalover on 2007-02-06
This is the result of the ifconfig -a (before moving everything to the router)

eth0      Link encap:Ethernet  HWaddr 00:17:31:81:CD:26  
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe81:cd26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56332881 (53.7 MiB)  TX bytes:2333503 (2.2 MiB)
          Interrupt:217 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:81:D7:B8  
          inet6 addr: fe80::217:31ff:fe81:d7b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:560874 (547.7 KiB)  TX bytes:21944 (21.4 KiB)
          Interrupt:74 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65532 (63.9 KiB)  TX bytes:65532 (63.9 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by kvonb on 2007-02-06
> **orcalover said:**
> Okay, let me try to understand...

> Am I going to actually remove (deactivate) the second nic from the server?

Yes, I would actually suggest physical removal, I don't really think you need it, and it will only confuse the issue right now.

> Will having the server on the router along with the other computers prevent other users from storing their files/documents on the server?

You **will** be able to use the Ubuntu machine as a file server AND squid/Apache server AS WELL if you want!

> I'm sorry, I think I'm just brain dead this evening, been up straight for the past 48 hours.

I know how you feel, I've been there myself on several occasions :).

> I think I can live with everything just going through the router, but I am wondering if the DynDns.org issue will allow this?


It will have no effect as long as you have a dyndns client running somewhere on your network.  Your router probably has this as a built in function, my old ADSL modem had it, again check the router docs for this.  It's not the end of the world if it doesn't support it, the worst is that you will have to visit dyndns once a month in order to update your IP, or whenever the connection is reset.  There is a Linux client available, but I haven't used it with Ubuntu yet, I should have, and will look into it and let you know what happens.

> Of course, I still haven't gotten it to work yet the way I have it, so I suppose it couldn't make it any worst.

oh, things can, and WILL always get worse! :).

> I'll admit that I am starting to freak out a bit. I really need to get this all sorted out before Thursday when my associates will be returning from Costa Rica. I pretty much decided to ditch the Microsoft Server while they were gone and managed to convince them that Ubuntu is the better way to go (and I still believe that, without a doubt). The last thing I want is for them to return to see me having problems.

We'll get you sorted, have faith :).

>  Once again, I REALLY appreciate the help and feedback. I'm still more than willing to pay someone to help walk me through this, via chat, etc. I think my problem right now is that my brain is still wrapped around the window's way of doing things. 


No need to pay, I didn't pay for the little knowledge I have, people here helped me, and I'm willing to share it with someone who is appreciative of it :).

Regards, Kev :)

---

### Post by kvonb on 2007-02-06
I'm assuming that you are not in Japan?  I would suggest removing IPv6, that also clouds the situation.

If you don't need IPv6 (I believe only Japan uses it), do this:

Open a terminal and type this:

```
sudo gedit /etc/modprobe.d/blacklist
```


add this line anywhere:

> blacklist ipv6

save, exit and reboot.

In Firefox, type about:config in address bar, in the Filter line type ipv6, double click on network.dns.disableIPv6, it should be true.

---

### Post by orcalover on 2007-02-06
Thanks for your help :)

I'm finally going to go sleep. First thing tomorrow I'm going to remove the nic card and re-configure the network layout so that everything is attached to the router. I'll report back to you at that point and let you know what the story is. 

I hope you don't think I'm a complete noob or anything, I've actually got a lot of experience with some of this stuff (well, not networking, but...). I've been programming in PHP and some other languages for some time (about ten years) - though I've never really attempted to learn anymore of Linux than I needed. I'm also very skilled at troubleshooting Windows, though it's more of a curse than a blessing. I'm the one everyone goes to when something goes wrong, and it literally makes my blood boil. 

I had to laugh when you said that things can always get worst, despite the problems I have had with Ubuntu, nothing could ever compare to the problems with Windows. I kid you not, the final straw for me was when the server crashed - AGAIN - last week while it was getting it's daily "update to a problem we didn't bother to look for". It somehow managed to wipe out the entire hard drive where we stored the backup. Any how, at that point, that was it. 

Once again, despite the FEW issues I have had with Ubuntu (which has to do with my lack of experience, not a fault of the OS), I'm very happy. I already love Ubuntu and I've only just begun. 

Sean

---

### Post by bonzini on 2007-02-06
I see you're getting some good help here.  Let me post a few ideas, maybe they'll help too.

You have a router with a 192.168.x.x private address range.

On that address range you have one Ubuntu machine and a few Windows machines.

You want to use the Ubuntu machine as a a "server" inside your 192.168 workgroup.

It's not clear to me whether you want to have people outside your workgroup accessing your "server" inside the network.  Let me assume "no" for now.

Here is the most straightforward way for you to deal with this.

First, look at your router documentation.  You will probably find that there is a range of addresses that the router manages through DHCP, and there is a range it doesn't manage.

For example, my router, a SAGEM Livebox, by default manages the range 192.168.1.10 through 192.168.1.50 inclusive.  The router itself lives at 192.168.1.1.

So I could pick any address outside that range and use it as a "fixed" address inside my local area network for my server - for example, I could use 192.168.1.101 for my server.

You should be able to do the same.  So pick a fixed address for your Ubuntu machine.  For sake of example, let's assume you pick 192.168.1.101 as well.

Then go into System > Networking.  Configure your Ubuntu machine to use that fixed address, rather than using DHCP.

(A side note, this is sometimes a nice way to deal with networked printers as well).

OK, assuming that's done, now you and all your colleagues should be able to get at your web server simply by typing

[http://192.168.1.101](http://192.168.1.101)

If you want to assign a symbolic name to that, given that you have a small private network, the easiest thing to do might be to add a line to the "hosts" file on each computer.

Let's say you decide to call your internal network "our.little.network", and you decide to call your ubuntu server "ubuntuserver".

A line in the hosts file that looks like

192.168.1.101    ubuntuserver.our.little.network

should do the job.

Then your internal people can get at your server via

[http://ubuntuserver.our.little.network](http://ubuntuserver.our.little.network)

The hosts file in Linux is /etc/hosts.  I used to know where it is in Windows but I've forgotten and I no longer have a Windows machine around to explore.  But I think it's somewhere down in C:\system32...

If you want outsiders to be able to get at your web server, then you have some more work to do, involving DynDNS and the like.

Basically, you will have to set up your router so that it passes accesses to port 80 through the firewall to your ubuntu server - this involves network address translation (NAT).

Then you need a registered domain name and you can affiliate that with your (moving) IP address through DynDNS.

The end of all of this is so that I could type in [http://your.registered.domain.name](http://your.registered.domain.name), whose IP address would be returned by DynDNS, and that would be the IP address of the web side of your router, which would NAT my request through its firewall to your Ubuntu machine, which would see the request coming from the private side of the router and respond to that, which response the router would NAT back through the firewall and back to me.

So you can see that the "external service" part is a game you play starting with your router and working outwards - you don't need to screw around with DHCP service on your Ubuntu machine, or multiple network cards, or anything like that.

OK?

---

### Post by Netherspirit on 2007-02-06
I have exactly the setup as described by bonzini and it works well. I use 192.168.1.100 for my server and my router is 192.168.1.1. My friend can also bring his Windows based laptop into my house and connect to the local wireless LAN with no problems. I love it. (Although I am trying to convince my friend to use Ubuntu instead!) :)

---

### Post by orcalover on 2007-02-06
Okay, I finally woke up this morning and re-configured the networking layout so that all computers, the "server" included, connect to the router. I also re-installed Ubuntu on all the machines to wipe out the garbage from my previous attempts at getting all this working. At this point, I'm starting off with a clean system. 

All computers (and the network printer) are connected to a switch which is connected to the router (which in turn, of course, is connected to the cable internet). 

**Router Information:**
Model: Linksys WRT54GP2
The IP address for my router is: 192.168.15.1
Local DHCP Server: Enabled
Start IP Address: 192.168.15.100
DHCP  Address  Range: 192.168.15.100 to 192.168.15.149


Obviously, all the computers now have access to the Internet. 

NOTE: The router does have support for DynDns.org, but I'm note sure if it is working because the status shows " The hostname does not exist.". I've entered the username, password and hostname correctly. The only thing I can think of here is that the built-in router support doesn't support custom host names.

That said, however, the domain name used with DynDns currently re-directs to the routers administration page. I'm not sure if this is because my internet provider hasn't assigned me a new dynamic IP address since the last update, or if the router config is actually working.  

**Outstanding Issues**

1. I am still unable to get my Samsung ML-2500 Network Laser printer working. When I had this printer working on the Window's network, I had to first install something called SynchThrough which added a port of some sort for the printer to use. I also had to install a program called IPconfig, which either assigned an IP address to the printer, or perhaps just discovered the IP address, not sure which. 

2. I have not attempted to setup the web server, or network file sharing, as I need some advice/guidance on this first. I want to use PHP, MySQL and Apache on the webserver - all of which I'm well experienced with in terms of installing. I also need a mail server (POP/SMTP/IMAP) - which I would also like some input on regarding the best packages to install. 

3. As for file sharing, I'm at a complete loss on this. Basically, I just want users on the network to be able to store and access their files on the network server (and for the server to be able to access files on their computers). I have NO idea how to accomplish this, and I'm VERY confused on this issue. I've read some things that lead me to believe that I need Samba,  but from what I can tell, Samba is only for getting Window's networks to talk to Ubuntu/Linux networks, which while this might be nice, it isn't really what I'm trying to do - and I'm not even clear if Samba would network the other Ubuntu computers or not. 

I also have seen something about NFS, but I have no idea what I would need to do to get this setup. 

The only other thing that I'm confused about is giving the server it's own IP address that is outside the DHCP range of the router. If I do this, how will the router direct requests to the server if  it isn't aware of the IP address being used? Can someone give me a little more detail on this so that I can understand it better. 

Thanks for all the help!

Sean

---

### Post by orcalover on 2007-02-06
Information RE; The Printer...

The software that came with the printer has installation files for "unix/linux" but as I mentioned in the previous post, I can't get it to work. The setup file is a shell script named setup.sh. 

From the terminal window, I navigated to the CDROM drive and (as SU) issued the following command:

[HTML]./setup.sh[/HTML]

This gave me the following error message:

[HTML]bash: ./setup.sh: /bin/sh: bad interpreter: Permission denied
[/HTML]

I then tried the following command:

[HTML]sh ./setup.sh[/HTML]

Which gives me this...

[HTML]
sh: Can't open ./setup.sh
root@sean-desktop:/cdrom# sh ./setup.sh
/root/.setup13189: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
[/HTML]

Not sure what this all means, but I figured maybe someone here could tell me what I'm doign wrong.

Sean

---

### Post by ^rooker on 2007-02-06
**Routing/DHCP etc:**
A server should have a static IP address - thus you should set it statically. 

DHCP range only means which IPs DHCP-clients will get assigned. Your server will not request any IP by DHCP since it already has one statically configured. e.g.: 192.168.1.5
Your router will have no problem at all finding your server, since your router can access its whole LAN - according to the IP mask set. 

e.g.: 192.168.1.0/24 - or 192.168.1.0/255.255.255.0 means that it can see 192.168.1.*

For requests from LAN clients to the server, the router is functioning simply as a network switch.



**Filesharing:**
Samba works for both ways: *nix/Windows and Windows/*nix. So you can see windows computers and they can see you.

I've found out that most newbies prefer samba also for sharing between Linux/Linux.

A web config frontend exists for samba, called SWAT.

---

### Post by ^rooker on 2007-02-06
About your printer:

The errors you're getting simply indicate that you don't have sufficient priviledges to access certain files.

You'd have to run "sudo ./setup.sh" instead of just "./setup.sh" - BUT: I assume that it's not necessary to install your printer drivers like that. Furthermore I guess you shouldn't do that at all.


You've mentioned that it's a network printer - so it's just attached to your network router/switch and access it by IP. Usually those printers can take their IP from DHCP, too - but if not, you could configure them locally (display/buttons on the printer) or with some software. If you need software, you're probably best of with configuring the printer's IP -once- from Windows and then access it by that IP from Ubuntu.

You can add new printers in "System/Administration/Printers".

---

### Post by orcalover on 2007-02-06
rooker,

I've tried installing the printer through System>Administration>Printers, but since it can't find the printer, it didn't work. I even tried just adding the printer as a local printer using the built-in driver, but again, it didn't work. 

Regarding the apparent permissions issue, I tried both SU, then SUDO and even logged in as root. Got the same message all the time. It seems as though I needed to use "SH ./setup.sh" to avoid the permissions issue. 

**Update**

As stated previously, I ran into problems running the setup program for the printer which kept giving me the following message:

```
sh: Can't open ./setup.sh
root@sean-desktop:/cdrom# sh ./setup.sh
/root/.setup13189: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

I solved this problem, it seems, by installing gdk-imlib1 and gdk-inlib11. Both were install through Aptitude (apt-get) which installed the dependencies required for these two files as well. I was able to run the setup, but the printer is still not working. 

After the setup program finished, it launched okay, but now I'm getting this error message:

```
CUPS_BackEnd: get-printers failed: client-error-not-found
```

At least I'm getting closer, I think...

---

### Post by kvonb on 2007-02-07
OK, I'm back :).

Because you are in a pickle and need to get this up and running asap, if you really need to speak to me "live", send me a PM and I will work it out. I will post all the steps taken to this thread in order for the community to benefit.

Let's get file sharing working first.

This is actually the easiest thing to do.  I would suggest creating a "king" folder to store all the shared sub-folders in, ie on my server I have a folder called "/shared" and in that I put each user's personal folder, ie dave/john/jane etc, this is basic stuff and I'm sure you get the drift :).

You can share ANY folder you want on the network, the easiest way is to run Nautilus (the file browser in Gnome), right click on the folder you want to share and select "Share Folder".  Then it will give you the option of selecting either NFS or Samba, obviously for MS Windows access, select Samba.

That's basically it, although you now have to deal with permissions and stuff, the easiest way I found of doing it is to directly edit the /etc/samba/smb.conf file, like so: (in a terminal type)

```
sudo gedit /etc/samba/smb.conf
```IT will be a mass of information, however the most important thing to do at this stage is look for the line "**security=**".  Now this is where I will get flamed by the people who **could** have helped but chose to remain silent!  However my backend is fireproof, and I don't care :).  I always select "share" as the security type, mainly because it bypasses all the unnecessary username/password security nonsense and just makes it available and working!  CAUTION this will make the files available to ALL on the local network!!!  I have included a sample smb.conf that will show you the basics, I modified it so that you can easily understand it.

So change the file how you want it, check to make sure there are no obvious typos, save, exit, then issue the following command in a terminal to restart samba and activate your changes:

```
sudo /etc/init.d/samba restart
```If it fails, check the smb.conf file for mistakes.  Otherwise you should now have file sharing available on your internal network!

Next, let's search for that pesky printer!

Run Synaptic (Menu->System->Administration->Synaptic Package Manager), and in the search box type "nmap" (no quotes of course!).  Select "nmap" and also "nmapfe", click on apply and wait for the software to be installed.  You can now close Synaptic.

Look on your menu under "internet", there should now be an icon entry for  "NmapFE", run it and in the box at the top labelled "Target", type in:

```
192.168.1.0/24
```...then click on "scan" which is on the rhs there :).

This will show you (albeit in a long text list!) ALL the devices/computers that are connected to the 192.168.1.0 range.  IF your printer is intelligent and assigns it's own IP address, or uses DHCP, you should see it listed somewhere in the output.  Now I use a HP laser with a network interface and it has a simple web-page access option, I just open a browser and type in the IP:PORT of the printer and it allows me to configure it remotely, I'm hoping that yours will do the same, check the manual for info.

OK, so you now know that the printer is "alive" and on your current network, the next part is the hard bit, installing a driver!  I have no experience with your brand of printer so I'm going to have to drop the ball on that one at this point, sorry!  I would recommend trying to contact the manufacturer, searching on the net, or fiddling with it, you might find that it has a HP Laserjet emulation mode and the HP Laserjet4 driver will work perfectly for it!  Look in Menu->System->Administration->Printing, and add a new printer.  It's basically the same process as the Windows add printer function, make it a network printer etc etc.  But try using the HPlj4 or other drivers until one works, not much to go on, but you never know :).

Do those things and let me know how you went :).

Regards, Kev :)

---

### Post by kvonb on 2007-02-07
ADDITIONAL:

Edgy has a problem with SMB networks, for some reason when you try to browse the network it gives you a "braindead" list of "non-icons"!

You have to click on them a couple of times and close the error messages that pop up, eventually it works!  This is only on the Ubuntu side though, Windows doesn't have a problem at all!

I filed a bug report when Edgy was first released but still nothing has been done!

For "production" machines, ie real working machines I believe it is still better to stick with Ubuntu 6.06 (Dapper) rather than Ubuntu 6.10 (Edgy)!

Kev :)

---

### Post by orcalover on 2007-02-07
Arg, this darn printer is driving me crazy :)

Okay, just read your notes and I am going to try things out to see if your methods resolve the printer problem. I have figured out the IP address of the printer, but it hasn't done me any good as of yet. 

The IP address for the printer is: 192.168.0.228

I've tried to install a new printer using all the available connection types, but nothing works, the print jobs (test page) either sits there, or it pauses itself. There doesn't actually seem to be a connection to the printer. 

I also figured out (thanks to these forums and google) that if I changed the /sh to /bash in all of the files on the Samsung CD, I could run their install program - which seems to be called the "Samsung Unified Driver". I ran the software and didn't seem to encounter any errors, but here again, nothing will print. 

I'm currently looking at the instructions on OpenPrinting.org [http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2251N]("http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-2251N")
and am downloading a file called Samsung-SmartGDI-all-GS.tar.gz  from [http://www.openprinting.org/download/printing/samsung-gdi/]("http://www.openprinting.org/download/printing/samsung-gdi/")

It seems as though some other's have gotten this model printer to work in Ubuntu, but they've failed to report back on how they did it (not on these forums, but other forums I've encountered via a long google search). 

Anyhow, if the IP address to the printer helps at all or gives you any ideas, let me know. I'm also considering uninstalling the Samsung Unified Driver software since it doesn't seem to be working. 

Sean

---

### Post by orcalover on 2007-02-07
Here's a question for you...

In reading through the smb.conf file I noticed that there seems to be a way to enable the server to act as a primary domain controller (PDC). This is somewhat the way I had things setup on the Window's network. 

Is there a way to allow for, say, dual login accounts (not sure how else to put it) where user accounts on the server will also work on all the client workstations? In other words, I would like to create a new user account on the server, which would allow that user to log on to ANY computer within the network. 

Ideally, I would just like a way to "synch" user accounts from the server to the workstation and vise versa, that way if the network is unavailable (a few workstations are laptops, for example) the user could still login to their computer - obviously they wouldn't have access to network files and printers, etc, but they would still be able to login to the workstation and access the files on the local system. 

Oh, one other thing, I have NOT yes assigned my server a static IP address. I'm going to attempt to work on that now. 

PS - I've PM'd you my IM contact info, which is also available in my profile here on the forums. 

Sean

---

### Post by orcalover on 2007-02-07
> **kvonb said:**
> OK, I'm back :).

Look on your menu under "internet", there should now be an icon entry for  "NmapFE", run it and in the box at the top labelled "Target", type in:

```
192.168.1.0/24
```...then click on "scan" which is on the rhs there :).


This is the output that I get:

```
Starting Nmap 4.10 ( http://www.insecure.org/nmap/ ) at 2007-02-07 00:51 PST
Nmap finished: 256 IP addresses (0 hosts up) scanned in 24.016 seconds
```

---

### Post by orcalover on 2007-02-07
** UPDATE **

I changed the IP address of the router to 192.168.0.1. I can now access the printers online setup section, though I am still unable to print at the moment. However, I am able to configure the printers setting, including the NIC settings and TCP/IP. I'm not really sure what these settings should be. 

Here are the settings as they are currently set.

**TCP/IP Settings:**

IP Address Assignment Method : [changed from DHCP] Static

IP Address : 192.168.0.228

Subnet Mask : 255.255.255.0

Default Gateway : 192.168.0.1

DNS Address : 192.168.1.1  // I'm not sure what this should be, or if this is even needed since I'm no longer using DHCP for the printer. 

 DDNS Domain : [changed from localdomain.local to:] left this field blank

**WINS Configuration:**

Primary WINS Server Address : 192.168.1.1

Secondary WINS Server Address : None, left blank

**NetWare Configuration:**

NetWare Enabled : Checked / Enabled

Novell Name : SEC00159900f832

IPX Address : 00000000.00159900F832 

Job Check Interval  : 5 seconds

Configuration Interval : 120 seconds

IPX Frame Type : Auto

**IPP Configuration**

Printer Name : Samsung

Printer URI : [this was blank, but I added this...] [http://192.168.0.228/](http://192.168.0.228/)

Operator Message : Operator Message 

Printer Location : Printer Location

Printer Information : Info

More Information : More

Multiple Operation Timeout : 300

Time to Keep Jobs In History : 1

**UPNP Configuration**

Auto IP Enabled : Checked / Enabled

Multicast DNS Enabled : Checked / Enabled

SSDP Enabled : Checked / Enabled

SSDP TTL : 1

---

### Post by orcalover on 2007-02-07
SUCCESS!!!

After MUCH trial and error, I some how managed to get the printer working. I'm not really sure WHAT I did, per se, but here are the settings that I have as of now. 

[From Printer Properties]
Model: ML2251N
Driver: hpjis

ALSO, this seems to be VERY important. 

On the ADVANCED tab, make sure that GhostScript pre-filtering is set to: Convert to PS level 1. 

I hope that this helps others who might me trying to setup the same model Samsung printer. 

If anyone else is having problems with their Samsung printer, feel free to PM me and I'll try to walk you through the process that I went through. 

Sean

---

### Post by kvonb on 2007-02-07
> **orcalover said:**
> Here's a question for you...

In reading through the smb.conf file I noticed that there seems to be a way to enable the server to act as a primary domain controller (PDC). This is somewhat the way I had things setup on the Window's network. 

Is there a way to allow for, say, dual login accounts (not sure how else to put it) where user accounts on the server will also work on all the client workstations? In other words, I would like to create a new user account on the server, which would allow that user to log on to ANY computer within the network. 

Ideally, I would just like a way to "synch" user accounts from the server to the workstation and vise versa, that way if the network is unavailable (a few workstations are laptops, for example) the user could still login to their computer - obviously they wouldn't have access to network files and printers, etc, but they would still be able to login to the workstation and access the files on the local system. 

Oh, one other thing, I have NOT yes assigned my server a static IP address. I'm going to attempt to work on that now. 

PS - I've PM'd you my IM contact info, which is also available in my profile here on the forums. 

Sean

Unfortunately that is advanced samba stuff, it gives me a headache just contemplating it!

However, I'm sure if you ask a question in the Networking section someone with advanced knowledge will turn up :).

I'm quite sure it will do everything you want, it's just a matter of fonding out how to do it!

BTW, glad to hear you got the printer working.

---

### Post by ^rooker on 2007-02-07
Using Samba for a PDC works charming - it's incredibly close to a windows server (and it'd probably already be ahead of it if it wasn't for the overhead of reverse-engineering microsoft things all the time).
You can (but I wouldn't rely on that working forever) use some management tools coming from the Microsoft domain-admin toolkit on their CDs.

However, there are plenty of excellent step-by-step HowTos out there describing how you can do that.

---

### Post by orcalover on 2007-02-07
To be honest, I'm at the point where I don't care about rather or not Ubuntu works well with Window's computers on the network, my only concern is setting up the Ubuntu network - which looks like is going to be fairly easy. 

I am VERY appreciative of all the help I have gotten here, and would like to thank Kvonb and rooker especially. I also want to point out that the problems I have had setting up Ubuntu have nothing to do with Ubuntu itself, the problems were merely the result of my inexperience with Ubuntu combined with a preconceived knowledge of doing things the "Microsoft" way. I can't stress this point enough, especially to those who might be reading this thread while considering switching from Microsoft to Ubuntu. 

I have nothing but praises for Ubuntu, and for the first time in a long, long while, it has me excited about computers again. I was reading a post in the Ubuntu Cafe where people were asked how they showed off their Ubuntu to non-linux users. Most of the posts involved things regardins Beryl or some other element. To be honest, the thing that impressed me from the start is the stuff most of you Ubuntu veterans probably take for granted and don't even notice. 

I literally almost passed out when Ubuntu first loaded after install and I noticed it had a working Internet connection. I couldn't believe it! I was once again stunned when I was filling out some forms and doing forums posts and noticed these red lines under some of the words - spell check on forms, I thought? The list goes on and on, and I intend to post my own thoughts in the Cafe thread. 

To anyone thinking about ditching Windows and moving to Ubuntu, let me just say this. I've been a computer geek for a long time. I started out with a computer running nothing more than DOS, and have been working on the Window's platform for as long as I've owned a computer. When I first installed Ubuntu, I was extremely furious to discover that everything I had seen and come to know in terms of using computers and accessing the Internet had only been a brief preview into a world of limitless possibilities. To things simply:

Using Window's is like seeing an interesting movie trailer on TV. You are able to see what the movie is about, who the stars are, and get enough information to decide rather or not you want to see the movie. It's wets your appetite, so to speak. Window's is nothing more than one long movie trailer, it gives a very small glimpse into what is possible. Ubuntu, on the other hand, is the action-packed, star studded movie that is every bit the blockbuster it claims to be; and you don't even need to buy a ticket. 

Sean

---

### Post by kvonb on 2007-02-08
Good on ya Sean, glad to hear that you're having some success.

When I first started using Ubuntu (over a year ago now), the thing that impressed me the most was the Forums.  People would actually explain how to do things, rather than the usual "rtfm" 
responses from other Linux distros.

It is a steep learning curve, and it will have you tearing your hair out every now and then, but I'm sure you will find an answer to every question you have :).

The main problem we (Linux in general) have is driver support, and that is not in our control unfortunately :/.

Regards, Kev :)

---

### Post by orcalover on 2007-02-08
Yes, I agree, the support here has been top notch (I'm especially thankful to you). An active community is not only important, but it shows a level of dedication and deep-rooted passion. It's easy to see that this is a community made up of people who really love Ubuntu. 

As for drivers, I suspect this will improve as more users start using Linux. I personally believe that the end of Microsoft's reign in the OS market is coming to an end, and the day can't come soon enough for me!

Sean

---

