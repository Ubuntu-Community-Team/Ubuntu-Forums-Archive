---
title: "Ubuntu Server - How to start a program on boot up?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by One_of_Six on 2007-06-22
Hi there. 

I have realy enjoyed the learning process of setting up Ubuntu Server - the first time I have used Linux.

I  have reached a point however where I need some help in understanding - How do I configure a program to start up and run each time the Server is booted up?

This is the situation:

I have a proxy server program called EchoLinkProxy.jar installed in /usr/local/echolink. It is started by entering the command:

"java -jar EchoLinkProxy.jar"

It works fine. The proxy server runs so long as the console is open. Close the console and the program stops.

What I want to do is configure Ubuntu to start the program at boot up (like my mailserver, ftp server and webserver do) and allow it to also run "in the background" continuously without the need for a console having to remain open

Can anyone please help me achieve this?

Many thanks

---

### Post by gustavocm on 2007-06-22
go to

System>Preferences>Sessions

in "Startup Programs" click on "New". In the "Command" text box you write:

java -jar /usr/local/echolink/EchoLinkProxy.jar

and in the "Name" text box you can put anything. Click on OK

That's it.
good bye

---

### Post by Quintin Riis on 2007-06-22
He asked how to start at boot, not login, although I don't know which he really wants.

You'd need to add a startup script to /etc/rc.d/rc2.d or so.

---

### Post by One_of_Six on 2007-06-23
> **Quintin Riis said:**
> He asked how to start at boot, not login, although I don't know which he really wants.

You'd need to add a startup script to /etc/rc.d/rc2.d or so.

Thanks for the reply. I want the program to start at boot so that it runs when no one is logged in. I will try your suggestion.

---

### Post by One_of_Six on 2007-06-24
> **Quintin Riis said:**
> He asked how to start at boot, not login, although I don't know which he really wants.

You'd need to add a startup script to /etc/rc.d/rc2.d or so.

Right, I've found the /etc/rc2.d directory and seen that it contains a number of script files which bring up each application at boot up. I took a look inside one script file to see how it is written with the hope of being able to write one for Echolink. At this point, my brain froze!

As this is the absolute beginner's forum, is there anyone who can point me in the direction of help so that I can write a script to start Echolink at boot up?

---

### Post by mattg89 on 2007-06-24
I'm pretty new to scripting, but try this:

```

#!/bin/bash
cd /usr/local/echolink && java -jar EchoLinkProxy.jar

```

Please someone say if there is something blindingly obviously wrong.

---

### Post by Quintin Riis on 2007-06-24
> **mattg89 said:**
> I'm pretty new to scripting, but try this:

```

#!/bin/bash
cd /usr/local/echolink && java -jar EchoLinkProxy.jar

```

Please someone say if there is something blindingly obviously wrong.
#!/bin/sh
java -jar /usr/local/echolink/EchoLinkProxy.jar 

..is proper.  

Also, the file should be in rc.d, and then a symlink to the file placed into the rc.2 directory.  Create symlinks like so: cd /some/dir ; ln -s /some/file

---

### Post by atria on 2007-06-24
The easiest way would be to edit /etc/rc.local and make sure that it is excecuted at boot by using sysv-rc-conf.

---

### Post by mattg89 on 2007-06-24
Yeh, that would be better. ^^

```
#!bin/sh
java -jar /usr/local/echolink/EchoLinkProxy.jar
```

Put that in /etc/rc.d

then do

```
ln -s /etc/rc.d/<filename> /etc/rc.2/<filename>
```

I believe that will work

---

### Post by One_of_Six on 2007-06-24
> **mattg89 said:**
> Yeh, that would be better. ^^

```
#!bin/sh
java -jar /usr/local/echolink/EchoLinkProxy.jar
```

Put that in /etc/rc.d

then do

```
ln -s /etc/rc.d/<filename> /etc/rc.2/<filename>
```

I believe that will work

Thanks for all the help. I have had a look (as root) in /etc and there is no rc.d file, only rc0.d - rc6.d, rc.local and rcS.d

I have run "find / -name rc.d" and nothing is found

---

### Post by mattg89 on 2007-06-24
Ah, I must have got the folder wrong.
Tbh, I'm not sure where to put it, or to put the symbolic link.
Argh.

---

### Post by arvevans on 2007-06-24
The various /etc/rc files are numbered to reflect the run-levels that they initiate.  If you look at the README files in each /etc/rc area you can see what they do and how they do it.  Your actual executable command will probably be put into /etc/init.d and then called from the appropriate /etc/rc file.  It depends on when you want to start the program.  By selecting the proper /etc/rc# file you can control whether it starts early in the boot process or toward the end.  FYI:  If you call it in the last /etc/rc# file it will be run at shutdown, not startup.
_._

---

### Post by One_of_Six on 2007-06-24
> **arvevans@earthlink.net said:**
> The various /etc/rc files are numbered to reflect the run-levels that they initiate.  If you look at the README files in each /etc/rc area you can see what they do and how they do it.  Your actual executable command will probably be put into /etc/init.d and then called from the appropriate /etc/rc file.  It depends on when you want to start the program.  By selecting the proper /etc/rc# file you can control whether it starts early in the boot process or toward the end.  FYI:  If you call it in the last /etc/rc# file it will be run at shutdown, not startup.
_._

Ok I think the advice is beginning to get the grey matter working...

If someone could cast their eye over the following for any problems:

I create a script (I'll call it RunEchoLInk) containing the lines:

#!/bin/sh
java -jar /usr/local/echolink/EchoLinkProxy.jar

I put the script in /etc/init.d

I create a link to /etc/rc2.d using the line:

"ln -s /etc/init.d/RunEchLink  /etc/rc.2/RunEchoLink"

Now when I re-boot the Ubuntu Server, the EchoLinkProxy.jar program will start and run until the server is either re-booted or turned off?

Any comments before I try it out? I don't want to mess up my server!

Many thanks

---

### Post by Quintin Riis on 2007-06-24
You're not going to mess up your server.  If you do, just undo whatever you did in the first place.  Pretty simple.

Rename the symlink to match to format of the other files.

---

### Post by One_of_Six on 2007-06-24
Right, using nano, I have created a file called  "RunEchoLInk" containing the 2 lines:

#!/bin/sh
java -jar /usr/local/echolink/EchoLinkProxy.jar

I put the  file in /etc/init.d

I then ran (as root):
ln -s /etc/init.d/RunEchoLink /etc/rc2.d/RunEchoLink

There is now a file in rc2.d called "RunEchoLink" which I assume is the simlink

so far so good"

Now when you say,

> **Quintin Riis said:**
> Rename the symlink to match to format of the other files.

 do you simply mean the format of the simlink's name? For example, in my rc2.d file, all the files are single words preceded by an upper case "S" and a number  between 1 & 99 e.g. S20samba, S20vftp, S91apache etc. I don't know what the prefix is all about - perhaps a priority or order of execution? if so what "Snumber" do I need for my RunEchoLink simlink?

---

### Post by Quintin Riis on 2007-06-25
[http://www.google.com/search?q=linux+boot+process&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=linux+boot+process&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by One_of_Six on 2007-06-25
Many thanks, Quintin. I found all I needed to know in the results from the google link you sent. I had tried Googling for an answer before coming on this forum but the search words I used did not come up with the result I needed. Perhaps I should learn more about how to use search engines before going any further with Linux hi!

---

### Post by Quintin Riis on 2007-06-25
Glad I could help.

---

