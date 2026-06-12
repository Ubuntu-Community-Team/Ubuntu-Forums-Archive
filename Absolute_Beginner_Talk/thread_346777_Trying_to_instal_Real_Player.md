---
title: "Trying to instal Real Player"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Swerve1000 on 2007-01-26
Hi to all the Linux guru's,

I have just tried to install Real Player as the instructions from the site were simple, I got owned. The site for the download:-

[http://www.real.com/linux?pcode=rn&am](http://www.real.com/linux?pcode=rn&am)

This is what is occuring:-

Firstly I typed into the command terminal the following to make the .bin file an executable:-

chmod a+x realPlayer10GOLD10.bin

The result was this-

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/Screenshot.jpg[/IMG]

I figured out that this was because it had already been changed to an executable file.

So, next I typed this into the terminal to try and install it:-

./RealPlayer10GOLD.bin

The result was:-

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/Screenshot1.jpg[/IMG]

I did burn the downloaded file using windows to put it onto a disc, then rebooted into Ubuntu and copied it onto the desktop, if that makes any difference.

Any ideas? I'm complete noob.

Thanks

---

### Post by HereInOz on 2007-01-26
You need to use sudo in front of the chmod, and then put in your password when asked.

Hope this helps

---

### Post by Swerve1000 on 2007-01-26
> **HereInOz said:**
> You need to use sudo in front of the chmod, and then put in your password when asked.

Hope this helps


thanks, so the command will be the following? :-

sudo chmod a+x RealPlayer10GOLD.bin

Should I enter it exactly like that?

I was confused as when I put the mouse pointer over the file the little mouse pointer pop up said it WAS an .exe. Do I still need to put the sudo command in?

---

### Post by benson444 on 2007-01-26
Hi,

You need to change to the directory  where the file is located:

cd /home/simon/Desktop

Then change the mode:

chmod a+x RealPlayer10GOLD.bin

Then run the installer with sudo:

sudo ./RealPlayer10GOLD.bin

When you're asked where to install to, type "/usr/bin/RealPlayer" (without quotes), choose yes for symbolic links and just press return for where to put the links.

I got this method from a book I have on Ubuntu. It's always worked fine for me.

---

### Post by Swerve1000 on 2007-01-26
Thanks for taking the time benson444, 

It's really appreiciated. 

I hope you win the lottery! hehe

---

### Post by benson444 on 2007-01-26
No worries. It's nice to help out when I see one of the questions I actually know the answer to... :-)

---

### Post by Swerve1000 on 2007-01-26
OK, entering the first two commands, which were :-

cd /home/simon/desktop

and 

chmod a+x realPlayer10GOLD.bin

ended in error or not working as I  hoped.

I then tried the 3rd command which was

sudo ./realPlayer10GOLD.bin

This worked and I was prompted for my password, which I enetered but then nothing happened.

This what I then did afterwards:-

[IMG]http://i25.photobucket.com/albums/c77/Swerve1000/Screenshot2.jpg[/IMG]

I can't get it to work and I'm totally noob to the Ubuntu filestructure and commands

I must be doing something wrong.

Any ideas? :D

---

### Post by ComplexNumber on 2007-01-26
in your home directory, make a directory called something like realplayer, then move it from your desktop to there. then try installing it again. then  "cd"(ie change directory) in the terminal so that the terminal is in  that directory (ie enter "cd /home/simon/realplayer"(without the quotes))

btw i installed realplayer, and found it quite difficult to uninstall. there is an uninstall script which is available, but it is not officially supported by realplayer.

---

### Post by chettyk on 2007-01-26
If you notice, you have an error message when you use the chmod command itself. The error says it can't locate the file. It is not clear what exactly is going on. Could you type the following two commands in terminal and post the output:

```
cd /home/simon/Desktop/
ls -lh
```

The second command will show what files exist in the Desktop folders and also what their permissions are.

---

### Post by benson444 on 2007-01-26
Do what chettyk said. The "ls" command lists the contents of the current directory. One of the files should be the RealPlayer file.

I noticed that when you type the chmod command you type "realPlayer" instead of "RealPlayer". Linux is case sensitive and you need to put the commands exactly as written. A very useful tool is tab completion. Once you have typed in enough to uniquely identify a file or folder hit the tab key and the rest will appear automatically. eg.

chmod a+x Real

...then hit tab. If only one file in the directory starts "Real" then the rest will be completed for you. Very easy and very handy.

Also, as ComplexNumber said, you could move it to another place and try again.

Can't see why it doesn't work though. Double checked and don't think I made any mistakes.

---

### Post by s26c.sayan on 2007-01-26
Isnt Realplayer 10 available from the PLF or commercial repositories??

You may try the following:

[B]Step 1: Enabling PLF/Commercial repos

[/B]```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

```Append the following lines to the sources.list file that comes up:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free             
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                              
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

```You may have to change Edgy to Dapper depending on your Ubuntu version.

[B]Step 2 : Installing Realplayer

[/B]```

sudo apt-get update
sudo apt-get install realplay
```This should do it!!! Try it and see.....:D

**Reference: **[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

---

### Post by mtxrawkus on 2007-03-01
> **benson444 said:**
> Hi,

You need to change to the directory  where the file is located:

cd /home/simon/Desktop

Then change the mode:

chmod a+x RealPlayer10GOLD.bin

Then run the installer with sudo:

sudo ./RealPlayer10GOLD.bin

When you're asked where to install to, type "/usr/bin/RealPlayer" (without quotes), choose yes for symbolic links and just press return for where to put the links.

I got this method from a book I have on Ubuntu. It's always worked fine for me.


benson444, that worked. Nice list of to-do's for noobs like me.

---

### Post by wataboutbob on 2007-03-07
Thanks benson444, it worked for me too. But I'm wondering... why is real10 so crippled with its music library management when compared to its Windows brethren?

---

