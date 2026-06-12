---
title: "help with command lines, upgrades"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by SR_Judd on 2007-06-19
So I just got ubuntu installed on my macbook with everything working. I just got some directions on how to change my resolution among many other things but I have no idea how to follow them. The instructions just give me a command line that i have no idea how to use like this: 
sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution

What am I supposed to do with that? I was also thinking about upgrading to beryl very soon, should I learn the OS a little more before I do so, or does it matter?

---

### Post by KIAaze on 2007-06-19
Do you know what a terminal is and how to use it?:
[http://www.psychocats.net/ubuntu/terminal]("http://www.psychocats.net/ubuntu/terminal")

Once you know how to open the terminal, all you have to do is basically paste the command-lines into it and press enter after each one. :)

> I was also thinking about upgrading to beryl very soon, should I learn the OS a little more before I do so, or does it matter?

You should certainly learn [the basics of how to use command lines]("http://www.tuxfiles.org/linuxhelp/cli.html").
Beryl can be installed just by clicking now however.

Open the "Synaptic package manager" (in System->Administration), search for "beryl", check the main package and click "apply".
Hopefully, you won't have any hardware acceleration issues.
Otherwise...well...you might need to learn more, like the command line for instance (and do some googling of course). ^^'

So, yes, you should learn the OS a little more before moving on I think.

_Note:_
Ubuntu Feisty comes with a 3D desktop by default: Compiz.
Just go to System->Preferences->Desktop Effects, click the &#8216;Enable Desktop Effects&#8217; button.

---

### Post by Tomosaur on 2007-06-19
Commands like that are supposed to be typed into a terminal. To get a terminal, click Applications, then Accessories, then Terminal. Paste the commands in one line at a time. The first command will ask you for your password, because it uses the 'sudo' prefix. This means that the command needs root privileges. Type in the same password you use to log on, but be sure to spell it correctly, because you won't 'see' it being typed in. The other commands probably won't ask you for your password, because by default sudo keeps you 'logged in' for about 15 minutes. You will still need to use the 'sudo' command, however, otherwise the command will be run with ordinary, non-root privileges.

---

### Post by crimesaucer on 2007-06-19
You copy and paste into your Terminal...and Beryl isn't that difficult.

---

### Post by wormser on 2007-06-19
You put those commands into the terminal (aka shell).

Applications> Accessories> Terminal

---

### Post by SR_Judd on 2007-06-19
Alright, I got it. Thanks a bunch

---

### Post by aeiah on 2007-06-19
the 'sudo' part gives you super user powers (**HURRAH!!11**) for the proceeding command. apt-get is the program that is used to download and install software from the repositories. the program synaptic is basically a front end for apt-get.

basically the commands do this:

sudo software-properties -e universe  <- this adds the universe repository to your repository list. its just a bigger stash of programs than the standard repository

sudo apt-get update <- this makes sure your catalogue of software is up to date

sudo apt-get install 915resolution <- this downloads and installs the program '915resolution', which i assume is what you need

you can type these commands in the terminal, one by one, pessing enter after each to run the command. the terminal is located at accessories > terminal

---

### Post by aeiah on 2007-06-19
christ im slow today. i might as well not bother :p

---

