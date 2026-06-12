---
title: "Brand new--Lots of questions"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by klemperal on 2007-09-09
I have only been using ubuntu Edgy for a couple of days now with no prior experience in Linux.  That being siad I have a ton of questions, but I'll narrow it down so you don't feel like your reading a book.

1.  Is there a program that will play multiple VTS files (VOB, IFO, BUP etc)?  Mplayer and movie player seem to only want to play singular files.  I need something like media player classic which hasn't worked for me through wine.

2.  How do I make a specific folder not hidden?

3.  How do I change specific icons?

4.   Can I get more theme packages?

5.  Is there a good DVD burner for linux?  Preferably one that can book type DVD+Rs.

6. Where and how do I download the above--what are some good sites for packages?

---

### Post by lisati on 2007-09-09
4 - check out the "Add/Remove appications" option of the Applications menu. For other applications you might want to visit [http://www.linux.org/apps/](http://www.linux.org/apps/)

EDIT: There are other themes around but the relevant url eludes my memory at the moment

5 - If you're into making your own DVDs, check out DeVeDe. You might have to use it to create an ISO file and then use Ubuntu's default "burn ISO" option.

---

### Post by Dr Small on 2007-09-09
1.  [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
2. Remove the . in front of the folder.
3. Right click on a folder, select properties, then click on the icon.
4. [http://gnome-look.org](http://gnome-look.org)
5. gnome-baker, or in other terms, right click on a file, or Places > CD / DVD Creator
6. You can use Synaptic to find packages, or [http://getdeb.net](http://getdeb.net) for Debians.

Dr Small

---

### Post by aktiwers on 2007-09-09
Hi and Welcome!

1) I think VLC player can do that!
Open up Terminal (Applications =>Accessories => Terminal)  and type:
```
sudo apt-get install vlc
```

Or go to Synaptic and search for "VLC player" without the quotes.
(System => Administration => Synaptic package manager)

2) Press CTRL + H to view Hidden folders, and to make them not hidden, rename them so they dont have an "." infront of there name. Alle hidden files/folders are named with a ".".

3) Right-click on the file and pick Properties. Then click the icon in the new Window.

4) Yes, have a look at Gnome-look:
[http://gnome-look.org/](http://gnome-look.org/)

Download whatever theme you like and go to:
System => Preferences => Theme
And drag/drop the file you downloaded in there.

5) Again open up Synaptic and search for:
"Burn DVD" without the quotes.

I like brasero, but there are lots of others, so you might want to take a look yourself. Nero is also available for Linux.

6) Must programms can be found in Synaptic Package Manager. To add more sources look here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Good luck! And again Welcome! :)

---

### Post by Aishiko on 2007-09-09
go to applications and chosse to download a multi-media palyer, I am partial to the Kaffeine that I configured to work (keyuboardish) like mcplayer, and I have VLC as a back up for any files Kaffeine won't play or play right (which is only a few) then I downloaded the 3 multi-media codec packages listed here
> **aquavitae said:**
> You can usually change all the keyboard shortcuts from the settings menu of any app.  

The problem with kaffeine is that codecs aren't installed.  Go to [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") for instructions on how to install them.
If you're using KDE, this might be more useful: [http://kubuntuguide.org/Feisty#Multimedia_Codecs_Installation]("http://kubuntuguide.org/Feisty#Multimedia_Codecs_Installation")

I personally find that the best is to use different apps for movies and music - kaffeine for movies and amarok for music.  I just set the keyboard shortcuts to be the same on both.

Hope this helps!
 yes this is the same post I got when I was looking for a media player like mcplayer. 
Just follow the directions and you should be golden at that point.  Oh and near there is a codec called libdvdcss2 or something like that you'll want that for DVD play back.

unhiding hidden folders even slect ones is doable by deleteing hte "." in front of the file/dirctery name however doing so can really break your system and IS NOT RECOMMENDED they are hidden for a reason, and changing their names can break depenacnies and links so.  DO NOT DO IT!  

Themes? be more specific are you refering to things like Gnome and KDE? or something else?

kb3 is, I'm told a decent cd/dvd burner.

Packages you should get thru Synaptc, they are known to be Ubuntu ready and won't break your system plus they auto add shortcuts to the menus.  

I suggest you read the FAQ, and do a search on the Repostiries, (which is what synaptc and commands like apt-get (terminal) go to for the apps.

---

