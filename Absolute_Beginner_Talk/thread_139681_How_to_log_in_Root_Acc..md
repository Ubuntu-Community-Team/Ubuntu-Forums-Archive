---
title: "How to log in Root Acc."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-04
I installed ubuntu 5.04 hoary tonight. Now i want to log in the root acc. so that i can change the resolution and network settings but on the login screen if i type root as username and my root password as password, it do not allows me to login and says administrator can't login from this screen whereas my normal user login is working fine. 
                         Kindly help me asap [-o<

---

### Post by Klaidas on 2006-03-04
Ubuntu is diferent from other with this root thing. More info here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)  ;)

---

### Post by taurus on 2006-03-04
You can't log in as root UNTIL you set up a password for it.  However, you can use "sudo" to do all the things that you have describe.  
```

sudo <command>

```
When it asks you for a password, use the same one that you log into your regular account.

On the other hand, Hoary is quite old so why don't you use Breezy which is the latest version of Ubuntu (until April when Dapper comes out)...

---

### Post by aysiu on 2006-03-04
You don't need to log into the root account:
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

### Post by animesh on 2006-03-04
Thanks for the prompt replies but i have 2 problems now :
1) i already did su root and was successful in changing to root but i don't know how to configure my ip,DNS,Gateway,Resolution from there 
2) When i try to do sudo passwd root it gives me some error saying postdrop : cannot find file public/pickup....and hence i am unable to activate the root acc. ,by logging in root acc. i can directly change the resolution and ip settings from the options in taskbar.
     i am unable to print the whole error here as at present i have to switch to windows for accessing net so kindly bear with me.

---

### Post by animesh on 2006-03-04
i am sorry for posting again but i am facing the above mentioned problems and can't find anything on net also.....please help me .

---

### Post by Mustard on 2006-03-04
[QUOTE=animesh]i am sorry for posting again but i am facing the above mentioned problems and can't find anything on net also.....please help me .[/QUOTE]

I think the problem for us is that the error message is the big clue as to what the issue is.  From reading just the portion of the error you have shown, my first thoughts are, you have mucked something up on your install.  Sudo should not be returning any errors on a clean default install if everything went according to plan.  Did you do a default install or an expert install when prompted by the install CD?  What changes have you made to your system since then?  The big unknown issue from my perspective is what have you been doing to reach this stage of a dysfunctional sudo command?  I simply have no idea at this point. :)

I'd be tempted to start from scratch if you haven't installed and configured much on your system at present.  After installing from scratch, I would be asking questions about network configuration as I think there would be a number of guides around online for Hoary Hedgehog 5.04.

---

### Post by animesh on 2006-03-05
thanks for the advice. i formatted the drive and reinstalled ubuntu by default pathway,think i was goofing up somewhere in expert installation.
                              Now i have configured my network settings...... and am posting from ubuntu ...yehhhh :) but how do i configure the resolution ?? 
what i have been trying is 
           system>preferences>screen resolution but it do not shows any other option than 640x480 and same holds for the refresh rate.

---

### Post by aysiu on 2006-03-05
This is a good resource:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by animesh on 2006-03-05
Done that too...... Thanks
now i am trying to install gftp 
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
The first error occured because your package list needs updating.  To do it via command line you would type this command..

```
sudo apt-get update
```

or in Synaptic, you would press the 'Reload' button.

Don't try to use apt-get while you have Synaptic open or vice versa.  If one is in operation it will lock the other out with a 'lock file'.

Either of these will download the latest package list from the online repositories. There is no need for you to download the tarball installation.  When you have updated your package list you will be able to find gftp.  If you can't then you should add the 'universe' and 'multiverse' repositories.

Also you have repositories in your sources.list above that are no longer available.  I don't know where you got them, but they are out of date.  The mirromax repositories are now defunct.  You should remove them from your sources.list.

I encourage you to learn how to use Synaptic Package Manager or apt-get via command line properly, as it will save you a lot of hassle.

If you have further problems I suggest you start a new thread, with a subject line that describes that problem.  Currently people perusing the forums are going to see this thread asking about logging into a root account, and possibly pass it by.  This is probably not a good way to get a solution on a repository problem.

---

