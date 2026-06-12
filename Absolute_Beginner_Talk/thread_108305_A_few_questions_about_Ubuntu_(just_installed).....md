---
title: "A few questions about Ubuntu (just installed)...."
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by Zeno50 on 2005-12-25
Hi, I just installed Ubuntu on my laptop Acer Aspire 2020 series (centrino).

Everything is working great.  The wireless internet started working without any configuration, gaim, firefox, and open office all run flawlessly I just have a few n00bie questions about using Ubuntu in general.

1.  At my login screen it says I'm using Edubuntu, I installed it off the bittorrent DVD version of Ubuntu so I'm not sure why it's calling itself Edubuntu.

2.  I have the Synaptic and the package manager figured out for the most part except I'm still a bit confused on how to install (non Synaptic) things in Linux.  For example, I downloaded Firefox 1.5 to the desktop and extracted it, but could not figure out how to "install" it.

3.  I've seen some screenshots where people are using customized themes and their desktop looks very different from default Gnome and KDE.  What is the best way to get some of these themes?

4.  I also noticed there are a variety of music playing programs.  I was wondering what is the most popular and if there is one that rips, plays, makes playlists, etc.

5.  Also, what is the best way to accustom myself to the command line.  I havn't used it yet and was wondering if there are any guides that summarize common tasks it is used for, etc.

Thank you in advance!

---

### Post by stimpack on 2005-12-25
1. Can only think you downloaded the Edubuntu torrent, no biggie you just have some extra rpograms installed.

2. Extract to /home/Zeno50/firefox or whatever and create a shortcut to the firefox program thats it!. If you want it usable by all users its a bit more involved [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29) is the recommended way.

3. kde-look.org for all your theming needs.

4. Amarok is the best by far. People may suggest other things for other needs, for for pure power and all the things you want... Amarok!

5. Not read it but [http://www.linuxcommand.org/](http://www.linuxcommand.org/) has been linked a few times.

---

### Post by Rinzwind on 2005-12-25
1. Dunno. 
2. Firefox is rather easy: [http://www.ubuntuforums.org/showthread.php?t=79283&highlight=firefox](http://www.ubuntuforums.org/showthread.php?t=79283&highlight=firefox)
But when it comes to other stuff you need to replack the files so they are set to be used in Debian/Ubuntu. There's a programm called 'alien'. You need to install it 1st tho. 
3. if you use Gnome install gnome-art. It lets you load, view and install themes etc from the web so you do not need to go to a website yourself. Websites: [www.kde-look.org](www.kde-look.org) is a good one for kde themes. 
4. Well I use k3b, amarok, xine, vlc and xmms (<- looks like winamp) and all have their good things. Amarok is VERY complete: info on albums like lyrics and shows covers and you can use mysql to make a local database of your colletion.
In general: install them and see for yourself is the best advice we/anyone can give you.
5. Trial and error.... Best bet is to learn a few of the basic commands.
With **sudo kwrite {file}** under kde and **sudo gedit {filename}** under gnome you can open en edit tekstfiles/configuration files.
Oh and all commands can be viewed with the **man** command. **man mv** shows the manual for the move command. 
There are some webpages with all the commands listed. That might be a bit of a start: [http://www.google.nl/search?hl=nl&hs=0iJ&client=firefox-a&rls=org.mozilla:en-US:official_s&q=linux+commands&spell=1](http://www.google.nl/search?hl=nl&hs=0iJ&client=firefox-a&rls=org.mozilla:en-US:official_s&q=linux+commands&spell=1)

Also:
Do bookmark **[www.ubuntuguide.org](www.ubuntuguide.org)** It's got alot about installing packages and the corresponding commands.

---

### Post by Zeno50 on 2005-12-25
Ok, one question about the themes.  I ventured to kde-look.org and also installed gnome-art.  (I was switching back and forth between kde and gnome).

I can't find gnome art.  How do you access an installed package if it's not in any of the menus?

Also, if you download a theme from kde look how do you install and apply it?


Thanks for your help!

---

### Post by anil_robo on 2005-12-26
Gnome art is seen in the System-->Preferences-->Gnome Art menu. (I guess you're using GNOME, not KDE).
Whatever theme you want to install, just download it to your desktop, and drag and drop it in the theme selector (System--> Preferences--> Theme). Then select your newly installed theme, and you can also configure various options there.

---

### Post by Zeno50 on 2005-12-26
Ok, I'm using KDE now.  I was switching between the two and decided that I like KDE better.

1.  I installed Automatix which I think installs a good chunk of packages except I can't really find them.  I guess this comes to a more general question of how do you know what is installed if it isn't in any of the shortcut menus?  Adept also tells me that Firefox is installed though it is not listed under the internet applications.

2.  I have the Acqua KDE theme downloaded to my home folder.  How do I apply this theme or add it to the built in theme manger?

Thank you!

---

