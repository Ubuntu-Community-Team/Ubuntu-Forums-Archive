---
title: "Oh...Dear...."
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-22
Well, while I was playing around trying to install things using this guide:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

I managed to do something to my source list which involves it now saying:

Internal error opening cache (1). Please report.

when I open Synaptic.



Well...

What the hell is happening. Im scared. Very scared.
Installing things havent worked properly since I tried to install LIlypond and now just get huge amounts of errors when I do anything.

Also, using that guide I installed LimeWire and the program and everything has appeared in my menu but it won't open. It just won't open.

Help Me.
Please.

---

### Post by Perfect Storm on 2005-12-22
You should only follow thte guide if you are using ubuntu 5.04, that's can be the reason if you added the sourcelist from 5.04 to 5.10


Limewire: try open limewire in the terminal and see what it says there.

---

### Post by bscbrit on 2005-12-22
Don't panic.  You have probably corrupted one of synaptics files, or the contents of the cache.  Neither will cause your computer to burst into flames so don't worry.

If you prefer to use synaptic, try 'Reload' and see if that helps.

If you use apt-get then

sudo apt-get clean
sudo apt-get update

will probably recover the situation.  Don't forget you can only use synaptic or apt-get one at a time.  They both use the same files but cannot share so always close one before opening the other.

If it still doesn't work, just come back here.

---

### Post by bscbrit on 2005-12-22
Ah, I see from AI's response what you have done!

---

### Post by Dr Von Bon Bon on 2005-12-22
Well, i tried both of those ideas and it's still coming up with the same error (and annoyingly still the Lilypond problem).

Could it be anything else do you think?

---

### Post by Dr Von Bon Bon on 2005-12-22
Yeah, I didnt realise that at the time so I think I must have destroyed my source files and then replaced them with the old ones.

Can you tell me how to change them back please?

---

### Post by Perfect Storm on 2005-12-22
Which version of ubuntu do you have? And how does your source list looks like?

```
sudo gedit /etc/apt/sources.list
```

delete all and add instead:

> 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


then in the terminal:

```
sudo apt-get update
```

---

### Post by bscbrit on 2005-12-22
Yes - I think AI's response was probably spot on.  Did you edit the sources.list to include new repositories as recommended by the guide?  If you did, you have input the wrong repositories - they are for version 5.04 and you are probably using Breezy 5.10.  Please check and when we know what is wrong we can set about correcting it.

---

### Post by bscbrit on 2005-12-22
AI - just so we don't confuse Dr VBB, I'll back out of this thread. Cheers.

---

### Post by Perfect Storm on 2005-12-22
okay cya, bscbrit ^^

---

### Post by Dr Von Bon Bon on 2005-12-22
Oh thank god.

Thanks you guys loads, god knows where I would be without this forum :) 

Yeah, I think that has sorted out the problem. Is there anyway though that you could tell me how to remove the LimeWire that i installed using that guide please?

Again, many thanks to the both of you.

---

### Post by Perfect Storm on 2005-12-22
```

cd /opt
sudo rm -r Limewire
cd /usr/bin
sudo rm -r runLime.sh

```

---

### Post by Dr Von Bon Bon on 2005-12-22
Thank you so very much, you guys are Lifesavers.

Thanks for looking out for the noobs of this world.

---

### Post by Perfect Storm on 2005-12-22
My pleasure ^^

Remember to have Java installed for limewire.

---

