---
title: "Dual Boot question - only Ubuntu to access internet?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-01-07
I'm sorry if this isn't the right place to ask this question, but I'm hoping someone here can help.

I've got two computers and I want to set up both to dual boot Windoze and Ubuntu 5.10.  I just ordered ADSL service from my local phone company (I've been on a dial up until now) and they are sending me a Westell router / ADSL modem to install.  One of the big reasons I continue to use Linux (even though most of the apps I use are Windoze) is for it's great security and virus protection while using the internet.

What I want to set up is this (highest priority): 

a.  Both computers can access the internet, but -only- if they are running Ubuntu.  I'm told the Westell router/ADSL modem supports up to 4 network connections, so hardware wise I should be able to do this.

b.  File sharing under Windoze through the router, but -no- internet access under Windoze.  I don't know Windoze all that well, does anyone know if I can do this?

I'd also like to be able to (lower priority):

c.  File share while both systems are running Ubuntu (I don't know how to set this up yet).

d.  File share while one system runs Windoze and the other Ubuntu (I've started to look at "Samba", but haven't tried it yet).

Any help or advice you can offer is greatly appreciated.  Thanks!!

---

### Post by Azriphale on 2006-01-07
Lets see how much I can help you with...

 A
---

Possibly the easiest way to stop your Windows machine from having external internet access is to give it a static IP address rather than have the router assign an IP by DHCP.

If you do this, you can leave the "Default Gateway" field blank, and windows will not know where to pass network requests that are not on the local network, and will, i believe, therefore not have external internet access.
This can be done by going to... uh... i need to try to remember this now. Let me go and look at my Dad's PC...

Start->Control Panel->Network Connections
Right click on "Local Area Connection" (or whatever your local connection is called, that is the default) and select properties.

In the window that comes up, select "Internet Protocol (TCP/IP)" [you may need to scroll down to find it] and click the properties button just below it.

click where it says "Use the following IP Address"
Assuming your router's IP is 192.168.0.1 with subnet 255.255.255.0

Enter 192.168.0.2 (for instance, can be anything between 192.168.0.2 and 192.168.0.254) into the IP Address field
Enter 255.255.255.0 into the subnet mask field.
Leave the "default gateway" and "DNS server" fields blank. Hit OK. Hit OK again.
Now, if you try to access anything on the internet, not on the local network, you should get a "Destination Host Unreachable" error, or some such.

I say give it a static IP because I do not know how to stop windows from assigning the Default Gateway when it gets a value from DHCP.

For the GNU/Linux machines, I would recommend assigning addresses by DHCP.

 B
---

You can now share files normally in windows. You will use Samba to access the shares from Ubuntu.

 C
---

Currently for sharing on Linux, I use Samba. NFS is probably recommended for sharing between multiple *nix machines, but I have not yet bothered to find out how in all my years of GNU/Linux experience. I probably should one of these days.

 D
---

Samba is really (and I mean really, really, really) easy to set up. Simply use synaptic to install the packages, and I will walk you through setting up shares. I must apologise about doing it the good old fashioned way of editing text config files.

Once you have installed Samba, you may need to enable it to start on every boot. 
To do this, go to the System menu on the GNOME Panel.
Go to Administration
And select Services.

Look for "Folder sharing service (samba)" and make sure the little check box next to it has a tick.

now. To edit the samba conf file.

You may either want to stick with their initial default settings, or create a new  file. I'd say open up the example file, because there are some helpful comments in it these days.

```
sudo gedit /etc/samba/smb.conf
```

each section of the file is indicated by a flag in square brackets.
Global server configuration goes under the [global] flag.
When you want to add a share, you put the name of the share in square brackes. So I want to share something that shows up as Anime when a remote computer is looking at my computer, i use the flag [Anime]


One thing that is missing is your computer needs a "NetBIOS Name". This is the name that Windows computers identify each other by.
Just under [global] add a line that says

```
NetBIOS Name = my_computer_name_here
```

you can change the workgroup to whatever you want. Leaving it as HOME is easier and simple, tho.

"server string" found just below that is a description of the computer. Make it whatever you want. Again, I just leave mine.

Leave everything until you get down to 
```
####### Authentication #######
```

Make sure there is a line that reads
```
security = user
```
and that there is no ";" or "#" (comment characters) at the start of the line. 
This makes it neccesary to enter a username and password to connect to the computer. I'll go through adding users later.

you can probably skip everything until you get to:

```
#======================= Share Definitions ======================
```

here you can add shares (well, you can add them anywhere after [global], but keeping them together is a good idea).

you should find one called [homes]
This is a default share that will export a user's home directory when that user connects over the network. From this template it is easy to see how to add other shares.

BUT, when you do add other shares, do not include the "browseable = no" flag

save the file and close gedit when you are done.

to allow users to use samba, run the command
```
sudo smbpasswd -a username
```
the "-a" is to add the user
It will prompt you for a password and to verify.

run the command
```
sudo /etc/init.d/samba restart
```

Samba should now be working.

You will probably want to clean out the file so it looks a little neater (personally I don't like using the example file because it looks messy). You can go through it and remove anything you don't think is required. anything starting with ";" or "#" is a comment

I know its a bit much to add/remove/change shares often, so you may want to look at "swat", which is the Samba Web Administration Tool, or webmin-samba. Both are interfaces to configure Samba from a web browser. I haven't used either in many years, tho. 
swat is an official samba project.

I hope this helps you somewhat.

That was a lot longer than I was expecting. Sorry about it being a little badly written.

---

### Post by Azriphale on 2006-01-07
Oh, yes, to access windows shares in Ubuntu, open up a Nautilus window, hit Ctrl+L to get the location bar and enter
```
smb://windows_computer_ip_address
```
hit enter and it should connect and display the remote shares in that Nautilus window.

---

### Post by bigkahuna on 2006-01-07
Thank you very, very much!  That's exactly the kind of thorough response I was hoping for!  I'm saving your response and will give it a try as soon as my router/modem arrives (should be here Monday).  I'll let you know how it goes.

Thanks again!!!

---

### Post by Azriphale on 2006-01-08
I hope it all works out.

---

