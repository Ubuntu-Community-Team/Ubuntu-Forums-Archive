---
title: "Boot-Up Manager (BUM) 1.3.x"
date: 2005-06-16
forum: BUM - Boot Up Manager
---

### Post by saltydog on 2005-06-16
**Version 1.3.0** is online!

Please download the deb package from the web site: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)  and read the changelog.

The documentation is on: [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

**Note:** If you experience that any service running on your machine is missing from the "human text" list, please update the page  [https://wiki.ubuntu.com/InitScriptHumanDescriptions](https://wiki.ubuntu.com/InitScriptHumanDescriptions)
You can put here the proposed description and the daemon name (if any).

**Update of July 13, 2005**
New version 1.3.1 is online.

**Update of July 18, 2005**
New version 1.3.2 is online

[IMG]bum1.3.0.jpg[/IMG]

---

### Post by dlpfmVfH on 2005-06-16
[QUOTE=saltydog]**Version 1.3.0** is online!

Please download the deb package from the web site: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)  and read the changelog.

The documentation is on: [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

[IMG]bum1.3.0.jpg[/IMG][/QUOTE]
 it works...very good

---

### Post by josuealcalde on 2005-06-17
Good work.

---

### Post by cogumbreiro on 2005-06-27
[QUOTE=saltydog]**Version 1.3.0** is online!

Please download the deb package from the web site: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)  and read the changelog.

The documentation is on: [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

[IMG]bum1.3.0.jpg[/IMG][/QUOTE]
 This is a very nice application. keep up the good work!

Here are some HIG compliance and usability tips:

 - You should swap of the buttons ("Apply Changes" and "Exit")
 - You should use the stock "Quit" button instead of the "Exit" button
 - Dialogs should be set transient to the parent window: I noticed the loading dialog and the about
 - Are those frames really needed? Frames should use the bold font and space on the left.
 - Why not use a "Ok"|"Apply" button instead of the "Apply Changes"|"Exit"

---

### Post by saltydog on 2005-06-29
[QUOTE=cogumbreiro]This is a very nice application. keep up the good work!

Here are some HIG compliance and usability tips:

 - You should swap of the buttons ("Apply Changes" and "Exit")
 - You should use the stock "Quit" button instead of the "Exit" button
 - Dialogs should be set transient to the parent window: I noticed the loading dialog and the about
 - Are those frames really needed? Frames should use the bold font and space on the left.
 - Why not use a "Ok"|"Apply" button instead of the "Apply Changes"|"Exit"[/QUOTE]

Thank you. I will take them in consideration for next release. Just one thing: the "About" dialog is the standard Gnome2::About. Its behaviour is exactly the same as in Nautilus...

---

### Post by pismikrop on 2005-06-29
some feature requests :)

highlighting of not - installed scripts
And custom script installation

---

### Post by saltydog on 2005-06-29
[QUOTE=pismikrop]some feature requests :)

highlighting of not - installed scripts
And custom script installation[/QUOTE]


The system cannot know which are the not-installed scripts!! The universe of debian has thousands of init scripts, so I cannot trace them all on your system...

Custom script installation is out of the scope of BUM. You need to write a script in bash, put it in /etc/init.d/ and just run BUM to activate it where you want..

---

### Post by pismikrop on 2005-06-30
[QUOTE=saltydog]
The system cannot know which are the not-installed scripts!!
[/QUOTE]


[https://wiki.ubuntu.com/InitScriptHumanDescriptions](https://wiki.ubuntu.com/InitScriptHumanDescriptions)

---

### Post by cogumbreiro on 2005-07-02
[QUOTE=saltydog]Thank you. I will take them in consideration for next release. Just one thing: the "About" dialog is the standard Gnome2::About. Its behaviour is exactly the same as in Nautilus...[/QUOTE]
 Nautilus is a different kind of application. Just open any other application, like File Roller or Gedit, even Firefox (which is not a GNOME/Gtk+ application) uses this method.

Dialog's should not appear in the tasklist, they should be transient to a certain window (have a parent), this includes preferences, small progress dialogs that depend on a window, etc.

It would also be nice if you could port your gnome-abut-dialog the new gtk-about-dialog, since the former is pretty much deprecated.

HIG, [Chapter 3 - Dialogs](http://developer.gnome.org/projects/gup/hig/2.0/windows-dialog.html):
> 
A dialog should not appear in the panel window list. Any open dialogs should be raised above the application when the application window itself is selected from the window list.


---

### Post by saltydog on 2005-07-03
[QUOTE=cogumbreiro]
It would also be nice if you could port your gnome-abut-dialog the new gtk-about-dialog, since the former is pretty much deprecated.
[/URL]:[/QUOTE]

Currently hoary installs libgtk2-perl v.1.061 and this version doesn't have the bindings for gtkAboutDialog. If breezy will come out with an update, I will change this.

---

### Post by saltydog on 2005-07-13
New version 1.3.1 is online:

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by zrr on 2005-07-14
Hi

Does this version of the Boot-Up Manager (BUM) work on PPC as well? Thanks for your Feedback and help.

Zeno

---

### Post by saltydog on 2005-07-14
[QUOTE=zrr]Hi

Does this version of the Boot-Up Manager (BUM) work on PPC as well? Thanks for your Feedback and help.

Zeno[/QUOTE]


I have no means to test, but as BUM only depends on Perl, Gtk2-Perl libGnome-perl, if you have those libraries installed for PPC, it should run.

---

### Post by saltydog on 2005-07-18
New version 1.3.2 is online. Please see changelog.

---

### Post by ar0d on 2005-07-20
very nice tool. been waiting for the distro to come out w/ something like that. Thankyou!

---

### Post by saltydog on 2005-07-20
[QUOTE=ar0d]very nice tool. been waiting for the distro to come out w/ something like that. Thankyou![/QUOTE]


Unfortunately, ubuntu's developers has selected another tool for Breezy, a sort of mini-BUM without all that extended functionalities.

---

### Post by SuperMike on 2005-07-24
Although you did this in Perl, I do a bit of Python/PyGTK/Glade-2 work myself. (I'm not fond of Python completely.) Most of the time, I just get Python to shell out, run GNU commands, and return the results in the screen. I must say that your work here, saltydog, is of the most excellent quality. It loaded up just fine in my Hoary Hedgehog 5.04.

Using PyGTK, I'm currently working on gvpnc, a GNOME front-end to vpnc, as well as a firewall tool that does not require lokkit and which is designed for people using dial-up, DSL, and cable modems. Both are designed, like your application, to be easy to use and ready for noobs. They are functional right now. As soon as I iron out the install kinks so that it works on most platforms, I'll have it up on the sourceforge. (I'm also the writer of pgst for PostgreSQL.)

---

### Post by autocrosser on 2005-07-25
BUM seems to work just fine on PPC--got the 1.3.2 release--installed with no problems . :)  Looks good--works same---THANK YOU!!

Cheers!!
Dean

---

### Post by saltydog on 2005-07-25
[QUOTE=SuperMike]Although you did this in Perl, I do a bit of Python/PyGTK/Glade-2 work myself. (I'm not fond of Python completely.) Most of the time, I just get Python to shell out, run GNU commands, and return the results in the screen. I must say that your work here, saltydog, is of the most excellent quality. It loaded up just fine in my Hoary Hedgehog 5.04.
[/QUOTE]

Thank you SuperMike. Let us know thru the forum when your work will be ready for testing!

---

### Post by kanem on 2005-07-30
[QUOTE=saltydog]Custom script installation is out of the scope of BUM. You need to write a script in bash, put it in /etc/init.d/ and just run BUM to activate it where you want..[/QUOTE]

So, I wrote a script and put it in /etc/init.d/ and ran BUM.... And now I still don't see a way to add my script. It isn't listed in any of BUM's menus. Could someone tell me what I'm missing?

Sorry if it's something obvious.

the script is just a simple```
#!/bin/bash
command
```
I chmodded it +x and ran it to make sure it's executable

---

### Post by saltydog on 2005-07-31
[QUOTE=kanem]So, I wrote a script and put it in /etc/init.d/ and ran BUM.... And now I still don't see a way to add my script. It isn't listed in any of BUM's menus. Could someone tell me what I'm missing?

the script is just a simple```
#!/bin/bash
command
```
I chmodded it +x and ran it to make sure it's executable[/QUOTE]

It is not important to chmod the script (BUM will do it) but it is important that the script name must NOT be followed by .sh Standard init scripts should not be named with extension .sh, but with no extension.

Mor on this: are you sure you are running latest BUM version 1.3.2? I have just checked again and it works straight.

---

### Post by kanem on 2005-07-31
[QUOTE=saltydog]It is not important to chmod the script (BUM will do it) but it is important that the script name must NOT be followed by .sh Standard init scripts should not be named with extension .sh, but with no extension.

Mor on this: are you sure you are running latest BUM version 1.3.2? I have just checked again and it works straight.[/QUOTE]
I think I may have discovered what the problem was. Earlier I had tried to do it manually without BUM and added a link to my script in /etc/rc2.d and /etc/rc3.d. When I got rid of those and started up BUM my script was visible.

thanks for the app!

---

### Post by saltydog on 2005-07-31
[QUOTE=kanem]I think I may have discovered what the problem was. Earlier I had tried to do it manually without BUM and added a link to my script in /etc/rc2.d and /etc/rc3.d. When I got rid of those and started up BUM my script was visible.

thanks for the app![/QUOTE]

Yes. Generally it is not a good idea to play manually with symlink. In your case, BUM has marked the script as *invalid* because a script MUST have a K link in rc0 rc1 and rc6 to be sysv compliant.
Please read the new docs at: [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

---

### Post by johnmc on 2005-08-02
Very nice program!
Thanks & keep up the great work! :)

---

### Post by sinbad782 on 2005-08-04
Looks like BUM is now in Debian Unstable! - 

[http://lwn.net/Articles/145984/](http://lwn.net/Articles/145984/)
[http://packages.debian.org/unstable/admin/bum](http://packages.debian.org/unstable/admin/bum)

Great work!

---

### Post by matthew on 2005-08-04
I've been using this for about a month, maybe 6 weeks and am very impressed. Thanks.

---

### Post by saltydog on 2005-08-04
[QUOTE=sinbad782]Looks like BUM is now in Debian Unstable! - 

[http://lwn.net/Articles/145984/](http://lwn.net/Articles/145984/)
[http://packages.debian.org/unstable/admin/bum](http://packages.debian.org/unstable/admin/bum)

Great work![/QUOTE]

Yes. But it is also on Breezy!
[http://packages.ubuntu.com/breezy/admin/bum](http://packages.ubuntu.com/breezy/admin/bum)

---

### Post by Parkaboy on 2005-08-30
it has been quite usefull to me

---

### Post by Knome_fan on 2005-09-01
Anyone else having problems with it on breezy?

It installs fine, but when I try to run it, I get the following error:
```
Can't locate stddef.ph in @INC (did you run h2ph?) (@INC contains: /usr/share/bum/ /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/bits/types.ph line 10.
Compilation failed in require at /usr/lib/perl/5.8/termios.ph line 9.
Compilation failed in require at /usr/lib/perl/5.8/bits/ioctl-types.ph line 8.
Compilation failed in require at /usr/lib/perl/5.8/sys/ioctl.ph line 9.
Compilation failed in require at /usr/share/bum//bumlib.pm line 29.
Compilation failed in require at /usr/bin/bum line 44.
BEGIN failed--compilation aborted at /usr/bin/bum line 44.

```

I don't know if this matters, but I'm trying this on ppc.

---

### Post by arnieboy on 2005-09-04
[QUOTE=saltydog]**Version 1.3.0** is online!

Please download the deb package from the web site: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)  and read the changelog.

The documentation is on: [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)[/QUOTE]
Is this app usable on fedora? if yes, can I get the source code for this so that I can compile it on fedora?
I only found the deb file on your website.

---

### Post by saltydog on 2005-09-04
[QUOTE=arnieboy]Is this app usable on fedora? if yes, can I get the source code for this so that I can compile it on fedora?
I only found the deb file on your website.[/QUOTE]

I don't know if fedora uses the same sysv-rc init system as debian, so I can't answer your question.

Anyway, you can download the source code here:
[http://ftp.debian.org/debian/pool/main/b/bum/bum_1.3.2.orig.tar.gz](http://ftp.debian.org/debian/pool/main/b/bum/bum_1.3.2.orig.tar.gz)

---

### Post by arnieboy on 2005-09-06
[QUOTE=saltydog]I don't know if fedora uses the same sysv-rc init system as debian, so I can't answer your question.

Anyway, you can download the source code here:
[http://ftp.debian.org/debian/pool/main/b/bum/bum_1.3.2.orig.tar.gz](http://ftp.debian.org/debian/pool/main/b/bum/bum_1.3.2.orig.tar.gz)[/QUOTE]
hey thanks for the reply, but I found an inbuilt Gnome app for the same in fedora.

---

### Post by hammett111 on 2005-09-09
Works great here

---

### Post by dabear on 2005-09-13
Feature request: It would be nice if there were some kinda «export» where you could dump the current services to a file

---

### Post by merlyn on 2005-09-16
[QUOTE=saltydog]Unfortunately, ubuntu's developers has selected another tool for Breezy, a sort of mini-BUM without all that extended functionalities.[/QUOTE]

You never know the devs just might pick it up and run with it at later stage, as happened with SMEG ;-)

---

### Post by FNM on 2005-09-17
Great little app. I disabled 7 services that I don't need.

---

### Post by lavarock09 on 2005-09-22
I'm struggling to install BUM

I was wondering if anyone here could help

So, I run this 

> sudo apt-get install bum

in terminal and it outputs this 

>  Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bum 

Can anyone help?

---

### Post by saltydog on 2005-09-22
[QUOTE=lavarock09]I'm struggling to install BUM

I was wondering if anyone here could help

So, I run this 



in terminal and it outputs this 

 

Can anyone help?[/QUOTE]


Download v.1.3.3 from here: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)
and follow installation instructions.

---

### Post by lavarock09 on 2005-09-22
I have done this, but where do I put the .deb file

---

### Post by flibblesan on 2005-10-16
[QUOTE=lavarock09]I have done this, but where do I put the .deb file[/QUOTE]

Download the deb file, then from a terminal do:
```
sudo dpkg -i bum_1.3.4-2_all.deb
```

to install. Ignore anything about apt-get :)

---

### Post by gorkhal on 2005-10-16
question...does this properly work with breezy???

thanks.

---

### Post by saltydog on 2005-10-17
[QUOTE=gorkhal]question...does this properly work with breezy???

thanks.[/QUOTE]


Yes !! It is IN breezy repositories...

sudo apt-get install bum

---

### Post by gorkhal on 2005-10-17
great...thanks a lot. :smile:

---

### Post by abqaussie on 2006-01-16
In order to get bum to run on PPC (Mac G3) I had to do the following:

1. Install the libgtk2-gladexml-perl library via Synaptic (or terminal)
2. Run the following in terminal:
wget [http://http.us.debian.org/debian/pool/main/b/bum/bum_2.1.4-1_all.deb](http://http.us.debian.org/debian/pool/main/b/bum/bum_2.1.4-1_all.deb)
sudo dpkg -i bum_2.1.4-1_all.deb

Thanks to kozimodo for posting on another thread.

---

