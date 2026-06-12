---
title: "GUI for server installation (7.04)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by 5circles on 2007-07-05
I suspect this is a dumb question, but the installation documentation doesn't make it very clear.

I installed the server version of Feisty Fawn.  It doesn't appear that there is any GUI installed or configured.  When I try to run startx, the message is that it is not installed.

If I want to use a graphical interface for administration, do I need the desktop version instead?  Do I lose any server features or performance?

Thanks

---

### Post by whizbaby on 2007-07-05
A server, to most people, is a machine where ONLY the services it provides should run. Any other process is a potential security risk, so on a real server you are likely not to find any Xserver...
Yes, you'll have to get the desktop for X, allthough I wouldnt recommend to run a server on that.
Terminal administration is not only easy to learn, it rocks!

---

### Post by mjwhitfield on 2007-07-05
Installing a desktop will of course lower the performance of your server, as you are taking resources from serveing.

What will the server be used for?

---

### Post by vbmds on 2007-07-05
The server edition by default does not come with a GUI - as I found out a while back...you can install a desktop GUI if you want via the```
 sudo apt-get install ubuntu-desktop
``` (I think thats right) console command - thats about 450MB download though.

Another alternative I read about is to install the ubuntu desktop edition - normal ubuntu, then install required server stuff and then once your all setup, disable the GUI from starting. This is the option I'm going to follow in the next week or so.

---

### Post by 5circles on 2007-07-05
Thanks for all the clarifications and suggestions.

I've decided to start with the desktop and add server features.  I'm not sure that everyone would agree with the position of servers having no GUI, but for me it is a matter of easy administration without taking too much time to learn how to do everything from the terminal.  I've got years of dabbling with *ix, but I usually find that the newer features are best used from the GUI.  Of course that doesn't always solve everything, but it works most of the time.

This machine is going to be the only Linux machine on my home LAN for the moment, so I'm not too worried about performance.  But disabling GUI stuff later will work too.

Thanks

---

### Post by az on 2007-07-05
> **5circles said:**
> Thanks for all the clarifications and suggestions.

I've decided to start with the desktop and add server features.  I'm not sure that everyone would agree with the position of servers having no GUI, but for me it is a matter of easy administration without taking too much time to learn how to do everything from the terminal.  I've got years of dabbling with *ix, but I usually find that the newer features are best used from the GUI.  Of course that doesn't always solve everything, but it works most of the time.

This machine is going to be the only Linux machine on my home LAN for the moment, so I'm not too worried about performance.  But disabling GUI stuff later will work too.

Thanks

Actually, installing a desktop does not provide you with any tools to configure or run your server.

Also, if you ever want to install the desktop on top of a server install, I suggest you install the generic kernel instead of running the server kernel.

sudo apt-get install linux-generic

---

### Post by Seisen on 2007-07-05
Why don't you do a server install and then add a lightweight WM like fluxbox and then add what applications you need instead of bloating your server.

---

### Post by whizbaby on 2007-07-05
So one simple question:
if you are not comfortable with terminal, what do you do if the GUI doesnt show up again (like it did in a certain dapper upgrade if you had an nvidia card like I had)? When something doesnt work its nice to have only a handful of processes to watch over...
Again, a server with important services (how important are yours, do you get money from it or is it private?) doesnt neither need nor want an xserver.

---

### Post by fjanon on 2007-08-09
> **vbmds said:**
> The server edition by default does not come with a GUI - as I found out a while back...you can install a desktop GUI if you want via the```
 sudo apt-get install ubuntu-desktop
```


[!! New to Linux !!]

I installed a 7.04 server on a machne and I need to get a GUI running to install Java, Tomcat and mySQL.

I ran the "sudo apt-get install ubuntu-desktop" command but now how do I get the desktop to run from the ubuntu-server prompt?

Thanks

Fred

PS: I looked and searched all around the forums without finding the info, if there is a thread with the answer I'll be glad to use it.

---

### Post by whizbaby on 2007-08-09
/etc/init.d/gdm start
(or '/etc/init.d/kdm start' resp. if you installed kubuntu)

Just go on setting up desktop computers and calling them 'server'...

---

### Post by RavUn on 2007-08-09
Is there no way to go through SSH to work on your server from a seperate desktop?  Isn't that what Putty or WinSCP does? or is that just for other stuff?  If so, what do they do???

---

### Post by fjanon on 2007-08-09
> **whizbaby said:**
> /etc/init.d/gdm start
(or '/etc/init.d/kdm start' resp. if you installed kubuntu)

Thanks for that.

> Just go on setting up desktop computers and calling them 'server'...

Would you mind expanding on that?

Thanks

Fred

---

### Post by tomutal on 2007-08-09
> **fjanon said:**
> Thanks for that.

[QUOTE=whizbaby]Just go on setting up desktop computers and calling them 'server'...

Would you mind expanding on that?

Thanks

Fred[/QUOTE]

Obviously whizbaby thinks that installing a desktop configuration on top of a server doesn't make sense. One should decide if one needs a server (no GUI) or a desktop and install the appropriate OS version. Can you contradict him?

Now, it hapend that I've installed a server (I've like the idea of having a LAMP installed in one go) then I've realised that since I am not that much of a linux geek I cannot manage without a GUI and a Firefox (so I can look for help when I need it). So, now I've installed the desktop on top of that and, well, all goes nicely but now I'm looking around for a way to do the following:

- have the computer boot in text mode (server)
- when needed start the GUI (startx) and do whatever task might be needed
- once the task completed also terminate the GUI and release resources

So, the concrete questions:
- what configuration file should I edit in order to remove the GUI from the startup sequence?
- how do I stop the GUI once it is no longer needed?

Dudes, I hope you can help me with this one.

Best regards,

---

### Post by lonetree on 2007-08-10
What's wrong with having GUI on a server machine? performance on speed? security? or what?

I agree with some of you that it isn't easy to administrate a server with no GUI, especially those that are new to linux and wish to learn about linux, having no GUI may cripple their abilities to obtain helps and resources from the web. I recently found one distro that has been made as a server with GUI and with many services that can be chosen.I am using that to learn and apply some of the knowledges on ubuntu and vice versa.

---

### Post by ABell on 2007-08-11
Anyone who says absolutely that a GUI should never be part of a server installation is just wrong, wrong, wrong.  How many thousands of Redhat and Suse installations, not to mentions Microsoft installations,  are in PRODUCTION around the world right now that have a GUI accessible?  Because they pack a GUI are they less secure?  No.  Less robust?  No, not not with multiple and/or multi-GHz processors.  So all this talk about a server being defined by the absence of a GUI is nonsense.  If having a GUI makes it easier for you to secure (and see that you have secured) your OS, apps, and data, then run a GUI-based installation.  If the Ubuntu "community" is predominated by interface snobs, then it's not a very welcoming community.  Given the state of computing skill and the tilt toward Microsoft in the general population, I welcome anybody who says, can you help me understand how Linux works?

---

### Post by PopcornEaterMan on 2007-08-12
I agree with tomutal.  I am in much the same situation.  I would like to release the gui related resources when I cannot figure out how to get something done with the command line alone.  Some of us are very limited on time; we have kids, work, school, or permutations of the above.  We may not always have the 1 or 2  hours spare to figure out what command line utilities exist and how to use them.  For some of us, it is a stretch to install and operate a linux system at all.

I have a full time job as a software developer, I'm getting my master's degree in CS, and I am planning a wedding. For people like myself, we just don't have 10 hours spare to learn the ins and outs of a text editor such as vim, when you can simply fire up a gui and fire up gedit instead.   It may take people like myself over a week to accumulate 10 hours of free time.  In my youth, sure, I would have gladly spent 10 hours in a single session on something like this.  But now, things are different for us, sometimes you just need to get stuff done.

So I ask the same question as people before me. Please help us out.  I've left Ubuntu before, frustrated with dealing with linux snobs.  
I have installed the Desktop with Apache, php, mysql, but I'm almost out of memory.

How can we stop our GUI so that we can run the server without the GUI?
How can we fire it back up again when we run into problems again?
How can we configure the system to boot into command line mode?
How can we configure the system to boot into GUI mode?

Again, we really appreciate the help of the community.  Without you, I wouldn't have even considered coming back to Ubuntu.

---

### Post by alan34 on 2007-08-12
To stop the desktop

Ctl Alt F1

Login

sudo /etc/init.d/gdm stop

To start the desktop

sudo /etc/init.d/gdm start - takes you to the login screen

Try "ps ax" and "top" commands (no quotes) in a terminal before stopping the desktop to see what services are running and then after you have stopped the desktop to check for released resources.

---

### Post by whizbaby on 2007-08-12
> **ABell said:**
>   How many thousands of Redhat and Suse installations, not to mentions Microsoft installations,  are in PRODUCTION around the world right now that have a GUI accessible? 

probably too much
> 
 Because they pack a GUI are they less secure?

YES
> 
  No.  Less robust?  No, not not with multiple and/or multi-GHz processors.  So all this talk about a server being defined by the absence of a GUI is nonsense. 

Ah yeah? What is then with gui problems? What is, when your GUI hangs?
> 
 If having a GUI makes it easier for you to secure (and see that you have secured) your OS, apps, and data, then run a GUI-based installation.  If the Ubuntu "community" is predominated by interface snobs, then it's not a very welcoming community. 
Im just saying: use the right tool for the appropriate work. Im not a console fetishist. Im using it because I NEED it.
Just to give you a death scenario (mentioned above):
Your servers service is down and your GUI hangs. What do YOU do to repair/check your server? Restart  and hope it will come up? Reinstall your OS? Still feeling smart?
THINK before you start to almost insult people.

---

### Post by whizbaby on 2007-08-12
> **lonetree said:**
> What's wrong with having GUI on a server machine? performance on speed? security? or what?
Main thing is security. A GUI comes with a load of known and unknown bugs. The less software you are running on the server, the more likely it is to only fail when the service itself fails or hardware is broken.
Next, look at my reply to ABell, if the GUI fails and you are entirely dependant to using it to talk to your machine, then you would have a problem (you wont even have to think about without GUI).
So if you are using GUI, you need to know how to do stuff in console too. Using a GUI because of not-knowing how to do it in console will simply not make you use the console.

---

