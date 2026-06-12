---
title: "Can figure out how to install VLC Media Player"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by jim@moneytime.ca on 2006-07-16
Man...  I thought I was good at using a computer but I feel like I am working on my very first XT computer.

I have recently (withing the last 3 days) installed ubuntu.  I have played around in the command line of a different compilation (but I can't remember)..  I just did some basic mount a drive, mkdir and so on.

I have been trying to install VLC and I went to the site and clicked on the Ubuntu Linux link and the following showed up:

[qutoe]
Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd.
[/quote]

So...  Naturally I found the Synaptic Package Manager and searched down the list for anything that sad Repository or univers.  But I couldn't find anything.

I went and googled the term "universe repository" and it didn't come up with anything helpful.

So, I turn to the community.  I have had very good success with forums in the past, so my fingers are crossed.

I was hoping that someone could please explain to me how the installation process works, also, what things are (like univers repository).

I have figured out how to do some basic things like networking drives and such, but I would really appreciate some help here.

Also, if anyone has a chance, if they could also explain how to install the Macromedia Flash plugin.  I went there, downloaded the file and then extracted it to the desktop.  I double clicked on the icon and it asked me if I wanted to run the installer and I said yes.  Then, it said I needed the following libraries - gsfonts and gsfonts-xll ...  however, I have no clue how to do that either.

I have tried in FF and the plugin isn't working so something didn't work right.

Any help is appreciated.

Jim

---

### Post by orb9220 on 2006-07-16
run synaptic click on search and enter vlc

if it dosn't show up then you need to add some repositories to synaptic
goto settings>repositories then click on Ubuntu 6.06.Lts (Binary)
                                         Ubuntu 6.06.Lts Backports (binary)
To add them close and try the 
search again for vlc

Good luck

---

### Post by catlett on 2006-07-16
If you want to know the in and outs you can search the wiki. If you want a cut and paste fix, here it is. Open up the terminal and enter these commands.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
```
sudo gedit /etc/apt/sources.list
```
When the document opens up, delete everything and cut/paste this in.
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

##Ubuntu proprietory repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial mainMake sure to save the document by hitting save on the toof the window. Close the document.
Go to the terminal and enter```
 sudo apt-get update
``` Then go back to synaptic and do a search for vlc media player.

If you want all your multimedia to work, follow the dapper guide. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
You will already have the necessary repositories. It will be a matter of cutting and pasting commands into the terminal.

---

### Post by jim@moneytime.ca on 2006-07-16
Thanks very much..

That was fast!

Any word on what went wrong with the flash plugin??

---

### Post by catlett on 2006-07-16
The Daper Guide has the commands but I'll post them here as well.
After you change your repository list, enter thses commands.
```
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
```

---

### Post by Uncle Spellbinder on 2006-07-16
```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```
This has not been working for quite a while. At least a week in my case. Always get **404 - NOT FOUND**.

---

### Post by catlett on 2006-07-16
Sorry about that, I didn't make the change on this computer. It seems that that PLF repo isn't online but this one is. Just put # in front of the other 2 lines and add these 2 so your list looks like this.
```
#deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
```

P.S. I'm going to editr the list above to reflect the change.

P.S.S. I don't know why it is editing the URL but I can only post it by erasing the ftp in front of the url. So if you want the entry, you have to add the ftp or just compare the 2 and you can see the parts left out by the ... 
deb ://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/[/url] dapper free non-free
deb-src ://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/[/url] dapper free non-free

---

