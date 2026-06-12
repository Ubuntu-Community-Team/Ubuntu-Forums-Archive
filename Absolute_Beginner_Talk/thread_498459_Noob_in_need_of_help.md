---
title: "Noob in need of help"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by absurdity on 2007-07-11
Alright so I literally just downloaded Ubuntu today and I still have pretty much no idea what I'm doing. I want to install Shockwave Flash but I have no idea. On the website it says:
 >    1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Step #4 is when I run into problems, I have no idea how to navigate to the directory so basically can someone please give me step by step directions on how to get this plugin installed. 

Helpful answers are greatly appreciated. ;)

---

### Post by Espreon on 2007-07-11
Are you trying to gain the ability to play Flash Vids on sites like YouTube if so, go to YouTube and when it says there are missing plugins click the Install Missing Plugins button, simple as that!

---

### Post by hackle577 on 2007-07-11
To navigate to the directory, the terminal command should be:

```
cd /home/username/Desktop/install_flash_player_9_linux
```

Go there and then type:  

```
./flashplayer-installer
```

That should work. Espreon's method will work too. Plus, it's easier!

---

### Post by dpar on 2007-07-11
Also, the plugins are available in synaptic.

---

### Post by pyros on 2007-07-11
I'd personally recomend installing it from the repositories. That way it will update with the rest of the system. for a good guide on doing this check [here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox).

---

### Post by hackle577 on 2007-07-11
@absurdity: OK, forget my way of doing. All these other ways are better.

@pyros: Installing it from within Firefox would update it when FF updates, right?

---

### Post by rickycodie on 2007-07-11
or you could automatix, i've never had problems with it.

---

### Post by hackle577 on 2007-07-11
So many choices! If Linux were a politician, it would be a libertarian.

---

### Post by pyros on 2007-07-11
I Don't think it updates through firefox, no.
As far as Automatix, I've never understood the appeal. You get so much more when you do it the "right" way.

---

### Post by cdgeorge1 on 2007-07-11
I am also new to this and would definately like shockwave to run on Ubuntu Feisty!!

This is because my daughter plays Disneys 'Virtual Magic Kingdom' ([www.vmk.com](www.vmk.com)) - and this only works with shockwave.

I am sure I read somewhere that I cannot use shockwave unless I download a copy of Firefox for Windows and run this using Wine on Ubuntu - it's the only way to make shockwave work!!

Can you confirm that I do not have to do this after all, and it's simply a package I can download? If so, that would be great!

---

### Post by absurdity on 2007-07-11
> **hackle577 said:**
> To navigate to the directory, the terminal command should be:

```
cd /home/username/Desktop/install_flash_player_9_linux
```

Go there and then type:  

```
./flashplayer-installer
```

That should work. Espreon's method will work too. Plus, it's easier!

Alright I figured out what I was doing wrong(I stupidly just copy'd and pasted without changing it to my username.
But now when I type in ```
./flashplayer-installer
``` it gives me an error that says: > ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


Does this mean that I need to install a different one like .rpm or YUM instead of .tar.gz?

---

### Post by krazyenglishman on 2007-07-11
1. Go to System > Administration > Synaptic Package Manager
2. Search for Flash
3. After Search is complete Scroll down the list and Tick the box next to flashplugin-nonfree
4. Click Mark for Installation
5. Hit Apply.
6. Wait for it to finish downloading, and installing by itself.
7. Restart Firefox and you now have Flash Installed.

Thats the easy way, no terminals or codes to remember.

---

### Post by absurdity on 2007-07-11
> **krazyenglishman said:**
> 1. Go to System > Administration > Synaptic Package Manager
2. Search for Flash
3. After Search is complete Scroll down the list and Tick the box next to flashplugin-nonfree
4. Click Mark for Installation
5. Hit Apply.
6. Wait for it to finish downloading, and installing by itself.
7. Restart Firefox and you now have Flash Installed.

Thats the easy way, no terminals or codes to remember.

When I open up Synaptic Package Manager, i get  an error message: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E : _cache->open() failed, please report.

---

### Post by pyros on 2007-07-11
> **cdgeorge1 said:**
> I am also new to this and would definately like shockwave to run on Ubuntu Feisty!!

This is because my daughter plays Disneys 'Virtual Magic Kingdom' ([www.vmk.com](www.vmk.com)) - and this only works with shockwave.

I am sure I read somewhere that I cannot use shockwave unless I download a copy of Firefox for Windows and run this using Wine on Ubuntu - it's the only way to make shockwave work!!

Can you confirm that I do not have to do this after all, and it's simply a package I can download? If so, that would be great!

Sadly no. there has never been a version of shockwave built to run on linux.

To fix the dpkg error, go to Applications>Accessories>Terminal and when the terminal opens, type
```

sudo dpkg --configure -a

```

As a side note, are you running the 64 bit ubuntu?

---

### Post by absurdity on 2007-07-11
Yeah.

---

### Post by pyros on 2007-07-11
> **absurdity said:**
> Yeah.

ok, that would explain some problems... there is not, at the moment a 64 bit version of flash. HOWEVER, there is a fix for it, take a look at the link I posted earlier (or just go [here](http://ubuntuforums.org/showthread.php?t=202537)) for further instructions.

---

