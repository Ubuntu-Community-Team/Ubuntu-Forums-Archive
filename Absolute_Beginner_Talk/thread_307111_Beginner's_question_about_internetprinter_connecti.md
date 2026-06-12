---
title: "Beginner's question about internet/printer connections..."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Skaliwag66 on 2006-11-26
Hi,
I am a newbie to Linux as well. I have had it up to here with Windows XP. I am having trouble with my internet connection starting up at boot and also having trouble setting up my HP printer.

I went through the ADSL setup process and the internet works fine. However, when I restart, I have to go through the process again in 'Terminal'. I selected the option of connecting at boot time every time but it doesn't work.

As for my printer, I am not sure if HPLIP is installed correctly. I cannot install my printer. When I try to enter the setup it doesn't do anything.



Anyone know what's going on?:-k 

Also, how do I get my other hard drives workin'?

My system: Intel Celeron 533, 320MB RAM, 10GB HDD, 

Printer: HP PSC 2175

---

### Post by steve.horsley on 2006-11-26
I can't help you with the internet thing. I've never set up ADSL on Linux. If you have to do a lot of commands every time, you could put them in a script and run the script. Make a text file with all the commands in it, but the first line should be:
> #!/bin/bash
Then right-click the file's icon, go to properties and make the file executable. Now it's a single command/program that you can run.

As for the printer, what are you trying to do? I added my HP printer by:
1) Turn on the printer
2) Menu to System->Administration->Printing
3) Double-click New Printer
I can't remember the rest, but it's straightforward. Is this what you are trying to do? If so, where do you get stuck?

---

### Post by RoyArne on 2006-11-26
> **Skaliwag66 said:**
> Hi,
... trouble setting up my HP printer.

...

As for my printer, I am not sure if HPLIP is installed correctly. I cannot install my printer. When I try to enter the setup it doesn't do anything.


Anyone know what's going on?:-k 

Printer: HP PSC 2175

You can also configure your printer from [http://localhost:631/]("http://localhost:631/"). Enter your username and password when asked for it.

---

### Post by steve.horsley on 2006-11-26
I found that it was possible to set conflicting settings on the Gnome setup thing and the CUPS web administrator (I set draft print quality on one and photo quality on the other). I found that the Gnome one was the one that really affected the printer output. I guess that they must store their settings in different places, which is odd. I've never found any good documentation on printing.

---

### Post by Skaliwag66 on 2006-11-26
> **steve.horsley said:**
> I can't help you with the internet thing. I've never set up ADSL on Linux. If you have to do a lot of commands every time, you could put them in a script and run the script. Make a text file with all the commands in it, but the first line should be:

Then right-click the file's icon, go to properties and make the file executable. Now it's a single command/program that you can run.

As for the printer, what are you trying to do? I added my HP printer by:
1) Turn on the printer
2) Menu to System->Administration->Printing
3) Double-click New Printer
I can't remember the rest, but it's straightforward. Is this what you are trying to do? If so, where do you get stuck?

Yeah I am trying to install my printer. But when I do it the way you described, it is 'reading printer database' and seems to not respond after a while. I always have to force quit it.

---

### Post by Skaliwag66 on 2006-11-26
by the way i got my printer to work using the online method :)
Thanks

---

### Post by Skaliwag66 on 2006-11-26
Ok everything's fine now.

Thanks for the help :)

---

