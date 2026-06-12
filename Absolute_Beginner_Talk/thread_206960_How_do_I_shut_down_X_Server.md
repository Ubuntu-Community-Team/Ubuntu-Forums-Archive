---
title: "How do I shut down X Server?"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by BIZKeT on 2006-06-30
I have an A8N-VM mother board and have finaly figured out where to get the drivers and how to install them, but when I attempt to I get a message saying I need to shut down the X Server. I have been unable to find instructions on how to do so. I am a total noob with Linux but I am familiar with DOS level command line so I am not afraid of 'getting my hands dirty'.

I am really pleased with the OS thus far and _very_ pleased with the community. The entire reason I have avoided Linux for so long was because I have Linux snobs as friends. They are great people to hang out with but they can't seem to dumb things down enough for me. From what I have seen in the forums here, I think I will really enjoy my Ubuntu experience.

Thanks,
BIZKeT

---

### Post by batholith on 2006-06-30
> I need to shut down the X Server. I have been unable to find instructions on how to do so

Go to the terminal and type

$sudo /etc/init.d/gdm stop

That should shut down X server...

---

### Post by BIZKeT on 2006-06-30
[QUOTE=batholith]Go to the terminal and type

$sudo /etc/init.d/gdm stop

That should shut down X server...[/QUOTE]

WHen I enter that I get the message " * Stopping GNOME Display Manager...                                     [ ok ]
" but when I run the NVIDIA driver I still get the message to shut down the X server. Can I run the command you gave me through a terminal window, or do I need to be logged into just the command prompt? If the later, how do I do so? I can't find that option when I boot.

Thank you very much for the help Batholith!

---

### Post by Dr. Nick on 2006-06-30
If just needs X to be restarted then you could also just save your work and reboot the entire computer, should do the trick,

Also ctrl+alt+backspace will log you off which will work sometimes when something needs x restarted.

The above response should work aswell, never used it before so not sure where it leaves you. It may just leave you in a command line, in which case if you want to restart x just retype it and use "start" instead of "stop"

someone please clarify the above, I cant test it right now

---

### Post by Dr. Nick on 2006-06-30
Ah, you trying to get the nvidia drivers from nvidia.com working?

I remember trying that. 

Think I ended up doing something like this
[B]
sudo init 1

[/B]or 

[B]sudo init 3

[/B]if that doenst work then when you boot try using the recovery option, it wont start X

---

### Post by Jucato on 2006-07-01
If you are trying to install NVIDIA drivers, might I suggest you take a peek at this guide at the Ubuntu Documentation Storage Facility (UDSF)

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by batholith on 2006-07-01
> Can I run the command you gave me through a terminal window, or do I need to be logged into just the command prompt?

Yes, you should open up terminal and run the command..after which you'll automatically be logged off (since the display manager has been stopped) and you'll be able to continue with the driver loading...

> might I suggest you take a peek at this guide at the Ubuntu Documentation Storage Facility (UDSF)

Follow this guide, make sure you pay attention to the warnings and such (I'd read it through a couple times before implementing) and it should set you up nicely!

---

