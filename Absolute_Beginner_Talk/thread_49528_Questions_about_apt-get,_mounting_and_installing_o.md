---
title: "Questions about apt-get, mounting and installing other software"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by Strangerdave on 2005-07-16
Greetings,

I am new to all this and just downloaded Ubuntu and really like it.  Quite different than windows that is for sure.

The reason that I am posting is that there are some things that I am still quite unsure of when it comes to Linux, especially Ubuntu.  If I could get some info either an expplanation or a link to sources that would be great.  I have searched this forum and done some googling to no avail...and my eyes are getting tired :? 

1) what are apt-get and synaptics?  I think they are ways to install programs and such, but how does one use them, or how do they work?  

2) I have a windows HD also on this machine, but it does not appear.  I know I have to mount it, but am unsure of the correct syntax to use.

3) I wish to upgrade my firefox to the latest and understand that one can download an RPM package, but how would I go about upgrading from the 1.0.2 that I have?

4) I noticed that there is no system try, but I would like to use GAIM, does this mean that I can not close it out and have it running in the backgroun?

Any and all help is greatly appreciated.  I know there is going to be a huge learning curve for me in the next little while, but I like this Ubuntu thingy ;-)  and hope to become more familiar with it.

SD

---

### Post by Umbra on 2005-07-16
1. apt-get is a command that connect to the internet and could find, search and install packages automatically, synaptic is a package manager.
Apt-get, look for the files you specify using a sources list defined in the file /etc/apt/sources.list
Ubuntu comes with a default list, but there many, many sources out there fortunely, right now, seems some source servers are having problems retreiving packages, u must backup your original sources.list file in another file and edit the original.

Like here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

2. [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

3. sudo apt-get install firefox 
    (you'll get the lataste version)


And hope this helps: 
This is a very useful guide that responds to all most common question when you are starting with ubuntu.

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Note:

I recommnd you to use this info to edit your /etc/apt/sources.list file, because the problems genarated with the example in the guide. Use this instead:

> ## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse
#deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

##Backup Security Mirrors
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

##Backports
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Strangerdave on 2005-07-16
Hey thanks for the tips, I will most certainly devour this info!! :smile: 

So far I am really liking this flavor.  So if I know the name of the program that I want I just type sudo apt-get name of program and if it is onthe mirrors it should install?

Also, is it best to use a root terminal to do this or just a regular terminal?

SD

---

### Post by Umbra on 2005-07-16
Yes, example:

You could bypass go to make a google search for a app in linux version, download and manually install using the apt-get command, but sometimes will be needed to do it manually.

If you type in a terminal: apt-get install gaim, you'll get it fast witouth doing the steps above, but you'll problably not see a desktop shurcut for the recently app installed with apt, but in that case just type the name of the app recently installed and it will be started like this:

user@pc#~: gaim

Sometimes, the names for the packages are not so obvios, so in those cases you may need to ask, like the flash player pluging, you could think:

apt-get install flashplayer

you'll get:  'package not found' because the correct is:

apt-get install flash-player.


You could do all this in a regular terminal by typing 'sudo' before the 'apt-get'; 'sudo' executes orders like if you're root, this is for security. Ubuntu uses this way at difference with other linux distrubutions.

---

### Post by Strangerdave on 2005-07-16
Wow thanks.

You know I tried the update for Firefox like you suggested, but I got this error

```
Errors encountered while processing
/var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5. 04ubp5_i386.deb

E: Subprocess /usr/bin/dpkg returned error code 1

``` 

Now firefox doesn't work at all.

Another question you maybe able to help with...
I noticed that in the list of mirrors, there was one for KDE, do I really need that one, since I am using GNOME?

I also wonder about a firewall for Ubuntu, how would I access it for configuration?

SD

---

### Post by poofyhairguy on 2005-07-16
[QUOTE=Strangerdave]Wow thanks.

You know I tried the update for Firefox like you suggested, but I got this error

```
Errors encountered while processing
/var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5. 04ubp5_i386.deb

E: Subprocess /usr/bin/dpkg returned error code 1

``` 

Now firefox doesn't work at all.[/QUOTE]

Lets try an easier way to install and upgrade software:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

> 
Another question you maybe able to help with...
I noticed that in the list of mirrors, there was one for KDE, do I really need that one, since I am using GNOME?

I also wonder about a firewall for Ubuntu, how would I access it for configuration?

SD


1. No for first question. You don't need thoe lines. Good observation.

2. You have to install a firewall first. Look in synaptic.

---

### Post by Strangerdave on 2005-07-16
Hey thanks there Hairy, or Poof.....or Guy!

That was an easy way of getting it done, but it seems to stall quite a bit.  Is that because of the servers?  It often fails to do the downloading.  Is it a matter of trying again at a later time?

SD

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=Strangerdave]Hey thanks there Hairy, or Poof.....or Guy!

That was an easy way of getting it done, but it seems to stall quite a bit.  Is that because of the servers?  It often fails to do the downloading.  Is it a matter of trying again at a later time?

SD[/QUOTE]

Yes....the servers have had some problems...as you can see at the top of the page we are looking for better hosting.

---

