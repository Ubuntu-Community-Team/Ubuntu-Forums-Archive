---
title: "the repositories idexes"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by Redneo on 2008-05-07
I having trouble downloading the repositories I did a clean install of hardy. started to update it says could not download the repositories. looked for fixes on the forums but no luck and one having the problem

---

### Post by uxe1 on 2008-05-07
i wouldn't worry about it, after each new release the servers are completely over loaded for a few weeks. if you can live with out a program do, or just wait a few days and let the servers calm down. I know it can be annoying, ive been wanting amsn for a coupla days now

---

### Post by frog_pilot on 2008-05-07
There is a major change in the sources.list for ppc architecture since hardy heron. And may be there is an installer bug and it installs the default sources.list also in hardy. As described [here]("http://www.xubuntu.org/news/hardy/ports") for xubuntu it is similar with all -buntus for ppc

Post yours and we could modify it.

Mainly you have to change all entrys from

archive.ubuntu.com/ubuntu, security.ubuntu.com/ubuntu to

ports.ubuntu.com/ubuntu-ports

then issue
```
sudo apt-get update && sudo apt-get upgrade
``` and you will be up to date. There is no server overload any more...

---

### Post by driven1 on 2008-05-07
Yeah, after installing Hardy, I kept getting repo errors for about three days, then everything worked without a hitch.

---

### Post by Redneo on 2008-05-08
changed the archive to posts and updated and grade and it now works thanks for the help.=D>

---

### Post by Reddirt on 2008-05-08
I think that this is the same problem I am having. I am just not clear on what exactly to change.  Could someone look at this and direct me.
 
**The following is the result of : sudo apt-get update**

Err hrrp://us.archive.ubuntu.com hardy Release.gpg
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy/main Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy/restricted Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy/universe Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy/multiverse Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-updates Release.gpg
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-updates/main Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-security Release.gpg
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-security/main Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-security/universe Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'
Err hrrp://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
   Could not resolve 'us.archive.ubuntu.com'

Reading package lists..... done
w: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) Could not resolve 'us.archive.ubuntu.com'

--This W: failed to fetch continues on all the above errors.--

**Here is my sources.list:**

#
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Please let me know what I can change to get the update to work.

Thanks

---

### Post by avtolle on 2008-05-08
@Reddirt, my current /etc/apt/sources.list follows. Note the changes to ports from archive. HTH.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-backports main restricted universe multiverse

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-security main restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-security universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-security multiverse


deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy main universe restricted multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security universe main multiverse restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-updates universe main multiverse restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-proposed universe main multiverse restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-backports universe main multiverse restricted

You could, if you wish, copy this for your use. If you choose to do so, then I'd do this: 
First, open gedit , select above list and copy it to a text file, called, e.g., sources.txt. Save file.
Second, at the terminal, do this:
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup #backup current file, just in case
```
Third, again at the terminal, do this: ```
 sudo nano /etc/apt/sources.list
```
Fourth, delete contents of file, then CTRL -O, return, CTRL-X.
Fifth, at the terminal (still) ```
 sudo cp /path/to/sources.text /etc/apt/sources.list
```
Sixth, ```
 cat /etc/apt/sources.list
``` to make sure everything copied over.
If so, then ```
sudo aptitude update
sudo aptitude safe-upgrade
```
to update sources and get upgrades.

If there is a problem, to restore your old sources list for manula editing, ```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
```
which will restore your old list to the file, where you can manually edit from archive to port, as has been suggested by others.
Finally, close the terminal (if you haven't done so already).
Hope this helps.

---

### Post by frog_pilot on 2008-05-08
very complicated suggestions, but it will work.

you could also execute first
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
now you have a backup of your old sources.list. Then open the file writable ```
sudo gedit /etc/apt/sources.list
``` replace the content with the suggested above. Execute ```
sudo apt-get update
``` and now have a look, if there still errors.

---

### Post by avtolle on 2008-05-08
Thanks for simplifying there, frog_pilot. I'm a bit old school, and tend to overly complicate things "just to be sure" for me. :-) BTW, I always use "gksudo" when I use gedit, FWIW.

---

### Post by Reddirt on 2008-05-08
I just retyped the whole file.  I tried sudo apt-get update and got the same result with errors.  I can ping the adressses from my server, but I can not complete the update.  The "err" and the "failed to fetch" result are pretty much the same as before just with the ports.ubuntu.com instead of the us.archive.ubuntu.com.  

I would post it but I don't know how other than to retype it.
Any advice?

-e

---

### Post by avtolle on 2008-05-08
> **Reddirt said:**
> I just retyped the whole file.  I tried sudo apt-get update and got the same result with errors.  I can ping the adressses from my server, but I can not complete the update.  The "err" and the "failed to fetch" result are pretty much the same as before just with the ports.ubuntu.com instead of the us.archive.ubuntu.com.  

I would post it but I don't know how other than to retype it.
Any advice?

-e
Grasping at straws here: go to System-->Administration-->Software Sources, and see if the changes to the list have been recognized (under the third party software tab, IIRC; the first page sources should not be checked, at least mine aren't. :)) Another thought: on the first page under Software Sources, use the arrows at the right of the scroll box that reads, in my case, "Main Server". You should find "Other"; select that, which will take you to a new page, then click on the "Select Best" button, and let it find which server is "best". Choose it, OK, and then close out. This should result in a reload, and then, when it is finished, try the terminal commands you've already done, or use the Update Manager to see if anything has changed. Sorry for the vagueness and length of this, hard for me to describe exactly what I mean. :(

---

### Post by frog_pilot on 2008-05-08
I wondered, if there were some mistakes in the sources.list by avtolle.

at the beginning of **every** line in my sources.list stands

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)

[HERE]("http://www.xubuntu.org/news/hardy/ports") is the official hint

---

### Post by avtolle on 2008-05-08
> **frog_pilot said:**
> I wondered, if there were some mistakes in the sources.list by avtolle.

at the beginning of **every** line in my sources.list stands

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)

[HERE]("http://www.xubuntu.org/news/hardy/ports") is the official hint
Hmm, I'll need to look at that. However, I get no errors when either using Synaptic or the terminal ```
sudo aptitude update
sudo aptitude safe-upgrade
```
such as 404 errors, etc.:confused:

---

### Post by frog_pilot on 2008-05-08
> **avtolle said:**
> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

[COLOR="Orange"]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy main restricted[/COLOR]

## Major bug fix updates produced after the final release of the
## distribution.
[COLOR="Orange"]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-updates main restricted[/COLOR]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Orange"]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy universe
[/COLOR]
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
[COLOR="Orange"]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy multiverse[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Orange"]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-backports main restricted universe multiverse[/COLOR]

[COLOR="Orange"]deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-security main restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-security universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy-security multiverse[/COLOR]


[COLOR="Red"]deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy main universe restricted multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-security universe main multiverse restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-updates universe main multiverse restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-proposed universe main multiverse restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) hardy-backports universe main multiverse restricted[/COLOR]

Here is your sources avtolle. Look at the red lines. this is the whole sources list (kind of duplicates of the above lines, marked orange, but in right syntax). Try to comment out the orange marked lines and see what will happen...

---

### Post by avtolle on 2008-05-08
> **frog_pilot said:**
> Here is your sources avtolle. Look at the red lines. this is the whole sources list (kind of duplicates of the above lines, marked orange, but in right syntax). Try to comment out the orange marked lines and see what will happen...

Got it! Thanks. The old tired eyes just refused to see it. What is interesting is that on the other Cube, the revised sources list (the one you so kindly colored) reads as you posted/suggested, with the "orange lines" already commented. Never had compared the two before. Again, my thanks.

---

### Post by Reddirt on 2008-05-09
I just switched all the URLs to include the ubuntu-ports.  This time during the apt-get the connection % went from 0% to 17%. 
The error is the same:
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) *hardy Release.gpg*(changes for request)
[INDENT]could not resolve 'ports.ubuntu.com'[/INDENT]

Is there some way to copy the sources.list onto this post without retyping it all. (thats what I have been doing)  I am typing in a windows environment. :confused:

I have not tried the admin > system instruction becuase I don't have a GUI.  and I am not sure how to accessess that via the CLI.

Am I correct in assuming that if I can ping addressess outside of my school's network that I should be able to complete this update. (provided I have the correct URL)

-e

---

### Post by cyberdork33 on 2008-05-09
just copy the soucres.list file and upload it as an attachment.

---

### Post by slacka-vt on 2008-05-09
Here's my sources.list
Works flawlessly on my PPC

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://ports.ubuntu.com/ hardy main restricted
deb-src http://ports.ubuntu.com/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ hardy-updates main restricted
deb-src http://ports.ubuntu.com/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ hardy universe
deb-src http://ports.ubuntu.com/ hardy universe
deb http://ports.ubuntu.com/  hardy-updates universe
deb-src http://ports.ubuntu.com/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ hardy multiverse
deb-src http://ports.ubuntu.com/ hardy multiverse
deb http://ports.ubuntu.com/ hardy-updates multiverse
deb-src http://ports.ubuntu.com/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ hardy-backports main restricted universe multiverse
deb-src http://ports.ubuntu.com/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://ports.ubuntu.com/ hardy partner
deb-src http://ports.ubuntu.com/ hardy partner

deb http://ports.ubuntu.com/ hardy-security main restricted
deb-src http://ports.ubuntu.com/ hardy-security main restricted
deb http://ports.ubuntu.com/ hardy-security universe
deb-src http://ports.ubuntu.com/ hardy-security universe
deb http://ports.ubuntu.com/ hardy-security multiverse
deb-src http://ports.ubuntu.com/ hardy-security multiverse


```

hope that helps

~s

---

