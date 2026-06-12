---
title: "Java Install (having problems)"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-09-28
What is the currect way to install java so that it will work on mozilla\firefox\konquerer?
I have jre-1_5_0_04-linux-i586.bin but everytime I use the console to install it it just makes a folder with all the files in the same folder where the jre-1_5_0_04-linux-i586.bin resides.
I down loaded the file to /home/nitricacid/java and ran it from there.

I don't quite understand where i am suppose to install programs to since they are not self installing to a directory where they are suppose to be installed to.

Thanks

---

### Post by Leif on 2005-09-28
my suggestion is to add 

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

to your /etc/apt/sources.list (use sudo), and then apt-get update, apt-get install sun-j2re1.5

---

### Post by nitricacid on 2005-09-28
[QUOTE=Leif]my suggestion is to add 
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java
to your /etc/apt/sources.list (use sudo), and then apt-get update, apt-get install sun-j2re1.5[/QUOTE]

Is there any way you could give me a list of 'deb http://ubuntu.whateversurl' to help me update like everything?

---

### Post by Leif on 2005-09-28
[QUOTE=nitricacid]Is there any way you could give me a list of 'deb http://ubuntu.whateversurl' to help me update like everything?[/QUOTE]

I'm sorry but I don't understand your question. The method I suggested will automatically update after a new release of java. Is that what you're asking ?

---

### Post by nitricacid on 2005-09-28
ok, i put that into the sources.list file and it still did nothing to help with java applets.
Also i am using Breezy and not hoary, would that matter?

---

### Post by Leif on 2005-09-28
no, it's ok with breezy. putting it in your sources isn't enough though, you still need to update and install it. afterwards, do this :

[http://ubuntuforums.org/showpost.php?p=258533&postcount=3](http://ubuntuforums.org/showpost.php?p=258533&postcount=3)

---

### Post by nitricacid on 2005-09-29
I followed the directions at the java site on how to install it and i did everything it said (even what [http://ubuntuforums.org/showpost.php...33&postcount=3](http://ubuntuforums.org/showpost.php...33&postcount=3) says)but when i start my browser it it just crashes out and never loads.
I am using Mozilla and not firefox since i like the composer feature that come with mozilla.
I have changed the line to accomidate for the mozilla folder but when the plugin is in the plugin folder in mozilla the browser never wants to load.

---

### Post by Leif on 2005-09-29
I'm afraid I can't replicate your problem, so I can't really help you. Can you just try installing firefox to see if it crashes too ?

---

### Post by nitricacid on 2005-09-29
could you just tell me the file where i need to install the Java.bin file to?
should i use java.com or java.sun.com or is there no dif?

---

### Post by Leif on 2005-09-29
if you followed my previous instructions, you already have java installed. if you want to reinstall it, you can download it from java.sun.com

---

### Post by bored2k on 2005-09-29
**Building your own debian package:**

If you have the jre-1_5_0_04-linux-i586.bin package:
```
sudo apt-get install fakeroot java-package
```
```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
```
sudo dpkg -i *.deb
```

---

### Post by nitricacid on 2005-09-29
~Bangs his head on the desk with frustration and humiliation~

Thank you very much :D
Everything installed and works great.

BTW, how do you find how codes like that so it will auto install as such?!

---

### Post by bored2k on 2005-09-29
[QUOTE=nitricacid]~Bangs his head on the desk with frustration and humiliation~

Thank you very much :D
Everything installed and works great.

BTW, how do you find how codes like that so it will auto install as such?![/QUOTE]
You don't easily "find" codes, you slowly grab them from the net, the forums or some irc channel. Just make sure you email them to yourself when you do ;).

---

### Post by helmethedd on 2005-10-02
[QUOTE=bored2k]**Building your own debian package:**

If you have the jre-1_5_0_04-linux-i586.bin package:
```
sudo apt-get install fakeroot java-package
```
```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
```
sudo dpkg -i *.deb
```[/QUOTE]
can either of you fellas walk me thru that?
I hate bein' a newbie, alas, thatz what I am.

---

### Post by bored2k on 2005-10-02
[QUOTE=helmethedd]can either of you fellas walk me thru that?
I hate bein' a newbie, alas, thatz what I am.[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=70428](http://ubuntuforums.org/showthread.php?t=70428) Clarified there.

---

### Post by helmethedd on 2005-10-02
below is the response i get from the terminal. What gives?
E: Couldn't find package java-package

---

### Post by bored2k on 2005-10-02
1. [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
2. Retry

---

### Post by helmethedd on 2005-10-02
Firstly, let me thank you kindly for all the help.
Furthermore, thank you for being so patient. i checked out the link, followed the instructs, and retried. below is a copy/paste of the results. See if you can make any sense outta it.
goatmilk@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
goatmilk@ubuntu:~$ sudo gedit /etc/apt/sources.list
goatmilk@ubuntu:~$ sudo apt-get install fakeroot java-package
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package java-package
goatmilk@ubuntu:~$ fakeroot make-jpkg downloaded_package_name.bin
bash: fakeroot: command not found

---

### Post by bored2k on 2005-10-02
You need to read guides CAREFULLY.
You skipped the sudo apt-get update step after the gedit job.

---

### Post by helmethedd on 2005-10-02
I think your right, i went back and checked my work, and so i repeated the whole process again. Here is the last few lines resulting from the sudo....update
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

afterward i tried the first code sudo apt-get install fakeroot java-package, and i got the same results as my last post. 
I sure hope this isn't going to be one of those embarassing moments for me....sheesh

---

### Post by helmethedd on 2005-10-02
i'm still open to help/ advice on this subject.

---

### Post by Qrk on 2005-10-02
type

java -version 

into the terminal. If it outputs something nice, I think the problem is your symbolic link to firefox. Try running

sudo ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

If this returns an error, you may have to delete an older link from the firefox plugins folder. You may also have to change the path to where you installed Java. The important thing is that you copy the link from the ns7 plugin folder, not the ns7-gcc29 folder.

If java -version doesn't return anything good, try redoing.
Get the jre-1_5_0_04-linux-i586.bin package from Sun ([www.java.com](www.java.com))

sudo apt-get install fakeroot java-package
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
sudo dpkg -i *.deb
java -version


If none of these work... well, you stumped me here. I can't think of anything else on the spot. Please reply if it does work -- I'm curious. I'll try to look it up to get another idea.

---

### Post by helmethedd on 2005-10-02
i've downloaded the java thingy to the desktop thing. Should it be somewhere else?

---

### Post by Ubunted on 2005-10-02
Okay, first off, forget everything you've read in this thread so far.

1: Right-click on your desktop and select "Open Terminal"

2: Type ```
cd /
```

3: Type (or copy and paste) ```
 sudo gedit /etc/apt/sources.list
```

4: Enter the following at the bottom of the document: ```
deb http://ubuntu.tower-net.de/ubuntu/ hoary java
```
5: Save and exit.

6: Back in the terminal window, type ```
sudo apt-get update
```

7: Type ```
sudo apt-get install sun-j2re1.5
```

Bam, done.

I just tested this, and it works.

---

### Post by helmethedd on 2005-10-02
[QUOTE=Ubunted]Okay, first off, forget everything you've read in this thread so far.

1: Right-click on your desktop and select "Open Terminal"

2: Type ```
cd/
```

3: Type (or copy and paste) ```
 sudo gedit etc/apt/sources.list
```

4: Enter the following at the bottom of the document: ```
deb http://ubuntu.tower-net.de/ubuntu/ hoary java
```
5: Save and exit.

6: Back in the terminal window, type ```
sudo apt-get update
```

7: Type ```
sudo apt-get install sun-j2re.15
```

Bam, done.

I just tested this, and it works.[/QUOTE]

well somehow it didn't with my system. cd/ didn't work, sudo gedit etc/apt/sources.list, only gave me a blank space within the window.
I tried to copy and paste it anyhow, and it wouldn't even save.
But, i like yer style brother, lets try again. I sure hope all these different suggestions from everyone isn't gonna frag up everything....

---

### Post by Ubunted on 2005-10-02
Ah, oops. Forgot the space between cd and /. Edited.

And barring any more typos, this won't frag anything up.

Edit: fixed another one, "sun-j2re.15" should be "sun-j2re1.5". Me no thinkie today.

---

### Post by TristanMike on 2005-10-02
Yeah, another typo, it's not ```
sudo gedit etc/apt/sources.list
```it's,```
sudo gedit **[COLOR="Red"]/[/COLOR]**etc/apt/sources.list
```

---

### Post by Ubunted on 2005-10-02
Both work for me.

---

### Post by helmethedd on 2005-10-02
windows is starting to look better and better....
at least i didn''t need a degree to download something...sheesh
can someone juss walk me thru it real fast? instead of this hit....wait....wait...miss...ask for help.....wait...wait wait....
excuse me for venting, this is just becoming frustrating.

---

### Post by Ubunted on 2005-10-02
Adding that repository and installing it through apt is as easy as Java gets on Ubuntu, unfortunately. Thanks to Sun's legal policies not allowing JRE to be placed in official repos it just gets harder from there. What part didn't work for you? I tried to make it straightforward as possible.

And believe me, I know very well the frustrations of Java. It's consistently been my most hated part of Linux.

If you want to PM me with your MSN screenname I can transfer you the package file that can be installed with a single command (similar to an .exe, or as similar as it gets in Linux), though it may take awhile to download.

---

### Post by TristanMike on 2005-10-02
[QUOTE=Ubunted]Both work for me.[/QUOTE]That suprises me, it certainly doesn't work for me, I get an empty gedit window with "etc/apt/sources.list" but it's fine with "/etc/apt/sources.list".  Anyway, it seems to be more proper etiquite to include the "/" as it does desginate a directory and you wont have somebody posting that they get a blank document.

EDIT: I see you did, but really, both work for you? (Hi fellow Canuck)

---

### Post by Ubunted on 2005-10-02
I found it interesting myself really, but I can either use or leave the / and both bring up the same file for me. I can see the value in keeping the slash for conformity reasons though.

---

### Post by H_Roark on 2005-10-02
I just tried the apt-get method above.  The machine indicated that it was downloading and installing Java, but somehow it still is not working with Firefox.  I've already tried the other, longer method listed(the download from Sun) and that also failed.  Am I missing something?  Should I give up any hope of having Java with Ubuntu?

---

### Post by tr6scott on 2005-10-02
helmethead, 
hang in there... I am 2 days into this and having the same problems.... remember that this is a learning process, and if the productivity today is an issue, stick with windows, if that is what you know. I am taking this as a learning experience, and I still have my main windows rig up while I am trying to learn. (it is furstrating, being sent back to kindergraten, when you know so much, I agree) 
Anyways, I just wanted to let you know that after two days this last stuff from ubunted worked for me, I too was having that E:java not found.. error. 
```
sudo apt-get install sun-j2re1.5
```
Looked to me that it downloaded the package again, and must have put it where it wanted it, and worked...
When I ran
```
java -version
```
I had good responses... but still not working in browser... 
So then I did Qrk's 
```
sudo ln -s /usr/java/jre1.5.0_04/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
```
and it worked... 
All this to get my ISP's (SBC) speed test page to work. 
anyways good luck... :)

---

### Post by whiterabbit on 2005-10-02
Don't freak out.  I'm an absolute newbie to linux and I had Java working in under 3 hours.

The above post is all you really need if Java is already installed.

If you're having trouble with creating the link, try doing it through the gnome interface.

```
gnome-open ~/.mozilla/ 
```

This'll open the Mozilla folder in gnome and you should be able to navigate your way into the plugin folder from there. So go into your installed Java folder/plugin/i386/ns7/ and right click on the .so file to create a link. Cut and paste the link into the Mozilla/plugins folder.

Then type about:plugins in Mozilla to make sure it's all good.

EDIT: Keep in mind that just because Java is installed(and it probably is after all this) you still have to enable the plugin in Firefox so the above should help with that.  Good luck.

---

### Post by Ubunted on 2005-10-02
[QUOTE=whiterabbit]I had Java working in under 3 hours.[/QUOTE]

And that's supposed to be reassuring? :D

---

### Post by whiterabbit on 2005-10-02
[QUOTE=Ubunted]And that's supposed to be reassuring? :D[/QUOTE]
For a newbie like myself?  Absolutely. ;)

---

### Post by xyz on 2005-10-03
[QUOTE=Ubunted]Okay, first off, forget everything you've read in this thread so far.
1: Right-click on your desktop and select "Open Terminal"
2: Type ```
cd /
```
3: Type (or copy and paste) ```
 sudo gedit /etc/apt/sources.list
```
4: Enter the following at the bottom of the document: ```
deb http://ubuntu.tower-net.de/ubuntu/ hoary java
```
5: Save and exit.
6: Back in the terminal window, type ```
sudo apt-get update
```
7: Type ```
sudo apt-get install sun-j2re1.5
```
Bam, done.
I just tested this, and it works.[/QUOTE]
Hi-
Thank you for this!I don't remember how many forums I 'studied' but I found it here.:) 
I'm new here with you and I thank you for welcoming me.I'm so glad I finally found a forum where I can click on 'Beginners' 'Absolute Beginners'.:D I'm gonna learn something!
see you 'round

---

### Post by wabble on 2005-10-06
For you guys using breezy badger just go to the applications menu and select add applications. Do a search for java.

Blackdown java (or something like that) should appear in a grey color. Press it with the mouse and answer yes to the box about repository update.

After the update make a hook on the blackdown java box and apply.

Accept the licence (the other box i unhook, not shure about what it does but it works without the hook).

Press next or what is says and presto.

Make sure firefox is restarted after install.

---

### Post by garnertr on 2005-10-06
OK, I'm in this boat myself, never have gotten freaking JAVA to work and I need it to complete training courses for where I work (do it @ home they say...)... anyway...

When I type "java -version" the following:

root@sonic:/home/tom # java -version
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)
root@sonic:/home/tom #

when I type "about:plugins" in firefox I get:

No plug-ins are installed
Find more information about browser plug-ins at Netscape.com.
Help for installing plug-ins is available from plugindoc.mozdev.org. 

Also for giggles, if I use my filebrowser and look at "/etc/alternatives" I see the following file "firefox-plugin.so", but if I CLICK on it (right-click), the file 'vanishes', if I backout of the directory, go back in its there, but if I attempt to click on the file it goes away again...

sigh.  however, I believe that I'm having a SYMBOLIC LINK problem right?  thanks for your assistance...

---

### Post by nitricacid on 2005-10-07
[QUOTE=garnertr]
sigh.  however, I believe that I'm having a SYMBOLIC LINK problem right?  thanks for your assistance...[/QUOTE]

Most likely it is the symbolic link that is cousing you to not view java applets within firefox.
Even if you have java installed you still need to make a symbolic link in the plugins folder of firefox\mozilla.

This is what i did to get java to work.
[QUOTE=bored2k]**Building your own debian package:**

If you have the jre-1_5_0_04-linux-i586.bin package:
```
sudo apt-get install fakeroot java-package
```
```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
```
sudo dpkg -i *.deb
```[/QUOTE]

---

### Post by garnertr on 2005-10-07
Funny, when I attempt to use the "sudo apt-get install" cmd, I get the following:

Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

Now the fun part is, I can put the disc in my drive and its not recognized at all...

---

### Post by bored2k on 2005-10-07
[QUOTE=garnertr]Funny, when I attempt to use the "sudo apt-get install" cmd, I get the following:

Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

Now the fun part is, I can put the disc in my drive and its not recognized at all...[/QUOTE][http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
You need the right repositories.

---

### Post by nitricacid on 2005-10-07
can't you just hash (##) out the CD part in the sources.list?
This happen to me when i first install Breezy preview and that is all i did.

---

### Post by garnertr on 2005-10-07
Thank you for the response bored2k, it seems that I forgot the crucial step of updating my repositories ... ok that is done and am moving on w/ the initial idea of attempting to install JAVA...

OK, following the previous steps, working the next part of the original post...

thanks gain...

---

### Post by Dayylin on 2005-10-07
[QUOTE=Leif]my suggestion is to add 

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

to your /etc/apt/sources.list (use sudo), and then apt-get update, apt-get install sun-j2re1.5[/QUOTE]


I have added the tower-net.de to the sources.list a couple times and have yet to be able to connect to it during an update. It hangs at 99% and then times out.

"Failed to fetch [http://ubuntu.tower-net.de/ubuntu/dists/hoary/Release.gpg](http://ubuntu.tower-net.de/ubuntu/dists/hoary/Release.gpg)  Could  not connect to ubuntu.tower-net.de:80 (81.169.176.107), connection timed outFailed to fetch [http://ubuntu.tower-net.de/ubuntu/dists/hoary/java/binary-i386/Packages.gz](http://ubuntu.tower-net.de/ubuntu/dists/hoary/java/binary-i386/Packages.gz)  Could not connect to ubuntu.tower-net.de:80 (81.169.176.107), connection timed out

---

### Post by garnertr on 2005-10-07
OK, I've completed the above steps w/ regards to apt-get install fakeroot java-package and all those steps... I completed them, restarted my firefox and went in to about:plugins and the following now shows up:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

But still no JAVA, I'm still under the impression that I have a broken link somewhere... anyway, any thoughts as to what the next step might be???

---

### Post by whiterabbit on 2005-10-07
So you've created the link and placed it in the Mozilla plugin folder? If you're having trouble with that, I suggest that you try what I pointed out in my last post.

---

