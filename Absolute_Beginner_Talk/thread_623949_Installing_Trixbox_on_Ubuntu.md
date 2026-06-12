---
title: "Installing Trixbox on Ubuntu"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by AndyInNYC on 2007-11-26
I have found several sites which claim to let me recompile and install trixbox (asterix, freepbx, mysql, etc) on a Ubuntu system (6.06 would be my choice).

Following these scripts, I seem to hit a snag and get errors on the compiles.

Has anyone compiled and installed trixbox on a Ubuntu system?
If yes, what pointers and helpful hints can you provide <g>?

Andrew

---

### Post by kelbizzle on 2007-11-27
[http://www.freepbx.org/forum/freepbx/installation/new-install-guide-for-asterisk-and-freepbx-on-ubuntu-6-06-lts](http://www.freepbx.org/forum/freepbx/installation/new-install-guide-for-asterisk-and-freepbx-on-ubuntu-6-06-lts)


This ought to get you started. I did a search for "trixbox ubuntu" It was the fourth result. Not sure which version you are running.

---

### Post by AndyInNYC on 2007-11-28
Yes, I've seen this site and done searches - the problem is that the compiles generate errors and I don't end up with a working system.

If someone has actually completed one of these 'install from source' installs, I'd like to hear what may be missing from the various guides.

Thanks for the link kelbizzle and I do appreciate the time you took reading the post.

andrew

---

### Post by Cochise on 2007-11-28
what errors do you get are they dependency errors?

---

### Post by AndyInNYC on 2007-11-28
Unfortunately, I gave up pre-Thanksgiving on this type of install and just used the ISO so I can't tell you what the errors were.

If you have installed from source on Ubuntu, what issues, if any, did you encounter?

Since Mommy and Daddy taught me how to reed and rite, I'm reasonably sure that I was able to follow the directions posted to the letter and that I didn't create a problem due to an inability on my part.

I'd like to keep Ubuntu as the distro on my various Linux machines rather than put Centos on one, so any help would be appreciated.  Got a spare machine you want to tear down and install while fully documenting all steps <g>?

Andrew

---

### Post by ectospasm on 2007-12-04
I have Asterisk (not Trixbox) running on an Ubuntu Server (7.10 or 7.04, I can't remember which), and I could compile it with no problems.  Of course, I got it from Digium's Subversion repository.  If you need MySQL and Apache on your Asterisk system, and you want to use Ubuntu, I suggest installing Ubuntu Server with the LAMP stack, as a base.  Then make sure you have build-essential installed, and you should be good to go.

HTH

---

### Post by lostinthemountains on 2008-02-06
I've been doing an Asterisk install with a TDM400P from source on Gutsy 7.10 recently, and as far as Asterisk itself goes, it's all been straightforward. Same here for the Digium Subversion repositories.  The first problem I did run into was clients unable to navigate the voicemail. This turned out to be one client buggy (don't use Zoiper; although the win32 client worked fine) and one misconfigured (incorrect DTMF setting). Asterisk was working perfectly. I've just finished persuading it to log to mySQL, and that has been troublesome, but it's running now. If you feel like giving Asterisk under Dapper another try, I'm willing to assist where possible. I've got a few machines running Dapper around, so I can use them to test.

---

### Post by AndyInNYC on 2008-02-18
OK,
I've installed 7.1 Server as LAMP.

apt-get update and upgrade
apt-get install php5 php5-cli php5-mysql mysql-server php-pear php-db openssh-server curl sox apache2 subversion build-essential libncurses5-dev libssl-dev linux-headers-`uname -r` libmysqlclient15-dev

cd /usr/src
svn co [http://svn.digium.com/svn/asterisk/branches/1.2](http://svn.digium.com/svn/asterisk/branches/1.2) asterisk-1.2
svn co [http://svn.digium.com/svn/zaptel/branches/1.2](http://svn.digium.com/svn/zaptel/branches/1.2) zaptel-1.2
svn co [http://svn.digium.com/svn/libpri/branches/1.2](http://svn.digium.com/svn/libpri/branches/1.2) libpri-1.2
svn co [http://svn.digium.com/svn/asterisk-addons/branches/1.2](http://svn.digium.com/svn/asterisk-addons/branches/1.2) asterisk-addons-1.2
svn co [http://svn.digium.com/svn/asterisk/trunk/sounds](http://svn.digium.com/svn/asterisk/trunk/sounds) asterisk-sounds
cd /usr/src/libpri-1.2 && make install
cd /usr/src/zaptel-1.2
sed -i 's!^#define ECHO_CAN_KB1!/* #define ECHO_CAN_KB1 */!' zconfig.h
sed -i 's!/\* #define ECHO_CAN_MG2 \*/!#define ECHO_CAN_MG2!' zconfig.h
make install
cd /usr/src/asterisk-1.2 && make install
cd /usr/src/asterisk-addons-1.2
sed -i 's/_GNU_SOURCE/_GNU_SOURCE -DMYSQL_LOGUNIQUEID/' Makefile
make install

- this should have me up and running with Asterisks - I get a 'bad fd number' error when I try to start asterisk.

Help?

The cut and paste above is from [http://www.aussievoip.com/wiki/index.php?page=freePBX-Ubuntu](http://www.aussievoip.com/wiki/index.php?page=freePBX-Ubuntu)

Regards,

Andrew

---

### Post by ectospasm on 2008-02-23
Any reason why you've installed 1.2 instead of 1.4?  1.2 is no longer being maintained, and 1.4 has been stable for several months.

That being said, to fix your problem change the init script to point to #!/bin/bash instead of #!/bin/sh.

 **EDIT**

You should change the first line of safe_asterisk to #!/bin/bash.  It shouldn't matter for the init script...

---

### Post by AndyInNYC on 2008-02-25
I'm attempting to use 1.2 due to the handling of faxes and the general stability.  My zapMicro card also doesn't seem to like the 1.4 installs I've tried.

Since I need to patch the zaptel files to get a dialtone on my phone, I'm trying to use what at least seems to work.

I'll try your script change now that I seem to have a reliable backup procedure.  Clonezilla seems to work and properly restore all partitions - I've tried using mondo, but it doesn't like CentOS 4.5 and Ghost 11 doesn't seem to restore the swap partition (etc).

I'll let you know if I succeed.

Thanks

Andrew

---

