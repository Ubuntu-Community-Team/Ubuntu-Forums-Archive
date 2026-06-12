---
title: "after installation"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by aquintz09 on 2008-01-21
what do you do once you have completed the installation process? this is for begginers who had ubuntu for the first time. do you install drivers? customize your themes or what so ever.:)

---

### Post by ice60 on 2008-01-21
i add a couple of extra repos (too many will break things if you ever do an OS upgrade i think) and install all the muiltmedia files.

---

### Post by Warpedflash on 2008-01-21
install my fav programs, make users, make sure it all works with each other then just go on the net :)
if im feeling flashy i change hte login screen

---

### Post by kostkon on 2008-01-21
> **aquintz09 said:**
> what do you do once you have completed the installation process? this is for begginers who had ubuntu for the first time. do you install drivers? customize your themes or what so ever.:)

Some things to do after the installation are:
[LIST]
[*]Install multimedia codecs
[*]Install any additional programs needed
[*]Install Flash
[*]Install Wine (if you play Windows games)
[*]Play with the user preferences (at System - > Preferences)
[*]Test that all the devices and peripherals work OK
[*]Add some additional repositories, like the [Medibuntu repository]("http://medibuntu.org/")
[/LIST]

---

### Post by frup on 2008-01-21
Use it?

Usually I will install flash, frostwire, install restricted codecs, set up pidgin accounts, do a little thing in OO.o that increases its start time, play a game of solitaire, sometimes install restricted graphics depending on the card (and whether the machine wants compiz fusion). Maybe add beryl and change the theme. It depends on who/what the install is for (me, a friend etc.)

If it's my first time with a new release I will usually open every program to see what is changed, read up on release walk throughs and look at each change and smile (usually)

---

### Post by housam on 2008-01-21
Connect to the internet and install Automatix2, this will help installing many other useful programs 
in the terminal write :
```
sudo apt-get install automatix2
```

---

### Post by Golem XIV on 2008-01-21
How about "I start using my computer"? :-)

On a more serious note, I do the following:
- add a couple of repos (medibuntu and wine)
- copy the apt cache that I have backed up to /var/cache/apt/archives.  This is where apt keeps all downloaded files - system updates, software installation files, etc.  With this the system update will have to download only the newest update files, if there are any.  Also, most of the software I will be (re) installing is also in this folder.
- install restricted drivers
- install ubuntu-restricted-extras
- recover the .mozilla folder from backup (removing the cache folder first).  This gives me back Mozilla with all my configs, passwords, bookmarks and even installed add-ons.
- recover from backup other configuration folders (.gnupg, .Skype, password files, Evolution backup and others)
- install Seahorse (GPG key management) and Revelation password manager so I have access to my passwords
- iinstall and set up pdnsd (from [this thread]("http://ubuntuforums.org/showthread.php?t=331850")).  It speeds up my browsing enormously.
- set up and test wireless (I have to blacklist the current driver and enable ndiswrapper)
- set up evolution
- recover the rest of the backup (personal files, videos, pictures, music, etc.)  This is a long process since I have 20+ GB of stuff backed up, so I leave it for the end.  YMMV.

After this it is a question of taste.  Continue installing software as you have need for it.  Customize your desktop.  Set up and configure compiz. Set up your session preferences (what programs to auto-load at startup). You get the idea :-)

Good luck!

---

### Post by hyper_ch on 2008-01-21
> **housam said:**
> Connect to the internet and install Automatix2, this will help installing many other useful programs 
in the terminal write :
```
sudo apt-get install automatix2
```

Automatix is not recommended for installation. Although some stuff might be "easier" installed through automatix they can also be installed in the "proper" ways. Automatix could render your system unusable.

---

### Post by housam on 2008-01-21
> **hyper_ch said:**
> Automatix is not recommended for installation. Although some stuff might be "easier" installed through automatix they can also be installed in the "proper" ways. Automatix could render your system unusable.

I used to install automatix with many distros of ubuntu ( starting from dapper till gusty ) and it works just fine and no problems with OS stability or usability.

---

### Post by hyper_ch on 2008-01-21
> **housam said:**
> I used to install automatix with many distros of ubuntu ( starting from dapper till gusty ) and it works just fine and no problems with OS stability or usability.

You just might have been lucky so far.

---

### Post by Thund3rstruck on 2008-01-21
[http://www.ubuntuguide.org]("http://www.ubuntuguide.org")

It's as simple as that

---

