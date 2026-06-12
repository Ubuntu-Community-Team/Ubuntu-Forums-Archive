---
title: "repositories list do not show"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2007-09-11
I have made a fresh instalation of feisty and i cant enable the universe repositories :(
no checkbox or items show when i go to system>administration>software sources>third party software

Here is a screenshot so you can understand my problem a bit better
[http://img96.imageshack.us/img96/2627/universerb4.png](http://img96.imageshack.us/img96/2627/universerb4.png)

anybody knows about a work around? I wouldn+t like to edit sources.list manualy, ist's not practical to maintain
thanks in advance

---

### Post by mlentink on 2007-09-11
Universe packages (afaik) do not show up under third party, but under Ubuntu, the first tab

Without editing it, you might post the output of
```
gedit /etc/apt/sources.list
```
so we can see how yours looks like

---

### Post by overdrank on 2007-09-11
> **pedrotuga said:**
> I have made a fresh instalation of feisty and i cant enable the universe repositories :(
no checkbox or items show when i go to system>administration>software sources>third party software

Here is a screenshot so you can understand my problem a bit better
[http://img96.imageshack.us/img96/2627/universerb4.png](http://img96.imageshack.us/img96/2627/universerb4.png)

anybody knows about a work around? I wouldn+t like to edit sources.list manualy, ist's not practical to maintain
thanks in advance

HI and this link may help.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by pedrotuga on 2007-09-11
That last link refers to ubuntu 6.06

I actually managed to add multiverse ( i checked how on feisty docummentation ) but now i am having this error:
```

W: GPG error: http://ftp.debian.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277

```

---

### Post by wolfen69 on 2007-09-11
here is a list of repos you can add to get anything.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

in terminal:
gksudo gedit /etc/apt/sources.list

add above repos as new lines and save.
then: sudo apt-get update

---

### Post by RomeReactor on 2007-09-11
Hi. In Synaptic, go to "Settings->Repositories" and on the first tab (Ubuntu Software) make sure all the cases are checked. Close the pop up window and press the **Reload** button.

What are you trying to install that you need the Debian repository? although not necessarily, it could cause compatibility problems on your system.

---

### Post by pedrotuga on 2007-09-11
romereactor, The debian repository is axactly what's not working... apparently there is some troubles with the key... :S

wolfen69,
I add those repositories to my sources.list asyou suggested but there is still problems with the signatures...

```

W: GPG error: http://packages.medibuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ftp.debian.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems

```

Stuff i want to install that is not yet available with my current repository configuration:
skype
mp3 support
microsoft fonts
...

---

### Post by overdrank on 2007-09-11
> **pedrotuga said:**
> romereactor, The debian repository is axactly what's not working... apparently there is some troubles with the key... :S

wolfen69,
I add those repositories to my sources.list asyou suggested but there is still problems with the signatures...

```

W: GPG error: http://packages.medibuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ftp.debian.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems

```

Stuff i want to install that is not yet available with my current repository configuration:
skype
mp3 support
microsoft fonts
...

Hi the key to the first error can be found here
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
And by the way on my first post I am sorry I thought your were using dapper. :(

---

### Post by pedrotuga on 2007-09-12
I should update my profile to fiesty user. Sorry.

There's a problem with the key

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277


I can use synaptic, apt or go to the software repositories dialog, i allways get an authentication denial :(

---

### Post by hyper_ch on 2007-09-12
why do you have debian repos in your sources list?

---

### Post by pedrotuga on 2007-09-12
> **hyper_ch said:**
> why do you have debian repos in your sources list?
The only change i made to my sources.list was adding the repositories wolfen posted a few messages above. I also proceeded as described in this page:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
now... why are debian repositories there... i didn't add them manually.

---

### Post by hyper_ch on 2007-09-12
I'd use that to generate the sources.list:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

It also says then how you can add the GPG keys to it.

---

### Post by dkaddict on 2007-09-12
To get the GPG keys you have to enter the following in your terminal. You have to replace the word "KEY" (I have bold and underlined for the first instance) with the numbers for the pub key which are supplied in your error message.

```
gpg --keyserver subkeys.pgp.net --recv **_KEY_**
```

This command gets the GPG key from the server.

Then, to input the key into your machine you have to enter>>

```
gpg --export --armor **_KEY_** | sudo apt-key add -
```

Simply replace the word "KEY" with the last eight (as in 1,2,3,4...) numbers on this part of your error message

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF53_**6070D3A1**_ 

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available:NO_PUBKEY B5D0C804_**ADB11277**_

I have bold & underlined the numbers you have to replace key with in each instance. They would then look like this

```
gpg --keyserver subkeys.pgp.net --recv 6070d3a1
```

then press 'enter' to get the key number '607D3A1' from the server

wait for the key to be verified (terminal will spew out a few lines of verification)

when successful, type>>

```
gpg --export --armor 6070d3a1 | sudo apt-key add -
```

In order to install the KEY '6070D3A1' into your machine

and your terminal will give

>  OK

and for the next key

```
gpg --keyserver subkeys.pgp.net --recv ADB11277
```


press enter, wait for term to return success message

then type
```
gpg --export --armor ADB11277 | sudo apt-key add -
```

wait for > OK

and you're all done.

DON'T FORGET TO FOLLOW UP THE ABOVE GPG KEY COMMANDS WITH THE ALL IMPORTANT 

```
sudo apt-get update
``` 

Just remember to replace the word KEY with the last 8 digits of the error message>>>

> W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF53_**6070D3A1**_ 

this has always worked for me and is the easiest way I have found to get missing keys. No searching the web, the key number is right there in the missing key error message. If I have made a mess of explaining, post again and I will try to elaborate.

Peace

DK

---

### Post by dkaddict on 2007-09-12
Just to clarify.

I want to add the 'Medibuntu' repos to my sources.list.

'apt-get update' gives me the following error after entering the medibuntu repo address in my sources.list>>>

> W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

To verify the problem, I simply take the last 8 digits '0C5A2783' and replace 'key' with them so>>

```
gpg --keyserver subkeys.pgp.net --recv KEY
```

becomes

```
gpg --keyserver subkeys.pgp.net --recv 0C5A2783
```

press return and apt will fetch the key from the server

and

```
gpg --export --armor KEY | sudo apt-key add -
```

becomes

```
gpg --export --armor 0C5A2783 | sudo apt-key add -
```

press return and apt installs the fetched key to your system

Voila, I have my keys.

Easy ain't it m8

Happy days

DK

---

### Post by bapoumba on 2007-09-12
In addition to all the different recommendations, could you please post your sources.list?
Open a terminal (> Accesories > Terminal) and paste the complete output to:
```
cat /etc/apt/sources.list
```
Mixing ubuntu and debian repositories is not a good idea. have you updated/upgraded with the sarge repos ?

---

### Post by pedrotuga on 2007-09-12
Ok... so before i proced....

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://ftp.debian.org sarge main
deb http://archive.ubuntu.com/ubuntu/ feisty-security restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://packages.medibuntu.org/ feisty free non-free
deb http://archive.canonical.com/ubuntu feisty-commercial main


```

---

### Post by hyper_ch on 2007-09-12
You still have the debian in there...

I'd use this:

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ch.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://ch.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://ch.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://ch.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror2.ubuntulinux.nl/ feisty-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
deb http://ch.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

# Upstream Wine
# GPG key: 387EE263
deb http://wine.budgetdedicated.com/apt feisty main 

# Upstream Opera
# GPG key: 6A423791
deb http://deb.opera.com/opera etch non-free 

# Upstream Beryl
# GPG key: ed8a569e
deb http://ubuntu.beryl-project.org/ edgy main-edgy 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com feisty-commercial main 

```

Backports, Wine, Opera and Beryl you may delete if you want...

---

### Post by dkaddict on 2007-09-12
Sorry to hijack the thread for a post or two here but I have, I reckon, a fairly important question to ask about updates when there are loads of third party etc repos on /etc/apt/sources.list.

Maybe you can help Bapoumba?

Ok. I have just added the 'Medibuntu' repo to my sources list. A couple of minutes after updating apt, my update manager came alive and has some (duh, obviously) updates which it is asking me to install. The packages, however, are almost identical to ones I have on my system. 

(See screenshot attached.)

Now my question is...

Would it be prudent to ignore such updates from third party sources like TuxFamily, Medibuntu, etc??

I am aware of the fact that some of the third party sources aren't properly maintained and that some have, in the past, even contained malicious or system threateningly faulty code.

Having said that, then, would it be the advice of someone such as yourself Bapoumba for people to only update their system through the official Ubuntu sources at Canonical etc?

I think that this is a pertinent question in this context with newbies and not so newbies using all of the third party etc sources.

PEACE

DK

---

### Post by pedrotuga on 2007-09-12
strange... i thought i hae replied to this one...

anyway...

bapoumba... :S yes i did update apt :S and software updates too...

I already got some "is not possible to update all packages"

damn... i think it was caused by the debia repos... like... i installed the debian menu and it doesn't show...
should i just remove/comment the line with the debian repos?

Another question: does sources.list holds all the repositories/keys settings? like, there is som many applications that access to it, I should probably go for a simple sources.list edit.

Does anybody have one with multiverse active?

BTW... i think i copy pasted a command from ubuntuwiki that added that sarge one. I can't find the page i followed now... i find the documentation very good but a bit messy when it comes to the way is organised/sorted.

---

### Post by dkaddict on 2007-09-12
The 'sources.list' file will only hold the default repos and whatever you have pasted or typed into it. Sites such as Trevinos blog which have sources.lists may have the keys listed with the sources but they will be commented out. If you do 'apt-get update' and still need keys to activate some repos, your terminal output will say so. If it does, just get the key code like I posted earlier and activate your missing keys.

Here is my /etc/apt/sources.list.  It is simplified because it is easier to read so I made it that way, has the 'universe' and 'multiverse' default repos activated, and contains a few extra third partyt etc repos I have added over the last few months. Also (you may know this already), #<<< that symbol is a 'comment': anything behind that on a line will not be 'read' as code so anything behind a # usually explains the code below it!

> ##############################################   ORIGINAL UBUNTU FEISTY SOURCES
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

############################################## E17 SOURCES

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17

## E17 Repository "e17.dunnewind.net"
deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17
deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) feisty e17


#############################################   AWN

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

############################Medibuntu


deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

######################################################### Canonical Commercial packages
# GPG key: 437D05B5

deb [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main
deb-src  [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main

################################################## Seveas' Ubuntu Packages
# GPG key: 1135D466

deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) feisty-seveas all 

############################################   AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
#AUTOMATIX REPOS END

All the keys have been activated and there are no errors when I do an update. 

When I was running Edgy I had a huge sources.list with loads of third party repos. I got fed up with using such a list because 'apt-get update' always returned errors about failing to find this or that repo if it actually managed to complete updating the list. I say that because it used to 'hang' regularly when trying to get some repo or another. IMHO, the less third party repos, the better. A lot of the repositories duplicate each others content and most of them never really had anything I wanted. I try to keep it simple. The default repos that come with an Ubuntu install, including universe and multiverse are packed with almost every app an average user would need, including the bleeding edge stuff. If you can't download, compile, and install from source the odd app that you need which isn't available in those default repos, then get the source and enable it. 

Believe me, it is easier to compile such files yourself m8.

Hope this may help.

DK

---

### Post by hyper_ch on 2007-09-12
ieeeks, automatix ;)

---

### Post by buddhacub1120 on 2007-09-12
> **wolfen69 said:**
> here is a list of repos you can add to get anything.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

in terminal:
gksudo gedit /etc/apt/sources.list

add above repos as new lines and save.
then: sudo apt-get update

i did everything you said to do and this is what i came up with:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


:confused:

---

### Post by bapoumba on 2007-09-13
Sorry to be late on this.

Third party repos are fine, as long has they have packages properly packaged for Ubuntu, and for the same Ubuntu release (for ex, use the feisty medibuntu repo if you are currently on feisty, etc.).
This ensures that the packages you install "fits" in your distribution, that all the dependencies are satisfied with the proper version numbers, that libs are correct...

Now, going with sarge repos (or more generally with debian repos, or with gutsy repos if using feisty) is likely to break things (especially if libc6 comes as a dependency of a package you wish to install). Then you have a conflict regarding central packages version numbers, and depending if you accept to install or not, the whole system can break (this is a disaster scenario, unlikely to happen if you refuse to break the dependency tree).

Am I making sense ?

For the error in the post above mine, would you be using both synaptic and apt-get or aptitude at the same time? Only one package manager can run at any given time, a lock files ensures it, so ou need to close synaptic.
If not, this is another problem. 

For the medibuntu key error, you need to get the key as said earlier:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Now to answer dkaddict question, *I* never upgrade or dist-upgrade with third party repos enabled. I enabled them, update the list, install a package of interest (or upgrade it), comment the repos in the sources.list file, and update the file again.
Same thing for the backports (I have seen versions of flashpluggin make it into the backports and cause much problems. That day, I did install the faulty version on purpose to test fixes and help people out ;)). Medibuntu is in the wiki, and maintained  by MOTUs, so I guess they are okay. The newbie in me is just extra cautious and got trapped once, and once only, with a broken dependency tree :KS

---

### Post by pedrotuga on 2007-09-13
I commented the sarge repository and made an update and surprisly i didn't got any dependence error...cool.

I might get back to this topic... for now thanks everybody for the quick help.

---

### Post by dkaddict on 2007-09-14
Thanx m8:)

---

### Post by kroiz on 2008-05-16
> **dkaddict said:**
> Just to clarify.

I want to add the 'Medibuntu' repos to my sources.list.

'apt-get update' gives me the following error after entering the medibuntu repo address in my sources.list>>>



To verify the problem, I simply take the last 8 digits '0C5A2783' and replace 'key' with them so>>

```
gpg --keyserver subkeys.pgp.net --recv KEY
```becomes

```
gpg --keyserver subkeys.pgp.net --recv 0C5A2783
```press return and apt will fetch the key from the server

and

```
gpg --export --armor KEY | sudo apt-key add -
```becomes

```
gpg --export --armor 0C5A2783 | sudo apt-key add -
```press return and apt installs the fetched key to your system

Voila, I have my keys.

Easy ain't it m8

Happy days

DK
Thanks, that fixed the problem for me.
I got  the message after following the medibuntu wiki [instruction]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") for adding a repo.
Should those instructions be fixed?

---

