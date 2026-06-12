---
title: "Ubuntu Server - setup help"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by CallMeDerek on 2007-05-29
I am wanting to migrate an old windows 2000 file and print server to Ubuntu Server.

I currently have two workstations running Kubuntu and am very comfortable with the GUI and basic commands but rely heavily on “Cut and Paste” when it comes to exorcizing my command line dependant work.

There in lies the rub...  I install Ubuntu server, get the prompt then...

Go across the room, lookup something... write it down...Type it in... mess it up...  go back to a desktop look up another option... write it down... etc...

Bottom line I have no idea what I am doing and not having a web browser handy with the terminal window from my server is very problematic.
Not having the system resources to run a GUI and share the desktop easly is really compounding my challenges.

So all that background for two simple questions.

 - Is there an easy way to install some type of remote terminal that I can access my server command line from a desktop?

 - Is there a simple concise guide on setting a simple file and print share server for Linux and Windows workstations?  Thinking I only need CUPS and SAMBA but I need “command line” configuration vs the nice and simple GUI setups.


Thanks in advance~

---

### Post by Dr Small on 2007-05-29
> - Is there an easy way to install some type of remote terminal that I can access my server command line from a desktop?

You could setup openssh-server, be at  your other computer and run the shell commands :)

Dr Small

---

### Post by dfreer on 2007-05-29
> **CallMeDerek said:**
> 
 - Is there an easy way to install some type of remote terminal that I can access my server command line from a desktop?

 - Is there a simple concise guide on setting a simple file and print share server for Linux and Windows workstations?  Thinking I only need CUPS and SAMBA but I need “command line” configuration vs the nice and simple GUI setups.

- SSH
Install it with:
```
sudo apt-get install openssh-server
```
You can then, from the client machine, type:
```
ssh *remote_username*@*server_name_or_IP_address*
```
it should ask you for your remote user's password and bing! you have access the terminal from any linux machine/windows machine with an ssh client installed

- For your other question, check out the ubuntu guide link in my sig. You will need to click on the guide for your ubuntu version (my sig linnks to feisty 7.04), but it should have all the commands you need to set up file sharing. print sharing too PROVIDED your printer even works with linux in the first place but that is another matter :D

Welcome to ubuntu!

---

### Post by stalker145 on 2007-05-29
I was going to say the same as dfreer. Once you're into your SSH session, you can <ctrl><Shift>V to paste into the terminal right out of the web pages... sweet.

Also, there's ```
sudo aptitude install webmin
``` if you want to control everything from a web interface. Just this last week i finally got around to setting up a CLI server with SSH and Webmin for those times when I can't be bothered trying to figure out the command line.

Have fun and check back if you have any trouble.

---

