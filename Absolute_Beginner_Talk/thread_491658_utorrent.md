---
title: "utorrent"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by -R4zi3l- on 2007-07-03
will utorrent work with Ubuntu if running it through WINE or Cedega?

---

### Post by NeoLithium on 2007-07-03
Yep, uTorrent works just fine under Wine :)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.C2.B5Torrent_under_Wine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.C2.B5Torrent_under_Wine)

---

### Post by xenoph0be on 2007-07-03
> **-R4zi3l- said:**
> will utorrent work with Ubuntu if running it through WINE or Cedega?

Search the forum and I'm sure you'll find at least 1 howto... :p

---

### Post by -R4zi3l- on 2007-07-03
no i dont need  how to, but later i will, this currently is for a friend

---

### Post by SpikeyMike on 2007-07-04
Hi
I installed utorrent using the installation guide shown here: 

[http://ubuntuguide.org/wiki/Ubuntu:F...ent_under_Wine](http://ubuntuguide.org/wiki/Ubuntu:F...ent_under_Wine)

I installed wine no problem but when I installed utorrent it seemed to go ok, utorrent started after the installation but when I closed it I couldn't find any links to it in the menus and cannot find how to start it again, also the following was output in the terminal:

[COLOR="Red"]21:39:27 (277.42 KB/s) - `uTorrent-1.6.1-install.exe' saved [697492/697492]

root@MyUbuntu:/home/mikey# wine uTorrent-1.6.1-install.exe
wine: creating configuration directory '/root/.wine'...
wine: '/root/.wine' created successfully.
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
fixme:shell:DllCanUnloadNow stub
root@MyUbuntu:/home/mikey# fixme:shell:DllCanUnloadNow stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x34edd8
fixme:keyboard:UnregisterHotKey (0x40040,1): stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1[/COLOR]

now when I try to download a torrent it asks if I want to use bittorrent, I hadn't installed this but it seems to work but it doesn't give me the option to use utorrent.  

Any help appreciated

Spikey

---

### Post by Nythain on 2007-07-04
[http://ubuntuforums.org/showthread.php?p=2948336](http://ubuntuforums.org/showthread.php?p=2948336)
a great thread for getting firefox to use utorrent by default when downloading a torrent

---

### Post by davidjmayo on 2007-07-04
What's going on here??

The link you include goes to a page with no text but the url is the same (maybe the page has been deleted?)

The error output is covered in smilies (why?)

Why are you running as root?

To answer your last question I don't know why utorrent isn't working but I had problems with wine. You had it working I didn't (couldn't get a number to work in the listen port)

Bittorrent is installed as part of the standard installation so that's why it's there (you're right you didn't install it--sort of)

I use ktorrent which looks similar to utorrent but doesn't need wine. To install it 

applications==>add/remove
it's under internet. Click the box to select it, apply and it will download and install

If you use firefox you can change the default bittorrent client

EDIT
> If you use firefox you can change the default bittorrent client oooops too slow

---

### Post by nitro_n2o on 2007-07-04
do this it'll simplify your life 

download the portable utorrent you don't to install anything 
get wine 

and right click the desktop and choose create launcher 

Type: Application 
Name: uTorrent 
Command: wine /home/<your account>/Desktop/utorrent.ext      (assuming that ur utorrent is in ur desktop) 

you can also add a photo and/or comment to describe what is this launcher for. 
I'm doing this and there are no problems at all

---

### Post by lbelloq on 2007-07-04
How's uTorrent performance? I mean, I installed Java+Azureus, and most of time Azureus can't fill up my 2 Mbps connection (it does in Windows).
Or maybe KTottent is a better option.

---

### Post by nitro_n2o on 2007-07-04
> **lbelloq said:**
> How's uTorrent performance? I mean, I installed Java+Azureus, and most of time Azureus can't fill up my 2 Mbps connection (it does in Windows).
Or maybe KTottent is a better option.

uTorrent is good!! I like it, and doesn't take up much memory

---

### Post by Speedoo on 2007-07-04
I was using utorrent with Windows before I switched to Linux.  Then I discovered Foxtorrent.  It seems to be a lot easier to use.  It's a Firefox extension that automatically starts your torrent downloads and continues downloading even if you leave the site or close Firefox.  Seems like a good deal to me....

---

### Post by lbelloq on 2007-07-04
But can actually use all the bandwidth? Might sound overkill, but my DSL connection is almost exclusively dedicated to torrenting anime.

---

### Post by davidjmayo on 2007-07-04
lbelloq

> But can actually use all the bandwidth? Might sound overkill, but my DSL connection is almost exclusively dedicated to torrenting anime.

how healthy are the torrents you're downloading?
Try any *buntu torrent with hundreds of seeds and one or 2 peers and it will go at max even in Azureus on ubuntu (I tried azureus before but found it slow on most torrents)

---

### Post by SpikeyMike on 2007-07-04
Hi
I am not sure why the output is covered in smiles, thats just the way it came out when I pasted the output in here :(

I am new to Ubuntu so I thought I needed to run as root to install software, is that not the case?

I tried going to applications add/remove but I couldnt find utorrent there either, not sure what has happened to it, I know it installed because it started after the installation.........

Spikey


> **davidjmayo said:**
> What's going on here??

The link you include goes to a page with no text but the url is the same (maybe the page has been deleted?)

The error output is covered in smilies (why?)

Why are you running as root?

To answer your last question I don't know why utorrent isn't working but I had problems with wine. You had it working I didn't (couldn't get a number to work in the listen port)

Bittorrent is installed as part of the standard installation so that's why it's there (you're right you didn't install it--sort of)

I use ktorrent which looks similar to utorrent but doesn't need wine. To install it 

applications==>add/remove
it's under internet. Click the box to select it, apply and it will download and install

If you use firefox you can change the default bittorrent client

EDIT
 oooops too slow

---

### Post by coolen on 2007-07-04
> **SpikeyMike said:**
> Hi
I am not sure why the output is covered in smiles, thats just the way it came out when I pasted the output in here :(

The server automatically replaces any occurance of colon-D with :D. You were just unfortunate.

> **SpikeyMike said:**
> I am new to Ubuntu so I thought I needed to run as root to install software, is that not the case?

Most of the time, yes, you should be root. Using the package manager requires it. Wine, however, maintains a per-user fake C directory. You'll have your own little fake C, and your siblings will have their own, etc. This directory is located at ~/.wine/drive_c by default.
So, installing software with Wine as root just dumps it in /root/.wine/drive_c, which is likely only readable by root.
You may be able to change the configuration (global...look in /etc) to put the fake c drive under a directory anyone can read/execute, then give root permissions to write.

> **SpikeyMike said:**
> I tried going to applications add/remove but I couldnt find utorrent there either, not sure what has happened to it, I know it installed because it started after the installation.........

Spikey

Add/Remove is software in the repositories, not installed software.
It's not added to your menu because Windows applications don't know where to put launchers (nor that they're running in a fake Windows environment. They're not even aware of directories outside of your fake Wine directories).
Right-click on Applications, and go Edit Menus. Add the launcher yourself to Internet (the command will probably be wine ~/.wine/drive_c/Program\ Files/utorrent, try it in a terminal first. Use Nautilus to find the correct file if it doesn't).
You can optionally go and find a nice icon for it, too.

---

### Post by lbelloq on 2007-07-05
> **davidjmayo said:**
> lbelloq



how healthy are the torrents you're downloading?
Try any *buntu torrent with hundreds of seeds and one or 2 peers and it will go at max even in Azureus on ubuntu (I tried azureus before but found it slow on most torrents)
Most of them are very healthy (6-10 hrs after the initial seeding, they get like 500 seeders and 800 peers, so I'd consider that healthy). But Deluge and the default client can't get more than 20 kB/s.

---

### Post by SpikeyMike on 2007-07-09
Ok, how would I change the config so it puts it in a different directory? I found uTorrent by using the sudo nautilus command in terminal and then opening the root directory, I found uTorrent in a folder there. I tried adding it to the applications menu so I could start it from there but when I try to start it it says 'Could not launch menu item, failed to execute child process(permission denied)' :(

Also sorry for my lack of knowledge here but what is the difference betweeen software in the repositories and installed software?

Spikey

> **coolen said:**
> The server automatically replaces any occurance of colon-D with :D. You were just unfortunate.

Most of the time, yes, you should be root. Using the package manager requires it. Wine, however, maintains a per-user fake C directory. You'll have your own little fake C, and your siblings will have their own, etc. This directory is located at ~/.wine/drive_c by default.
So, installing software with Wine as root just dumps it in /root/.wine/drive_c, which is likely only readable by root.
You may be able to change the configuration (global...look in /etc) to put the fake c drive under a directory anyone can read/execute, then give root permissions to write.

Add/Remove is software in the repositories, not installed software.
It's not added to your menu because Windows applications don't know where to put launchers (nor that they're running in a fake Windows environment. They're not even aware of directories outside of your fake Wine directories).

Right-click on Applications, and go Edit Menus. Add the launcher yourself to Internet (the command will probably be wine ~/.wine/drive_c/Program\ Files/utorrent, try it in a terminal first. Use Nautilus to find the correct file if it doesn't).
You can optionally go and find a nice icon for it, too.

---

