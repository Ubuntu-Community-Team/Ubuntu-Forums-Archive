---
title: "Install new version of Firefox [Resolved]"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by pete stahl on 2007-03-23
It took me a while to get connected to the internet with FF and Ubuntu and now I need to update the version of FF I'm using. I downloaded file firefox-2.0.0.2.tar.gz and don;'t know what to do with it. I was spoiled with the windoze version as it has a self installer. Is there a terminal command I need to do. Still very green to Linux.

thanks, Pete

---

### Post by docshawnc on 2007-03-23
Here's a script that I've used - works great and is a no fuss way to do it

---

### Post by mikewhatever on 2007-03-23
[http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)

---

### Post by Obor on 2007-03-23
if you wonder what to do with that script:
Download it to your desktop and paste these commands in the terminal:
```
cd ~/Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh
```
More info [here.]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by Bigadada_saba on 2007-03-23
sudo apt-get autoremove firefox
to get rid of the old ff
sudo apt-get install firefox
to install the new one
or
install automatix and install swiftfox from there and all its plugins:guitar:

---

### Post by docshawnc on 2007-03-23
Thanks Obor for the original link (couldn't find that) and further advise on how to execute .sh files - (didn't think of adding that)

---

### Post by Obor on 2007-03-23
> **Bigadada_saba said:**
> sudo apt-get autoremove firefox
to get rid of the old ff
sudo apt-get install firefox
to install the new one

That will not give him Firefox 2 on Dapper version of Ubuntu

---

### Post by lolwhites on 2007-03-23
I tried installing the new firefox using option 4 of the instructions [here]("http://www.psychocats.net/ubuntu/firefox") and when it got to backing up my old bookmarks I got this:

> cp: cannot stat `/home/laurie/.mozilla/firefox/t9mjx96t.default/sessionstore.js': No such file or directory
Previous command did not complete successfully. Exiting.


Any idea what went wrong?

---

### Post by pete stahl on 2007-03-23
I tried to use the script as posted above but this is what I get when I do it. Used cut/paste and also typed it in by hand.

ps@Techspec56:~$ cd ~/Desktop
ps@Techspec56:~/Desktop$ chmod +x installnewfirefox.sh
ps@Techspec56:~/Desktop$ ./installnewfirefox.sh
bash: ./installnewfirefox.sh: /bin/bash^M: bad interpreter: No such file or directory
ps@Techspec56:~/Desktop$

Thanks for all the replies so far, really appreciate the help.

---

### Post by pete stahl on 2007-03-23
Ok I deleted the script file tha docshawnc had in his post and used the one from the link in obor post. Went into the Terminal and tried it again and the script ran this time. Not sure if it worked or not because I haven't restarted firefox yet. Let you know if the new one shows up.

---

### Post by pete stahl on 2007-03-23
I ran the script again and at the end it says that the new firefox is installed but I go to the Help menu and it says I still have version 1.5, is there something else I need to do?

---

### Post by pete stahl on 2007-03-23
I used the command below and got the new FF but lost all the Bookmarks. Where are the bookmarks stored maybe it backed up the old version?


gksudo firefox &

Don't know what I did for sure as I restarted FF several times but my Bookmarks and History stuff is back. Hope this thread help someone as it helped me a lot. Thanks to all who replied and please add more stuff if you think of anything else.

---

### Post by wiseguy on 2007-03-25
> **Obor said:**
> if you wonder what to do with that script:
Download it to your desktop and paste these commands in the terminal:
```
cd ~/Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh
```
More info [here.]("http://www.psychocats.net/ubuntu/firefox")

Worked great. Doesn't get much easier than that. 8-)

---

### Post by watkinsted on 2007-11-10
ted@ted-desktop:~$ cd ~/Desktop
ted@ted-desktop:~/Desktop$ chmod +x installnewfirefox.sh
ted@ted-desktop:~/Desktop$ ./installnewfirefox.sh
bash: ./installnewfirefox.sh: /bin/bash^M: bad interpreter: No such file or directory
ted@ted-desktop:~/Desktop$ 

is what i'm getting, is there something I'm not doing right?

---

