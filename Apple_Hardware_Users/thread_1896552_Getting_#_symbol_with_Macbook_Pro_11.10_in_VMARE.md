---
title: "Getting # symbol with Macbook Pro: 11.10 in VMARE"
date: 2011-12-17
forum: Apple Hardware Users
---

### Post by myotis on 2011-12-17
Can anyone tell me how to get the the # symbol on a Macbook pro (UK keyboard) running Ubuntu 11.10 in VMWare.

I have tried the different keyboard options and the one that lets most keys work is English (UK Macintosh), even though the keyboard illustration for this keyboard doesn't match the laptop keyboard.

There are also other issues such as the ~ key needing hit twice to work.

As the laptop layout is the same as the bluetooth keyboard that comes with iMacs is there a actual driver available to download that will make these keyboards play nicely with Ubuntu. 

Searching on this seems to just turn up problems with the function keys but most of them work as expected, but only when the English (UK Macintosh) option is selected, so I am still stuck with the # and ~ problems.

Thanks,

Graham

---

### Post by davidryderuk on 2011-12-18
Hi,
Are you sure you're not using 'UK Macintosh International' layout? You can type a # key on this keyboard by pressing the right alt key and then the \ key. The other problem you mentioned sounds like the dead key feature (hence why I thought international).

[http://spanish.about.com/od/writtenspanish/a/dia_ubuntu.htm](http://spanish.about.com/od/writtenspanish/a/dia_ubuntu.htm)

If you are using the international version, then try the ´UK, Macintosh´ version. If you find the ~ and § keys are messed up you can use the following two commands to fix them (this works for me, but since every keyboard is different you might want to read a tutorial on xmodmap):

```
xmodmap -e "keycode 49 = section plusminus grave asciitilde notsign notsign notsign notsign"
xmodmap -e "keycode  94 = grave asciitilde grave asciitilde brokenbar bar brokenbar bar"

```

When I'm using the 'UK, Macintosh' keyboard layout I can type the # key by pressing the right alt key and then the 3 key.

---

### Post by myotis on 2011-12-18
David,

> **davidryderuk said:**
> Hi,
Are you sure you're not using 'UK Macintosh International' layout? 


Thanks, but I only have the "English(UK,Macintosh" keyboard layout available as an option under keyboard layout. I tried the other options, but even fewer keys worked than with this layout. Is this the one you mean. 

None of the shortcuts you describe work for me. I have also now installed Ubuntu/VMWare on a Mac Mini with the bluetooth Mac keyboard, and none of these short cuts work there either. Some are dead keys and others give a slash or pipe symbol.

However, the two keyboards are behaving slightly differently.

I wonder if I am missin some othere "related" setting. The language support is all set to English (UK).

:-(

Graham

---

### Post by davidryderuk on 2011-12-19
Hi,
I am running 11.10 with bootcamp on a Macbook with a British keyboard, using the 'English (UK, Macintosh)' keyboard layout. I haven't changed any of the additional options (until I read your post). Apart from the § and ` keys being messed up I don't have any problems. 


Perhaps the problem might be caused by vmware. I found the following post, that might help:

[http://ubuntuforums.org/showpost.php?p=9242716&postcount=7](http://ubuntuforums.org/showpost.php?p=9242716&postcount=7)

If that doesn't work, another person in the same thread recommends installing Ubuntu without the 'use easy install' option in vmware being checked.

[http://ubuntuforums.org/showpost.php?p=9212870&postcount=5](http://ubuntuforums.org/showpost.php?p=9212870&postcount=5)

---

### Post by myotis on 2011-12-19
David,

> **davidryderuk said:**
> Hi,
I am running 11.10 with bootcamp on a Macbook with a British keyboard, using the 'English (UK, Macintosh)' keyboard layout.


Thanks again, it was a fresh install on the mini and an update on the Macbook pro.  But I have now lost file sharing on the Macbook Pro, and can't get it back !!. It wasn't working on the Mac Mini either but several re-installs of VMWare tools has fixed it, but the same approach isn't working with the MacBook Pro.

I am tempted to a) try Virtual Box, and b) try a non easy install re-install.

I was hoping for an "easy" solution.

Cheers,

Graham

---

### Post by myotis on 2011-12-19
David,

I have now installed Virtual Box and Ubuntu 11.10 (on the Mac Mini) and the bluetooth keyboard is now acting as you are describing :-)

But it still isn't on VMWare :-(

The weird thing is that VMWare on the MacBook Pro is now behaving like Virtual Box on the Mini, but I still can't get the shared folders working :-(

I may well switch to Virtual Box, anyway, as the I am not comfortable with the flakieness of the shared folders with VMWare.

Any way, thanks for your help, it was very useful.

Graham

---

### Post by davidryderuk on 2011-12-19
Hi,
I recently tried the VMWARE fusion 4 trial. Keyboard and file sharing (I assume you mean with the host OS?) seems to work fine on that version. Virtual box probably has two main differences you'll notice:
[LIST]
Configuring the shared folders, the virtual machine and installing the correct drivers is more difficult and requires the command line in places (see my next post).[/LIST]
[LIST]The 3D graphics aren't quite as good (although there isn't much in it).[/LIST]

It does sound like the drivers on your version of VMWARE are a bit out of date. If you do switch to virtual box then you can probably rely on getting more regular updates to the drivers (without having to pay more money) and hence being able to use more recent versions of Ubuntu.

If you want to copy files between VMWARE and virtual box, you're best bet might be to use an external hard drive or memory stick.

---

### Post by davidryderuk on 2011-12-19
I just found two guides on how to enable file sharing and 3D graphics using Virtual box and Ubuntu 11.10. These instructions sound much easier than the process described in the manual:

[http://www.liberiangeek.net/2011/10/no-need-to-install-guest-additions-to-enable-3d-support-in-ubuntu-11-10-virtualbox-guest-machines/](http://www.liberiangeek.net/2011/10/no-need-to-install-guest-additions-to-enable-3d-support-in-ubuntu-11-10-virtualbox-guest-machines/)

[http://www.liberiangeek.net/2011/10/access-virtualbox-shared-folders-within-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/access-virtualbox-shared-folders-within-ubuntu-11-10-oneiric-ocelot/)

Please post back whether or not you manage to get everything to work.

---

### Post by myotis on 2011-12-19
David,

VMware has been working fine, and with no problems with shared folders until now,  it seems linked to a recent VMware update

I set up the shared folders in Virtual Box, with the menu, but it needed the command line to add me to  the vbox user group.

It all seems to be working now.

Thanks once again,

Graham

---

### Post by davidryderuk on 2011-12-19
> VMware has been working fine, and with no problems with shared folders until now, it seems linked to a recent VMware update

That's good. Hopefully it's just a bug they can fix then. Not sure if it covers anything that will be new to you, but I thought I would post this link:

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

