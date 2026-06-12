---
title: "Installing Netscape Internet Service in Ububtu"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Temis on 2006-01-08
Hallo everybody, this is my first post.
I installed Ubuntu 5.10 with no problem. Just need to connect the internet.
I have a cd from netscape.ca ISP. This cd loads in Windows. On Ubuntu however it will not execute the program. It just shows the files when it is loaded. Is there anyway around it.

---

### Post by Terry of Astoria on 2006-01-08
I don't know but Ubuntu won't run windows programs natively.
You might want to check at the web site of your ISP to see if there's a linux version or instructions.

---

### Post by Temis on 2006-01-08
Unfortunately Netscape supports only Windows. That means I cannot connect to the internet via ubuntu. Too bad.

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=Temis]Unfortunately Netscape supports only Windows. That means I cannot connect to the internet via ubuntu. Too bad.[/QUOTE]
You can probably connect without the front end they provide you.  Is it dial up of broadband?

---

### Post by Temis on 2006-01-08
Only dial up is available here. My apologies for misspelling ubuntu

---

### Post by cwaldbieser on 2006-01-09
[QUOTE=Temis]Only dial up is available here. My apologies for misspelling ubuntu[/QUOTE]
You can probably pull the settings out of Windows that you need--  See if your Windows dialer has a configuration section in it.  You will need to pull out your phone number, username, password, and probably your DNS settings.

What kind of modem do you have?  Internal or external?  If you have the info available, you can try using "pppconfig" from the terminal.  It is a text-based wizard that an help you get connected.

---

### Post by Temis on 2006-01-10
Thank you for your reply cwaldbieser. I actually tried the procedure you outlined
before posting this thread. I tired it again without success.
I cannot get the modem connection to remain active. It deactivates as soon
I leave the set up. Not sure about the communication port setting.
My computers communication port is COM 1. But if I enter this value the modem does not activate. Not sure which one from the drop-down menu to choose. The 
autodetect feature cannot find the modem.

---

### Post by cwaldbieser on 2006-01-10
[QUOTE=Temis]Thank you for your reply cwaldbieser. I actually tried the procedure you outlined
before posting this thread. I tired it again without success.
I cannot get the modem connection to remain active. It deactivates as soon
I leave the set up. Not sure about the communication port setting.
My computers communication port is COM 1. But if I enter this value the modem does not activate. Not sure which one from the drop-down menu to choose. The 
autodetect feature cannot find the modem.[/QUOTE]
COM1 is /dev/ttyS0, COM2 is /dev/ttyS1, etc.

---

### Post by Temis on 2006-01-11
Hallo again cwaldbieser, I went through the set up once more, but the modem
connection deactivates as soon as I leave the set up. How would I tell ubuntu
to connect to the internet anyway.

---

### Post by canadianwriterman on 2006-01-11
If you're using Netscape's accelerated Internet service, I don't think you'll get it to work because it uses Slipstream software to achieve the acceleration.

---

### Post by Temis on 2006-01-11
I can disable the accelerator. My problem is connecting to the internet in first place.

---

### Post by safetycopy on 2008-07-08
I've been trying to get Netscape Connect to work in Hardy Heron, and it seems that the problem is authenticating my username/password because I can't find the domain used by the netscape software for this purpose... Aargh!

---

