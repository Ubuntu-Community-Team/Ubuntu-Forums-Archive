---
title: "Networking"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by jungulistic on 2006-08-07
hey all, just gone and bought new laptop and router because i have recently installed ubuntu on my desktop pc and have not been able to use it for the love of money. im up and running with the laptop and router but am not able to understand how to get ubuntu working with it. its a netgear gt.... wireless router and i am aware that getting wireless jobbies to work with linux can be a hard job if your like me and used to using windows os'. but i believe the problem lies deeper than that, basically i havent got the first clue really about networking. i have connected the pc with ubuntu to my router via an ethernet cable so therefore eliminating the wireless issue, but i am still clueless as to how to get the net working. i would like to create a network between the pc and the windows laptop but dont want to connect directly to one another if that makes sense well i do but wirelessly eventually. so i want to share the net between the router... can some one help? bear in mind i hav been working all day so am quite tired and not really aware of what im talking about 

cheers people

---

### Post by kidders on 2006-09-03
Hmmm... sounds like you need to read a little about networks! I'll get you started though.

Firstly, every networkable device has a (supposedly) unique address called a MAC (Medium Access Control) address. To form a network, you simply associate something called an IP (Internet Protocol) address with the MAC address of one of your PC's network cards. Of course, one computer doesn't make much of a network :(

To add more machines, you need to start providing some basic network services. These include DNS (a way of avoiding having to refer to computers by number all the time) and DHCP (a way of auto-configuring machines to work on your network). On top of that, you then add file/printer sharing, iTunes, web/mail services, etc.

Basically, you have two options:

1 - Designate one PC your "network server", capable of controlling every aspect of your network, and always leave it switched on. (**THE SMART OPTION**)

2 - Let your internet router handle all the nasty stuff and leave *it* in charge of the network. (**THE EASY OPTION**)

Option 1 requires two network adapters in one of your PCs. One of them can be wireless if you like. Let's start with option 2 though, and work up from there.

Your ISP's DSL router will be controlling DNS (the ability to call Google by its name, rather than its number -- 66.249.93.99) and DHCP (the ability to avoid having to tinker around all day with configuration files to get anything to work).

From a terminal window, type **sudo ifconfig -a** and check that you have something called "eth0". Then, make sure the following appears in /etc/network/interfaces:

```

auto eth0
iface eth0 inet dhcp

```

Plug your Ubuntu box and one other PC into your router with a cable, and you should be set. After a few moments, check each PC's network settings for an IP address. They may start with something like 192.168.. or 10.. Typing **sudo ifconfig eth0** will show you your Ubuntu box's IP.

Try to ping one computer from the other. Whether Linux or Windoze, the command is the same: **ping 192.168.1.1**, or whatever the destination IP might be. Assuming you get positive-looking responses, you're successfully networked. Try opening a web page, to see if internet access is available. If not, visit [http://66.249.93.99/](http://66.249.93.99/) to see whether the problem you're having is easy to fix.

Post back and let us know how far you get with this much, and we can go from there!

---

### Post by Kodiak3000 on 2006-09-03
Thanks for this - I'm following along, because when I did my first install, I just plugged my cable in and I got networked.  But this time it's not working.  I have internet, but no network access to shared folders, etc.

I did ping the host, and it worked, but when I go to connect to server, or network servers, the host isnt' there.

Any thoughts?

---

### Post by kidders on 2006-09-04
Ohh... you *have* internet access? That's great news.

There are LOTS of ways to share files and printers with Linux, but I'm assuming you want to use a Windows-compatible one, so here are a few questions:

[LIST=1]
[*]Have you installed Samba?
[*]Have you started the service?
[*]Did you play with /etc/smb.conf and break it?
[/LIST]

Two yes's and a no? Good :) In that case, your Windoze filesharing should at least be *half* working. Try the following, in order:

[LIST=1]
[*]Wait a moment after initially starting the samba service
[*]Try to access your Ubuntu box's samba shares from the PC itself ... if you're using KDE, hitting ALT+F2 and running **smb://localhost/** is enough to do that.
[*]Now do the same, but use the address *other PCs* would use to access your Ubuntu box ... **smb://192.168....**
[*]Now try it again, using the *name* of your Ubuntu PC.
[/LIST]

These checks ensure that (a) your Samba is even working, (b) that you are sharing something, (c) that Samba is listening on the right network interfaces, (d) that you don't have some kind of name resolution difficulty. If you get through these, it's time to try it from another PC. Address your Ubuntu box directly ... don't expect it to pop up in your network neighbourhood or some such ... and see how far you get. Do this from a Windoze PC by hitting START+R and running **\\192.168....** and again, using the actual *name* of your Ubuntu box.

Still with me?

Now you have to bear in mind that the Windows filesharing protocols are a very odd beast, a little overcomplicated and tempermental. Quite obviously, you'd prefer your network to "just know" where you're shares are, rather than having to be told; this can take up to 15 minutes on Windoze networks. So, wait 15 minutes and open Ubuntu's remote places and Windows' network places, to see if anything's there.

Post back with how far you get :)

---

### Post by ngtmagicks on 2006-10-16
I hope you don't mind if I jump in here.  Using kde desktop and after a reinstall and update I lost any opportunity to set sharing permissions.  Zeroconf is blank, as is the sharing-system settings > file sharing windows, it gives me the prompt for admin, but then comes up blank.

I can browse to other network shares, but can't set/enable any on the reinstall machine.  

Any suggestions for checking which services need to be running on start?

Thanks

---

