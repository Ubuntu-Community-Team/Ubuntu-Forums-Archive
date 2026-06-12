---
title: "Can't install VMWare?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by tenchi86 on 2006-08-14
Ok heres my problem. I heard about VMWare and tried to install it using;
> sudo apt-get install vmware-playerWhich seemed to go ok up until a point where I got these errors;
> Starting VMware services:
Virtual machine monitor failed
Virtual ethernet failed
Module vmnet is not loaded. Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
. After that I checked and VMWare Player can be found under Applications/System Tools though when I load it I get a menu to load a .VMX file which I then reliezed was just a way to load certian applications when I want a full emmulation. So I was trying to follow the guide on here about installing VMWare Server and got to the part where you are asked to load the installer when I get;
> ----@-----:~$ cd Desktop/vmware-server-distrib
----@-----:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.
So I tried 
> ---@----:~$ sudo apt-get remove --purge vmware
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vmware
In order to remove it but as you can see it failed. I also looked in Add/Remove programs but I cannot find it. Besides that whenever I try to install a new application VMware tries to reinstall and always fails, so it's getting a little annoying. **My question is, how do I go about fully removing VMWare so I can install the Server edition?** I was not sure if this would go in the VMware install thread as it's not so much about the guide as it is my OS being partially messed up. Thanks for any help and if you can please be as simple as possible with me as I have only been on Linux now a few days.

---

### Post by NetworkGuy on 2006-08-14
Maybe the right syntax is 

sudo apt-get remove --purge vmware-player

---

### Post by djsroknrol on 2006-08-14
> **tenchi86 said:**
> Ok heres my problem. I heard about VMWare and tried to install it using;
Which seemed to go ok up until a point where I got these errors;
. After that I checked and VMWare Player can be found under Applications/System Tools though when I load it I get a menu to load a .VMX file which I then reliezed was just a way to load certian applications when I want a full emmulation. So I was trying to follow the guide on here about installing VMWare Server and got to the part where you are asked to load the installer when I get;

So I tried 

In order to remove it but as you can see it failed. I also looked in Add/Remove programs but I cannot find it. Besides that whenever I try to install a new application VMware tries to reinstall and always fails, so it's getting a little annoying. **My question is, how do I go about fully removing VMWare so I can install the Server edition?** I was not sure if this would go in the VMware install thread as it's not so much about the guide as it is my OS being partially messed up. Thanks for any help and if you can please be as simple as possible with me as I have only been on Linux now a few days.

in a terminal, go to:

/usr/bin/ and look for a file called vmware-uninstall.pl and run that..it should remove everything and them you can install VMware server edition with this [link]("http://ubuntuforums.org/showthread.php?t=183209") to a good guide

---

### Post by tenchi86 on 2006-08-14
Thanks for the advice so far. I tried 
> sudo apt-get remove --purge vmware-player
and it seemed to work as in it claimed to be removing everything. However even though the vmware-player now appears removed I still get the same error about there already being vmware installed. I also tried running vmware-uninstall.pl but was not to sure how so tried this. 
> ----@----:~$ cd /usr/bin/
----@-----:/usr/bin$ sudo ./vmware-uninstall.pl
sudo: ./vmware-uninstall.pl: command not found
----@-----:/usr/bin$ sudo vmware-uninstall.pl
sudo: vmware-uninstall.pl: command not found

both failed as you can see. So I went there and tried running the file in terminal using the open application option but nothing happened. As before thanks for looking over this.

---

### Post by djsroknrol on 2006-08-14
Can you go to /usr/bin/ using nautilus and see the file in there?..it almost sounds like the file isn't there....

---

### Post by tenchi86 on 2006-08-14
Well I am not sure how to open Nautilus off hand but using the built in file browser with "show hiddein files and folders" on, no I am actually not able to find it in there. I ran a search for it and found many VM files though from what I can tell they are all in the vmware-server-distrib folder. I tried restarting my computer to see if that would help and it's no longer telling me I need to update my software as it was before. Though I also am still gettign the same error message as before, so it seems slightly fixed but not enough to install the Server distribution.

---

### Post by djsroknrol on 2006-08-14
> **tenchi86 said:**
> Well I am not sure how to open Nautilus off hand but using the built in file browser with "show hiddein files and folders" on, no I am actually not able to find it in there. I ran a search for it and found many VM files though from what I can tell they are all in the vmware-server-distrib folder. I tried restarting my computer to see if that would help and it's no longer telling me I need to update my software as it was before. Though I also am still gettign the same error message as before, so it seems slightly fixed but not enough to install the Server distribution.

The vmware-uninstall .pl file should be in:

vmware-server-distrib/bin/

poke around in there...I can't remember where the file is right off as I'm not on my Desktop box at the moment, but it will set things straight so you can reinstall it right...

---

### Post by tenchi86 on 2006-08-15
Your correct the file is there, though I am not sure how I go about running it. Also is that file universal or will that only work for the Server install?

---

### Post by JerMe on 2006-08-15
Do I know you? :)

Next time you need to find something, use **locate**.  For example:
```
locate vmware
```

will give you an assload of results for "vmware".  I have vmware server installed, so when I locate **vmware-uninstall.pl**, I get
```
/usr/bin/vmware-uninstall.pl
/home/jerme/downloads/vmware-server-distrib/bin/vmware-uninstall.pl
```

To run your vmware-uninstall.pl script, just locate it, then put the whole (absolute) path to the script.  For example, to uninstall my vmware server, I'd issue
```
sudo /home/jerme/downloads/vmware-server-distrib/bin/vmware-uninstall.pl
```

The .pl extension is to identify the script as a perl script.  If it's giving you trouble, prepend a perl to it:
```
sudo perl /home/jerme/downloads/vmware-server-distrib/bin/vmware-uninstall.pl
```

The vmware-uninstall.pl script is probably specific to the version of the vmware that it was packaged with, so it's likely that the server uninstall won't work to uninstall the vmware-player files.

Go back to the OC, man. :twisted:

---

### Post by djsroknrol on 2006-08-15
> **JerMe said:**
> Do I know you? :)

Next time you need to find something, use **locate**.  For example:
```
locate vmware
```

will give you an assload of results for "vmware".  I have vmware server installed, so when I locate **vmware-uninstall.pl**, I get
```
/usr/bin/vmware-uninstall.pl
/home/jerme/downloads/vmware-server-distrib/bin/vmware-uninstall.pl
```

To run your vmware-uninstall.pl script, just locate it, then put the whole (absolute) path to the script.  For example, to uninstall my vmware server, I'd issue
```
sudo /home/jerme/downloads/vmware-server-distrib/bin/vmware-uninstall.pl
```

The .pl extension is to identify the script as a perl script.  If it's giving you trouble, prepend a perl to it:
```
sudo perl /home/jerme/downloads/vmware-server-distrib/bin/vmware-uninstall.pl
```

The vmware-uninstall.pl script is probably specific to the version of the vmware that it was packaged with, so it's likely that the server uninstall won't work to uninstall the vmware-player files.

Go back to the OC, man. :twisted:

I've used it to uninstall a botched player install before, so I can vouch for the fact that it will work...

---

### Post by JerMe on 2006-08-15
so you used the vmware-server version of the vmware-uninstall to uninstall vmware-player?

---

### Post by XaeroDegreaz on 2006-08-29
I can vouch for the dude's problem. I just installed Ubuntu a couple days ago and I'm workin with Linux for the first time. I have followed every un-install step that I have seen on these forums and nothing seems to work. I still cannot install VMWare Server.

I'm wondering, when I used the 'Locate vmware' function, that if I just deleted every single thing that I saw (Besides the directory that I wish to install the new VMWare from) would that be bad? I know some of that shit just isn't the build from the VMWare player. I know some of it is important stuff, that comes with Ubuntu.

If someone finds a way to do this perfectly, or if the original poster solves his problem, please post it, because I need to use Windows =}~

Thanks, great help so far though guys!

---

### Post by XaeroDegreaz on 2006-08-29
I just had an idea.... I'm thinking that there is some sort of flaw going on, bcause there are no traces left of the old VMWare stuff, so, I'm going to make a backup of the new installer, and then I'm going to edit the Perl script and take out the lines that halt the execution ;) I'll repost if it works.

---

### Post by XaeroDegreaz on 2006-08-29
Okie doke. I edited tha vmware-install.pl and commented with a # the lines that produce the error:

```

#if ($status) {
    #remove_tmp_dir($bkp_dir);
    #error('Failure' . "\n\n");
#}

```

Aight, in Perl when the function 'error()' is invoked, it automatically stops all remaining script. SO once commented, the script processes as normal, installing everything as it should be.

Also, once the stuff started installing, I happened to notice something that I had saw earlier while looking for something that was halting the installation. There are some folders: 

```

/etc/init.d/vmware-player
/etc/rc0.d/K20vmware-player
/etc/rc1.d/K20vmware-player
/etc/rc2.d/S20vmware-player
/etc/rc3.d/S20vmware-player
/etc/rc4.d/S20vmware-player
/etc/rc5.d/S20vmware-player
/etc/rc6.d/K20vmware-player
/etc/vmware

```

That may contain files. You can check by using the 'locate vmware' command in the terminal. My folders are empty, and here is why: (This will all make sense in a moment, bare with me).

After I finished installing this 'patched' install, I then UNINSTALLED, using the vmware-uninstall.pl located in the /bin dir. This went ahead and actually cleared all of the files, it finally found everything that was blocking the initial install :) Sweet right?

After you uninstall the installation that you have just installed, re-install (WITHOUT THE COMMENTED ERROR STATEMENT).

If your uninstall step worked, then you will no longer recieve the error, finish the installation.

At the time of me writing this, I have still not completed my setup, I still need to re-run the vmware-config because  guess I'm missing some plugins. But, I hope this fixes everyones problem!

If anyone else is having this problem, please refer them to this post. I have tested it and it works. Happy virtualizing!

---

