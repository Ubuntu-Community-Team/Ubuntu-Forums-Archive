---
title: "[SOLVED] Lots of minor errorsand questions"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-10-22
There is going to be a lot of questions here, so be prepared!

I have heard of a program out there that can emulate Windows on a Linux system. What is it called an how does it work? (I want to use Snes9x and Autodesk Inventor 11, in case you were wondering. That is all! ^-^; I will not betray Linux!)

As for upgrading to Gutsy, I seem to be unable to due to a gtkpod error. Has there been a bug reported about this, or is it a common issue that can be dealt with? If so, how?

Synaptic seems to have problems with me. I have been trying to download Ubuntustudio, but I keep on coming up with a message that is closely related to a type of file dependency, of which prevents me from downloading it. How can I get around this? I will post an example of what I mean here: [[img=http://img481.imageshack.us/img481/3195/screenshotin8.th.png]](http://img481.imageshack.us/my.php?image=screenshotin8.png)

That is all I can think of right now, so thank you very much for your suggestions in advance!

---

### Post by Cheese Roller on 2007-10-22
They HAVE SNES Emulators for Linux.

---

### Post by shad0w_walker on 2007-10-22
The program your looking for (Windows programs on Linux) is wine. It is a hit and miss issue if  you can get programs working but it is getting better and popular applications get fairly reasonable support. You can check how well a program works by having a look on the Wine website:

```
http://appdb.winehq.org/appbrowse.php
```

As for snes9x there is no need to use Wine, it's open source and available for Linux. It's even included in the repo's for Ubuntu.

---

### Post by ShadowMKII on 2007-10-23
I see! I thought that the Snes emulator for Linux was just a mystery. Does that mean that I will have to convert all of the files that I have for the Snes over to a certain format? Also, I thought there was something called VMWare or something that could emulate Windows, unless I am horribly mistaken.

As for the Gutsy upgrade error, I remember what it was. It was: [http://www.gtlib.gatech.edu/pub/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.10-2_amd64.deb/dists/feisty/main/binary-amd64/Packages.gz](http://www.gtlib.gatech.edu/pub/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.10-2_amd64.deb/dists/feisty/main/binary-amd64/Packages.gz)

Has there been any problems similar to this little bit?

Thank you for the quick responses by the way.

---

### Post by rickycodie on 2007-10-23
yes vmware dows exist and is also in the repo's. i like virtual box though, available through thier website in .deb format.

---

### Post by shad0w_walker on 2007-10-23
You don't need to convert anything for the snes. Its exactly the same program as the windows version just the linux version.

---

### Post by ShadowMKII on 2007-10-23
That is a whole bunch of good news in terms of Snes! Do you know where to get it from?

As for VMWare and Virtual Box, what is the difference? Does one have more support than the other?

Lastly, does anyone have any details regarding my Synaptic and Gutsy problems?

---

### Post by shad0w_walker on 2007-10-23
Snes9x should be available from the repos so do a search in synaptic (I believe its called gsnes9x in the repos) and it should show up.

VMware and VirtualBox both provide pretty much the same functionality. They will both allow you to run virtual machines and both have pretty good performance.

The major differences:

VMware is a commercial solution so it would require purchase or using VMplayer (A stripped down version of VMware) which cannot create new virtual machines. I am a little bit out of touch with VMware so anyone feel free to correct me if this has changed. VMware has one reasonable advantage over Virtualbox in the fact it is capable of limited 3d acceleration (Don't expect to be gaming with it) so is capable of basic 3d functionality

VirtualBox is now open source and available for easy install from the repos. It has all the same major functionality of VMware and the other major players in this area so there is no sacrifice of features. The only major disadvantage is to my knowledge (I could be wrong) Virtual box is not capable of 3d support.


As for your synaptic problems, are you sure you have all the extra repos enabled? It looks like it requires a package but is unable to find it in your repos.

---

### Post by ShadowMKII on 2007-10-24
Well, I got GSnes9x from Synaptic, and everything worked there. Now I have the problem of not being able to find any help files whatsoever, as I do not know how to configure the controls for GSnex9x. Any help on how to get the documentation?

As for VWare and VirtualBox, I have not tried them yet. I will probably get get VirtualBox as it appears to have a bit more support.

So far, I believe that I have all of my repositories enabled. I will give you a screen shot to check just in case I am mistaken. [[img=http://img142.imageshack.us/img142/8061/screenshotoy0.th.png]](http://img142.imageshack.us/my.php?image=screenshotoy0.png)

If there is something missing, please tell me. I also get an error message every time I reload Synaptic that states that this:

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://www.gtlib.gatech.edu/pub/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.10-2_amd64.deb/dists/feisty/main/binary-amd64/Packages.gz:](http://www.gtlib.gatech.edu/pub/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.10-2_amd64.deb/dists/feisty/main/binary-amd64/Packages.gz:) 404 Not Found [IP: 128.61.111.11 80]"

There you have it! Hope this information helps a bit.

---

### Post by shad0w_walker on 2007-10-25
Looks like you have all your repos enabled. As for the error take a look in your 'Third-party software' tab in synaptic, it looks like you have an external repo that isn't responding. Find the entry that starts off like the address ([http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu)) in your error message and remove it.

As for Gsnes9x, i am now dumping my recommendation of using that (Just installed it and its horrid) I recommend giving zsnes a try. It's in the repos and whilst its a little different than snes9x it should do what you want and is a load easier to configure than snes9x.

---

### Post by ShadowMKII on 2007-10-26
That helped a lot. Now that I deleted that thing from my "Third-party software" tab, I was able to upgrade to Gutsy and have been able to get some needed updates. Thank you a lot for that!

As for Gsnes9x, I have got rid of it as well. There is a problem though, where should I go to get zsnes? I have gone to Synaptic and it is not there, unless you meant something different. I am going to try and look around for it on the net and get back to you on that.

---

### Post by shad0w_walker on 2007-10-26
Very strange, it should be in the repos, strange it's not showing up. Anyway, this is a link to the download from the Ubuntu packages list.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fz%2Fzsnes%2Fzsnes_1.510-1_i386.deb&md5sum=a892d4fa3f1cd9534e1dfbe472fc63aa&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fz%2Fzsnes%2Fzsnes_1.510-1_i386.deb&md5sum=a892d4fa3f1cd9534e1dfbe472fc63aa&arch=i386&type=main)

---

### Post by ShadowMKII on 2007-10-26
Never mind, I have it all solved now! I had to do a little work so I could find it in Synaptic by clicking a link and downloading a repository that linked me to Zsnes so I could force the i386 architeture on my i586 machine! It was a quick and easy terminal experience, and it is right here:
```
jordi@Shadow-Slate:~$ echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list
[sudo] password for jordi:
deb http://packages.dfreer.org gutsy main
jordi@Shadow-Slate:~$ wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
--14:03:04--  http://packages.dfreer.org/7572013D.gpg
           => `-'
Resolving packages.dfreer.org... 66.209.138.18
Connecting to packages.dfreer.org|66.209.138.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,718 (1.7K) [text/plain]

100%[====================================>] 1,718         --.--K/s             

14:03:05 (997.31 KB/s) - `-' saved [1718/1718]

OK
jordi@Shadow-Slate:~$ sudo apt-get update
Get:1 http://packages.dfreer.org gutsy Release.gpg [189B]
Ign http://packages.dfreer.org gutsy/main Translation-en_CA
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_CA
Get:3 http://packages.dfreer.org gutsy Release [6896B]
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://archive.ubuntu.com gutsy/universe Translation-en_CA
Ign http://archive.ubuntu.com gutsy/main Translation-en_CA
Get:4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_CA
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_CA
Get:5 http://archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_CA
Get:6 http://packages.dfreer.org gutsy/main Packages [4213B]
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_CA
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_CA
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://archive.ubuntu.com gutsy-security Release
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Sources
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages
Hit http://archive.ubuntu.com gutsy-security/restricted Packages
Hit http://archive.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy-security/multiverse Sources
Hit http://archive.ubuntu.com gutsy-security/restricted Sources
Hit http://archive.ubuntu.com gutsy-security/universe Sources
Hit http://archive.ubuntu.com gutsy-security/main Sources
Fetched 11.3kB in 1s (5762B/s)
Reading package lists... Done
jordi@Shadow-Slate:~$ sudo apt-get install zsnes32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32ao2
The following NEW packages will be installed:
  lib32ao2 zsnes32
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 611kB of archives.
After unpacking, 3280kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://packages.dfreer.org gutsy/main lib32ao2 0.8.8-3.0 [20.4kB]
Get:2 http://packages.dfreer.org gutsy/main zsnes32 1.510-3.0 [590kB]
Fetched 611kB in 4s (122kB/s)   
Selecting previously deselected package lib32ao2.
(Reading database ... 105962 files and directories currently installed.)
Unpacking lib32ao2 (from .../lib32ao2_0.8.8-3.0_amd64.deb) ...
Selecting previously deselected package zsnes32.
Unpacking zsnes32 (from .../zsnes32_1.510-3.0_amd64.deb) ...
Setting up lib32ao2 (0.8.8-3.0) ...

Setting up zsnes32 (1.510-3.0) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jordi@Shadow-Slate:~$
```

Thank you for all of your help! You made this person one happy Ubuntu user! Woo hoo! Time to go and play some Chrono Trigger and Super Metroid! ^-^

---

### Post by wolfear on 2007-11-16
> It was a quick and easy terminal experience
I know what you meant, but I got a chuckle out of that one.

---

### Post by tru infini on 2008-06-22
ok i figured this was a place to get a little help. i cant seem to get any sound from my zsnes and i cant get any movement when i try and play Mario paint on my gsnes9x any help?

---

### Post by ShadowMKII on 2008-06-24
You came to the right place for help! Well, not exactly, which is why I am going to redirect you.

There is another thread, and it is called something along the lines of the "Zsnes sound fix all end all." If you type in Zsnes and sound into the search field, you should be able to find the thread, which will help to solve your sound problems. It is a pretty hot topic at this point.

As for Gsnes9x, I tried it and it pales in quality compared to the Zsnes. That is just my opinion, however. I also have not tried it in about 6 months, so keep that in mind.

If you would like some more help, there is another Zsnes thread somewhere that is maintained by one person (just like that "Zsnes sound" one), but I forgot the name. If you search for it for a while, you will find it.


I hope that helped you! If you have any more questions, just PM me and I will try to take a look into it. ^^

---

