---
title: "Newb asking"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Ron G. on 2007-09-27
I installed Ubuntu on my brother-in-law's old Compaq.  Best use of it's life!  But I have some questions - 

1)  How do I connect it to the 3 Windows boxes on my net?
2)  Related to above - Windows has workgroup designation that makes it easy to see computers, etc.  Is there something similar in Ubuntu?
3)  My net printer is connected to the biggest computer on the network.  Can I get a pointer to the right documentation?
4)  My router/dsl modem functions as the DHCP server.  I haven't been able to 'see' the internet even though Ubuntu reports that it is connected.  What am I doing wrong?
5)  I had heard that Linux was much faster on old Windows boxes than the previous Windows.  However, I am not finding that to be true.   So what did I do wrong?

OK - you swamped yet?  :lolflag:  All help appreciated.

---

### Post by un_dave on 2007-09-27
I'm a bit of a noob as well, but i think i know 1 & 2:

The windows file sharing system can be accessed from Ubuntu 7.04 out of the box, from your main menu. There should be a 'Network' link in the 'Places' menu on the panel. 
If you want to setup shares on your Ubuntu system that can be accessed from other windows boxes on your network, you'll need to setup SAMBA, which a quick search of the forum should give you plenty of guides on how to install.

---

### Post by HermanAB on 2007-09-27
Regarding the printer: There is a printer wizard somewhere - "Applications, Settings, Printing".  Printing is handled by CUPS and Samba.  In general, you will have better luck when you attach the printer to a Linux machine than when it is attached to a Windows machine, because the Windows XP firewall is specially designed to make things difficult and successfully sharing a printer from a XP machine is a rare event.

Linux makes any printer look like a postscript printer.  So then you don't need to install any special drivers when printing from Windows - just select the first convenient postscript driver - I always use Apple Laserwriter II, since it is at the top of the list.

---

### Post by dwhitney67 on 2007-09-27
Your problem is quite simple... you installed Ubuntu on your brother-in-law's computer... not your sister-in-law's.  All of your problems could've been avoided if you had done things properly.


Just kidding.


It seems that question 1, 2, and 3 have been answered.  I cannot confirm the validity of the response for question 3 because the only experience I have is using the appropriate driver for the printer (even if it is connected to a windoze server).

For question 4, you stated that your Ubuntu system "thinks" it is connected to your router.  Can you confirm this by running this command (from a terminal) and posting the results:

[FONT="Courier New"]$ /sbin/ifconfig[/FONT]

If you have an IP address similar to 192.168.1.xxx, try to see if you can ping the router.  The command for that is:

[FONT="Courier New"]$ ping -c 3 192.168.1.1[/FONT]

Also try to ping the other systems on your network (say the windoze system with the printer).  You will need the IP address assigned to them (it).  The command to find an IP address under windoze is 'ipconfig'.

---

### Post by Ron G. on 2007-09-27
OK (revealing more newb than was known before)

The kind posts above pointed me to various tools that show me that I am connected to the router and fellow computers.  Indeed I have seen the Internet.  <awe>

However, why is there no network depiction?  In Windoze (I got that from above) there is a Work Group that I can see the other computers.  I know they are there - but is Linux a buncha singletons that have to manually connect to each other to work together?  (ponders the stupidity of an approach such as that)

I added a printer that should print on the printer on the Windows box - but doesn't yet.  Perhaps that is the port thing.

So - am I back to the 60s and typing a buncha stuff in text windows? 
Or perhaps there is a GUI I didn't install?  Or...?

:confused:

---

### Post by dwhitney67 on 2007-09-27
I do not have windoze machine anymore so I do not know if the following will work for you, but if you click on **Places** -> **Network**, wait a moment or two, and then double-click on **Windows Network**, maybe then you will see your other systems.

If you do not "see" your other machines and are still lamenting using the Linux command line, then I strongly recommend that you punt on Linux and go back to being a windoze drone.  I bet you $5 your windoze machine can't "see" the Linux machine, unless of course you configure it properly.  Why would you expect any different from Linux?

Lastly, look into Samba.

For printing, configure your printer by opening a browser on your Linux system and visiting this site for CUPS where you can add a printer:  [http://localhost:631](http://localhost:631)

---

