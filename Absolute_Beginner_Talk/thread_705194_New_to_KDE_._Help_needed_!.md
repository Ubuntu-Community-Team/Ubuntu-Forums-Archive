---
title: "New to KDE . Help needed !"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2008-02-23
Hi all
I had been using gnome since 3 years , Now I loved some KDE desktop screenshot so I thought of shifting to KDE>. Please help me in customizing KDE..and solving some of my problem .. Is there any customization guide for KDE ..I am currently using KDE 3.5.7 in Kubuntu gutsy :) Please help me..

I am getting this error after I close Dolphin Window

```
Unable to save bookmarks in /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.
```


Which is the default icon format ? .tar.gz is not getting installed From Appearance -> Icon themes.. It says file format not valid ? Also there is no .~ folders in home/user name ? How to install Compiz Fusion in KDE 7.10 ? I mean terminal command I can do that via Adept cause terminal commands are much easier 

Is there anything like **gtweakui** ? Also from where to set preferred applications ? How to change Icon of K menu .. There are lots of gr8 Main Menu mod in kde-look hot to install it ?

---

### Post by FrozenFox on 2008-02-23
> **Dark Star said:**
> Hi all
I had been using gnome since 3 years , Now I loved some KDE desktop screenshot so I thought of shifting to KDE>. Please help me in customizing KDE..and solving some of my problem .. Is there any customization guide for KDE ..I am currently using KDE 3.5.7 in Kubuntu gutsy :) Please help me..

I am getting this error after I close Dolphin Window

```
Unable to save bookmarks in /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.
```


Which is the default icon format ? .tar.gz is not getting installed From Appearance -> Icon themes.. It says file format not valid ? Also there is no .~ folders in home/user name ? How to install Compiz Fusion in KDE 7.10 ? I mean terminal command I can do that via Adept cause terminal commands are much easier 

Is there anything like **gtweakui** ? Also from where to set preferred applications ? How to change Icon of K menu .. There are lots of gr8 Main Menu mod in kde-look hot to install it ?

You can probably fix your problem by sudo chown shashwat::shashwat /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml  and/or sudo chmod 777 /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml

The default icon theme format is .tar.gz, but not all of them are packaged properly to work in kde. Gnome icon sets of course are not done so. You can manually install them, but I don't know how off the top of my head, but I know it is not difficult, you just need to put it in the right folder and change 1 file setting. Personally I always download the .deb for nuvox or look for correctly functioning icon sets ;)

As for compiz fusion, you install it the same way you normally would.. open up synaptic, or in the terminal sudo apt-get install compiz-core (i believe thats the pkg name anyway). If you are using hardy on the machine in question despite your title to the right there, install fusion-icon too and put a shortcut/link to that in /home/yourname/.kde/Autoshare so that it auto-starts when kde does. If you are not using hardy, you might want to take a visit to the "Linux Stuff" (not linux sweetness at the left) tab at the top of my home page ([http://frozenfox.freehostia.com](http://frozenfox.freehostia.com)), and under the .debs section you can find the .deb for fusion-icon that works fine in gutsy.

I dont know about tweakui stuff, because kde lays out most of its stuff in front of you, particularly in kcontrol.

In konqueror, you can unhide dotted folders via view-->show hidden files.

For preferred apps, load kcontrol, and look under kde components --> file associations.

Most of the menus you see are from kbfx. Install kbfx from the terminal or your favorite means, and add it as an applet to your start menu bar (kicker). I personally prefer the Tasty Menu / Mint Menu.

---

### Post by Dark Star on 2008-02-23
Also suggest me some appliccations for daily use :) How to install Styles and all /?

---

### Post by Dark Star on 2008-02-23
> **FrozenFox said:**
> You can probably fix your problem by sudo chown shashwat::shashwat /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml  and/or sudo chmod 777 /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml

The default icon theme format is .tar.gz, but not all of them are packaged properly to work in kde. Gnome icon sets of course are not done so. You can manually install them, but I don't know how off the top of my head, but I know it is not difficult, you just need to put it in the right folder and change 1 file setting. Personally I always download the .deb for nuvox or look for correctly functioning icon sets ;)

As for compiz fusion, you install it the same way you normally would.. open up synaptic, or in the terminal sudo apt-get install compiz-core (i believe thats the pkg name anyway). If you are using hardy, install fusion-icon too and put a shortcut/link to that in /home/yourname/.kde/Autoshare so that it auto-starts when kde does.

I dont know about tweakui stuff, because kde lays out most of its stuff in front of you, particularly in kcontrol.

For preferred apps, load kcontrol, and look under kde components --> file associations.

Most of the menus you see are from kbfx. Install kbfx from the terminal or your favorite means, and add it as an applet to your start menu bar (kicker). I personally prefer the Tasty Menu / Mint Menu.

I am using Kubuntu and I can't find File Association any where.. Buudy please be a bit clear next time I am new to KDE... Also where is the ~./icons , and other ~./xyz folders located  ? How to install themes manually ? Please suggest some must have applications for KDE ;):lolflag:

I figured how to Compiz via terminal ```
sudo aptitude install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
```

---

### Post by FrozenFox on 2008-02-23
[http://www.kde-look.org](http://www.kde-look.org)

Load kcontrol in the console if you can't find it in the start menu anywhere.

Generally, full "themes" are a pain to install and are few and far between. Themes include the whole shebang, icon stuff, font stuff, wallpaper, color scheme, and widget style.

 "styles" are usually pretty easy to install and there's an easy to install .deb for kubuntu. If you want to install a "style", just follow the installation instructions given on the page where you found it (or install the deb, or even look in the repositories to find it. most peoples' favorite styles are qtcurve or domino. I think both of those can be installed from the repositories. In the console, aptitude search qtcurve  or aptitude search domino and install which one you want via sudo apt-get install blahblah). Styles are the shape of all of the window widgets, and style of them, and even color. It includes how they are drawn, animation, and all sorts of stuff. It's easier to understand when you try it out and look.

"color schemes" are just that-- the way the system colors windows, and nothing else about it. You can just import these from the color schemes section of kcontrol, you download them from kde-look or make them yourself from that section of kcontrol.

"Decorations" are just like in gnome, window decorations you can choose from -- titlebar, border, stuff about the titlebar or border. Installation instructions are, like styles, most easily found from where you downloaded the file: the author's instructions.

Please go back and read my last message again, I edited it a little bit for clarity and extra information.

Did you install kde from a ubuntu install or from the kubuntu cd? You should see the stuff i described in kcontrol..

As for suggested applications, everyone has different favorites, you'll have to look around and see what you like. I personally like kooldock (the version in the repositories is old, however. i think i have a new deb on my site), kpdf, vlc, ktorrent, kftpgrabber, and most of the stuff that comes with kubuntu.

---

### Post by Dark Star on 2008-02-23
I get this error ```
shashwat@shashwat-desktop:~$ sudo chown shashwat::shashwat /home/shashwat/.kde/share/apps/d3lphin/bookmarks.x ml and/or sudo chmod 777 /home/shashwat/.kde/share/apps/d3lphin/bookmarks.x ml
chown: `shashwat::shashwat': invalid group
shashwat@shashwat-desktop:~$    
```

While executing the command you gave me.. Domino is not available in the repos. :(

---

### Post by FrozenFox on 2008-02-23
Apologies.

Please, in the terminal, try this:

sudo chown shashwat /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml

then run dolphin and see if you still have the same problem. If you do, run this in the terminal

sudo chmod 777 /home/shashwat/.kde/share/apps/d3lphin/bookmarks.xml

As for domino, let me see if I can find a .deb.

EDIT: You can find a .deb here.

[http://www.kde-look.org/content/show.php/Domino+Deb+package+for+Kubuntu?content=74031](http://www.kde-look.org/content/show.php/Domino+Deb+package+for+Kubuntu?content=74031)

EDIT 2: Err, I'm not sure why it keeps adding a space between the m and l in .xml at the end of the commands I give you, but make sure they aren't there when you try those commands.

---

### Post by Dark Star on 2008-02-23
Thanks for the help.. It worked. yep the probem was the space b/w x and ml :p . Just a question .Is this theme problem is only with Kubuntu or with KDE .. I mean no manual installation ? How to change the icon of KDE main menu :p The crystal project icon theme get installed but this 1 is not getting installed [http://kde-look.org/content/show.php/Crystal+Diamond+Icons?content=45576](http://kde-look.org/content/show.php/Crystal+Diamond+Icons?content=45576) I guess the problem is improper compilation :(

---

### Post by FrozenFox on 2008-02-23
Edit: Just noticed your own post, so take this response lightly as a response to your post pre-edited.

I'm not sure what you mean by theme problem. The fact that in general, entire "themes" -- packages including wallpaper, icons, fonts, styles, and color scheme combined -- are not available is simply because they are so much work to make and few people have enough similar stuff to put together in a coherent theme and instead choose to split it into small parts, not because it is difficult to install. To the contrary, as long as you have the correct style installed, installing a theme is as simple as importing the downloaded file from kcontrol.

Color schemes are quite easily installed by importing downloaded ones or making them on your own within kcontrol. Most of the time, styles are a piece of cake to install and often include a .deb for simple double click installation if it's not in the repositories. Most styles you find are spinoffs of qtcurve or domino that can be installed from within the qtcurve/domino settings menu under kcontrol.

65%+ of icon themes on kde-look work fine from importing them from kcontrol. The reason that so many -don't- work is because the authors of the icon packs did not make them work with kde, -not- the other way around. I have no idea why many of the authors don't package it for kde, or at least make an alternative package as such, because from what I've heard it isn't very difficult.

---

### Post by Dark Star on 2008-02-23
I got this error while doing cut past from desktop to my NTFS partition ```
Could not change permissions for
/media/sda5/KDE_Crystal_Diamond_2.7_Kubuntu_Mod.tar.gz
```

and sorry for that EDIT thing :p 

Edit: And as far as themes I was referring to installation of Visuals and Icon theme.. Like in Gnome its very easy to install but in kubuntu specially its pretty irritating ..

---

### Post by FrozenFox on 2008-02-23
I would agree that sometimes it's irritating, but it's (mostly) no fault of kde's or kubuntu's, but the fault of those releasing content not making it comform to the kde system's theme import specs -- which afaik haven't changed for some time. The nice thing about kde's themes over gnome though is that they're much more able to be fine-tuned and comform to your system, instead of say, a pre-defined look a'la windows or gnome. It's hard to describe what I mean adequately unless you've thoroughly used all three.

As for that error, I have no idea. My only guess is that you do not have write access to your drive partition in question. Please open the terminal and type cat /etc/fstab and show me what it says. Also, please type whereis ntfs-3g in the terminal and report back what it says.

---

### Post by Dark Star on 2008-02-23
Nopes it is still showing the error I even installed ntfs-config but it is not getting started :||

---

### Post by FrozenFox on 2008-02-23
Ack. I'm really not sure what to do though I still suspect a write/hd permission issue, but it would probably be helpful to you to make a new post with a title something along the lines of "NTFS cannot change permissions" and describe the problem. You may as well output the results of cat /etc/fstab there too to see if that helps. If noone responds to this thread, I'd suggest marking this one as solved and making that new thread accordingly, because not many 'experts' are likely to go to a thread with a title asking for generic KDE help :)

Good night, good luck, welcome to KDE :)

---

### Post by Dark Star on 2008-02-23
^^ Just one more my fonts in Firefox has increased for some other site. .I did CTrl + Mouse Wheel but it didn't helped :"(

---

### Post by Dark Star on 2008-02-23
> **Dark Star said:**
> ^^ Just one more my fonts in Firefox has increased for some other site. .I did CTrl + Mouse Wheel but it didn't helped :"(
Bumpo :| How to install KBFX also. how to change The KDE logo of Main Menu ?

How to make my desktop icon look like this ? I can not those icons anywhere ? [http://kde-look.org/content/show.php/Gutsy+Kubuntu?content=71513](http://kde-look.org/content/show.php/Gutsy+Kubuntu?content=71513)

---

