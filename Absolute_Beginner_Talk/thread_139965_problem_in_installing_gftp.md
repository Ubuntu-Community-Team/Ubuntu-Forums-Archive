---
title: "problem in installing gftp"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-05
i am trying to install gftp 
1) if i do sudo apt-get install gftp it says 
> Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
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
E: Couldn't find package gftp

2) so i d/lded a .tar.bz2 of gftp and when i do ./configure it says
> checking for glib-2.0 >= 2.0.0... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
checking for glib-config... no
checking for GLIB - version >= 1.2.3... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: gFTP needs GLIB 1.2.3 or higher
   
hence i d/lded a .tar.bz2 of glib 2.8.6 and installed it without any error,but still when i do ./configure for gftp it gives me the same error so what should i do now??

---

### Post by Mustard on 2006-03-05
I saw this question in your first thread, but I'm glad you posted a new one on the subject. :)

Firstly you have the mirromax repositories enabled, which I am pretty sure are now defunct (remove those).  Secondly try running this command

```
sudo apt-get update
```

alternatively, just go into synaptic and hit the 'Reload' button.  Basically you are doing the same thing either way you do it.  Another hint is, don't try to use Synaptic and apt-get at the same time.  The system won't allow it and you will lock file errors.

Its not necessary for you to install gftp using the tarball installation, nor was it necessary for you to install glib using a tarball installation.

Once you work out how to use Synaptic and/or apt-get properly, you will find installation a lot easier.

---

### Post by animesh on 2006-03-05
yeah actually i tried that update ......but i wasn't able to connect then i did by exporting proxy.....
                  so i have done update but still when i do sudo apt-get install glib it says 

W: You may want to run apt-get update to correct these problems
E: Couldn't find package glib

also with what links should i replace those mirrormax defunct ones???

---

### Post by Mustard on 2006-03-05
[QUOTE=animesh]yeah actually i tried that update ......but i wasn't able to connect then i did by exporting proxy.....
                  so i have done update but still when i do sudo apt-get install glib it says 

W: You may want to run apt-get update to correct these problems
E: Couldn't find package glib

also with what links should i replace those mirrormax defunct ones???[/QUOTE]

This is a pretty good Hoary Hedgehog sources.list I think.  Nothing out of the ordinary in it. :)

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu hoary main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu hoary universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu hoary universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
```

If you want to manually edit your sources.list use this command..

```
sudo gedit /etc/apt/sources.list
#opens the file 'sources.list' in a graphical text editor
```

Then get rid of your old sources.list completely and replace it with the one I have shown you above.

Run the update again after changing the sources.list

```
sudo apt-get update
```

With regards to finding packages and there proper names you might try searching in Synaptic, or use the apt-cache search <keyword to search with> command or you could search for packages at [http://packages.ubuntu.com](http://packages.ubuntu.com)

Also, are you trying to install gftp when you get that error?  If you have run the update then you should be able to do...

```
sudo apt-get install gftp
```

This will download and install gftp and ALL its dependencies...which is the main reason I am attempting to get your apt-get/Synaptic working.  Your problem with sudo apt-get install glib is that 'glib' is not the name of the actual package. It's probably more like libglib2.0-dev or something like that, that you are after.  Forget about installing 'glib' and just install gftp via apt-get or Synaptic.

Compiling from source ie from the tar.gz file is somewhat of an advanced skill and not one I recommend you try without becoming more familiar with linux.  There really isnt any need for you do so atm.

---

### Post by animesh on 2006-03-05
now if i am trying to do
  
sudo apt-get install gftp

i get
> animesh@ubuntu:~$ sudo apt-get install gftp
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gftp-common gftp-gtk gftp-text
The following NEW packages will be installed:
  gftp gftp-common gftp-gtk gftp-text
0 upgraded, 4 newly installed, 0 to remove and 128 not upgraded.
Need to get 515kB of archives.
After unpacking 3871kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to in.archive.ubuntu.com (82.211.81.151)]

and it just hangs there forever
same with synaptic ,it says d/lding file 1 of 4 and hangs there

---

### Post by Mustard on 2006-03-05
[QUOTE=animesh]now if i am trying to do
  
sudo apt-get install gftp

i get


and it just hangs there forever
same with synaptic ,it says d/lding file 1 of 4 and hangs there[/QUOTE]

Ok, so you are connecting via a proxy you mentioined earlier?

---

### Post by animesh on 2006-03-05
yes.....and its working because i am accessing net via it

---

### Post by Mustard on 2006-03-05
**Setting up apt-get to use a http-proxy**

```
gedit ~/.bashrc
```

add these lines to the bottom of your .bashrc file

```
http_proxy=http://yourproxyaddress:proxyport
export http_proxy
```

Save the file. Close your terminal window and then open another terminal window

Test proxy with sudo apt-get update and whatever networking tool you desire. I use firestarter to see active connections.

If you make a mistake and go back to edit the file again, remember to close the terminal and reopen it. It will not function with the new settings until you do.

---

### Post by animesh on 2006-03-05
wow............. i did exactly what you told me and yes now my update as well as install is working fine........Thanks a ton .....

---

### Post by Mustard on 2006-03-05
I can't tell you how relieved I am to see its finally working. :)

I hope things run smoothly for you now. ;)

---

### Post by chrispy on 2006-03-16
Hi, 

I'm having a very similar problem with apt-get update, except i need to connect using an auto-cofiguring proxy, I've told ubuntu to use the proxy via the option in the preferences menu, but it's still refusing to work.

Any help would be appreciated greatly

---

### Post by Mustard on 2006-03-16
[QUOTE=chrispy]Hi, 

I'm having a very similar problem with apt-get update, except i need to connect using an auto-cofiguring proxy, I've told ubuntu to use the proxy via the option in the preferences menu, but it's still refusing to work.

Any help would be appreciated greatly[/QUOTE]

Hmmm..I'm not sure how you would configure it for an autoconfiguring proxy. I can tell you how I worked something like this out on IRC one time though.  This fellow had his browser set up for an autoconfiguring proxy, and we ran a netstat command from terminal and found out what proxy address his browser was connecting to, using the output of netstat.  I can't remember what options we used with netstat to get the output we wanted.  I remember fiddling around with it for a while before we finally worked it out.

This is an extremely clumsy solution I know, but it's all I've got for an answer.  I hope someone has a better answer for you soon. :)

---

