---
title: "Firefox disaster"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by malty on 2007-12-01
Firefox updates itself, no problems. Today Firefox will not start (at all). I have tried....
Uninstall, reinstall. Complete removal, reinstall ( I found out afterwards that I should NOT have done this ) Installation via Ubuntuzilla 4.4.4 deb. Still nothing.
After the Firefox update every time I opened my IGoogle homepage it also opened the normal Google page in another tab.
I also, after the recent update, had installed a lot of Adobe fonts from windows on C drive, also installed Azeurus although Firefox ran OK after this.
Comments /  help please
                                       Malty

---

### Post by XVII on 2007-12-01
Have you tried uninstalling, deleting the firefox folder in your home directory, and then reinstalling?

---

### Post by malty on 2007-12-01
I tried your suggestion....in synaptic I removed Firefox, then removed the Firefox folder in the home directory. No luck "starting Firefox"  then nothing, also no new, replacement folder in the home directory. I saved the old one (in the skip)
                           Malty

---

### Post by nanotube on 2007-12-01
rename the .mozilla folder in your home dir, and start with a fresh profile. 
see if that makes it behave.
if so, then you can copy your bookmarks etc from your old renamed profile, and reinstall your extensions.
if not... then we can try thinking of something else. :)

---

### Post by alienexplorers on 2007-12-01
You can create a new profile using the command:
> firefox -profilemanager
You can then migrate your extensions ect over to it by following this write up:
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by malty on 2007-12-02
Did I open a can of worms with this one ! I already tried to create a new profile, no good.
I tried deleting the default profile folder in my home directory ( so desparate I am not bothered about starting again), no good. Creating a new mozilla profile folder, no good. Installing / reinstalling Firefox (again) no good, nothing..."starting Firefox" then nothing. I Googled   "firefox wont start in Ubuntu" More advice out there than the labour governments lies. Here was me thinking Linux really was superior to windows, at least I could totally nuke a programme inXP and start again, can I not do the same in Ubuntu ?.
                                                                             Malty

---

### Post by bollix47 on 2007-12-02
Have you tried starting Firefox via Terminal (Applications - Accessories - Terminal)?

Perhaps some error messages will show up in the terminal window that could lead to a solution.

---

### Post by dfreer on 2007-12-02
It might be helpful to try launching firefox from the terminal, to see if it posts any error messages:
```
firefox
```

Also, a complete removal isn't a bad thing per se, you'd remove firefox like so:
```
sudo apt-get remove --purge firefox
mv -v ~/.mozilla ~/.mozilla-backup
```

There may be some other firefox related packages on your system, so we can try removing those as well (keep notes as to what is uninstalled here, so you can reinstall it later):
```
sudo apt-get remove --purge firefox* mozilla-firefox*
```

Now to reinstall:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install firefox
```

That should result in a complete removal. A regular "apt-get remove" will just uninstall the program, leaving any files specified as configuration files behind (this generally means any files in /etc). The "--purge" option tells dpkg to uninstalll those configuration files as well.

The "apt-get clean" command deletes your local apt cache, which basically keeps all of the programs you install so that if you wanted to reinstall, you wouldn't have to download the entire package again. The problem with this can be if your original package was corrupted for some reason, which might explain the problem you are having now (doubtful though), you would just be reinstalling the same corrupted package again.

You would still be left with your user preferences in the ~/.mozilla folder in your home directory. Normally, you don't want to delete this but just move it (you don't want to delete all of your bookmarks/settings do you?). Once you move it, firefox when run will create a brand new ~/.mozilla, and if things are working, you should be able to reintergrate your settings into the new ~/.mozilla folder.

---

### Post by malty on 2007-12-02
I launched Firefox via the terminal and got.....
     Floating point exception ( core dumped )
                                              Malty

---

### Post by malty on 2007-12-02
The following is what I got in the terminal
 john@john-desktop:~$ sudo apt-get remove --purge firefox
[sudo] password for john:
Sorry, try again.
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblog4j1.2-java libswt3.2-gtk-java libseda-java libcommons-cli-java
  libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  firefox* mozilla-firefox-locale-en-gb*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 27.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122569 files and directories currently installed.)
Removing mozilla-firefox-locale-en-gb ...
Removing firefox ...
Purging configuration files for firefox ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
john@john-desktop:~$ mv -v ~/.mozilla ~/.mozilla-backup
`/home/john/.mozilla' -> `/home/john/.mozilla-backup'
john@john-desktop:~$ sudo apt-get remove --purge firefox* mozilla-firefox*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
E: Couldn't find package firefox-2.0.0.11.tar.gz
john@john-desktop:~$ sudo apt-get clean
john@john-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB [21.3kB]      
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB [2395B] 
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB [4405B]   
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB [8133B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Get: 9 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Get: 10 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release.gpg [189B]               
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Translation-en_GB
Get: 11 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release [5535B]
Hit [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages
Fetched 42.1kB in 15s (2715B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
john@john-desktop:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
john@john-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblog4j1.2-java libswt3.2-gtk-java libseda-java libcommons-cli-java
  libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
Suggested packages:
  firefox-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9185kB of archives.
After unpacking 26.6MB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main firefox 2.0.0.10+2nobinonly-0ubuntu1.7.10.1 [9185kB]
Fetched 9185kB in 2m46s (55.2kB/s)                                             
Selecting previously deselected package firefox.
(Reading database ... 122057 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.10+2nobinonly-0ubuntu1.7.10.1_i386.deb) ...
Setting up firefox (2.0.0.10+2nobinonly-0ubuntu1.7.10.1) ...
Please restart any running Firefoxes, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
john@john-desktop:~$ 

This time Firefoxes import settings dialogue appeared after that ... nothing
                     Malty

---

### Post by malty on 2007-12-03
Me again (malty minus firefox)
I have narrowed the problem down, I think, to...." floating point exception ( core dumped )"
I have tried recreating new profile folders for Mozilla ( succsessfully ) and Firefox (after creating it in Firefox profile manager I can`t find it !)
In the words of an old gaffer of mine " where do we go from here ", mind you, he said that after we built a big chunk of a VC10 flying command centre that was 8'-6" wider than the factory door, well what would you do? 
                                                                  Malty:confused:

---

### Post by treris on 2007-12-04
> **malty said:**
> I launched Firefox via the terminal and got.....
     Floating point exception ( core dumped )
                                              Malty

Getting the same error here on a number of sites, such as for instance news.google.com which makes firefox crash as soon as you reach the bottom of the page, furthermore firefox seems to be crashing when entering specific word combinations in the google search bar, one of these combinations is:
Floating point exception firefox

I don't know what's going on, but I sure am not liking it, firefox being on the fritz is maddening!!!

Any help would be incredibly appreciated!

Edit: Using the ubuntuzilla script I have now installed the official build of Firefox and that seems to have solved the problem, so my guess is that there is something wrong with the firefox package in the repositories

Edit: see here for more information [https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861](https://bugs.launchpad.net/ubuntu/+source/libcairo/+bug/173861), potentially the problem might also be solved by downgrading the libcairo2 package to the previous version

---

### Post by malty on 2007-12-06
Treris
         I tried to install Firefox via Ubuntuzilla....zilch, nuffink, same terminal error.."floating point exception". I am not clear about whether or not the Ubuntuzilla installation overwrites the original synaptic package installation as I seem to only have one version now ( applications / internet / Firefox icon )
         Some further points...

I did import from WinXP about 650 of my Adobe fonts using the font installer at about the time Firefox fell out of its pram, although it was running for 2 / 3 days first. The is nothing wrong with the fonts in windows, I have had and used them for 2 years. 
I had insalled FireFTP in Firefox some days before the problem stated, again Firefox was running OK in that time.
I think, judging by the shear amount of forum traffic out there, both Ubuntu and others, that Firefox in Linux needs some very serious fettling ! I use Firefox in WinXP, as my default browser, (hands up all those who think that IE is the worst product ever to come out of the computer industry), heavily laden with its own and Google goodies, no problems at all, a tad slow but you would expect that.
Using in Linux is a pain..very slow, or will not speak to me. Pro tem I have gone back to Opera which is blindingly fast compared with Firefox, although the reason I ditched it 2 years ago was that every time it updated it shafted itself. Konqueror of course is a little beauty of a browser but lacks a lot of Google supprt.
                                                         Regards    Malty minus Firefox

---

### Post by andyho on 2007-12-06
Ok.. this might be far fetched.. but somehow after I tried updating my firefox, it just didn't want to work.. I'd search for my post, but there probably wasn't anything good in it anyways! LOL! I originally used the ubunuzilla script too but after updating, it was just kaput.. soooo.. uninstalled and reinstalled a few times, new profiles, all that other good stuff.. on the last re-install I decided to check where the shortcut was pointed to.. changed  it and lo and behold, it worked!! So maybe just double check that and maybe you'll be back up and running :)

---

### Post by treris on 2007-12-06
Malty

Try downgrading the libcairo2 package to the previous version, as I said in the edit to my earlier post there is a bug reported with this package and others have reported good results with downgrading it, as you can see here:
[http://ubuntuforums.org/showthread.php?t=632085&highlight=floating+point+exception&page=2](http://ubuntuforums.org/showthread.php?t=632085&highlight=floating+point+exception&page=2)

I hope this works for you, I know how intensely frustrating it can be to have something as important as firefox not working right.

kind regards and good luck!

---

### Post by malty on 2007-12-10
After giving the matter serious consideration, and bearing in mind that life is short, trees to fell, logs to chop, dogs to walk, etc, I dun bin an gone an dun it....I installed Gran Paradiso, rough edges and all ( things can only get better ) So up yours Firefox 2,  you and I could not go on meeting like we did, see you in Paradiso.
                                                                Warm thanks to all who tried to shed enlightenment upon an obviously knotty problem.
                                                       Malty minus firefox but with Gran Paradiso.:)

---

### Post by treris on 2007-12-10
Malty, 

The issue should be fixed now, I have just gotten an update to the libcairo2 package which is supposed to fix the floating point exception problem, you should see it too, or otherwise maybe a little later if the servers are still updating.

Treris

---

