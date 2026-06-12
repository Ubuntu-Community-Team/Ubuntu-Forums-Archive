---
title: "I'd like to install a firewall . . ."
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by eric.stone on 2005-10-08
What is the best firewall for a relative novice?  Bastille?  Firestarter?  I'd like to install via apt-get.  Thanks!

---

### Post by matthew on 2005-10-08
The most commonly recommended around here is Firestarter. It is easy to setup and understand and works well. Also, if you have questions you are likely to find someone who knows how to use it in these forums.

---

### Post by eric.stone on 2005-10-08
Thanks!  Is the command: Apt-get install firestarter?:cool:

---

### Post by Efwis on 2005-10-08
[QUOTE=eric.stone]Thanks!  Is the command: Apt-get install firestarter?:cool:[/QUOTE]
you want to be in terminal so you enter the following. you do not need to type the $.

```
$ sudo apt-get install firestarter
```

This will install it, then do the following to restart your gnome-panel. don't worry it will restart on its own.

```
$ killall gnome-panel
```

next click on applications>system tools>firestarter and follow the prompts to configure it. any questions ask :)

---

### Post by eric.stone on 2005-10-08
Got the following.  Do I have the name of the app correct?  

root@XXXXXXX:/home/XXXXX # sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter

Thanks,
Eric

---

### Post by Efwis on 2005-10-08
if you want save yourself a little heartach, use synaptic instead. just do a search for Firestarter after a couple of seconds it should pop up, if it doesn't let me know you may need to do some work on your repository list.

system>administration>synaptic package manager

---

### Post by mustang on 2005-10-08
[QUOTE=eric.stone]Got the following.  Do I have the name of the app correct?  

root@XXXXXXX:/home/XXXXX # sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter

Thanks,
Eric[/QUOTE]

This might be because you haven't added the extra repositories:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Mustard on 2005-10-09
[QUOTE=mustang]This might be because you haven't added the extra repositories:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]

That link is out of date.  It's still got the defunct backports sections listed. This one below will add the new official backports.

[https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)
[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

---

### Post by eric.stone on 2005-10-09
Ran the search on synaptic, no firestarter.   How do I add the extra repositories?  I tried the ubuntu guide and I got to the point where I was supposed to swap out some code.   I'm lost.   What type of file am I editing?  I can cut and paste, but I'm not sure what it is that I'm editing.  Thanks, 
E

---

### Post by Maniak on 2005-10-09
Just follow the guide in what it says. Best idea is to open a terminal and then copy and paste the commands across. That will get you started by cranking up GEdit. Then copy and paste their recommended code (over the top of the old stuff), close and save when asked.
Go back to Synaptic - reload and rerun your search. You **should** be away laughing.

---

### Post by matthew on 2005-10-09
Hi, Eric,

You can look here if my instructions aren't clear enough: [https://wiki.ubuntu.com//AddingRepositoriesHowto]("https://wiki.ubuntu.com//AddingRepositoriesHowto")

I would just do this: open a terminal. Type
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` This will make a backup of your current repositories list just in case. Now type
```
sudo gedit /etc/apt/sources.list
``` If you are using Ubuntu 5.04 (aka Hoary) delete everything there and paste this in:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports and extras
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
``` If you are using Ubuntu 5.10 (aka Breezy) use this:
```
## Uncomment the following two lines to fetch updated software from the network
 deb http://archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe
 
 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
 
 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
 
 deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
``` Save the newly edited file.

Open synaptic. It may give you an error...ignore it, we are about to fix the problem it will try to tell you about.
Click "reload". wait.
When it is done loading the list of programs form the repositories, scroll down and you should find firestarter listed.

Hope this was helpful! Hang in there, it gets easier!!

---

### Post by eric.stone on 2005-10-09
Just added the extra repositories and firstarter showed up in synaptic!  Will go look for it now. Thanks.

What do I get by adding the backports?  Is it as easy as adding the extra repositories?
E

---

### Post by eric.stone on 2005-10-09
Matthew,
Firestarter showed up after I added the repositories through synaptic.  I've got the app on my desktop ready to run through the "Firewal wizard."  Is there any reason to do the command line cut and paste that you set out for me now?  I will if there is some advantage.
Eric

---

### Post by eric.stone on 2005-10-09
Mustard,
The instructions worked great for the adding the repositories, should I also add the backports?
Thanks,
Eric

---

### Post by Perfect Storm on 2005-10-09
If you want firestarter to start up automatically:

```

sodo gedit /etc/sudoers

```

add in the bottum of the page:
**<insert your username> ALL= NOPASSWD: /usr/sbin/firestarter**
Save it.

Now go to System ---> Preferences ---> Sessions
Switch to Startup Prgrams tab and click *add* button.
In the command box: **sudo firestarter --start-hidden**
and order box: **50**

---

### Post by eric.stone on 2005-10-09
Artificial,
Tried that code, didn't work.   Sodo?
Eric

---

### Post by eric.stone on 2005-10-09
OK, I ran it as sudo.  Following your steps now.
Thanks,
E

---

### Post by eric.stone on 2005-10-09
Artificial,
Done.  HOw do I know if I did it right?
Eric

---

### Post by Perfect Storm on 2005-10-09
ops sorry, spell error :/

---

### Post by Perfect Storm on 2005-10-09
Restart the machine and if the firestarter icon appears in the sys tray then everything is okay :)

---

### Post by Mustard on 2005-10-09
[QUOTE=eric.stone]Mustard,
The instructions worked great for the adding the repositories, should I also add the backports?
Thanks,
Eric[/QUOTE]

If you used mathew5's sources.list,  you should have it all.

---

### Post by eric.stone on 2005-10-09
Art, All,
Thanks for all the help w/Firestarter.  App is up and running.  While I'm at it, should I install "Hoary Extras"?
E

---

### Post by eric.stone on 2005-10-09
All,
Thanks for the great support.  I've got a lacrosse game tomorrow (old guys division) so I've got to get some sleep.  I'll read any further responses in the morning.  I'm especially interested in the "Hoary Extras."
Eric

---

### Post by Bunro on 2006-03-16
[sudo gedit /etc/sudoers

add in the bottum of the page:
<insert your username> ALL= NOPASSWD: /usr/sbin/firestarter
Save it.

Now go to System ---> Preferences ---> Sessions
Switch to Startup Prgrams tab and click add button.
In the command box: sudo firestarter --start-hidden
and order box: 50]

I did the installation and I followed the steps as described above. But added the lines
<insert your username> ALL= NOPASSWD: /usr/sbin/firestarter at the bottom of the page with sudo gedit /etc/suers.

With a restart it is not working.
When I try to edit egain the file via sudo gedit /etc/sudoers
I am getting the following error:
“ >>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

I can not get in to the sudoers file.

Does any body have an idée?

Regards, Robert

PS. I tried to enter synaptic to reinstall firestarter but I am getting the following error:
[Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status.]

---

### Post by Bunro on 2006-03-16
I solved my problem by restarting my system en Esc at startup and entering the recovery mode. In this mode you have root privileges and editing from here the file.

Please read other threats about installing Firestarter!!
Do not edit it with gedit but with visudo!!!
This could have solved my problem for instance at the beginning and pointing me on my mistake before I messed up my system.

I still keep on learning.
Regards, Robert

---

### Post by mcduck on 2006-03-16
As nobody has yet mentioned this, I'll do it:

There is no need to run Firestarter all the time, as it's just a tool to configure firewall that's already built into Linux. All you need to do is install Firestarter, run it and answer the questions. After that firewall will start on every boot.

---

