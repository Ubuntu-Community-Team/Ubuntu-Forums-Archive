---
title: "command line and madwifi on CD"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Luxx on 2007-10-25
I just loaded Ubuntu 7.04 and discovered I have a troublesome wireless internet card, NETGEAR WPN311. I found in my searches that it should work with madwifi and I have copied madwifi to a CD, but don't know how to access it so that it will work. 

Unfortunately I am unable to access the internet from my computer at home (posting this from a friend's computer) and cannot do this the easy way. 

Also I have had little luck in finding information on how to use a command line, which seems to be something I would need in this case. One thing I've noticed about command line advice is that nobody explains WHERE to enter the command line. I believe if this small detail were not so commonly assumed to be obvious by those who know, the command line would not be so frustrating to newbies. I did finally find [http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_run_commands_in_the_command_line_terminal](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_run_commands_in_the_command_line_terminal)
but am a little confused because it seems contradictory to the instructions in Ubuntu help for making internet connection changes, but those instructions were impossible....again, "enter command line" but no field in the window specified to do so.

Please keep in mind that I am very new to this and may need something I can print out and take home to follow. Once online I'm sure my adventures will go a bit more smoothly. Is there a way to get madwifi working in Ubuntu from the CD? 

I also have the NETGEAR CD that came with the card but have not been able to identify the driver on it. I would be greatly appreciative of any advice that can get me online.

---

### Post by RedSquirrel on 2007-10-25
To enter commands in the terminal, you type them in at the prompt, which is the line that ends in $. You can also paste them (see the menu: Edit -> Paste).

This might help:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

I can't help with the wireless issue. Sorry.

---

### Post by Hospadar on 2007-10-25
also, you can install madwifi from the repositories, so you probably don't need to do any custom installing to get madwifi working.

System->Adminstration->Synaptic Package Manager->search for "madwifi" and install the "madwifi-tools" package.

---

### Post by Hospadar on 2007-10-25
Oh, also for command line stuff, you should open up a terminal, Applications->Accesories->Terminal

You can enter command line stuff here.

---

### Post by Luxx on 2007-10-26
System->Adminstration->Synaptic Package Manager->search for "madwifi" and install the "madwifi-tools" package.

This was one of the first things I tried and it said there was no package found. 
Thank you for confirming the terminal is where the command line is used. I'm sure that seemed pretty redicuclous.

After playing in the terminal with things I don't understand in the madwifi files (nothing seemed to work according to anything I found in the readable files), I accidently found myself online. I have NO IDEA what I did. Initial problem fixed :) but no understanding of how or why. :confused:

---

