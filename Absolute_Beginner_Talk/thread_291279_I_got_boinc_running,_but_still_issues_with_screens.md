---
title: "I got boinc running, but still issues with screensaver and browers integration."
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Bentov on 2006-11-02
Good Morning,

Well I have a uptime of 1 day, 14 hours and 14 mintues.  :)   And I've only broken gnome once, but I'm digressing.   

Boinc ](*,) 

I've got it installed, for those that don't know how.

```


sh <insert name of downloaded boinc file here>


```

So now, I wanted to set it up like a screensave like my xp box, but I don't see away to do that on linux, however, I'm not sure sure I want to given how much slowerit is on linux.  Reguardless any hints on that would be appreciated. 

Also,

When clicking the links in the boinc manager, I get an error message:

"BOINC Manager - Can't find web browser"

BOINC Manager tried to display the webpage but coudln't fine a web browser.  To fix this, set the environment variable BROWSER to the path of the your web browser, then restart the BOINC Manager.


So is it talking about the system's environment file, or it's own? The system seems to already know where firefox is.  I"m confused.  Any help would be appreciated.


Bentov

---

### Post by tribaal on 2006-11-02
Glad to have anothe BOINCer around :)

The easiest way to install BOINC is still to "sudo apt-get install boinc-manager" (it's in universe repositories).
Unfortunately the screensaver option isn't available on linux :( So you'll be crunshing in the background for the sake of it, I don't think there's a way to make the screensaver work in linux... :( 
However if there is I'd be more than interested to find out how, hlaf for the eye candy effect and half to increase my tech knowledge ;)

There was a problem with previous versions of the repositorie's BOINC where it couldn't find the web browser, but now it works out of the box with the latest package.

Not sure if it has been backported to Dapper though, what version of Ubuntu are you running?

- trib'

---

### Post by Bentov on 2006-11-02
Thanks for the reply, I'm running Edgy.  I didn't use the repo's, just downloaded it and followed the directions from [http://boinc.berkeley.edu/sea.php](http://boinc.berkeley.edu/sea.php)

But maybe it seems that wasn't the best way to do it.  I might just blow it away and install via apt-get. I guess I need to ask, do I need to totally remove it?  Or can I just install over it?

Bentov

---

### Post by autocrosser on 2006-11-03
I've been working on the graphic issue--I had it working on my Dapper install, but when Edgy went to the new Xorg--no go--As for the client to use--I am running the Debian-unstable--take a look at:

[http://wiki.debian.org/BOINC](http://wiki.debian.org/BOINC)

And add the DebianUnstable to your /etc/apt/sources.list
(In plain talk--open a terminal &  sudo gedit /etc/apt/sources.list
you will be asked for your password--return--copy/paste the info from the Wiki & save the file) open synaptic & update--when it finishes, you will have the newest Boinc packages available to you.

As soon as I know about the graphics (and HOPEFULLY the way to insert into a screensaver--have questions with Xorg-request list & Boinc-Seti list) I'll post it in a HowTo--the wiki info for graphics might or might-not work for you--give it a try8)

---

### Post by sheenaramone on 2006-11-11
> **Bentov said:**
> Thanks for the reply, I'm running Edgy.  I didn't use the repo's, just downloaded it and followed the directions from [http://boinc.berkeley.edu/sea.php](http://boinc.berkeley.edu/sea.php)

But maybe it seems that wasn't the best way to do it.  I might just blow it away and install via apt-get. I guess I need to ask, do I need to totally remove it?  Or can I just install over it?

Bentov

Hey, Bentov and other BOINCer's!  When did you download your Edgy?  The one I downloaded and installed last month on two different computers wouldn't run BOINC from my home folder.  I would get a file not found error, even though the files were there.  Someone suggested I put #!/bin/bash at the start of the scripts to get it to work but that didn't work for me.

Did you do anything special to make it work or did they change the dash/bash thing in Edgy?

---

### Post by autocrosser on 2006-11-11
I have been running Edgy from Knot1--I reset the SETI project at that time--the files are now located at /var/lib/boinc-client.

I just accepted that the location changed & went on from there--didn't loose any data units that were in progress.(I let my Dapper install finish the old units & Edgy was the only one allowed to get new work--I run two Ubuntu installs)

---

