---
title: "Here's an easy Firefox Q"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by djfick on 2007-12-22
What packages am I missing that is causing some websites not toload properly.  A specific example is pizzahut.com.  the applet (fash,java i dunno) won't load correctly so I can't order dinner online.  Please help. Thx

---

### Post by jrusso2 on 2007-12-22
Did you try to install adobe flash and Sun Java?

---

### Post by taurus on 2007-12-22
It's flash alright.  Too bad I just ate.

You can download it here, [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz).

Then can then install it by hand.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo ./flashplayer-installer
```

And when the installer asks you the path to plugins, type in /usr/lib/firefox/plugins.  When it's done, restart firefox.

---

### Post by djfick on 2007-12-22
Iknow that flash is installed (flashplugin-non free)  what's the package name for java?  I have beanshell2, is that it?

---

### Post by Syndacate on 2007-12-22
I'm turning away from firefox b/c it seems to have some issues with Gutsy - I don't know.

Some add-ons make it crash upon download - can't get flash to work with it - so on and so forth.

Anybody know any other good browsers?  Konqueror is nice, but nothing recognizes it as a browser, much like Safari.

---

### Post by Zenthes on 2007-12-22
```
sudo apt-get install gnash
```

Lets get you using open source versions.  open up a terminal and use "ctrl+shift+v" and you'll be able to just paste that in

---

### Post by taurus on 2007-12-22
> **djfick said:**
> Iknow that flash is installed (flashplugin-non free)  what's the package name for java?  I have beanshell2, is that it?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by Zenthes on 2007-12-22
Try using gnash, i had a problem installing it with Firefox a bit ago.

---

### Post by perlluver on 2007-12-22
To install Java, go to add-remove programs and look for Sun Java 6.  That should solve the problem with Java. 

Edit: Or follow the above, I was to slow, or try this way.  Either way you will then have Java Installed.

---

### Post by werewolfzx8 on 2007-12-22
> **Zenthes said:**
> Try using gnash, i had a problem installing it with Firefox a bit ago.

I'm all for OpenSource alternatives, but I had so many problems with Gnash, I thought I was going to explode.

If you're having problems with Flash, download and install it from the Adobe website.

Edit:
But if Gnash works for you, then great, use it instead for sure. ^-^

---

### Post by Zenthes on 2007-12-22
Yeah but then it doesn't update properly

---

### Post by djfick on 2007-12-22
I installed java and that ain't the cure.  It's definitely a flash issue.  I downloaded the tar.gz for flash player 9. what's the best way to install it now?

---

### Post by werewolfzx8 on 2007-12-22
> **Zenthes said:**
> Yeah but then it doesn't update properly

True, I definitely recommend at least giving Gnash a shot, but it just didn't work for me.

If something in the repos doesn't work, I install it from source, but keep an eye out for bug fixes. xP

(I know that's not for everybody, some people just want it to work)

---

### Post by werewolfzx8 on 2007-12-22
> **djfick said:**
> I installed java and that ain't the cure.  It's definitely a flash issue.  I downloaded the tar.gz for flash player 9. what's the best way to install it now?

Instructions are right on the site.

Extract it first, the run the installer from the terminal, it should automatically detect firefox.

Edit:
To the post bellow: I missed it, too... xD

---

### Post by taurus on 2007-12-22
> **djfick said:**
> I installed java and that ain't the cure.  It's definitely a flash issue.  I downloaded the tar.gz for flash player 9. what's the best way to install it now?

Did you see post #3?  ](*,)

---

### Post by Zenthes on 2007-12-22
mm remove the bum version 
```
sudo apt-get remove flashplugin-nonfree
```

then install the free version 

```
sudo apt-get install gnash
```

just in case restart windows X "ctrl+alt+backspace"

---

### Post by djfick on 2007-12-22
> **taurus said:**
> Did you see post #3?  ](*,)

i pasted that code and got errors

---

### Post by taurus on 2007-12-22
> **djfick said:**
> i pasted that code and got errors

It would be extremely helpful if you include the command and the whole error message when you run that command.

---

### Post by djfick on 2007-12-22
> **Zenthes said:**
> mm remove the bum version 
```
sudo apt-get remove flashplugin-nonfree
```

then install the free version 

```
sudo apt-get install gnash
```

just in case restart windows X "ctrl+alt+backspace"

i already have the latest version of gnash (so my terminal tells me!)

---

### Post by djfick on 2007-12-22
> **taurus said:**
> It would be extremely helpful if you include the command and the whole error message when you run that command.
chris@chris-desktop:~$ cd ~/Desktop
chris@chris-desktop:~/Desktop$ tar xvzf install_flash_player_9_linux.tar.gz
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
chris@chris-desktop:~/Desktop$ cd install_flash_player_9_linux
bash: cd: install_flash_player_9_linux: No such file or directory
chris@chris-desktop:~/Desktop$ sudo ./flashplayer-installersudo apt-get install gnash

---

### Post by djfick on 2007-12-22
in the meantime i've ordered my pizza from my laptop

---

### Post by taurus on 2007-12-22
Where did you save install_flash_player_9_linux.tar.gz to since you said you just downloaded it?  Did you save it to your $HOME or to ~/Desktop?

```
ls -la ~/Desktop
ls -la ~
```

---

### Post by djfick on 2007-12-22
desktop

chris@chris-desktop:~$ ls -la ~/Desktop
total 8
drwxr-xr-x  2 chris chris 4096 2007-12-15 18:44 .
drwxr-xr-x 36 chris chris 4096 2007-12-22 19:00 ..
chris@chris-desktop:~$ ls -la ~
total 520
drwxr-xr-x 36 chris chris   4096 2007-12-22 19:00 .
drwxr-xr-x  3 root  root    4096 2007-12-15 18:38 ..
-rw-------  1 chris chris   1562 2007-12-22 19:01 .bash_history
-rw-r--r--  1 chris chris    220 2007-12-15 18:38 .bash_logout
-rw-r--r--  1 chris chris   2298 2007-12-15 18:38 .bashrc
drwxr-xr-x  3 chris chris   4096 2007-12-15 18:44 .cache
drwxr-xr-x  5 chris chris   4096 2007-12-15 19:16 .config
drwxr-xr-x  2 chris chris   4096 2007-12-15 18:44 Desktop
-rw-------  1 chris chris     28 2007-12-20 08:50 .dmrc
drwxr-xr-x  2 chris chris   4096 2007-12-15 18:44 Documents
-rw-------  1 chris chris     16 2007-12-15 18:44 .esd_auth
lrwxrwxrwx  1 chris chris     26 2007-12-15 18:38 Examples -> /usr/share/example-content
drwxr-xr-x  2 chris chris   4096 2007-12-16 13:55 .fontconfig
drwx------  2 chris chris   4096 2007-12-20 08:57 .gcjwebplugin
drwx------  5 chris chris   4096 2007-12-20 08:50 .gconf
drwx------  2 chris chris   4096 2007-12-22 19:01 .gconfd
drwxr-xr-x 22 chris chris   4096 2007-12-16 13:55 .gimp-2.4
-rw-r-----  1 chris chris      0 2007-12-22 18:32 .gksu.lock
drwxr-xr-x  4 chris chris   4096 2007-12-16 11:31 .gnome
drwx------ 15 chris chris   4096 2007-12-22 18:38 .gnome2
drwx------  2 chris chris   4096 2007-12-15 18:44 .gnome2_private
drwxr-xr-x  2 chris chris   4096 2007-12-16 13:29 .gstreamer-0.10
-rw-r--r--  1 chris chris    108 2007-12-20 08:50 .gtk-bookmarks
-rw-r--r--  1 chris chris     87 2007-12-15 18:44 .gtkrc-1.2-gnome2
-rw-------  1 chris chris    346 2007-12-20 08:50 .ICEauthority
drwxr-xr-x  2 chris chris   4096 2007-12-15 19:15 .icons
drwxr-xr-x  3 chris chris   4096 2007-12-15 18:44 .local
drwx------  3 chris chris   4096 2007-12-15 18:44 .metacity
drwx------  3 chris chris   4096 2007-12-15 21:26 .mozilla
drwx------  3 chris chris   4096 2007-12-15 21:26 .mozilla-thunderbird
drwxr-xr-x  2 chris chris   4096 2007-12-17 22:14 .mplayer
drwxr-xr-x  2 chris chris   4096 2007-12-15 18:44 Music
drwxr-xr-x  3 chris chris   4096 2007-12-20 08:49 .nautilus
drwx------  3 chris chris   4096 2007-12-22 16:21 .openoffice.org2
drwxr-xr-x  4 chris chris   4096 2007-12-22 12:22 Pictures
-rw-r--r--  1 chris chris    566 2007-12-15 18:38 .profile
drwxr-xr-x  2 chris chris   4096 2007-12-15 18:44 Public
drwx------  4 chris chris   4096 2007-12-15 23:37 .purple
-rw-------  1 chris chris    565 2007-12-17 23:12 .recently-used
-rw-r--r--  1 chris chris 128230 2007-12-22 18:40 .recently-used.xbel
-rw-r--r--  1 chris chris      0 2007-12-15 18:44 .sudo_as_admin_successful
drwxr-xr-x  2 chris chris   4096 2007-12-15 18:44 Templates
drwxr-xr-x  2 chris chris   4096 2007-12-15 19:15 .themes
drwx------  4 chris chris   4096 2007-12-15 23:35 .thumbnails
drwx------  2 chris chris   4096 2007-12-15 18:44 .Trash
drwxr-xr-x  2 chris chris   4096 2007-12-20 08:45 .update-manager-core
drwx------  2 chris chris   4096 2007-12-15 18:44 .update-notifier
drwxr-xr-x  2 chris chris   4096 2007-12-15 18:44 Videos
drwxr-xr-x  2 chris chris   4096 2007-12-15 23:35 .wapi
drwxr-xr-x  4 chris chris   4096 2007-12-22 15:26 .wine
-rw-------  1 chris chris    124 2007-12-20 08:50 .Xauthority
-rw-r--r--  1 chris chris 200134 2007-12-20 21:22 .xsession-errors
chris@chris-desktop:~$

---

### Post by taurus on 2007-12-22
I thought you said you have already downloaded flash from Adobe's site.

Run these commands from a terminal.

```
cd ~/Desktop 
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo ./flashplayer-installer
```

Firefox plugin directory is /usr/lib/firefox/plugins.

---

### Post by djfick on 2007-12-22
i uninstalled it 5 min ago to make sure that gnash would load properly
i'm going to reboot

---

### Post by djfick on 2007-12-22
Still won't display the pizza hut site properly.  these are the issues i'll have to solve in order to convince my lovely wife that ubuntu is worthwhile!

---

