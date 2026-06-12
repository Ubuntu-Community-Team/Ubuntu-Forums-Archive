---
title: "Can anyone teach this Debian-based dog tricks from the other side of the family tree?"
date: 2013-02-21
forum: Any Other OS
---

### Post by ausrick on 2013-02-21
At our office I am our only Linux Sys Admin. My background is almost completely from the Debian/Ubuntu side of things. This all stems back to when I was in college we used whatever versions of Linux and BSD were available in 1999. I enjoyed pounding my head into the keyboard about as much as working on the campus' AS/400 but I digress.  It wasn't until much later that someone introduced me to Ubuntu and Debian that things clicked or made sense and I've followed in that channel of comfortability ever since.

Now Vendors have their own way of doing things, and I am looking at 2 RHEL 4 Servers, 1 RHEL 5 server, 2 RHEL 6 servers, and 3 CentOS 6 servers that by me being the defacto "Linux Sys Admin." I'm just supposed to know how to admin them.

Granted, I can type things like "cd /etc/" which may be tons more than some of my Windows Only coworkers. (yay I can get the slashes the right direction! :D ) But I'm still looking at some culture shock. I know I probably can't do a sudo apt-get install, instead I have to say "this food looks delicious" or "yum" I think. ;) Does nano work? (or do I have to vi or pico or something else?) Does sudo even work? why is there an actual root user? I'm used to using my username and being in the sudoers group.

Can anyone help make this less painful for me? Sure I can spend hours reading things that may or may not actually be of use, but a crash-course of caveats fit better with my time-tables and tolerances for suffering. thanks. ):P

(btw this isn't meant to be a which is better or debate, There's no debating it... I'm looking at these boxes running these OS's in front of me right now and saying "OK! what am I supposed to do now!?")

---

### Post by snowpine on 2013-02-21
Your subscription entitles you to use the documentation here: [http://kbase.redhat.com](http://kbase.redhat.com)

If you prefer a printed book, I highly recommend Michael Jang's "RHCSA/RHCE Red Hat Linux Certification Study Guide."

And of course you can take classes through Red Hat: [http://www.redhat.com/training/courses/](http://www.redhat.com/training/courses/)

Good luck---enjoy RPM world! :)

---

### Post by CharlesA on 2013-02-21
> **snowpine said:**
> Your subscription entitles you to use the documentation here: [http://kbase.redhat.com](http://kbase.redhat.com)

If you prefer a printed book, I highly recommend Michael Jang's "RHCSA/RHCE Red Hat Linux Certification Study Guide."

And of course you can take classes through Red Hat: [http://www.redhat.com/training/courses/](http://www.redhat.com/training/courses/)

Good luck---enjoy RPM world! :)

There isn't much I can add that hasn't already been said above, except this:

Practice, practice, practice.

The differences between RedHat and Debian aren't too major - different package managers, different ways of managing services and sometimes they have different file locations, but Linux is Linux and if you know one, you can almost certainly learn another flavor. :)

---

### Post by mamamia88 on 2013-02-21
> **CharlesA said:**
> There isn't much I can add that hasn't already been said above, except this:

Practice, practice, practice.

The differences between RedHat and Debian aren't too major - different package managers, different ways of managing services and sometimes they have different file locations, but Linux is Linux and if you know one, you can almost certainly learn another flavor. :)

what he said and yes vi and nano will work.   They are just text editors and distro independent.  Honestly if you are getting paid to do this you obvisouly know enough about linux to be trusted to do it.   Some files will be in different places and the commands to update the system will have slightly different syntaxes but overall it's pretty much the same

---

### Post by ausrick on 2013-02-21
Well, It's been fun so far looking like an Idiot. some things that have came out of my mouth today are:

"I'm trying to edit this config file but none of the keys are working... what? i to get into insert mode? I'm in control mode? what's that?"

"I type adduser <username> and it just goes down to the next line... I'm used to it being interactive... so I have to do something else to change their password. Do they even have a home folder? Where do I put in their Full Name? shoot... I think I just changed MY password. ~sigh"

"sudo adduser <username> sudo doesn't work... what the heck is usermod -G? what's wheel? like on my car?"

"When I first log in it doesn't tell me if there are any updates available or whether my Server needs rebooted or not? How can I tell?"

"I seem to be missing /etc/hostname"

"Where is /etc/network/interfaces!?"

"I thought tcp_wrapper and hosts.deny and .allow were deprecated?"

"Where are my /etc/apache2/apache2.conf and sites-enabled sites-available?? a2ensite <sitename> doesn't work?"

"Bind is installed, but I don't see any /etc/bind directory, and it's evidently not version 9 because "sudo service bind9 restart doesn't work..."

So I suppose the only reason I still work here is that the other windows-centric users on my team don't have the audacity to fail... I'm sure it's not for the awesome progress I've made on-lining these systems over the last 6 hours. Not sure how I would itemize that if I billed like an independent contractor. :(

---

### Post by ausrick on 2013-02-21
> **mamamia88 said:**
> what he said and yes vi and nano will work.   They are just text editors and distro independent.  Honestly if you are getting paid to do this you obvisouly know enough about linux to be trusted to do it.   Some files will be in different places and the commands to update the system will have slightly different syntaxes but overall it's pretty much the same

I know I can vi (vim) in both, but I thought I remember being told that Red Hat didn't ship with Nano.

And I know I can set down and just start reading manuals at Chapter 1 or whatever (though thanks for the links) I just thought that there might be some major pitfalls to avoid that maybe everyone but me knew about and/or maybe some sort of focused guide like "What the Debian User needs to know about RedHat" or some-such.

I'm especially feeling pressure when basically higher-ups made this decision and from their perspective it's "RH,Debian,BSD...same thing right?" and they want to know why I've worked on something for X hours that I supposedly already "know" how to do and it's the end of the day and it's not magically working yet. Maybe it will be my turn to Laugh when they decide they need Windows 2012 Servers and I get to hear one of my compatriots whine about Metro in frustration, (but I wouldn't gloat, at least not out loud :P  ) but for now I'm feeling a lot of frustration and pressure myself.

---

### Post by mckenna1977 on 2013-02-21
Howrya? It's going to take you a bit of time but...

Instead of yum update use apt-get update

Instead of configuring your network @ /etc/sysconfig/network/ifcfg-eth0

Configure your network @ /etc/network/interfaces

Instead of doing service <service_name> start | stop
/etc/init.d/<service_name> start | stop

likewise-open is useful for integrating authentication with active directory

Use ssh/sshd for all your configuration and configure that @ /etc/ssh/sshd_config

Use sudo for elevating privileges but if you need need a shell then do sudo bash or sudo -s

You can view users at /etc/shadow or in /etc/passwd
You can view groups in /etc/groups

To change system name do hostname <new_system_name>

To be able to see other systems in your environment, add their names to the /etc/hosts file

Configure /etc/resolv.conf with the name of your DNS server

Use ifconfig to view your network config

Use ps -ax to view what process/services are running

If things won't fit on a screen use the more command

Find specific words using grep
e.g. more <file_name> | grep <search_term>

install apache by doing apt-get install apache2
Apache installs to /var/www

Search for any files using find / -name <file_name>

The above might get you started!

---

### Post by mckenna1977 on 2013-02-21
Most of what I said stands except it's for a move from CentOS to Ubuntu! You'll find the network stuff where I referred to though...

wheel is the admins group in CentOS/RedHat

Add a user to wheel by
usermod -G10 <username>

Let me know if there's any specific stuff you need to do

---

### Post by ausrick on 2013-02-21
Oh, also on the two boxes that I run cat /etc/issue on and get:

Red Hat Enterprise Linux AS release 4 (Nahant Update 8)

...They don't appear to have yum.

Basically people other than me here decide to give lots of money to whatever 3rd party vendor for their proprietary software and the hardware it comes on... and vendor says "our software and scripts will only run on said OS version and flavor"

So I suspect we as a company didn't even get access to the RHEL support because being my luck the Vendor's probably hold the license.

Basically I was greeted this week with FedEx Deliveries and emails with login credentials and I feel real or perceived miracle-worker expectations.

I think I was looking for some quick fixes (or shoulders to cry on), or maybe a quick method to save some face or make me feel like I have some better direction about the situation I'm in.

(and I try to incorporate a bit of humor, mainly as a coping mechanism... The only people that heard me ask most of those questions have been my computer screen and you guys.)

---

### Post by CharlesA on 2013-02-21
Wow, that's an old(ish) version of RH as they are now up to RH6.
[https://access.redhat.com/knowledge/articles/3078](https://access.redhat.com/knowledge/articles/3078)
[https://access.redhat.com/support/policy/updates/errata/](https://access.redhat.com/support/policy/updates/errata/)

I have no idea when EoL is for that version.

EDIT: Derp, I should have scrolled down a little more. EoL for RHEL4 is February 28, 2015, which is in about two years.

---

