---
title: "&quot;Service is not running&quot;"
date: 2012-11-28
forum: Any Other OS
---

### Post by brendonwp on 2012-11-28
Hi All

I am running Linux Mint 13 64 bit(based on Ubuntu 12.04 packages).  I installed Ubuntu One successfully. and it ran fine for a while.  I disconnected the service some time ago, and when I went to reconnect it I found it does not respond.

Clicking on the icon I see that it says "Service is not running".  Using u1sdtool I get the message below:

u1sdtool --status

Traceback (most recent call last):
  File "/usr/bin/u1sdtool", line 59, in <module>
    from ubuntuone.platform.tools import (
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/__init__.py", line 34, in <module>
    from ubuntu_sso.xdg_base_directory import xdg_home
ImportError: No module named xdg_base_directory

Any suggestions?

Thanks!

---

### Post by brendonwp on 2012-12-22
OK, I now understand that ubuntuforums has a policy of not responding to posts for non-"official" releases. So I am not going to get any help here as I am asking about a deviant distro :)

For the benefit of anyone who arrives here with a similar problem, here are a few notes below.  If you have found a solutions, please post a link here!

Notes:
1.  There are directions for installing Ubuntu One on Linux Mint 13 and 14 - one that worked for me in the past is:  
 [http://www.noobslab.com/2011/08/install-ubuntu-one-on-linux-mint.html](http://www.noobslab.com/2011/08/install-ubuntu-one-on-linux-mint.html)
2. I used "apt-get remove" to remove my non-functioning installation, and then reinstalled using the above guide.  The syncdaemon was not installed (checked using synaptic), so I then ran:
 "sudo apt-get install ubuntuone-client-dbg"
These are python debug codes, so should not cause a problem.  The daemon was then installed as part of this process, but did not start.
3. I still had the same problem using u1sdtool. I tried using python to start the syncdaemon in /usr/lib/ubuntuone-client in the terminal, and received the same error. Same with the login script. Googled around and found someone else with the same problem in Mint (Mate Window manager):
[http://forums.linuxmint.com/viewtopic.php?f=47&t=118514](http://forums.linuxmint.com/viewtopic.php?f=47&t=118514) 
4. I am now using SpiderOak (free but proprietary) to backup my Ubuntu One data now.  It would be great if I could use Ubuntu One instead, but I've now run our of time.
5. The most promising line of investigation seems to be the one raised in 3 above - I've tried using "apt-get install ubuntuone-installer", but that just never completes running and raises a nautilus-related error.

---

### Post by lisati on 2012-12-22
*Thread moved to **Other OS/Distro Talk**.*
Although based on Ubuntu, Linux Mint is a distro in its own right.

---

### Post by offgridguy on 2012-12-22
Hello brendonwp;  probably the reason you never got a response before was due to the fact you were posting in different sub-forum,
There is no policy of not responding to non-ubuntu releases, OtherOS/Distro Talk
is for that very thing. Good luck and welcome to the forum. ):P

---

### Post by sja45uk on 2013-02-25
I got a related 'xdg_base_directory' error message but when trying to run the 'ubuntuone-installer'. [http://askubuntu.com/questions/218547/ubuntu-one-on-ubuntu-studio-12-04](http://askubuntu.com/questions/218547/ubuntu-one-on-ubuntu-studio-12-04) was also similar to my problem.  None of the fixes that I Googled seem to help. My fix was to use the Synaptic Package Manager to "Mark for Complete Removal" & "Apply" all packages found as installed when using 'ubuntuone' as a "Quick Filter" string. 

Then I used 'sudo aptitude install ubuntuone-installer' to get a clean install.  I understand that 'aptitude' does a better job than 'apt-get' when there are dependency issues on a single package. I just accepted the suggestions for other packages to remove or install hoping to get a consistent installation. Finally I could get ubuntuone-installer to open a GUI without the error report 
"... from ubuntu_sso.xdg_base_directory import xdg_home ImportError: No module named xdg_base_directory"

---

