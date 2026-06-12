---
title: "silly question about ubuntu"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by natman on 2005-10-03
hi i have just set up ubuntu on my system and want to use a GUI interface for LaTeX, anyway i asked this question in here before and got the following reponce

in a terminal type "sudo apt-get install tetex-extra kile".

if you prefer a GUI approach, you can achieve this by starting system->administration->synaptic, search for tetex, mark tetex-base, tetex-bin and tetex-extra, search for kile, mark that too, then install them all.

then use kile to edit instead of winedt.

So what do i do to get the GUI approach, please i need a paint by numbers explaination if possible, do i open a terminal or what?

Thanks - sorry if i am trying the patience of the forum

---

### Post by Ampersand on 2005-10-03
You should have three menus on the top bar of the desktop, saying 'Applications', 'Places' and 'System'. (If you don't have this, right click on the bar, go to 'add to panel, and add a menu bar.)

Click on 'System', then 'Administration'. You should see 'Synaptic Package Manager' in the menu that appears. Click on it and type your password when prompted.

When Synaptic opens, click the 'Status' button at the bottom, then 'All' from the menu on the left. You can then scroll though the programs listed until you get to the programs you need (or use the search button at the top).

---

### Post by natman on 2005-10-03
hi, yeah i dont have any tabs at the top saying 'places' or 'systems' so i did as you said and right clicked, and went to add panel but there was no opion to get places or system, can anyone help?

---

### Post by darkmatter on 2005-10-03
[QUOTE=natman]hi, yeah i dont have any tabs at the top saying 'places' or 'systems' so i did as you said and right clicked, and went to add panel but there was no opion to get places or system, can anyone help?[/QUOTE]

Running KDE? (do you have a 'K' for a 'start' button?)

If you do, then in the Menu, go to System ->kynaptic. Just search for the packages you were originally told to find, select them for installation and hit apply.

Just let them install and you should have everything you need.

---

### Post by natman on 2005-10-03
hi, i am not running KDE but i found the synaptic package manager thing anyway (i was just a bit slow)
Anyway i was told to install the tetex among other things, there is no tetex in the list, can anyone help me get a GUI for kile LaTeX
Thanks:

---

### Post by darkmatter on 2005-10-03
[QUOTE=natman]hi, i am not running KDE but i found the synaptic package manager thing anyway (i was just a bit slow)
Anyway i was told to install the tetex among other things, there is no tetex in the list, can anyone help me get a GUI for kile LaTeX
Thanks:[/QUOTE]

Just use the search button in the toolbar.

If you search for 'tetex', you should find several packages. It's faster and more likely that you'll find anything you'll ever need using the search function.

As for kile. it is a GUI for LaTeX (it is a LaTeX text editor for KDE, but will run in GNOME). Using the same method listed above, search for 'kile'

Hope that helps.

---

### Post by natman on 2005-10-03
I tried to search for kile and tetext, and did not find find anything, am i doing something wrong or am i missing some component?

---

### Post by Mustard on 2005-10-03
I found 'kile' in synaptic, through typing kile in the search function, but I couldn't find 'tetext' either, if that helps. :)

I'm not sure whether you need to add any extra repositories to find 'tetext'.

---

### Post by natman on 2005-10-03
did you find kile by just tying it in search in synmptic window?

---

### Post by darkmatter on 2005-10-03
[QUOTE=natman]I tried to search for kile and tetext, and did not find find anything, am i doing something wrong or am i missing some component?[/QUOTE]

Post the contents of /etc/apt/sources.list

---

### Post by Mustard on 2005-10-03
[QUOTE=natman]did you find kile by just tying it in search in synmptic window?[/QUOTE]
Yep...I'm wondering what repositories you have enabled in your synaptic package manager.

The easy way is to go to your menu in synaptic and choose *settings > repositories*, and seeing if there are any more repositories you can add.

If you feel like opening up a terminal and typing..

```
sudo gedit /etc/apt/sources.list
```

and then copy and pasting the contents of that file into the forum using the [noparse]```
 .... 
```[/noparse] format, it might be helpful, as it shows the complete list of repositories you currently have available.

---

### Post by natman on 2005-10-03
in responce to posting that command "/etc/apt/sources.list"

I opened a terminal typed it and got premission denided
I added sudo and was asked for password, at that point the cursor would no longer respond to keybord input, ie i pressed numbers and letters on keybord an nothing came up on the terminal

---

### Post by darkmatter on 2005-10-03
[QUOTE=natman]in responce to posting that command "/etc/apt/sources.list"
I opened a terminal typed it and got premission denided
I added sudo and was asked for password, at that point the cursor would no longer respond to keybord input, ie i pressed numbers and letters on keybord an nothing came up on the terminal[/QUOTE]

The terminal won't display what you are typing for your password, not even a '*'.
Don't fret, the shell is still registering the input. Just type the password and hit enter.

You can also use nautilus to navigate to /etc/apt and right click sources.list as a normal user and select 'open with text editor'. This will open the file read-only in gedit. Then just use the edit menu to select all, then copy the contents to your post.

---

### Post by Mustard on 2005-10-03
The password is hidden when you type it.  You need to type in your **user password** too, not the root password.

---

### Post by natman on 2005-10-03
yeah typed in 
"sudo gedit /etc/apt/sources.list" and got the following

deb cdrom [Ubuntu 4.10 Warthy Warthog - Preview 1386
 Binary - 1 (20041020)]/unstable main restriced

## Uncomment the ... (next two lines)
#deb [http://archive.....com](http://archive.....com)  warthy main resticted
#deb-src http://      "          

##Uncomment
##repostry
##NB software from the repository is ENTIRELY SUPPORTED by Ubuntu
## you software rights to use the software,ALso pls note that the software is........

---

### Post by Mustard on 2005-10-03
Hmmm...there is a lot missing from sources.list. :)

If you could enclose the listing of your source.list contents using the forum posting code [noparse]```
<insert your code here>
```[/noparse] it would be helpful, as its stops the forum from incorrectly formatting the output.

I'd try to get someone to post up their sources.list for Warty Warthog.
Mine is Hoary Hedgehog source.list unfortunatly and I'm not sure of the differences.

This is mine.

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

Yours should look fairly similar, but with 'warty' in place of 'hoary' in the URL's.

To be certain though, as I said earlier, you should get a copy of a sources.list from someone who is running Warty Warthog.

---

### Post by natman on 2005-10-03
I looked in settings_>repositories, and only one was checked, should i just check the rest and see what happens?

---

### Post by Mustard on 2005-10-03
[QUOTE=natman]I looked in settings_>repositories, and only one was checked, should i just check the rest and see what happens?[/QUOTE]

Yeah..thats an excellent idea.  When you do that, it will update your sources.list with the new entries.  Hopefully things will start to work properly then.

If not, then you will need to search around on the forums for a warty warthog sources.list and use

```
sudo gedit /etc/apt/sources.list
```

..to edit the sources list.  Copy and paste a good copy of the sources.list into gedit and save.

---

### Post by NeoSNightmarE on 2005-10-03
Most likely you didn't add the extra repository to the distro. That would be my bet at least.

---

### Post by natman on 2005-10-03
i will try it tmrw mustard i shall be on again about an hour before this, its now 1 am for me - really tired i just got linux about 5 hrs ago.

anyway thanks for the help, i might start a new thread tmrw also with an approiate name
Thanks again - everone here is so nice

---

### Post by Mustard on 2005-10-03
Ok, natman.  Take care and good luck. :)

---

