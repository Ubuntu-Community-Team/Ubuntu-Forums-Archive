---
title: "How do i install a .tar file?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Lameboy on 2006-10-12
Hi!

I need to install a .tar file. It's a program i downloaded, sbackup. The extracting was the easy part.

But now..how do i install this thing? I'm using ubuntu desktop, but help using terminal would also be appreciated..

arigato gozaimashita!!!!!

---

### Post by Bachstelze on 2006-10-12
Why didn't you just *sudo apt-get install sbackup* ?

---

### Post by Tamil on 2006-10-12
[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

---

### Post by jethro10 on 2006-10-12
As stated, most prog's are in synaptic, including this one. Use that its much easier.
If however the program is not in the Synaptic system, or its a really old version, go to [http://www.getdeb.net/](http://www.getdeb.net/) and see if the .deb is there, then just double click it to install.

Downloading tar's and installing from source or raw binaries is a last resort for a newbie.

J

---

### Post by xyz on 2006-10-12
Terminal for Beginners
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

to start with! Good luck.

---

### Post by Lameboy on 2006-10-12
Ok thx guys, the only prob is i havn't got a clue how to use sanaptic to install this program that i downloaded. All i need to know in ubuntu is how to install files. 

Say for ex. if you download a game, or like in my case a backup program in .tar format and you extracted it to the desktop. Step by step what do you do?

Forgive my windows mind.](*,)

---

### Post by xyz on 2006-10-12
Click on System > Administration > Synaptic Package Manager > Search > type in: sbackup... and wait!
then right click on it to get "Mark for Installation.
Hope this is clear enough! Good luck."

---

### Post by PriceChild on 2006-10-12
This is a good all round guide to install anything.

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by Toxicity999 on 2006-10-12
Synaptic is just a pretty face for apt-get. apt-get is a deb fetching terminal program. If you already know the name of what you want you can use:

sudo apt-get install programhere

so in your case,

sudo apt-get install sbackup

would be the ticket. Just to help you out with the terminal side of things it's a nice shortcut ocne you get more into it all.

---

