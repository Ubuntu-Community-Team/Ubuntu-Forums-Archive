---
title: "Look At Ubuntus Stupidity"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-07
ok i cant install wine the normal way so i have downloaded the source code and am trying to compile it as it tells me how to in the read-me.

what do you make of this.....

```
   ***sphinx*** cd //home/sphinx/wine-0.9.9
 ***sphinx*** ./tools/wineinstall
WINE Installer v0.75

Running configure...

./configure: line 996: config.log: Permission denied

Configure failed, aborting install.
 ***sphinx*** sudo ./tools/wineinstall
WINE Installer v0.75

You are running wineinstall as root, this is not advisable. Please rerun as a user.
Aborting.
 ***sphinx***
  
```

dont anyone tell me to set the permissions on the files coz they are all set.
ubuntu is pissing me off big time.
why is every install and simple task full of errors and hardships??
everyone says "its a learning curve", well i say "its like banging a nail into a piece of wood with your head ](*,) "

---

### Post by gn2 on 2006-10-07
> **uk_sphinx said:**
> ok i cant install wine the normal way so i have downloaded the source code and am trying to compile it as it tells me how to in the read-me.

what do you make of this.....

```
   ***sphinx*** cd //home/sphinx/wine-0.9.9
 ***sphinx*** ./tools/wineinstall
WINE Installer v0.75

Running configure...

./configure: line 996: config.log: Permission denied

Configure failed, aborting install.
 ***sphinx*** sudo ./tools/wineinstall
WINE Installer v0.75

You are running wineinstall as root, this is not advisable. Please rerun as a user.
Aborting.
 ***sphinx***
  
```

dont anyone tell me to set the permissions on the files coz they are all set.
ubuntu is pissing me off big time.
why is every install and simple task full of errors and hardships??
everyone says "its a learning curve", well i say "its like banging a nail into a piece of wood with your head ](*,) "


Last time I looked Automatix could install Wine for you. Auto-magically.
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Never bang the nail in with your head, just force it in with pure telekinetic thought control.

If the cap doesn't fit, don't wear it.

Other Distros are available.

---

### Post by Phatfiddler on 2006-10-07
It appears as if it is aborting because you are installing under super-user.  Have you tried installing it as a normal user?

---

### Post by aysiu on 2006-10-07
Why can't you install Wine the normal way?

---

### Post by uk_sphinx on 2006-10-07
>   It appears as if it is aborting because you are installing under super-user. Have you tried installing it as a normal user?  

for gods sake man look at the code.
i did the first time.
if you read the code before writing that i wouldnt have to answer.

hey aysiu, your the man for the job, you always seem to help me out.
i have started another thread explaining it.sorry.that automatix???
i cant download it to start with.

---

### Post by aysiu on 2006-10-07
Okay. This is how you would install it the normal way.

**Step 1.** Get a fresh repositories list with the Universe repositories in it by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2.** Paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install wine
``` If that doesn't appear to work, please post back the output of that last command, and we'll go from there.

---

### Post by uk_sphinx on 2006-10-07
i will post the results as an edit of this post. i will also take a screen shot to show you the repository list.
i know that website is yours and i have read every tutorial in it word for word.
that website is how i feel comfortable on ubuntu.

[edit]
can i send you the screen shots through email?

---

### Post by aysiu on 2006-10-07
No need to take a screenshot of your repositories list. Just get a fresh one and start again.

If you do want to post your repositories list, just copy and paste the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by Old Pink on 2006-10-07
> **uk_sphinx said:**
> for gods sake man look at the code.
i did the first time.
if you read the code before writing that i wouldnt have to answer.

It's easy to get agitated at times like this, but please, don't. :)

---

### Post by picpak on 2006-10-07
I really wouldn't recommend compiling something like Wine from source. Here's a direct link to the download:

[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.22~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.22~winehq0~ubuntu~6.06-1_i386.deb)

---

### Post by uk_sphinx on 2006-10-07
how do i install it from the archive that i download from that link m8?
i couldnt figure out how to install the flash plugin when i downloaded it to desktop.

---

### Post by picpak on 2006-10-07
Are you using Dapper?

If so, just double click it and click Install.

---

### Post by ian.l on 2006-10-07
What are you trying to run under Wine? I am asking because many people (including myself) run World of Warcraft under Wine, but I can tell you that Wine needs to be patched and compiled from source if you want to run WoW without a targeting problem occurring ingame.

I would research other people's experiences with specific Windows Applications under wine so that you know what to expect. Just FYI.

---

### Post by Anonii on 2006-10-07
Get in the directory of the file you downloaded, using the terminal and execute:

[B]sudo dpkg -i win*.deb
[/B]

(Careful with that youth angst.)

---

### Post by uk_sphinx on 2006-10-07
i dont know how to install it from desktop if i download it that way.
is it easyer??


alysiu
can i send the screenshots to your e-mail address??


```
  ***sphinx*** sudo aptitude update && sudo aptitude install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Get:5 http://gb.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://gb.archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Get:6 http://gb.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Get:7 http://gb.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://gb.archive.ubuntu.com dapper-backports/main Packages
Get:8 http://gb.archive.ubuntu.com dapper-backports/restricted Packages [14B]
Hit http://gb.archive.ubuntu.com dapper-backports/universe Packages
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
Get:9 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://gb.archive.ubuntu.com dapper-backports/main Sources
Get:10 http://gb.archive.ubuntu.com dapper-backports/restricted Sources [14B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://gb.archive.ubuntu.com dapper-backports/universe Sources
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://wine.budgetdedicated.com dapper Release.gpg
Hit http://wine.budgetdedicated.com dapper Release
Ign http://wine.budgetdedicated.com dapper/main Packages
Err http://wine.budgetdedicated.com dapper/main Packages
  404 Not Found
Fetched 62B in 1s (53B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
 ***sphinx***
 ***sphinx***
 ***sphinx***
 ***sphinx***
 ***sphinx***
 ***sphinx*** sudo apt-get update && sudo apt-get install wine
Ign http://wine.budgetdedicated.com dapper Release.gpg
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get: 2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get: 3 http://gb.archive.ubuntu.com dapper Release.gpg [189B]
Get: 4 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get: 5 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://wine.budgetdedicated.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Get: 6 http://gb.archive.ubuntu.com dapper-backports Release.gpg [191B]
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper Release
Errhttp://wine.budgetdedicated.com dapper/main Packages
  404 Not Found
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/main Sources
Hit http://gb.archive.ubuntu.com dapper/restricted Sources
Hit http://gb.archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-updates/main Sources
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-backports/main Packages
Hit http://gb.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://gb.archive.ubuntu.com dapper-backports/universe Packages
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com dapper-backports/main Sources
Hit http://gb.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://gb.archive.ubuntu.com dapper-backports/universe Sources
Hit http://gb.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 6B in 0s (10B/s)
Failed to fetch http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
 ***sphinx***
  
```

---

### Post by uk_sphinx on 2006-10-07
i need it for a few things.
i need to decompile a basic program i made for a start.
possibly install basic

i want firefox windows version coz i cant see most pictures and videos under linux version.

i cant change my 3d settings in ubuntu. even though iv installed latest drivers.

more things i cant be bothered to type them all out.

mainly my programming stuff though.

---

### Post by picpak on 2006-10-07
Oh no, I didn't know you use amd64.

Try this guide:

[http://porg.es/blog/wine-on-ubuntu-with-amd64](http://porg.es/blog/wine-on-ubuntu-with-amd64)

Semi-confusing, but should work.

---

### Post by aysiu on 2006-10-07
I don't know what all the *sphynx* stuff is in your output, but I would recommend getting a fresh sources.list as per my last instructions. I see a lot of gb.archive in there as well as wine.budgetdedicated.com

By the way, one of those said AMD64... are you using a 64-bit Ubuntu? If so, I'm not sure if you can install Wine easily. Wine is really for 32-bit, as far as I know.

---

### Post by AndyCooll on 2006-10-07
> **aysiu said:**
> I don't know what all the *sphynx* stuff is in your output, but I would recommend getting a fresh sources.list as per my last instructions. I see a lot of gb.archive in there as well as wine.budgetdedicated.com

By the way, one of those said AMD64... are you using a 64-bit Ubuntu? If so, I'm not sure if you can install Wine easily. Wine is really for 32-bit, as far as I know.

There's nothing wrong with the "gb", that's how it should be for users accessing the UK repositories.

However I noticed that you get an error message when trying to update the Wine repositories. Not sure whether that means they are temporarily unavailable or there's something else.

Earlier on in this thread you also mention issues playing videos in Firefox. You shouldn't need to use the Windows version to resolve this. Installing something like the mozilla-mplayer-plugin through Synaptic should do the trick. 

Finally, as Aysiu points out above if you have a 64bit pc installing Wine might be quite tricky.

---

### Post by aysiu on 2006-10-07
You're right--there's nothing inherently wrong with using the UK mirrors, but it means that uk_sphynx didn't follow my instructions for getting a fresh repositories list.

---

### Post by uk_sphinx on 2006-10-07
i have pentium 4 3ghz
i think thats 64 bit??
someone told me that 64 bit would be ok playing 32bit programs coz its only an improvement

shall i just forget it then???

[edit]
also, how do i get a fresh list.???
do i just delete it and do the repositorys again??
or shall i delete the contents of the text file???

---

### Post by aysiu on 2006-10-07
There are plenty of packages in the repositories that are not packaged for 64-bit or PowerPC.

Who told you it could just use 32-bit packages?

There are some tricks to get 32-bit packages working in 64-bit. I think someone earlier in the thread may have linked to one for Wine specifically. If you want things to work easily, though, your best bet is to use x86 Ubuntu instead of AMD64 Ubuntu. My opnion.

---

### Post by uk_sphinx on 2006-10-07
youve lost me m8
you want me to install a different versiion??
the 32 bit ubuntu

yeah it said not compatible to me a min ago when i manually right clicked and installed.

i cant believe im having problems because my computers too fast

what do i click on to find out my exact version coz i didnt write it down on my cd

[edit]
>   I don't know what all the sphynx stuff is in your output, but I would recommend getting a fresh sources.l  

i just pressed enter a few times to seperate the 2 different types of installation i did.
thought you might read it a little better if i seperated it.
aptitude -------  gedit

---

### Post by gn2 on 2006-10-08
The problem you may have is that AMD64 isn't Intel Pentium....

You wouldn't put petrol in a diesel engine...?

Wine is a compatibility layer which will help run 32-bit Windows apps so it might struggle on a 64-bit OS?

If you are using 64-bit edition of Ubuntu, then perhaps you should install 32-bit version instead.

And perhaps consider changing your thread title?

---

### Post by handy on 2006-10-08
& you won't really notice any speed difference using 32bit as opposed to 64bit.

You will have an easier life with Ubuntu though...

64bit is not really suitable for beginners, I know, I've been there too!  

(***Edit:** Been to 64bit Breezy, still a beginner!* ;)  )

---

