---
title: "package installation"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Caitilin on 2007-08-28
Hi

I've installed a few packages using synaptic package manager. None appeared in my menu's. I went through the similar questions listed here and didn't find an answer that I appeared to be able to apply yet. I restarted linux (yes i'm from a windows background, why do you ask? *grin*) 

I've found them in the \usr\share\doc directory, but there only appear to be text files and no executables. in the usr\bin directory i found a python script, but double clicking that only gives me the source code. 

is there something i missed? How do I get this into my menu? I'm sorry for asking what seems an obvious question!

---

### Post by oilchangeguy on 2007-08-28
what version of ubuntu are you using?

---

### Post by Caitilin on 2007-08-28
Feisty Fawn.

---

### Post by Mornedhel on 2007-08-28
What packages exactly have you installed ? Only apps will add their shortcut to the menu. Libraries, for instance, will never do that.

/usr/share/doc is where the documentation will be placed, so no wonder you only get text files there. Python scripts always are source code (OK, so not always, but almost), but you as a base user should never have to execute directly anything from there.

---

### Post by s26c.sayan on 2007-08-28
What are the packages which you want to see in the start menu??

---

### Post by Caitilin on 2007-08-28
bittorrent and an astronomy program - i'm an amateur stargazer and there is an eclipse tonight.

---

### Post by Mornedhel on 2007-08-28
OK. If you installed the 'bittorrent' package, it only provides command-line utilities as torrent support comes in another GNOME application (gnome-btdownload). So there is no reason it would show up in the menu. Torrent support comes out of the box in Feisty, I believe. Just double-click a .torrent file.

As for your astronomy package, some older packages (or maybe because of lazy packagers) do not add a menu entry. There is always a console command though. If you give us the exact name of the package you installed, we may find the corresponding command. Try opening a console and typing the first few letters of the package's name, then hitting TAB.

---

### Post by Caitilin on 2007-08-28
ok, so how can i find torrents then if its a command prompt? 

Sorry if i'm appearing dense - I'd like to get the hang of this!

---

### Post by Mornedhel on 2007-08-28
Don't worry, most of the time people don't get what I say because English is not my first language, not because they're dense (though that may have been the case several times...).

What do you mean by "finding torrents" ? I usually download the .torrent file wherever I have to, save it to my home directory, then double-click it. I rarely have more than one torrent open at the same time (most of the time I have none, in fact). Azureus is available in the reps if you need a heavy GUI (be warned : it's really heavy stuff, resource-wise). If I need to torrent from a distant box, I use rtorrent (much much lighter, but ugly as only an ncurses interface can get).

The bittorrent utilities seem to all have aliases starting with 'bt' . Just type bt and hit TAB at a console, it'll show you a list of what starts with bt and is executable. It doesn't seem to be meant for the casual user though.

---

### Post by Caitilin on 2007-08-28
its not my first language either - i'm dutch. 

ok, let me restate the problem as maybe I am going wrong there. 

I understood bittorrent was a client to download p2p files (torrents) with, and that if  you had a dodgy connection (as I have) then it could join up or restart them without having to redownload the entire package. (at 350 mb for a Who ep, that gets tedeious!) 

That is what I'm looking for - something that can download files, basically, on a p2p sharing network.

---

### Post by Mornedhel on 2007-08-28
OK, that's correct. I think you're confusing the .torrent files and the actual content being downloaded, though. What you have to do is download a tracker (DrWho_season18episode42.torrent) from a specialized site, then open (double-click) the file. This opens gnome-btdownload which is the BitTorrent client shipped with Ubuntu (or you can get it from the gnome-btdownload package anyway). This will start the download (after prompting for a location where the Dr Who episode will be saved).

What of your astronomical problems ? Did you manage to start the application ?

---

### Post by Caitilin on 2007-08-28
Ok, so a tracker is to a download what a pointer to a memory address? Right, then all i need to do is find the trackers...I take it its not like kazaa where i can just double click?

Astronomy package is not being particularly helpful. 

i've got it installed, according ot it. In the diretory i have a cgi script, a changelog, a copy right text file with no useful information, 2 readme files with propaganda but no useful info, a perl script that hwen opens gives me the script in gedit, and an update and a readme that do the same. I suspect i need to run one of these, but can't figure out how. 

LOL, changing OS, sometimes fun, always a challenge!"

---

### Post by Mornedhel on 2007-08-28
That's correct for the torrent part.

I have until now never heard of a package providing an application but no command to run it. If there really is none, try running 'perl <name of the Perl script here>' when you are in that directory.

But there really should be a command.

What is the name of that package again ?

---

### Post by Caitilin on 2007-08-28
Cool! thanks re the torrents. 
the package is  astrolog  
I dont' know much about it bar it was mentioned on a news site together with stellarium (which did work just fine on download). 

trying hte perl option tells me there is no such file (its still zipped by the look of it) Unzipping tells me i don't have those rights.

---

### Post by Mornedhel on 2007-08-28
OK, I installed astrolog, just for you, and 'cause I don't feel sleepy yet.

Turns out astrolog does, after all, create its own command. At a console, just type 'astrolog'. It's a text-based program, so it wouldn't create a shortcut in the main menu.

Since you installed it with Synaptic, it should work. (It does for me.)

---

### Post by Caitilin on 2007-08-28
bloody hell, it works! it actually works! 


You rock! Have I mentioned that? If not - let me do it again, you rock! 

*does a happy dance*

---

### Post by mysticmatrix on 2007-08-28
> **Caitilin said:**
> Cool! thanks re the torrents. 
the package is  astrolog  
I dont' know much about it bar it was mentioned on a news site together with stellarium (which did work just fine on download). 

trying hte perl option tells me there is no such file (its still zipped by the look of it) Unzipping tells me i don't have those rights.

Well little bit off the topic, but I would suggest you to use Add/Remove unless you want to install a really obscure package/software not present there. It has a nice interface, categorizes various applications and also tell after installation that whether you have a menu option or not.

Also, happy to find a astronomy enthusiast here. Today is a lunar eclipse, but not visible in my part of world :(

---

### Post by Mornedhel on 2007-08-28
You're welcome !

(Now that mysticmatrix mentions it, the lunar eclipse is not visible at all in the Eastern hemisphere, is it ?)

---

### Post by Caitilin on 2007-08-28
add/remove point duly noted and thank you. 

No, the eclipse isn't visible here, at least not via our own skies (wich, being in dublin, is lovely and cloudy too) but I'd hoped it might be on one of the astronomy sites or programs to watch.

---

