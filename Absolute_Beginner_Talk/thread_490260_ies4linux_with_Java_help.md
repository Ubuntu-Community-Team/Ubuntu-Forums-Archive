---
title: "ies4linux with Java help"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by novusopiate on 2007-07-02
Hey everyone;

I am still fairly new to using linux much less ubuntu but I have recently installed it on my company laptop after it blue screened with windows. I need to be able to run jre with IE so that I can access our intranet but I have had some issues. I have been following the guide [here]("http://rmathew.blogspot.com/2007/04/running-java-applets-in-internet.html") but run into issues at the 
```

export WINEPREFIX=$HOME/ies4linux/ie6
wine jre-1_5_0_11-windows-i586-p.exe

```
section. 

I always get ```
wine: the '/root/ies4linux/ie6' directory specified in WINEPREFIX doesn't exist.
You may want to create it by running 'wineprefixcreate'.

```
so i try typing that and get:
```
mkdir: cannot create directory `/root/ies4linux/ie6': No such file or directory
Could not create /root/ies4linux/ie6, aborting
```
So I am officially lost and not really sure where to head from here.

Any help would be much appreciated.


Thanks

Mike

---

### Post by eternalsword on 2007-07-02
why are you logged in as root?  It's showing $HOME as being /root so you're somehow logged in as root, either that or $HOME is not correctly assigned.  I'm guessing it may actually be the latter since you couldn't use mkdir.  Try this instead
```
export WINEPREFIX=/home/$USER/ies4linux/ie6
wine jre-1_5_0_11-windows-i586-p.exe
```

---

### Post by novusopiate on 2007-07-02
I was logged in as root so I tried logged out and same reaction.

Also tried what you posted and it gave me the same output......:(

---

### Post by eternalsword on 2007-07-02
just a question, but have you installed ies4linux yet?

---

### Post by Enverex on 2007-07-02
Never run anything Wine related as root unless you don't mind every drive attached to your system being wiped...

---

### Post by novusopiate on 2007-07-02
Yes ies4linux is installed and I can run it great, just no java.



Thanks for the heads up Enverex!

---

### Post by eternalsword on 2007-07-02
okay, looks like the guide is a bit off. try ```
export WINEPREFIX=$HOME/.ies4linux/ie6
wine jre-1_5_0_11-windows-i586-p.exe
```

notice the period in front of ies4linux.

---

### Post by novusopiate on 2007-07-02
Well, you are right that helped, but now it is at a prompt   "wine-dbg>" and is seemingly waiting for input....any idea what it might want?

---

### Post by eternalsword on 2007-07-02
wine-dbg is wine's debugger meaning it didn't run the executable properly.  not sure what to tell you after that.

edit: maybe try the newest jre release from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

---

### Post by novusopiate on 2007-07-02
Downloaded the new version and same thing...

Thanks for your suggestions!

---

### Post by eternalsword on 2007-07-02
what version of wine are you running?

---

### Post by novusopiate on 2007-07-02
wine-0.9.40

---

### Post by eternalsword on 2007-07-02
most people on the wine apps site have listed the jre as garbage, so it doesn't surprise me that it's not working for you.  is there any particular reason you need to run the java applet in internet explorer as opposed to natively in firefox, opera, etc?

If it must be IE, you could try running vmware or some other sort of virtual machine.

---

### Post by novusopiate on 2007-07-02
In order to access the intranet system in my office it has to do several things:

One:  It has to download a little "host checker" application which at this point, I do not know if it will run in wine but I want to at least try

Two: It is picky with Firefox.. I have run it in firefox on a windows machine  but when I try to run on firefox, it acts like there is no java executable to run....

I take a look at vmware and see where I get with that.

---

### Post by eternalsword on 2007-07-02
you may have the default java installed then, you should try sun

```
sudo apt-get install sun-java6-jdk
```

then 

```
sudo update-alternatives --config java
```

type the number in front of 
/usr/lib/jvm/java-6-sun/jre/bin/java

and then to get the plugin for firefox, etc
```
sudo apt-get install sun-java6-plugin
```

hope it works after that

---

### Post by novusopiate on 2007-07-02
I'll have to give that a try. Here at work, the way they have the proxy servers all set up will not allow me to use "apt-get" so I have to do alot of my work at home with packages and whatnot....


Thanks again!

---

### Post by eternalsword on 2007-07-02
do you have a machine at home and a machine at work, if you do, you should be able to forward through an ssh tunnel.  I did that when I was at college.  You can also download the .deb files from [http://packages.ubuntu.com](http://packages.ubuntu.com) it has package search features, but make sure you choose the right version of ubuntu.  

When installing from those debs, you need to make sure all of the dependencies are installed before you try to install them, which would mean manually installing the debs of the dependencies, which is why apt-get is so nice when you can use it since it automatically handles all of that stuff.

---

### Post by novusopiate on 2007-07-02
Share a home pc with the little lady so its a mac.....nice and pretty and easy to use..

---

### Post by eternalsword on 2007-07-03
mac os x should come with an ssh server, thanks to the *nix base ;)

I believe following the guide at [http://www.samspublishing.com/library/content.asp?b=Mac_OS_X_Unleashed&seqNum=201&rl=1](http://www.samspublishing.com/library/content.asp?b=Mac_OS_X_Unleashed&seqNum=201&rl=1) would help you.

I would suggest setting it up to run on port 443, then it will look like https data.  I doubt your company would block that.  Also, if you are behind a router at home, make sure to forward whatever port you use.

Make sure your ssh password is very strong as it allows remote connections.  Or even more preferable set it up to use public private key pairs.  No password necessary but much more secure.  There are various guides on the net for doing that, but I'll leave it to you to find it if you want to go that route.

I will tell you how to set up a socks proxy via ssh.

On the ubuntu machine, open the terminal and
```
ssh -D 1080 user@host -p ####
```
you would replace user with your os x sshd login name and host with the ip address of your mac.  If you have a dynamic ip, you can look into getting a free account with [http://dyndns.org](http://dyndns.org) though you'll have to find some sort of program or script for os x to keep the ip address up to date.

#### would be replaced by the port number you set sshd to run on

after you have connected, you can use localhost port 1080 as a socks proxy.

---

### Post by mr_shedges on 2007-08-12
IF any one still looks at this thread try to add "" to the location i.e.

WINEPREFIX="/home/$USER/.ies4linux/ie6"

I had a bit of bother and found that this worked. Worth a try

---

