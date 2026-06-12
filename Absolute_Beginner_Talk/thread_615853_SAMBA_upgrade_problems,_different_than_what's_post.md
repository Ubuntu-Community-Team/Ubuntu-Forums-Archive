---
title: "SAMBA upgrade problems, different than what's posted"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Howlin' Hobbit on 2007-11-17
I am getting different error messages about the recent SAMBA upgrade problems (i.e. no "access forbidden" stuff). When the upgrades first appeared in my notifier and I ran the update manager I got this message:

> The following problems were found on your system:

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.4_i386.deb: subprocess new pre-removal script returned error exit status 102

Then the notifier said I should either do: sudo apt-get install -f or use Synaptic to fix the broken packages.

Using apt-get I end up with a load of text but the key stuff (I think) is at the bottom...
> 
Unpacking replacement swat ...
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.5_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Preparing to replace samba-common 3.0.22-1ubuntu3.4 (using .../samba-common_3.0.22-1ubuntu3.5_i386.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-doc 3.0.22-1ubuntu3.4 (using .../samba-doc_3.0.22-1ubuntu3.5_all.deb) ...
Unpacking replacement samba-doc ...
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Note that toward the beginning it says "Correcting dependencies... Done" but apparently not.

OK... on to Synaptic then... I apply the "broken" filter -- I *think*... I could be doing something wrong there -- and it works on it a while and then gives me about the same error as the update manager, meanwhile throwing in some stuff about 404 errors on some of the "non-official" repositories I've got checked.

*Now* when I try to start the upgrade manager I get:
> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

How do I fix this so that the SAMBA upgrades install and the little orange icon goes away (for a bit)?

One suggestion I read in a different thread was to go to System/Admin/Software Sources and have it choose the best server but I don't *have* a System/Admin/Software Sources.

If you need further info let me know.

Any help appreciated! Thanks!

---

### Post by mikeyphi on 2007-11-18
What happens if you open a terminal and enter:

sudo apt-get -f install

and if that's no good try:

sudo dpkg --configure -a

---

### Post by Howlin' Hobbit on 2007-11-18
> **mikeyphi said:**
> What happens if you open a terminal and enter:

sudo apt-get -f install

and if that's no good try:

sudo dpkg --configure -a

Near as I can tell  the syntax is "sudo apt-get install -f" and the results of running it are in my initial post.

What does "sudo dpkg --configure -a" do? Will I need to know config options as it's running?

Thanks for your time!

---

### Post by mikeyphi on 2007-11-19
Just enter each of the commands  - there won't be any further options, it'll either fix the problem or do nothing!!

---

### Post by Howlin' Hobbit on 2007-11-19
"sudo apt-get -f install" returns:

> Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/2850kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
(Reading database ... 109620 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.5_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

"sudo dpkg --configure -a" returns:

> dpkg: dependency problems prevent configuration of swat:
 swat depends on samba (= 3.0.22-1ubuntu3.5); however:
  Version of samba on system is 3.0.22-1ubuntu3.3.
dpkg: error processing swat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 swat

Hovering the mouse over the "update manager" icon gives me:

> 
An error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong.
The error message was: ' Error: BrokenCount > 0'

Still broken. Anyone with any other ideas?

---

### Post by mikeyphi on 2007-11-20
OK
Looks as though you will have to 'force' install of the Samba update:

Quote
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.5_i386.deb) ...
...
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb (--unpack):


I suggest you open Synaptic, find Samba and, if samba_3.0.22-1ubuntu3.5 if shown as available (probably as latest version), use the menu option to force installation.
If this version of Samba is not shown then use a terminal to force install:

sudo dpkg -i --force-install /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb

---

### Post by Howlin' Hobbit on 2007-11-20
Neither of the "force" variants worked. I'm getting the same errors, no SAMBA install, the update manager icon is still sitting there telling me the same thing.

I try to use the "broken filter" in Synaptic and then tell it to fix them. It says it "successfully fixed" the broken packages but it *hasn't*.

In the case of the "force" via terminal the error is: dpkg: unknown force/refuse option `install'

I can't pick through the help file to figure out the proper syntax as I've never done this before.

How do I get rid of this?!?

---

### Post by Clogger on 2007-11-21
I have exactly the same error and have followed all the fixes to no avail. 

I am using Dapper lts.  I restored a recent backup hoping that I had a corrupt script that would be fixed by restoring but when I updated the backup to current spec, the same error returned exactly as before.  

Can anyone please suggest a fix for this?

TIA

---

### Post by Howlin' Hobbit on 2007-11-23
I, too, am running Ubuntu lts. Should have mentioned that before, sorry.

---

### Post by Clogger on 2007-11-28
Bump

Anyone please?

---

### Post by Leso on 2007-12-14
I would also like to know, if someone managed to fix this problem. Software properties was rendered useless, because of this single package.

Edit; By the way, forcing a different version gives the following messages;
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory.


Edit of the edit; I did what Sebata_Afrika suggested in [another topic]("http://ubuntuforums.org/showpost.php?p=1408484&postcount=3") , and it worked!

> **Sebata_Afrika said:**
> Seems like Rudi (a colleague) helped me solve the problem, here are the steps.
- got inside this folder by: $ cd /etc/rc2.d/
- and checked all the links, particularly to see the link between K09samba and samba by: $ ls -al (this is what we found  K09samba -> /samba)
- then removed K09samba by: $ sudo rm K09samba
- then removed samba by: $ sudo apt-get remove -f samba
- we then did this: sudo apt-get -f install (might not do anything)
- the install samba: $sudo apt-get install samba
- and created the soft link: $ sudo ln -s ../init.d/samba K09samba
Then everything worked. We followed the same procedure in rc3.d strating changing the directory.

---

### Post by Howlin' Hobbit on 2007-12-14
This sounds quite hopeful! However, I have two questions... first:

When I get to the ls command in either /etc/rc2.d/ or /etc/rc3.d/ I find S91samba -> /samba. Should I assume that when I get to the soft link part (after reinstalling) I should assume it's S91samba again? And thus enter:

$ sudo ln -s ../init.d/samba S91samba

Correct?

Second, the last line of the fix says to do everything in the list again in /etc/rc3.d/ over again. Am I going to be re-removing and re-reinstalling samba or am I going to end up with two installations of samba?

---

### Post by Leso on 2007-12-15
Not sure, actually. I'm no samba expert, i was born with two left feet. I am using ubuntu dapper, so i assume that, if you have the same bug, you are also using dapper. Your soft link seems to be different of what i had. I lent my laptop to my sister, so i'm not able to make a comparison right now.

 I bet she is still trying to find winamp.

I believe that  reinstalling twice is kind of overkill, so you should be able to fix that skipping the installation in rc3.d/ . Just deleting and recreating the soft link in the second directory might be enough. If it doesn't work, you might try the whole process. Samba is not working already, so you have got nothing to lose.

---

