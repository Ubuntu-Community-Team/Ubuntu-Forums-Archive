---
title: "Install Macromedia Flash Player??"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-10
I have Dapper 6.0.6 , and have downloaded the flashplayer to the desktop.
How do I find the Firefox plugins directory to copy the files there? Thanks ](*,)

---

### Post by kaamos on 2006-06-10
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by Drakkor on 2006-06-17
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

---

### Post by charles on 2006-06-18
For some reason which escapes me , for the last 24 hours, any attempt to install  flash player plug ins (non free) meets with the same crash - This effect is identical in all attempts ie sudo apt-get - or using automatix or easyubuntu
The crash occurrs in all cases at "seeting up flashplayer plugins nonfree 7.0.53 ub.....   " The package manager indicates it to be installed - but she don't go!!!

---

### Post by 5-HT on 2006-06-18
[quote=charles]For some reason which escapes me , for the last 24 hours, any attempt to install  flash player plug ins (non free) meets with the same crash - This effect is identical in all attempts ie sudo apt-get - or using automatix or easyubuntu
The crash occurrs in all cases at "seeting up flashplayer plugins nonfree 7.0.53 ub.....   " The package manager indicates it to be installed - but she don't go!!![/quote] 
Going another route, you could grab flash from adobe/macromedia's site, extract the archive, and place the contents into ~/.mozilla/plugins (sorry Drakkor...was a tad too late).

---

### Post by Kilz on 2006-06-18
[QUOTE=5-HT]Going another route, you could grab flash from adobe/macromedia's site, extract the archive, and place the contents into ~/.mozilla/plugins (sorry Drakkor...was a tad too late).[/QUOTE]
Even better, get [Swiftfox]("http://www.getswiftfox.com/releases.htm"). Extract it, add a launcher to its firefox excutable, and add plugins through firefox like its designed to. Personaly I think the people at Swiftfox should make the linux version of Firefox.

---

### Post by nalmeth on 2006-06-18
flashplayer-nonfree did the same crashing routine for me, then I installed the [old breezy flash]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flash&searchon=names&subword=1&version=breezy&release=all")

---

### Post by InDenial on 2006-06-18
Hmmm I had the same problem installing the flashplayer. It would just hang at Setting up flashplugin-nonfree. Today however when I tried it worked. BUT.. when doing the sudo update flashplugin I got the following:
> 
automatic installation failed due to network problems or upstream changes


---

### Post by nickpaton on 2006-06-18
Dapper: Been trying various methods including those given here with little success.

What works for me is:

Download Flash from:
 [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

and save in your Home folder.

Uppack and uncompress: 

tar -xzf install_flash_player_7_linux.tar.gz

Open Terminal and Login as root: 

sudo su

Navigate to newly created "install_flash_player_7_linux" folder in your Home directory: 

cd /install_flash_player_7_linux

Then to install:

./flashplayer-installer

Respond to various questions and when prompted accept the folder offered to install the required files

 Done!

(Modified to correct the file location to install the required files)

---

### Post by charles on 2006-06-18
Thanks for the interest and reply

Yep - tried that too.. but the installer routine won't allow - I can choose from a list of Mozilla, Opera (or ALL) , but it wont respond to a handtyped in reference of /usr/lib/mozilla-firefox - returns an error and insists on choosing from it's list

---

### Post by InDenial on 2006-06-18
[QUOTE=charles]but it wont respond to a handtyped in reference of /usr/lib/mozilla-firefox - returns an error and insists on choosing from it's list[/QUOTE]

Just use /usr/lib/firefox

/usr/lib/mozilla-firefox is a symlink to /usr/lib/firefox I believe.

Works like a charm here

---

### Post by charles on 2006-06-18
Nup
The routine won't allow it - it will accept (m) mozilla (o) opera or (a) All  - and wont accept any other input

---

### Post by InDenial on 2006-06-18
Weird... can you copy paste it?  and where did you get the file? macromedia.com?

---

### Post by Guns90 on 2006-06-18
Hi, I was having the same problem.  I just tried something and it appears to have worked.  I went to the 'old breezy flash' that nalmeth gave before, downloaded the 'non-free plug-in' portion and tried to run it.  It said it had a dependency problem and needed 'libruby' and 'ruby'.  I installed them then in the terminal did:

cd directory 
sudo dpkg -i /home/gary/Desktop/flashplugin-nonfree_7.0.25-5ubuntu0.1_i386.deb

it asked for, and I input':~$ sudo apt-get install -f

This is what it then did.
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-nonfree
Suggested packages:
  mozilla-browser mozilla-browser-snapshot mozilla-firefox
Recommended packages:
  libstdc++2.10-glibc2.2
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/16.5kB of archives.
After unpacking 20.5kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 76108 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 7.0.25-5ubuntu0.1 (using .../flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...


As you can see, it now lists (7.0.63.3ubuntu3) ...
 in stead of flashplayer plugins nonfree 7.0.53 ub.....

Hope this helps

---

### Post by nickpaton on 2006-06-18
[QUOTE=charles]...it wont respond to a handtyped in reference of /usr/lib/mozilla-firefox - returns an error and insists on choosing from it's list[/QUOTE]

I have since reinstalled Flash after it stopped Java from working (is there any end to the agony we put ourselves through??!! - the solution to getting both to work is further down).  When it came to installing Flash I simply accepted the folder offered as InDenial says.

If you do try it and it doesn't work, I would suggest uninstalling the libflashplayer.so and flashplayer.xpt files from the associated plugin folders (navigate to the plugin folder and sudo rm <filename.xxx>) to keep everything clean & tidy.

I think the overall conclusion is that flash is a b###h to get going, but it seems that perserverence is the name of the game!  Let us know how you get on.

Nick

(modified to correct file path to install and problems with Java and solution)

---

### Post by FastZ on 2006-06-18
[QUOTE=nickpaton]Dapper: Been trying various methods including those given here with little success.

What works for me is:

Download Flash from:
 [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

and save in your Home folder.

Uppack and uncompress: 

tar -xzf install_flash_player_7_linux.tar.gz

Open Terminal and Login as root: 

sudo su

Navigate to newly created "install_flash_player_7_linux" folder in your Home directory: 

cd /install_flash_player_7_linux

Then to install:

./flashplayer-installer

Respond to various questions and when prompted where to install, specify:

/usr/lib/mozilla-firefox

This will automatically install the correct files into the mozilla-firefox plugins directory.

 Done![/QUOTE]

That worked for me!  Thanks.  One question though, why does Firefox still come up saying I need to install the Flashplayer plugin?  Yet it shows flash working correctly on webpages???  I dont really care because it works but it gets annoying to have to close that plugin banner all the time.  :wink:

---

### Post by nickpaton on 2006-06-18
Further to my previous post here, when I installed Flash having first installed Java, I found that Java had stopped working, and any attempt at re-establishing the Java symbolic links resulted in broken links.

To overcome this I had to uninstall both Java and Flash, together with all files and symbolic links and reinstall.

Details of how I did this can be found at:

[http://www.ubuntuforums.org/showthread.php?t=138067](http://www.ubuntuforums.org/showthread.php?t=138067)

Fastz: glad you've managed to install Flash but sorry that your browser is showing the plugin is missing.

Unfortunately I don't have sufficient knowledge to advise - anyone else?

Nick

---

### Post by FastZ on 2006-06-19
Well, apparently, I should have waited until after I restarted Firefox.  After restarting Firefox, the plugin banner doesnt show up anymore.

---

### Post by nickpaton on 2006-06-19
Matt - glad you're sorted!  (Are you the geezer in the red hat LOL!!)

As a matter of interest does Java work OK as well?

---

### Post by charles on 2006-06-19
Thanks all 4 the help
Finally sorted my problems - installed the package from the Macromedia site and then MANUALLY copied the libflasher.so and flashplayer.xpt across to the /usr/lib/mozilla-flashplayer/plug-ins -- and as the actress said to the bishop...there ya go....


Taa all

---

### Post by someusernoob on 2006-06-19
I did the manual install of flash a few days ago, but it seems its not working very well.

On korn.com (no im not a fan, just an example lol) there is no text in the upperbar + menu's where it should be. 

After installing the flashplugin-nonfree it works fine.

---

### Post by mcpish on 2006-06-20
is anyone else actually having problems downloading the file from Macromedia's site..  it seems to be insanely slow for some reason.  I've been trying to download that file for weeks, no matter what time of day, no matter what browser I use, that file transfer ALWAYS times out, is there something weird about the macromedia website?  It's the only site that gives me this problem.

---

### Post by charles on 2006-06-20
The sites of these files seem back up again today - have had three succesful downloads/install this arvo

---

### Post by someusernoob on 2006-06-20
It still wont work here as it should:

```

someusernoob@ubuntuforum:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
someusernoob@ubuntuforum:~$ sudo update-flashplugin
installation failed
someusernoob@ubuntuforum:~$

```

Uninstall > reboot > install - did the trick. It works well indeed.

---

