---
title: "shutdown / reboot hangs -- help please"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-09-01
Hello all,

In installed smb for some file sharing and now when I shutdown or reboot the computer hangs on shutting down the smb (samba) service. Can someone give me some guidance on how to resolve it?

Regards,

Joe Hildreth

---

### Post by GMachine_24 on 2007-09-01
Hey - you need to give us more information.

1. Which version of Ubuntu are you running.
2. When you say you 'installed' Samba what did you do? Did you do the apt-get install samba routine and then configure the smb.conf file and if you did what are your smb.conf file settings? Did you set up a Samba user password?
3. Do you get an error message? If so, what is it?
4. Does your Samba set up work? Can you see your shared files on other computers?

Did you search the forums for possible answers from others who have had similar problems?

More information such as this would be helpful - if the computer is attempting, but failing, to stop the samba daemon there is, of course, a reason why. Let us see what you did - in detail - because right now it's sort of anyone's guess.

--gm

---

### Post by wjhildreth on 2007-09-01
You are right. I must have brain farted. Let me give better explanation.

I enabled SMB file sharing to allow some file sharing between two Ubuntu boxes, both running 7.04.. (So the system installed what ever was required to make that work). That all seems to work fine. When I go to shutdown the machine that shares the files, it stops the HP Linux Printing and Imaging system, then tells me "Stopping Samba Daemons" and just puts "." (periods) on the screen. It never shuts down. Now, I am running Feisty Fawn (v. 7.04).

Where do I need to look to help find the problem? Any guidance for this newbie?

Warm Regards,

Joe Hildreth

---

### Post by loaderboy on 2007-09-01
been working on a similar problem for two days now. Running ubuntu server 7.04 w/GUI on top and can't get the system to shut down. Seems to be a common problem with machines built prior to 2000 that don't have apci bios enabled I think
I have tried to set up APM in /etc/modules and still no luck.
I will keep searching and if I find the answer I will post here.:(

---

### Post by wjhildreth on 2007-09-01
This is a Toshiba Satellie, but it is newer than 2000. This started after enabling smb file sharing. I guess I can disable it and try that way. I thought maybe there was a lo0g or something I could look at.

Joe

---

### Post by GMachine_24 on 2007-09-02
Hey - when you say you 'enabled' Samba file sharing what, precisely, did you do?

You can shutdown the computer, or at least attempt to, by 

<code>

user@computer:~$sudo shutdown now -r
password: xxxxxx

</code>

You might see more info on your screen as the computer attempts to shut down - and restart (the 'r' is for restart). If you just want the machine to shut down replace 'r' with 'h' (no quotes). 

You also might try to stop and start samba from the command line - very simple - as in:

<code>

user@computer:~$ service smb start
user@computer:~$ service smb stop
user@computer:~$ service smb restart

</code>

Obviously if the Samba daemon starts on boot you'd want to skip the first step.

--gm

---

### Post by wjhildreth on 2007-09-02
GMachine:

I went to places | home folder, right clicked the folder I wanted to share and selected share folder.

Entered my password.

In the share folder dialog for share through, I selected "Windows Network" (SMB) unchecked read only and clicked OK.

=============================

Now when I issue:

```


sudo shutdown -r now


```

from the terminal I get what looks like a series of startup messages:

* Starting portmap daemon...
* Already running.
* starting CUPS

...

* Checking battery state
* Running local boot scripts (/etc/rc.local)

Then hangs.

Let me force a cold reboot and I will post the rc.local file

Joe

---

### Post by wjhildreth on 2007-09-02
Here is my rc.local file.

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

Regards,

Joe

---

### Post by GMachine_24 on 2007-09-02
Hi:

Ok, you haven't set up Samba. There are many "how tos" of course but basically you need to do at least these things:

First, make sure the Samba package is installed. To do this:

<code>

user@computer~$sudo apt-get update
password: xxx

</code>

Then

<code>

user@computer~$ sudo apt-get install samba

</code>

Even though you probably have a Samba folder at /etc/samba you will need to install the program - so you will have a smb.conf file to configure, and other things.

The install should be short and sweet.

Then, I recommend for you to configure your smb.conf file using the command line. Before you do anything to this file - found at /etc/samba - cd at the command line until you are in the /etc/samba folder and then copy the existing, default smb.conf file in case you need to refer back to it.

<code>

user@computer~$sudo cp smb.conf smb.conf.old

</code>

This is the code if you are in the /etc/samba folder. If not, you need to put the path to the smb.conf folder in otherwise Linux won't know what to copy.

Now, I could go on, but there has been so much written about all this that it's pointless. I usually refer people here:

[http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590)


It is an article about building a terabyte back up system using Samba, and it contains basics on setting up Samba. You can ignore the part about ssh encryption, etc.

You will need to configure the smb.conf folder - and also a samba password.

The article above will show you how to create a samba user name and password. your samba user name must be a user name on the linux box where you installed samba.

The article can also show give you the basics of creating a samba share. You must remember to enable the samba share for read/write (write only if you want others to be able to write to it). This will bring you in touch with the "chmod" (change mode) command. I use chmod 777 because it enables read/write at all levels - which is because I use my Samba files for back ups and restores and similar.

As I said, there are many other resources for samba configuration- I think ubuntu's is complicated and confusing. once you get the hang of it you can configure a samba share in less than 10 minutes, easily.

good luck.

--gm

P.S. Before beginning, it might be a good idea to undo the original "enable" that you did. Linux might see the share and be searching for samba, which, as i said, i'm guessing isn't installed.

---

### Post by Pumm4 on 2007-09-02
Not surprisingly, the Web provides an excellent source of additional information about Samba. Somewhat surprisingly, the Samba project itself provides some excellent documentation, as well as an online version of a great book about the current version of Samba, which is Samba version 3. You can install your own copies of the Samba documentation by installing the samba-doc and samba-doc-pdf packages when you install the Samba server. For more information, consult any of the following:

[SIZE=4]*****[/SIZE] [[FONT=Arial][SIZE=3]www.samba.org[/SIZE][/FONT]:]("http://www.samba.org:") The main site for the Samba project, at which you can find the latest tips, tricks, and source code.
[B]
[SIZE=4] *[/SIZE][/B] [FONT=Arial][SIZE=3]/usr/share/doc/samba-doc/htmldocs/Samba3 - HOWTO[/SIZE][/FONT]: A directory containing a HOWTO file in HTML format that explains how to install and configure Samba version 3, and answers many common questions. (You&#8217;ll want to open the file index.html in this directory from your Web browser.) The HTML version of this document is provided in the samba-doc package.
[B]
[SIZE=4] *[/SIZE][/B][FONT=Arial][SIZE=3] /usr/share/doc/samba-doc/htmldocs/Samba3[/SIZE][/FONT][FONT=Arial][SIZE=3]- ByExample[/SIZE][/FONT]: A directory containing an HTML version of an excellent, hands-on book about Samba 3. This book was written by John Terpstra, one of the leaders of the Samba project, and explains how to install and configure Samba 3 for a complete spectrum of networked environments, from smaller SOHO environments to enterprise environments with thousands of users. (You&#8217;ll want to open the file index.html in this directory from your Web browser.) The HTML version of this docu- ment is provided in the samba-doc package.

If you don't find this post useful, just ignore it [IMG]http://www.mysmiley.net/imgs/smile/winking/winking0050.gif[/IMG]

---

### Post by GMachine_24 on 2007-09-02
Yeah.... what he said......


:)

---

