---
title: "How to install Firefox... update?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Mygly on 2006-05-21
Hey everyone,
 I'm trying to install firefox 1.5.0.3 and i've downloaded the tar.gz. I extracted it into the tmp directory where the tar.gz was downloaded to. After doing so I fired up the terminal and navigated to the firefox diretory. ./configure yielded no results and told me there was no such file or directory. I proceeded to try to make it, but it said there was no make file found. I'm running firefox 1.0.7 right now and would like to update. Hope someone can help. I'd also like to update my gaim to 2.0 beta 3, it looks like those are all in rpm flavor. Here's my terminal jargon. Please help me. ```
mygly@ubuntu:/tmp/firefox$ ./configure
bash: ./configure: No such file or directory
mygly@ubuntu:/tmp/firefox$ make
make: *** No targets specified and no makefile found.  Stop.
mygly@ubuntu:/tmp/firefox$

```

---

### Post by aysiu on 2006-05-21
Delete the .tar.gz and the folder you got from it. Use this script instead. It's easier.

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by ubuntu_jazzbach on 2006-05-22
You don't have to delete anything !!!! Just untar the .tar.gz file in the /tmp directory (exactly as you did before) and change to that directory. Inside you're gonna find plenty of files. Find the one that says "firefox" and run it in a console: "./firefox" and voila !!!.

If you wanna have a "shortcut" in your desktop, just right-click on any place of the desktop and select "create launcher". Once done, click the "Browse" button that's in front of the "Command" text zone and go where the "firefox" bin is located (if you untar-ed firefox in /tmp, then you should select /tmp/<the name of the firefox directory>/firefox).

---

### Post by aysiu on 2006-05-22
[quote=ubuntu_jazzbach]You don't have to delete anything !!!! Just untar the .tar.gz file in the /tmp directory (exactly as you did before) and change to that directory. Inside you're gonna find plenty of files. Find the one that says "firefox" and run it in a console: "./firefox" and voila !!!.[/quote] Yes, you can just run it straight out of the folder, but...

1. Running the command *firefox* will run 1.0.7, not the new version.
2. None of your plugins will work (Flash, for example, if you have that installed).
3. Any program that calls on Firefox (say, your email client, if you click a URL) will not call on 1.5.0.3.

In other words, running it straight as is will not integrate it into your system in any way.

Use the script I linked to if you want any of that integration. If you hate scripts for whatever reason, follow this tutorial: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

My script basically automates the Wiki tutorial so you don't have to copy and paste every single command.

---

### Post by jason.b.c on 2006-05-22
Whats wrong with just using the automatic updater already installed in firefox.??

**Help** button / **Check for updates**

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=jason.b.c]Whats wrong with just using the automatic updater already installed in firefox.??

**Help** button / **Check for updates**[/QUOTE]

Sure you can if you want...

"The first way is to close Firefox and give your user (yourself) file ownership: sudo chown -R ${USER}:${USER} /opt/firefox Start Firefox normally and update (Help -> Check for updates...) Once the update is completed, close Firefox and then restore ownership to root: sudo chown -R root:root /opt/firefox Do NOT browse other sites while firefox has these elevated permissions, that is without changing back the ownership of /opt/firefox over to root. Such a practice is not safe."

or

"Note that the following alternative method may give some files in your home directory root ownership and cause problems. The first method above is safer. To update firefox you can run Firefox from the terminal with  gksudo firefox . Be sure to close any running version of Firefox first. Enter your password where prompted. Then check update (Help -> Check for updates...). It may prompt you to restart Firefox. When Firefox restarts you should see a Mozilla page confirming that you're using the latest version. Close Firefox and open it as a normal user (the way you usually open it). Firefox should now be updated to the newest version for all users. This way you don't have to change any file permissions and you wont forget to not change them back."

from [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

EDIT: Whoops, user is using 1.0.7

---

### Post by aysiu on 2006-05-22
[QUOTE=jason.b.c]Whats wrong with just using the automatic updater already installed in firefox.??

**Help** button / **Check for updates**[/QUOTE] 1.0.7 didn't have the automatic updater in it. That came with 1.5 [quote=mygly]I'm running firefox 1.0.7 right now and would like to update.[/quote] Yup. The automatic updater isn't going to help the OP.

---

### Post by jason.b.c on 2006-05-22
Yea, I guess this:>[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)  dosen't look so bad after all, Looks easy enough..:-D

---

### Post by aysiu on 2006-05-22
[QUOTE=jason.b.c]Looks easy enough..:-D[/QUOTE] That's why I wrote it. Without it, you have these other options:

1. Use Automatix
2. Be satisfied with 1.0.7 or 1.0.8
3. Install Dapper
4. Follow the Wiki instructions

Those aren't bad alternatives, but my script is the least involved.

Automatix is good if you want to also have a ton of other stuff (popular stuff, granted, but it changes up your repositories and installs another application, too--Automatix itself).

1.0.8 might patch up some security holes, who knows? But the OP wanted 1.5.0.3, so that won't do.

Dapper is a bit extreme. Oh, you want this application? Install a new operating system version, too. It probably will happen eventually, though, as the official release date is less than two weeks away.

The Wiki instructions are what I based the script on, so I know they work. They're just a pain to follow. Copy command. Paste command. Copy command. Paste command. *ad nauseum*.

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=aysiu]That's why I wrote it. 
Those aren't bad alternatives, but my script is the least involved.[/QUOTE]

I just tried it and it works flawlessly. Thank you aysui!

---

### Post by jason.b.c on 2006-05-22
> 1.
2.
3. Install Dapper
4.



So then dapper will have 1.0.5.3  already .?   From **Ship-It**.?

---

### Post by aysiu on 2006-05-22
[QUOTE=jason.b.c]So then dapper will have 1.0.5.3  already .?   From **Ship-It**.?[/QUOTE] Yes. I believe Dapper already has 1.5.0.3 right now.

---

### Post by geezerone on 2006-05-22
I have tried that script which displays the information as you have said but after installing and starting firefox the timer on the mouse displays for a few seconds but nothing happens? I uninstalled and it runs ok (as version 1.0.8 though).

---

### Post by aysiu on 2006-05-22
[QUOTE=geezerone]I have tried that script which displays the information as you have said but after installing and starting firefox the timer on the mouse displays for a few seconds but nothing happens? I uninstalled and it runs ok (as version 1.0.8 though).[/QUOTE] Next time you try the script and run Firefox, run it from the terminal and post the output back here.

Try running these three separate commands from the terminal:
```
firefox
``` ```
mozilla-firefox
``` ```
cd /opt/firefox
./firefox
```

---

### Post by Mygly on 2006-05-22
[QUOTE=geezerone]I have tried that script which displays the information as you have said but after installing and starting firefox the timer on the mouse displays for a few seconds but nothing happens? I uninstalled and it runs ok (as version 1.0.8 though).[/QUOTE]
This happened to me also. However, I still had the firefox tar.gz as well as the extracted directory sitting in my tmp. After deleting those and going through the process again (which only takes about 30 seconds) it worked perfectly and I could start getting the lovely extentions I had with my windows firefox that I can't live without.

---

### Post by clarkth on 2006-05-22
[QUOTE=bluevoodoo1]I just tried it and it works flawlessly. Thank you aysui![/QUOTE]

I just upgraded also with this script too.  Thank you!

---

### Post by Mygly on 2006-05-22
aysiu, if you don't mind me asking. What is that script written in? and Also, can you recmmend a good text editor for php, c, c++, javascript, perl, css, html, xml... I'd like to learn ruby as well, but I need to stick to the php path right now. Mostly need it for php, css, html, xhtml, javascript. Haven't really written in perl yet, the time will come though. I really liked PHP Designer, but it's windows only. Perhaps I should start a new thread in a different category?

---

### Post by mostwanted on 2006-05-22
[QUOTE=Mygly]aysiu, if you don't mind me asking. What is that script written in? and Also, can you recmmend a good text editor for php, c, c++, javascript, perl, css, html, xml... I'd like to learn ruby as well, but I need to stick to the php path right now. Mostly need it for php, css, html, xhtml, javascript. Haven't really written in perl yet, the time will come though. I really liked PHP Designer, but it's windows only. Perhaps I should start a new thread in a different category?[/QUOTE]

I'm not aysiu but...

From the .sh extension I'd wager it's a regular shell script.

Gedit is an excellent editor for many languages. I do all my Ruby, HTML, CSS, JS, even C# in Gedit.

---

### Post by aysiu on 2006-05-22
It is, as mostwanted said, just a simple shell script, and that's as close to programming as I get--there are no variables or complex procedures... it's just a bunch of commands, one after the other.

As for text editor, I use whatever's native. If I'm in Gnome, I use Gedit. If I'm in KDE, Kate. If XFCE, then Mousepad.

---

### Post by clarkth on 2006-05-22
[QUOTE=bluevoodoo1]I just tried it and it works flawlessly. Thank you aysui![/QUOTE]

I just upgraded also with this script too.  Thank you!

---

### Post by Mygly on 2006-05-22
I've run into a new problem, when trying to stream video from a site, like if there's a link to a video and I click on it. Firefox crashes, where when i would do this in windows VLC or the appropriate video player would open and play the stream. Any ideas?

---

### Post by aysiu on 2006-05-22
These two links should help you:
[http://www.ubuntuforums.org/showthread.php?t=103930](http://www.ubuntuforums.org/showthread.php?t=103930)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by geezerone on 2006-05-22
[QUOTE=aysiu]Next time you try the script and run Firefox, run it from the terminal and post the output back here.

Try running these three separate commands from the terminal:
```
firefox
``` ```
mozilla-firefox
``` ```
cd /opt/firefox
./firefox
```[/QUOTE]

My mistake, I am using AMD64 iso - oops! :rolleyes: I suppose I will have to wait for the 64 bit version. Also, is the update just selecting the US version as living in the UK I would presume this to be the more pertinent choice?

Cheers!!

Geezer

---

### Post by aysiu on 2006-05-22
You can use Swiftfox for AMD64:
[http://getswiftfox.com/rel-athlon64.htm](http://getswiftfox.com/rel-athlon64.htm)

I don't have a working install script, though, as I don't have AMD64 and, thus, cannot test it.

Do you want to be my guinea pig? ```
#!/bin/sh
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Firefox are installed
"
sudo apt-get -y install firefox libstdc++5
echo "
Backing up old Firefox preferences
"
cp -R ~/.mozilla ~/.mozilla_backup
echo "
Changing to home directory
"
cd
echo "
Downloading Firefox from the Mozilla site
"
wget -c http://getswiftfox.com/builds/releases/swiftfox-1.5.0.3-athlon64.tar.bz2
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -xvvf swiftfox-1.5.0.3-athlon64.tar.bz2
echo "
Removing the unzipped .tar.gz
"
rm swiftfox-1.5.0.3-athlon64.tar.bz2
echo "
Linking plugins
"
cd /opt/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
echo "
Linking launcher to new Firefox
"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/swiftfox/swiftfox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/swiftfox/swiftfox /usr/bin/mozilla-firefox
echo "
The new Firefox is installed."
``` Oh, and, yes, the script does download the US version. Are there noticeable differences between the US and UK versions? I guess I should probably put in some kind of warning about that or create a separate script for the British version.

---

### Post by jimrz on 2006-05-22
[QUOTE=aysiu]

In other words, running it straight as is will not integrate it into your system in any way.

 aysiu,

   I recently upgraded FF on both my desktop and laptop using your script. It worked beautifully and fast on both. Thank you. However, on both machines I had to manually change the System>Preferences>Preferred Applications in order to get other apps (noted this pretty quickly from links in Evolution and mail notifications in Gaim)to connect to the new 1.5.0.3. Once changed all works correctly. Not sure if this was missed by your script or if something in my Breezy setup prevented the script from making this change (did not note any error msg's at all while script was running or upon completion).

   In any event, it was no big deal to correct and, again, thank you for providing the script.

  -  jim

---

### Post by aysiu on 2006-05-22
Firefox still has to be your preferred application. The issue is really that even if you make Firefox your "preferred web browser," running Firefox straight out of the folder without integration will mean that Evolution will open version 1.0.8.

---

### Post by houseshadow on 2006-05-22
Nice!  I was apparently running 1.5.0.1 and this update script worked like a charm.  Nicely done, aysiu.

---

### Post by jimrz on 2006-05-22
[QUOTE=aysiu]Firefox still has to be your preferred application. The issue is really that even if you make Firefox your "preferred web browser," running Firefox straight out of the folder without integration will mean that Evolution will open version 1.0.8.[/QUOTE]

aysiu,

   After script ran Preferred Aps/Web browser had " Custom" command firefox %s and Evolution/Gaim did not find the new one, nor did they open an instance of the old one. When I selected the radial button for "Select" and then used the drop down to select Firefox (as shown in attached screenshot) all worked as it should using the new version of FF.

Jim

---

### Post by aysiu on 2006-05-22
Let me see if I understand this.

So ```
firefox %s
``` didn't work but ```
firefox
``` did? What happened when you used ```
firefox %s
```? Did it even try to load up? Or did it load up weirdly? I'm just curious.

---

### Post by jimrz on 2006-05-22
[QUOTE=aysiu]Let me see if I understand this.

So ```
firefox %s
``` didn't work but ```
firefox
``` did? What happened when you used ```
firefox %s
```? Did it even try to load up? Or did it load up weirdly? I'm just curious.[/QUOTE]

Did not ever enter manually. Rather I clicked on a link in Evolution, went to another workspace where the new FF was running expecting to find the link I had clicked in a new tab. About the same time I realized there was no new tab, Gaim popped a notification of new e-mail @ my yahoo acct, so clicked open mail. This also should have opened a new tab. In both cases nothing happened at all. I found no other instances of FF (old or new) running, received no error msg of any kind. Just nothing happened. I then went and changed the Preferred Web Browser as described above, tried the same link again in evolution and a new tab was opened for that site in the new FF. To test again, I sent an e-mail to my yahoo acct from another acct, got the notification from Gaim and this time it did open the yahoo mail login page in a new tab, as expected. Not exactly sure how/why but it appears all is now working as expected using the new FF ver and have not noticed any other odd behavior from the system over the almost 3 days since this all occurred.

EDIT: Just for grins, I decided to try clicking a link from OOo Writer and this also opened a new tab, as expected.

---

