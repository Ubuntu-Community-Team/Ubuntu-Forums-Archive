---
title: "LAMP Server"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by arst06d on 2006-10-25
Hi
I've just installed a LAMP server from CD.  All very easy and I assume it all went well.  However, I have no UI and, a s acomplete noob and gardened windows user, I'm scared of text.

Can I install a UI on the server version?
What do you recommend?

What GUI tools do I need to install in order to manage/administer MYSQL, PHP, APACHE on this box.  Oh, and how do I install them?

Also I have set this box up on my green (internal lan) zone of smoothwall, and I used ifconfig (he says, smugly) to find the ip.  I can access the box from my xp machine via that ip, so all looks to be working nicely.  I want to move the box onto the DMZ so how do I set up a static IP address, please?

Many thanks in advance, chaps.

---

### Post by bsussman on 2006-10-25
I found it simpler to install MySQL, php4 and php5, Apache2 on a desktop ubuntu install, thus I have all the ubuntu management goodness, including updates and security.

php = no management
MySQL = use phpMyAdmin from anywhere in your network
Apache needs almost no management, learn the text editing for the configs.

---

### Post by raycherng on 2006-10-25
sudo apt-get install ubuntu-desktop

you will have the gnome desktop enviroment

---

### Post by arst06d on 2006-10-25
groovy - thanks for that.
I assume it will just add the desktop to the server rather than replace the whole installation?
Will it automaticall then boot into the desktop or do I have to configure something?

---

### Post by arst06d on 2006-10-25
As suggested I tried
sudo apt-get install ubuntu-desktop

took ages to process and now I don't get any screen output after reboot - says Signal out of Range.

I think I'm gonna reinstall server, but that brings me back to my original question - how can I easily and reliably install a ui from command line?

Don't want the full desktop, 'cos I noticed that was installing open office & loads of stuff I'm not gonna need.

Thanks

---

### Post by az on 2006-10-25
> **arst06d said:**
> As suggested I tried
sudo apt-get install ubuntu-desktop

took ages to process and now I don't get any screen output after reboot - says Signal out of Range.

The server kernel may not play well with desktop hardware (and graphics)  Install the linux-386 package and you will get a desktop kernel.


> **arst06d said:**
> 
I think I'm gonna reinstall server, but that brings me back to my original question - how can I easily and reliably install a ui from command line?

A GUI for what?  Configuring your server apps?  Mostly, no.  If you want a graphical session and a file manager, just install one.

Enable the universe repository and install

sudo apt-get install x-windos-system-core gdm icewm xfm gedit xterm

But it is far easier to just install ssh and manage your server box remotely.  the reason there are no fancy apps like you describe is because it really isn't that hard to use the command line.

---

### Post by bobmct on 2006-10-25
One consideration for sysadmin without the desktop gui on the server... download and isntall webmin and then access your server machine with a browser at port 10000.  This is the next best thing to a gui without having the overhead of a gui just to manage a few things.

Works great ([www.webmin.com](www.webmin.com))

Give it a try.

Bob:)

---

### Post by arst06d on 2006-10-26
Ok , more problems ...

I got winscp working by downloading ssh, and I can log in and see the files on my new ubuntu server box from my xp box.

Tried to install webmin by downloading, copying across and unpacking the package using sudo dpkg --install /tmp/webmin_1.300_all.deb.

Gave me dependency errors for perl libraries.
I downloaded, copied across and ran tar zxvf stable.tar.gz, then tried the webmin again.  No dice.

I've searched the forms and cannot find anything to help - or it may be that I don't recognise what I'm looking at!

Can someone please advise me, step by step, what I need to do to enable me to administer my ubuntu server from an xp box on the LAN - ie janet & john setup for webmin and all dependencies, please.

Many thanks

---

### Post by Streetwalker32 on 2006-10-27
> **bobmct said:**
> One consideration for sysadmin without the desktop gui on the server... download and isntall webmin and then access your server machine with a browser at port 10000.  This is the next best thing to a gui without having the overhead of a gui just to manage a few things.

Works great ([www.webmin.com](www.webmin.com))


Bob:)

Can webmin be installed on a Windows machine ?
(To manage my ubuntu installation on another machine)

---

### Post by az on 2006-10-27
> **Streetwalker32 said:**
> Can webmin be installed on a Windows machine ?
(To manage my ubuntu installation on another machine)

Webmin runs on the server.  You just see the webmin interface on your web browser as you browse your server on port 10000

...Not that I recommend webmin - I think it is horribly broken....

---

### Post by compmodder26 on 2006-10-27
Is this a live production server or just a simple test server?  If you are running this for a production server, I would strongly recommend you leave the gui off.  

First of all, the command line is far more powerful than the gui, and with a little practice and teaching, it can be faster to use.

Second, the gui just adds another potential security hole for an attacker.

---

### Post by bobmct on 2006-10-28
I'm surprised about the "missing" perl as the LAMP server should include perl itself. 
While I've installed the webmin .deb package myself, I also have downloaded the tarball (tar file) that is available then untar'ed in into a chosen directory, cd'ed into that directory and read the README which describes how to run the install script.  Its usually that simple.

In regards to someones post about webmin being broken...  I find some parts of it seem to be.  But the OP asked about configuring the lamp server via a gui-like tool without having xwindows installed.  Webmin does and will provide that.

Again - just my $02 worth.

ps: I personally like SUSE's YAST2 system configuration tool but since I've switched to all Ubuntu its no longer available.   However, seeing that Novell has put it in the public domain, perhaps the Ubuntu folks would consider adopting it.

Bob

---

