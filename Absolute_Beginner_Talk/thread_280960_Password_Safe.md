---
title: "Password Safe"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-10-20
In Windoze I have a password safe. Is there anything for Linux like this? Everything I have seen so far is for Windoze.

---

### Post by Klaidas on 2006-10-20
What's "password safe"?

---

### Post by Ben Sprinkle on 2006-10-20
Maby he means encrypted? Like passwd'd rar files?

---

### Post by taurus on 2006-10-20
Or maybe he means a program to enforce a good password:  no names, places, cities, things like that...

---

### Post by Sgurd on 2006-10-20
While we're guessing: I'd guess they want a program that manages every other password (email, websites, programs) with one master password.  

Perhaps similar to Mac's 'Keychain'.  ? - JD

---

### Post by Ben Sprinkle on 2006-10-20
KWallet ftw.

---

### Post by HareBall on 2006-10-20
> **Klaidas said:**
> What's "password safe"?
It is this [http://www.schneier.com/passsafe.html](http://www.schneier.com/passsafe.html)

---

### Post by jordanmthomas on 2006-10-20
You could try kwallet or revelation.

---

### Post by PriceChild on 2006-10-20
Gnome has a keyring does it not?

---

### Post by steve.horsley on 2006-10-20
> **PriceChild said:**
> Gnome has a keyring does it not?

I believe it does, but I've never seen any documentation.

I keep all my passwords in a password protected OOo spreadsheet.
One password to rule them all, one password to find them...

---

### Post by moore.bryan on 2006-10-20
[I]hareball...
i think you're asking for something like keepass.  i use [keepass]("http://keepass.sourceforge.net") at work on xp and now there's a linux version which can read the keepass database and key files called [keepassx]("http://keepassx.sourceforge.net").

excellent program!
[/I]

---

### Post by HareBall on 2006-10-21
> **PriceChild said:**
> Gnome has a keyring does it not?

How do you install it? I didn't see it in the Synaptic Package Manager.

---

### Post by HareBall on 2006-10-21
> **HareBall said:**
> How do you install it? I didn't see it in the Synaptic Package Manager.

Sorry to bump my message, but nobody has told me how to do this:(

---

### Post by jordanmthomas on 2006-10-21
The packages are called
```
gnome-keyring
gnome-keyring-manager
```

---

### Post by HareBall on 2006-10-22
> **jordanmthomas said:**
> The packages are called
```
gnome-keyring
gnome-keyring-manager
```
OK, both are loaded, but I can't get it to run. I can't find where it put them or get it to run from run application. I get an error message saying,
Could not open location 'File:///keyring'
Details: The location or file could not be found.
What next?

---

### Post by jordanmthomas on 2006-10-22
you would want to do this:
Alt + F2
```
gnome-keyring-manager
```

I'm not sure this is even the app you're looking for, though (I've never really used gnome-keyring)

---

### Post by HareBall on 2006-10-22
> **jordanmthomas said:**
> you would want to do this:
Alt + F2
```
gnome-keyring-manager
```

I'm not sure this is even the app you're looking for, though (I've never really used gnome-keyring)
Thanx, that worked.

I'm not sure either, but I figured it would be worth looking at.

---

### Post by CupofDice on 2006-10-22
KeePassX is great and very easy/safe. Full gui. No need to worry about keyrings or anything like that ;). zerone gave me a lot of help here- [http://ubuntuforums.org/showthread.php?t=255350&highlight=KeePass]("http://ubuntuforums.org/showthread.php?t=255350&highlight=KeePass"). I think you can install it in your whatever directory you want (by moving the folder there before installation (I recommend home)), and don't lose your kdb file. You can open up your kdb in Windows/Mac. 
[http://keepassx.sourceforge.net/]("http://keepassx.sourceforge.net/")

---

### Post by george_apan on 2006-10-22
I'm using gpass, since it could import my Password Safe stored passwords that I had in windows.

---

### Post by HareBall on 2006-10-22
> **george_apan said:**
> I'm using gpass, since it could import my Password Safe stored passwords that I had in windows.
I will try this later tonight when I get home from work:)

---

### Post by Ben Sprinkle on 2006-10-23
If you are using Ubuntu, it already has a keyring on it.
If you are using Kubuntu, it already has Kwallet on it.

---

### Post by HareBall on 2006-10-23
> **george_apan said:**
> I'm using gpass, since it could import my Password Safe stored passwords that I had in windows.

I need to know the command line to get this to work. The webpage was too vague for someone like me:confused: 
I think this is what I want to use.
I looked at keyring and didn't care for it.

---

### Post by HareBall on 2006-10-23
> **HareBall said:**
> I need to know the command line to get this to work. The webpage was too vague for someone like me:confused: 
I think this is what I want to use.
I looked at keyring and didn't care for it.
Never mind, I found it in the Synaptic Manager](*,)

---

### Post by HareBall on 2006-10-23
> **HareBall said:**
> Never mind, I found it in the Synaptic Manager](*,)
Well, I am posting from Windoze:( I managed to do something to crap my desktop, again. Third or fourth time I have done this.
I wqas uninstalling keyring and I obviously took out something I needed. I was using Synaptic Manager and started watching it on the terminal. I noticed it seemed to be taking a long time and saw things like Nautilus being removed. I knew something was wrong, but didn't know what to do. When it got through, I didn't have any of my games and only had terminal and one other thing in Accessories
I guess I better start a new thread to see if someone can help me get everything back](*,)

---

### Post by Ben Sprinkle on 2006-10-23
Don't need 2 topics for that HareBall. Just do:
```

sudo apt-get install dapper-desktop
```
If you can still terminal login. Else just reinstall.

---

### Post by HareBall on 2006-10-23
> **synectics said:**
> Don't need 2 topics for that HareBall. Just do:
```

sudo apt-get install dapper-desktop
```
If you can still terminal login. Else just reinstall.

Done, thanx:p

---

### Post by Ben Sprinkle on 2006-10-23
Good good. :)

---

### Post by santo on 2006-10-25
KeePass is indeed a very good password manager for windows so I guess KeePassX is as good for linux.

Another solution is to use the java-based PassReminder.
You can just download the prog, unpack it and start using it.
The advantage of this one is of course that you can use it on both windows and linux
[http://passreminder.sourceforge.net](http://passreminder.sourceforge.net)

---

### Post by moore.bryan on 2006-10-25
[I]passreminder looks pretty good... the only thing i didn't like was i couldn't find under what license it's released.  silly, but i'm particular about free software actually being free... ;-)  has anyone been able to find what license it uses?

as a keepass on xp user (stupid job), i love keepassx because it reads the same database file and key file as its xp counterpart.  
[/I]

---

### Post by santo on 2006-10-25
According to the sourceforge details ([http://sourceforge.net/projects/passreminder)](http://sourceforge.net/projects/passreminder)), it uses the BSD license:

Project Admins: chiefofthejojos, passreminder
Operating System: All 32-bit MS Windows (95/98/NT/2000/XP), All POSIX (Linux/BSD/UNIX-like OSes), Linux
**License: BSD License**
Category: Internet, Security

---

### Post by moore.bryan on 2006-10-26
> **santo said:**
> According to the sourceforge details ([http://sourceforge.net/projects/passreminder)]("http://sourceforge.net/projects/passreminder%29"), it uses the BSD license:

*awesome...thanks santo...*

---

