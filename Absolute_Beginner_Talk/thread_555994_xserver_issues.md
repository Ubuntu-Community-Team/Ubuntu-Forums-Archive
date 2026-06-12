---
title: "xserver issues"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by j_trune on 2007-09-20
Hello all,
I'm sorta new to Ubuntu.  I've been into Linux for quite a while but that was mostly Fedora and Knoppix, and more dabbling than anything else.
Anyways I decided I wanted to dual boot windows xp and Ubuntu Dapper Drake so I got everything set up for it and everything was working great.  Then I heard about Compiz-Fusion and decided I wanted to install that....

I've tried various ways to get an Nvidia driver for my computer, and none of them have worked.  I tried envy (something about a module assistant having problems), then I tried downloading the driver directly from Nvidia and running it from the terminal (following the instructions on Nvidia's site).  That also didn't work.  I've even retried both of the above methods.  Finally I tried installing the Nvidia Legacy driver via Synaptic, and then reconfiguring xserver with the command "dpkg-reconfigure xserver-xorg" which also didn't work.  So since the beginning I've managed to screw up Ubuntu 2-3 times and I've had to reinstall.

So currently my computer is all set up (dual boots fine) with a fresh clean install of Ubuntu.  I have tried envy once on this installation (only to get the same error), and since then I've given up.  I could really use some help with this.  I'm hoping someone can tell me how to get Compiz-Fusion running.

Thanks ahead of time,

~Jeff

---

### Post by w4ett on 2007-09-20
Here is a step by step how-to:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

I used it myself...Good Luck

---

### Post by j_trune on 2007-09-20
It looks like a good guide, but it has you using Envy which doesn't work for me.  I downloaded it again, and ran it and the error message I get is "Error: Dependency is not satisfiable: module-assistant."  If I could just fix Envy, then perhaps that guide would be just the thing I needed.

---

### Post by w4ett on 2007-09-20
try booting into recovery mode and run Envy from the command line by:

```
sudo envy -t
```

Remove the old attempted driver install (option 8 or 9, I believe) and then reattempt the install.

---

### Post by j_trune on 2007-09-20
Nothing happened.  It said it couldn't find the command "envy."

---

### Post by w4ett on 2007-09-20
Try running it from the terminal.

---

### Post by j_trune on 2007-09-20
The same thing happened (nothing-it doesn't recognize 'envy' as a command).  I don't know enough about the terminal to know the goal of that command, so I tried typing it with envy's full destination, and with the whole name of the envy file on my desktop.  I figured I might as well try it, but nothing happened.

---

### Post by w4ett on 2007-09-20
> **j_trune said:**
> The same thing happened (nothing-it doesn't recognize 'envy' as a command).  I don't know enough about the terminal to know the goal of that command, so I tried typing it with envy's full destination, and with the whole name of the envy file on my desktop.  I figured I might as well try it, but nothing happened.

Envy will run from the terminal if it is installed.....When you select:

> Applications>System Tools>Envy

Will it run in the GUI format?

---

### Post by j_trune on 2007-09-20
I'm guessing that error (Error: Dependency is not satisfiable: module-assistant) I listed above means it wasn't installed then.  Cause I don't have 'envy' listed anywhere in any of the menus at the top.  I didn't think to say it before but this error comes up when I double click on the envy icon on my desktop.  There's a button in the envy window that comes up that says "install package" but it is shaded (i.e. I can't click it.).

---

### Post by j_trune on 2007-09-21
I found a helpful hint on [_this_]("http://72.14.209.104/search?q=cache:fPs1EL0C6aYJ:albertomilone.com/wordpress/%3Fp%3D83+%22Dependency+is+not+satisfiable:+module-assistant%22&hl=en&ct=clnk&cd=3&gl=us") site in the comments.  Some guy got the same error I got.  Someone else tells him later down to fix it by ensuring "repositories (multiverse and uninverse) are enabled."  I'm not sure I know how to add repositories to Synaptic (assuming you even use Synaptic), but I'm gonna try some stuff.  Any advice here is greatly appreciated.

Thanks for the help so far.

---

### Post by w4ett on 2007-09-21
Here is the official wiki:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Pretty simple actually....a cut and paste operation.

---

### Post by j_trune on 2007-09-21
Ok, so that worked.  Now I"m trying to follow that guide you posted a link to (in your first reply) and I can't do step 3.  When I type the stuff it said to type it asked for my password and then nothing came up.  I tried to go and manually edit the file, but it tells me I don't have permission.  For whatever reason I also can't seem to login as root from the login screen "root doesn't login here" or something like that.  I see the light at the end of the tunnel, but I can't get there....

---

### Post by j_trune on 2007-09-21
Ok, well I figured out how to login as root, and I changed the file 'sources.list' just like it says to do in step 3 of[ _that guide_]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/").  Then I was doing step 4 and 5 and it seemed to be going fine, except that when I entered the second of this:

gpg --export --armor 81836EBF | sudo apt-key add -

Nothing seemed to happen.  I thought maybe nothing was supposed to happen, so I went on.  Then while I was entering the next 4 command it tells you to enter in the terminal I saw something that came up with all the text after one command that said something to the effect of "no pubkey found"->whatever that means.  I went on nonetheless in hopes that that was normal.  Then I got to the end where you type "compiz --replace" in the run window and.....nothing happened.  

I don't know where to go from here.

EDIT:  I forgot mention.  I think that envy went ok-it seemed to at least(I didn't see anything that struck me as bad).  I'm not sure how to check though.

---

### Post by j_trune on 2007-09-21
Ok, so I've looked around, and I can't find much about 'pubkey' or whatever.  I'm not sure if I should try reinstalling or if there is another way of diagnosing the problem.  I guess it was stupid not to write the error thing down-sorry.

---

### Post by j_trune on 2007-09-22
Ok...well I decided to retry steps 2-4 on that guide again, but this time I recorded what I saw as problems, so here goes...


It should be noted that I only recorded what I saw as important.
Step two goes fine.

The repositories step 3 says to add have been added just fine. 

Step 3's first terminal command is "gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF" from which I get the message 'public key [B]imported' and "no ultimately trusted keys found" amongst other things.

Step 3's second command "gpg --export --armor 81836EBF | sudo apt-key add -" just yields "gpg: no ultimately trusted keys found" and then "ok"

Then we goto step 4.

The first listed command seems to go fine.  When I put in the second command though, nothing seems to happen except that "root@emmeline:~#" or the normal starter of a line in the terminal for me turns into a ">"

The next command talks about broken packages in its ouput

The last thing is that I'm going to post the whole of everything that happened in the termal window from step 3's gpg commands and forward.  I know it's a bit much, but I'm sure people on the forum will understand it far better than I do and hopefully this will help with the diagnosis.

root@Emmeline:~# gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: /root/.gnupg/trustdb.gpg: trustdb created
gpg: key 81836EBF: public key "Treviño (3v1n0) <trevi55@gmail.com>" imported
gpg: **no ultimately trusted keys found**
gpg: Total number processed: 1
gpg:               imported: 1
root@Emmeline:~# gpg --export --armor 81836EBF | sudo apt-key add -
gpg:  **no ultimately trusted keys found**
OK 
root@Emmeline:~# aptitude -y update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages [14.8kB]
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 29.1kB in 5s (5016B/s)
Reading package lists... Done
root@Emmeline:~# aptitude install compiz compiz-gnome \
> compizconfig-settings-manager compiz-fusion-plugins-extra \
> compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done 
[B]The following packages are BROKEN:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-fusion-plugins-unofficial compiz-gnome compiz-plugins
  libcompizconfig-backend-gconf libcompizconfig0 libdecoration0
  python-compizconfig[/B] 
The following NEW packages will be installed:
  compiz compizconfig-settings-manager
0 packages upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 7648kB of archives. After unpacking 22.4MB will be used. 
[B]The following packages have unmet dependencies:
  libcompizconfig0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                    Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
  libdecoration0: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
  libcompizconfig-backend-gconf: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                               Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                                 Depends: liborbit2 (>= 1:2.14.1) but 1:2.14.0-0ubuntu1 is installed.
                                 Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                                 Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                                 Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                                 Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                                 Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
  compiz-plugins: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                  Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.                  Depends: libdbus-1-3 (>= 0.94) which is a virtual package.
                  Depends: libfuse2 (>= 2.6) but it is not installable
                  Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                  Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed.
                  Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.2 is installed.
                  Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
  python-compizconfig: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                       Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                       Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                       Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                       Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                       Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                       Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
                       Depends: python (>= 2.5) but 2.4.2-0ubuntu3 is installed.                       Depends: python-support (>= 0.3.4) but it is not installable
  compiz-fusion-plugins-unofficial: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                                    Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                                    Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is installed.
                                    Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                                    Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                                    Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is installed.
                                    Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                                    Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                                    Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                                    Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                                    Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
  compiz-fusion-plugins-extra: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                               Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                               Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                               Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                               Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                               Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                               Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                               Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                               Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
  compiz-core: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
               Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
               Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
               Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
               Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
               Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.  compiz-fusion-plugins-main: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                              Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                              Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                              Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                              Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
                              Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                              Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is installed.
                              Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
                              Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is installed.
  compiz-gnome: Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is installed.
                Depends: libbonobo2-0 (>= 2.15.0) but 2.14.0-0ubuntu2 is installed.
                Depends: libbonoboui2-0 (>= 2.15.1) but 2.14.0-0ubuntu1 is installed.
                Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
                Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is installed.
                Depends: libdbus-1-3 (>= 0.94) which is a virtual package.
                Depends: libdbus-glib-1-2 (>= 0.73) but 0.60-6ubuntu8.1 is installed.
                Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is installed.
                Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed.
                Depends: libgnome-keyring0 (>= 0.7.1) but 0.4.9-1ubuntu1 is installed.
                Depends: libgnome-window-settings1 which is a virtual package.
                Depends: libgnomeui-0 (>= 2.17.1) but 2.14.1-0ubuntu3 is installed.
                Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.14.2-0ubuntu1 is installed.
                Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed.
                Depends: liborbit2 (>= 1:2.14.1) but 1:2.14.0-0ubuntu1 is installed.
                Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed.
                Depends: libpopt0 (>= 1.10) but 1.7-5 is installed.
                Depends: libwnck18 (>= 2.15.90) but 2.14.2-0ubuntu1 is installed.
                Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is installed.
                Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
compiz [0.0.2-4ubuntu2 (dapper)]
compiz-gnome [0.0.2-4ubuntu2 (dapper)]
libxcomposite1 [1:0.2.2.2-0ubuntu2 (dapper)]

Keep the following packages at their current version:
compiz-core [Not Installed]
compiz-fusion-plugins-extra [Not Installed]
compiz-fusion-plugins-main [Not Installed]
compiz-fusion-plugins-unofficial [Not Installed]
compiz-plugins [Not Installed]
compizconfig-settings-manager [Not Installed]
libcompizconfig-backend-gconf [Not Installed]
libcompizconfig0 [Not Installed]
libdecoration0 [Not Installed]
python-compizconfig [Not Installed]

Leave the following dependencies unresolved:
compiz recommends compiz-kde
Score is -489[/B] 

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
root@Emmeline:~#

---

### Post by j_trune on 2007-09-23
This is more of a bump than anything else, I'm just hoping someone will tell me what went wrong in the terminal lines I posted above.

Thanks

---

### Post by Hobo Joe on 2007-09-23
I'm not sure if you tried this, but what you need to do is boot into recovery mode, and run this command:

```

sudo sh NVIDIA-Linux-x86_---64-100.14.19-pkg2.run

```
That's just an example name though, yours may be, and probably is different. You need to make sure to put the EXACT name of the file you downloaded.

---

### Post by j_trune on 2007-09-23
I thought envy took care of the driver installation?  The terminal lines I posted are from me trying to run the commands from step 3 of [this guide]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") to installing compiz-fusion.  There's stuff in the terminal lines about stuff 'being broken" or and other stuff that isn't found.  I'm pretty sure I'm set for a graphics driver via envy.  I'll edit that terminal post and bold what I think is wrong, but I don't know much about the terminal.

---

