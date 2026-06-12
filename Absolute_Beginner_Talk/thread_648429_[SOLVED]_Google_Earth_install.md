---
title: "[SOLVED] Google Earth install"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Watchguy on 2007-12-23
Hi all. I am a newbe to this Ubuntu/Linux thing. But I'm up and running and everything on my desktop computer works and I'm loving it. Just can't figure out how to make some things work. I don't know much about the terminal (I need to get a book).

I've researched lots of threads till I'm blue in the face but I can't figure out how to install Google Earth.
It must be easier than I think but it's eluded me so far.:confused:

I downloaded the google earth bin file but can't get it to run from the terminal, but then the terminal is kind of a mysterious place.

Any help would be appreciated.:)

---

### Post by Biggy on 2007-12-23
Open up a terminal Applications > Accessories > Terminal
type in terminal :

sh GoogleEarthLinux.bin

---

### Post by Moop on 2007-12-23
Google Earth is in the medibuntu repository. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Watchguy on 2007-12-23
> **Biggy said:**
> Open up a terminal Applications > Accessories > Terminal
type in terminal :

sh GoogleEarthLinux.bin

Says "can't open GoogleEarthLinux.bin"

---

### Post by haggus on 2007-12-23
try chmod a+x GoogleEarthLinux.bin then sudo sh GoogleEarthLinux.bin or even easier add the mediubuntu repositories by following the link
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then type sudo apt-get install googleearth.

---

### Post by Watchguy on 2007-12-23
> **Moop said:**
> Google Earth is in the medibuntu repository. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")


Says  GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
 You may want to run apt-get update to correct these problems

Tried to run update and get " apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

:confused: kind of lost at this point. Guess I'm not going to make much progress in Ubuntu for a while.

Anyway I can surf the web, That's a good thing:)

---

### Post by icechen1 on 2007-12-23
in a terminal do chmod a+x GoogleEarthLinux.bin
then ./GoogleEarthLinux.bin

---

### Post by haggus on 2007-12-23
Enter this in the terminal to download the GPG key

Code:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

then

Code:

 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


sudo apt-get update

and you should have no more errors.

---

### Post by Watchguy on 2007-12-23
> **haggus said:**
> Enter this in the terminal to download the GPG key

Code:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

then

Code:

 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


sudo apt-get update

and you should have no more errors.

Sorry. Still get the same GPG error, NO_PUBKEY 58403026387EE263

---

### Post by zhouxing on 2007-12-24
1. Download latest Google Earth Linux
2. Copy it to your homefolder
3. Open Terminal
4. type:  chmod +x GoogleEarthLinux.bin
5. type: sudo ./GoogleEarthLinux.bin

wola, you should be able to install and run Google Earth now, provided your have proper display driver for 3D acceleration installed.

---

### Post by byenary on 2007-12-24
Install automatix and from there its just a click away

---

### Post by lgambett on 2007-12-24
I suggest you to follow instructions from zhouxing and NOT install from automatix. Automatix works, but change your setup in a wway that in the future will be more difficult to maintain updated your Ubuntu.

---

### Post by ray bot on 2007-12-24
Sounds like your gpg error is not related to medibuntu, but to wine.  You must have added the winehq repository without getting the gpg key for it.  This should fix it: ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by beanco on 2007-12-25
> **Biggy said:**
> Open up a terminal Applications > Accessories > Terminal
type in terminal :

sh GoogleEarthLinux.bin

I did the above ^^^^^

have anice google earth icon on my desktop but when I open it i get logged off

so what ' s that all about?

robi

---

### Post by Watchguy on 2007-12-25
> **zhouxing said:**
> 1. Download latest Google Earth Linux
2. Copy it to your homefolder
3. Open Terminal
4. type:  chmod +x GoogleEarthLinux.bin
5. type: sudo ./GoogleEarthLinux.bin

wola, you should be able to install and run Google Earth now, provided your have proper display driver for 3D acceleration installed.

OK. That did it. Thanks! Your a peach\\:D/

---

### Post by beanco on 2007-12-26
I tried yoru method zouxhing as well and it still does not work.

when I open google earth i get logged off!


so, now I want to completely remove it and try anew.

How can I do that?

I tired 

```
 sudo aptitude remove --purge google-earth
```

but it did not work..... help this n00b get rid of goole earth so he can install it properly...

robi

---

### Post by zhouxing on 2007-12-26
What do you mean that when you open Google Earth you got log off? What I understand is that you have successfully installed Google Earth, but it crash (log out your X window) when you try to run it. It may not be the installation issue. Have you check your display card driver? Is it 3D enabled?

Sometimes, when you are under firewall, Google Earth might not run properly. I had this experience when I was using my Laptop in a 5-star hotel, their WatchGuard firewall prevented Google Earth from log in to Google server.

I am glad that my method helped someone.

Try to use Synpatics, find googleearth, then remove it completely. Then use my method to reintall the latest version (make sure that you always use the latest version of Google Earth, or it might not work).

---

### Post by beanco on 2007-12-26
I get sent back to the log in screen....

i will try removing it with synaptic....

and then try to reinstall usuing your methods.

not sure abou the video card, how can I check?

Def not a firewall issue....

robi

ps I am on feisty, coudl this be part of the problem

---

### Post by zhouxing on 2007-12-26
What's your display card? ATI or Nivida? Can you run 3D games properly in feisty?

Google Earth should have not problem running in feisty. But why don't you upgrade it to gutsy?

Remove old version, download  latest one and reinstall it. any problem just post here.

---

### Post by beanco on 2007-12-26
I have no idea what video card I have adn no idea how to find out.

but now I have to run... maybe later I can figure it out... 

anybody want to point me in the right direction


robi

---

### Post by rmores on 2007-12-27
Try this:

```

DISPLAY=:0 googleearth

```

Looks like you have the same problem I have. 

I can't run 3D acceleration for some odd reason involving ATI drivers(fglrx), DRI,  and compiz(which works fine).

That code won't run googleearth for me, unless i switch back to vesa drivers which means no 3D support.

Basically, I'm getting a X restart because the X server is trying to start DRI in another display besides 0:0 . I suppose yours is the same problem?

There are a few threads about ATI cards around, but no definitive solutions so far.

I use an ATI Radeon X1650 card.

---

