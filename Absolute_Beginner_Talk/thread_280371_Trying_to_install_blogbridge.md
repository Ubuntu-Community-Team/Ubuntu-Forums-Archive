---
title: "Trying to install blogbridge"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by lutzman on 2006-10-19
I'm very new to Ubuntu and trying to install Blogbridge. The site for Blogbridge offers a Linux version which I downloaded as a .tgz and extracted to a folder which includes a .sh file. 

I read the guide 'How to install ANYTHING in Ubuntu!' at *[http://htmldesign.dk/blog3/ubuntu/installing/#script](http://htmldesign.dk/blog3/ubuntu/installing/#script)* but find that the instructions for installing with the .tgz and .sh don't work for me.

From the folder the 'make' and 'sudo checkinstall' both return messages *command not found* and when I try the sh blogbridge.sh command I get a message including
[I]Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
[/I]

I tried updating sun-java5-bin and sun-java5-jre but still get the same response.

Any ideas where I'm going wrong.

---

### Post by DarkN00b on 2006-10-19
You need to install the "build-essential" package in Synaptic. Then open a terminal window and go to the directory where you saved the files and type:

```

./configure
make
```

If you have any more problems, just post 'em here. Someone will be glad to help.

---

### Post by lutzman on 2006-10-19
Thanks for that, when I try the ./configure I get
*bash: ./configure: No such file or directory*
and with make
*make: *** No targets specified and no makefile found.  Stop.*

Out of interest, why is the need to install the "build-essential" kept such a secret? If it's needed to run third party installs, shouldn't it be part and parcel of the main operating system. I don't want to come across as bitter, but this is just one of the problems I am having with installing Ubuntu. I am trying to remain positive, but it is getting more difficult when you come from a world where installing software just needed a double click.

---

### Post by DarkN00b on 2006-10-19
You would think it would come installed by default. I have no idea why it isn't.

As far as your current problem, I can't help. The one time I got something to compile with no errors it completely ruined my video and I had to reinstall.

That's what I get for using official drivers huh? ](*,) :mrgreen:

---

### Post by lutzman on 2006-10-19
Thanks anyway. I'll revisit this problem tomorrow. Maybe the faries will fix it overnight.[-o<

---

### Post by marlowe on 2006-12-19
Hi lutzman.

Hope you've fixed your problem by now, but I just stumbled onto this thread, so here's some info that may help you if you're still struggling.

Although you'd normally be absolutely correct in your approach of
```
./configure
make
make install
``` BlogBridge doesn't need any of that. It's a native java application, so you don't need to compile it for your system (that's what ./configure etc does). Once you've un-tarred the archive (which you say you've done already, but ```
tar -zxvf foo.tgz
``` if you haven't), you can run it by simply executing the shell script (the file that ends in .sh).

Shell scripts are simply text files with a list of commands to be executed by the system. You can think of them as the equivalent of batch files in DOS or Windows (although they're far more powerful than that). In this case, the blogbridge.sh script tells the system to find your java installation, and then start the blogbridge application with it. You don't need to worry about the contents of the shell script, just run it from a command line like this:

```
$ sh ./blogbridge.sh &
```

The ampersand (&) after the command is optional, but if you include it it will allow you to continue using your command line terminal whilst blogbridge is running.

Some shell scripts will require root access to execute properly (although blogbridge doesn't). To execute a script like this, use the "sudo" command to temporarily gain root access:

```
$ sudo sh ./foo.sh &
```

You'll be prompted to enter your password, and then foo.sh will be run as root. As always, be very selective in what you choose to run if you're running as root. Danger, Will Robinson, especially if you just run random shell scripts without knowing what they do.

I hope you haven't given up on BlogBridge - it's a great RSS reader (and I've tried darned near every RSS reader ever written in my quest to find the perfect feed reader). Give it another try, and hit me back if you're still having trouble.

---

