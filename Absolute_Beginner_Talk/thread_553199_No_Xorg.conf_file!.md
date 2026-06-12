---
title: "No Xorg.conf file!"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by cf_al_bs on 2007-09-17
Ok, so i installed 7.04 the other day. While trying to edit the xorg.conf file to add in monitor resolutions and install compiz-fusion, I found it was missing!
I didn't make a typo, i know its case sensitive etc.
I've typed in sudo gedit /etc/X11/xorg.conf and all i get is a blank file. So i went to /etc/X11/ and the file isn't there! I did a search for it all over the system and there is an xorg.conf file but its in X11/xkb/rules.
[a little off topic: Also when I load ubuntu and have the option to select session what should be listed there, shouldn't x window session or something be there instead of xclient session?]
Thanks,
Alan,

---

### Post by rsambuca on 2007-09-17
Do you still have the link the to iso file that you downloaded to install ubuntu?  It sounds very much like you have just installed a command line or server edition.

---

### Post by por100pre1 on 2007-09-17
Welcome to the forums. If you are watching gedit and gdm you are already in X, I don't understand... :confused:

---

### Post by cf_al_bs on 2007-09-17
the iso is the standard one (live cd, etc.) and i didn't add any command lines during install.

the only problem i've had (apart from this) is that I was getting the 'list file for package missing final newline' problem with apt-get
[http://ubuntuforums.org/showthread.php?t=268582&highlight=list+file+for+package+missing+final+newline+archive](http://ubuntuforums.org/showthread.php?t=268582&highlight=list+file+for+package+missing+final+newline+archive)

this was fixed by renaming the info directory at /var/lib/dpkg (following these instructions but it worked after this point so i didnt continue: [https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html))

any ideas?

edit: the system is full updated now that apt-get is fixed.

---

### Post by rsambuca on 2007-09-17
I really think there was a problem with your installation.  Since you just installed it, I would probably just reinstall.  A few things to consider:

1.  What version of ubuntu did you install?  (You still didn't really say)
2.  Did you check the md5sum after downloading it?
3.  Did you burn the cd at a low rate?
4.  Did you do the CD check prior to installation?

---

### Post by cf_al_bs on 2007-09-17
> **rsambuca said:**
> I really think there was a problem with your installation.  Since you just installed it, I would probably just reinstall.  A few things to consider:

1.  What version of ubuntu did you install?  (You still didn't really say)
2.  Did you check the md5sum after downloading it?
3.  Did you burn the cd at a low rate?
4.  Did you do the CD check prior to installation?

1) 7.04 ubuntu desktop edition
2) no
3) yes 4x
4) no

Ok well i can see where I can improve... :) But shouldn't that system not work? I thought the xorg.conf file was very important? (ive fiddled a little too much in the past with it :))

ok well i could reburn it (possibly redownload) check the md5sum and run the cd check before i install. 

thanks for your help. :)

---

### Post by diatribe on 2007-09-17
> I note that X.Org 7.2.0
supports autoconfiguration meaning that "in most cases"[1], the X server
should be able to start without an xorg.conf file.

just grab a copy of a default xorg.conf, and edit it to your needs.  or you could try reconfiguring your xserver, this should generate a new xorg.conf

---

### Post by bodhi.zazen on 2007-09-17
To reconfigure X : 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

But, keep in mind that linux is case sensative so I presume you either mis-typed or forgot to "gksu" with your gedit, withoer way -> blank file.

In the commnad line you can :```
sudo tail /etc/X11/xorg.conf
sudo head /etc/X11/xorg.conf
```

To see the end or start fo the file as you wish ...

---

### Post by cf_al_bs on 2007-09-17
alanrice@alanrice-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
alanrice@alanrice-desktop:~$ sudo tail /etc/X11/xorg.conf
tail: cannot open `/etc/X11/xorg.conf' for reading: No such file or directory

still the same. I might just be better with a reinstall cause obviously something is messed up. it also means i can't configure my ati graphics cause it can't find the xorg.conf file!

---

### Post by diatribe on 2007-09-17
you can still get a copy of the default file and edit it by hand, unless you really dont care about reinstalling

also, what are the results of "sudo locate xorg.conf"

---

### Post by cf_al_bs on 2007-09-17
where could i get a default copy?

---

### Post by diatribe on 2007-09-17
> **cf_al_bs said:**
> where could i get a default copy?

[http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt](http://www.geocities.com/randomnumbergenerator2001/xorg.conf.breezy.txt) is an old copy but a good layout

---

### Post by cf_al_bs on 2007-09-17
thanks very much for your help. ill try it out. :)

---

