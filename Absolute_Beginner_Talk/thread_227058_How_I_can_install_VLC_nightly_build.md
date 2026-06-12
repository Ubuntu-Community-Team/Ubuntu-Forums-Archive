---
title: "How I can install VLC nightly build"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Bezvardis on 2006-08-01
Can anybody please explain me (step by step) how to install VLC latest nighly build? There is some new functionality (supposedly) that I need but I cannot get it done ([http://nightlies.videolan.org](http://nightlies.videolan.org)) I followed the instructions on their page but there it stops. I still I guess have the old version... 

(yes - not really in line with the above, but maybe it is indeed - can somebody explain me why installation is such a pain in Linux (Ubuntu) if compared to MacOSX or even Windows?)

---

### Post by koshari on 2006-08-01
"can somebody explain me why installation is such a pain in Linux (Ubuntu) if compared to MacOSX or even Windows?"

what you need to do by installing nightly builds is compile from source, 

and compiling on windows is something not many users would do!

you can often get newer versions of vlc from other repositorys.

---

### Post by Bezvardis on 2006-08-01
> **koshari said:**
> 
you can often get newer versions of vlc from other repositorys.

and how can I do that?

---

### Post by koshari on 2006-08-01
[http://nanocrew.net/?p=129](http://nanocrew.net/?p=129)

---

### Post by catlett on 2006-08-01
This is as easy as windows. This is the part you want 
#
```
Debian Sid I386 (unstable): add the following line to your sources.list

deb http://nightlies.videolan.org/build/sid-i386/arch ./

or [COLOR="DeepSkyBlue"]download here[/COLOR]

```Just click on the link. At the server index page click on this link
```
[DIR] arch/                   10-May-2006 14:17    -  
```
Then select from here the deb you want, It appears they list plugins seperate. Just a note, I do not know why thw dates are May 10, I can only guess they list the date of the last release and don't date the nightly build?
```
[   ] gnome-vlc_0.8.5-svn20060203-0_i386.deb          03-Feb-2006 15:15  1.2K  
[   ] gvlc_0.8.5-svn20060203-0_i386.deb               03-Feb-2006 15:15  1.2K  
[   ] kvlc_0.8.5-svn20060203-0_i386.deb               03-Feb-2006 15:15  970   
[   ] libvlc0-dev_0.8.5-svn20060203-0_i386.deb        03-Feb-2006 15:15  1.0M  
[   ] mozilla-plugin-vlc_0.8.5-svn20060203-0_i386.deb 03-Feb-2006 15:15  2.1M  
[   ] qvlc_0.8.5-svn20060203-0_i386.deb               03-Feb-2006 15:15  954   
[   ] vlc-plugin-alsa_0.8.5-svn20060203-0_i386.deb    03-Feb-2006 15:15   10K  
[   ] vlc-plugin-arts_0.8.5-svn20060203-0_i386.deb    03-Feb-2006 15:15  3.8K  
[   ] vlc-plugin-esd_0.8.5-svn20060203-0_i386.deb     03-Feb-2006 15:15  4.5K  
[   ] vlc-plugin-ggi_0.8.5-svn20060203-0_i386.deb     03-Feb-2006 15:15  5.5K  
[   ] vlc-plugin-glide_0.8.5-svn20060203-0_i386.deb   03-Feb-2006 15:15  3.9K  
[   ] vlc-plugin-sdl_0.8.5-svn20060203-0_i386.deb     03-Feb-2006 15:15   10K  
[   ] vlc-plugin-svgalib_0.8.5-svn20060203-0_i386.deb 03-Feb-2006 15:15  4.2K  
[   ] vlc_0.8.5-svn20060203-0.dsc                     03-Feb-2006 15:15  1.6K  
[   ] vlc_0.8.5-svn20060203-0.tar.gz                  03-Feb-2006 15:15   21M  
[   ] vlc_0.8.5-svn20060203-0_i386.changes            03-Feb-2006 15:15  3.0K  
[   ] vlc_0.8.5-svn20060203-0_i386.deb                03-Feb-2006 15:15  7.1M  
[   ] wxvlc_0.8.5-svn20060203-0_i386.deb              03-Feb-2006 15:15  438K  
```deb files install automaticallt. You can selecy "open with-Gdebi package installer" and it will install automaticaly.

OR YOU CAN ADD IT TO YOUR REPOS LIST SO THEY APPEAR IN SYNAPTIC PACKAGE MANAGER

Open the repo list with this command 
```
sudo gedit /etc/apt/sources.list
```

Put this line in at the bottom of the list 
```
deb http://nightlies.videolan.org/build/exp-i386/arch ./
```

Next you have to add the gpg key for the server
Download the key with ```

wget -O /dev/stdout http://nightlies.videolan.org/key|apt-key add - 
```
Add it to your list with this 
```
	gpg --keyserver subkeys.pgp.net --recv-keys 81CACA84
```
	```
gpg --list-sigs 81CACA84 (check for errors)
```
```
	gpg --export 81CACA84 -a|sudo apt-key add -
```
Next update your repository cache with```
 sudo apt-get update
```Now you can get the package through synaptic or you can get it with apt-get install vlc.. (whatever the exact name of the package is)


Either wau should work without a problem

---

### Post by koshari on 2006-08-01
you want WMV9 support dont you you sneaky bugger :-0
:lol:

---

### Post by catlett on 2006-08-01
> **koshari said:**
> you want WMV9 support dont you you sneaky bugger :-0
:lol:

Is that what this is about? I am not into this so I do not know.Do you mind if I ask why the nightly builds? Is it just to be on the cutting edge or is what koshari said. Just interested.
The directions I do not know from using the nightly build, I just went to the link and read them. 

P.S. For the future, Ubuntu is a modified Debian Sid. So if you see packages for sid, you can use them for ubuntu (most of the time)
Also i386 is for regular 32 bit systems and AMD64 is of course for AMD64. I am sure you know this but I wanted to point it out since I only showed the i386 choice,

---

### Post by Bezvardis on 2006-08-01
> **catlett said:**
> Is that what this is about? I am not into this so I do not know.Do you mind if I ask why the nightly builds? Is it just to be on the cutting edge or is what koshari said. Just interested.


I guess it is about these (whatever is the name) Windows media file formats. We have a local telecom company in Latvia that provides kind of cable TV to its customers. But they have made it only with Windows in mind. After installation of Ubuntu, I keep Windows partition for one reason only - to watch this TV. Now, I had the same problem with my Macintosh laptop, but a couple of days ago I discovered that the nigthly builds of VLC for Mac allow me to watch the TV. So I thought - if Mac version of nightly build can do it, then probably Ubuntu version can do it as well. That's the sole reason. In fact I don't need the nightly builds but only any which could do the job. Unfortunately I cannot speak about this in the Ubuntu forums because the service I am trying to use is for the subscribers of that telecom company. But in Latvian Linux forums I got only as far as receiving direction to 'compile VLC with w32 codecs and the thing will run nicely'. So I got nothing :-( But - yes - now you see the problem I am trying to solve.

---

### Post by catlett on 2006-08-01
Did you understand how to get the nightly builds of VLC? Feel free to say I did a bad job of explaining. My intention is to help you get the nightly builds, I want to know if I wasn't clear so I could clarify.

You mentioned win32codecs. Do you know how to install them? I will post it anyway just in case.
Open a terminal and issue these 2 commands
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```
If there are other multimedia issues, sometimes it is because it is a "restricted format". This tells how to enable some of them [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Post if you are having issues.

---

### Post by Bezvardis on 2006-08-02
> **catlett said:**
> 
You mentioned win32codecs. Do you know how to install them? I will post it anyway just in case.
Open a terminal and issue these 2 commands
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

Post if you are having issues.

Thank you!!! Unfortunately some things did not work, and I could not proceed. With installing win32 codecs, I got the following after the second command:

```
~$ sudo dpkg -i w32codecs_20060611-0.0_i386.deb
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb
```

---

### Post by catlett on 2006-08-02
Alright. It appears there is a problem with wget'ing the file. You can add the repo like you added the vlc repo. Afterr it is added, go to synaptic and search for "w32codes". It is spelled differently in synaptic. 

O.K. here we go again. Open up you list with ```
sudo gedit /etc/apt/sources.list
```
Add this line to it 
```
deb http://www.debian-multimedia.org stable main
```
Save and then close the file.
This repo has a gpg key that you have to get. Do these to commands
```
gpg --keyserver pgp.mit.edu --recv-key 07DC563D1F41B907
```
```
gpg --export --armor 1F41B907  | sudo apt-key add -
```
The second command should look something like this
> gpg: no ultimately trusted keys found
OK

Now enter ```
sudo apt-get update
```
Then open up synaptic package manager and search for w32codecs.
If it doesn't appear, the server must be down. This is a well known and popular repo. I doubt it is out of service. It is most likely down for maintenence or some other temporary thing.

---

