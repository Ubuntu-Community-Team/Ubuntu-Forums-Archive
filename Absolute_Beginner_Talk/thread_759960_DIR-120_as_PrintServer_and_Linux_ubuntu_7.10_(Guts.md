---
title: "DIR-120 as PrintServer and Linux ubuntu 7.10 (Gutsy Gibbon)"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by nilsgn on 2008-04-19
Hello! 

How To get access to my printer (HP psc 1210 aio) connected to D-Link DIR-120 (USB)? 

Drivers for the printer is in ubuntu. 

Routerns IP = (default) 192.168.0.1 

and (in router DIR-120): 
tcp port http = 80 
tcp port printer = 515 
tcp port jetdirect = 9100 

I have try a lot of configurations and read a lot of tips. Now I'm out of ideas. 

Regards!

---

### Post by quirks on 2008-04-19
Have you tried following this walk-through?

[http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html](http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html)

I can see the setup wizard has an option for SMB-shared printers and HP JetDirect. Both configurations might work in your environment. If you can connect to the printer from a Windows PC, you should have no trouble printing to it from Ubuntu using the SMB configuration.

---

### Post by nilsgn on 2008-04-20
quirks:
Thanks for the link.

But, there is a problem. In my printer setup I can not choose between 'Local or Detect Printer' and 'Network Printer'

When I go to: System-Administration-Printing (Printer Configuration - localhost) and choose 'Add New Printer'. The window is different?

I hawe a Swedish translated ubuntu.

I have to dig some more...

---

### Post by quirks on 2008-04-20
Sorry, I forgot they changed the printer setup. I have attached a screenshot that shows how to do the same with the new setup (sorry, mine is German).

1. Open the printer options: go to System -> Administration -> Printers
2. Click New Printer.
3. Select AppSocket / HP JetDirect from the devices list.
4. Enter the IP address of your router (192.168.0.1) into the IP address field. The port should match yours (9100).
5. Complete the rest of the wizard (printer model, name, etc.).

If this doesn't work, we can also try to connect via SMB. Post it, if you have any trouble.

---

### Post by nilsgn on 2008-04-20
Hello quirks!

Thanks,

I solve the problem in a different way. And I'm not sure why the ordinary way not goes well.

I install the tool: HPLIP Toolbox
From there I get to:  CUPS. Common UNIX Printing System 1.3.2.: [http://localhost:631/](http://localhost:631/)

Now I have a printer: socket://192.168.0.1:9100
that works.

The strange thing is that I tried that with the ubuntu printer setup tool.

It seems that I in some way must be logged in as root. Or log in as a member with root previlegies. 

In the ubuntu printer tool setup this newer appear.

In the CUPS tool. [http://localhost:631/](http://localhost:631/). I have to login, in the end of the process.

I think that it is this differens that matter. But I'm not sure.

Regards

---

