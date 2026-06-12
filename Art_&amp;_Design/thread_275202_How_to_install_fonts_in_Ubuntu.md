---
title: "How to install fonts in Ubuntu?"
date: 2006-10-11
forum: Art &amp; Design
---

### Post by Aleksandersen on 2006-10-11
Hi,

I have a .ttf font file here and I am wondering how I install it into the system?

---

### Post by mssever on 2006-10-11
This is one of the best-kept secrets in Ubuntu. Open up Nautilus, hit Ctrl+L, and type fonts://<Enter>.

It's possible that you'll need a root nautilus for this: ```
gksudo nautilus
```

---

### Post by Aleksandersen on 2006-10-11
Well, I cannot seam to be able to copy the font over! Not even as root.

---

### Post by eg-maverick on 2006-10-11
when I do this, it looks like it is going to copy (I have a server that has thousands of TTF). it asks for a password and a window pops up saying that it is preparing to copy. Then when I enter the password, the windows disappear happily but the font does not appear in the font directory. Any ideas?
Thanks.

---

### Post by mssever on 2006-10-11
I wrote a script a while back that installs fonts. Save the script somewhere in your $PATH and make it executable. Type ```
sudo mkdir -p /usr/share/fonts/truetype/font-install
```  Then, cd to the directory that the fonts you want to install are in, run the script from a terminal window, and follow the prompts. Remember that Linux is case-sensitive, so if some files have a ttf extension and some hava a TTF extension, you'll either need to rename them or run the script twice.

```
#!/bin/bash
#
# This script helps to install fonts
#
# Set your default font storage directory here
##DEFAULT_DIR="$HOME/fonts"
DEFAULT_DIR=`pwd`
# Set the default font installation directory here
DEFAULT_DEST="/usr/share/fonts/truetype/font-install"


# Don't edit anything below unless you know what you're doing.

echo "In which directory are the fonts?"
echo -n "[$DEFAULT_DIR] "
read DIR

echo
echo "What is the extention (without the dot) of the fonts?"
echo -n "[ttf] "
read EXT

echo
echo "Where should the fonts be installed?"
echo "DO NOT CHANGE THIS UNLESS YOU KNOW WHAT YOU'RE DOING!"
echo -n "[$DEFAULT_DEST] "
read DEST

if [ -z "$DIR" ]; then
    DIR="$DEFAULT_DIR"
fi

if [ -z "$EXT" ]; then
    EXT="ttf"
fi

if [ -z "$DEST" ]; then
    DEST="$DEFAULT_DEST"
fi

sudo -v
if [ $? != 0 ]; then
    echo "Unable to obtain the necessary privileges. Exiting..."
    echo -n "Press <Enter> to continue. "
    read WER
    exit $?
fi

echo
echo

if [ ! -d "$DIR" ]; then
    echo "Directory $DIR does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read SDF
    exit 2
fi

if [ ! -d "$DEST" ]; then
    echo "Directory $DEST does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read DFG
    exit 1
fi

echo "Copying fonts..."
cd "$DIR"

for i in *."$EXT"; do
    sudo cp -iv "$i" "$DEST"
done

echo
echo
echo "Updating the font cache..."
sudo fc-cache -fv

if [ $? != 0 ]; then
    echo "Error updating the font cache. Your fonts haven't been completely installed. Try running sudo fc-cache -fv manually. Exiting..."
    echo -n "Press <Enter> to continue."
    read FSF
    exit $?
fi

echo
echo
echo "Finished."
echo
echo "You will probably need to restart running programs to use the new fonts."
echo -n "Press <Enter> to exit. "
read WERT
exit 0
```

---

### Post by eg-maverick on 2006-10-11
thanks for the script. 
before i do damage to myself, what is the correct DEFAULT_DIR? I have standard dapper 6.06. I assume it is /home/'myusrname'/fonts . Is that correct?
thanks, Craig

---

### Post by eg-maverick on 2006-10-11
That did it! Thanks so much!

---

### Post by mssever on 2006-10-11
> **eg-maverick said:**
> thanks for the script. 
before i do damage to myself, what is the correct DEFAULT_DIR? I have standard dapper 6.06. I assume it is /home/'myusrname'/fonts . Is that correct?
thanks, Craig

This script is set up for Dapper. $DEFAULT_DIR can be anything you want. It defaults to the current directory. So, if you cd to the directory containing the fonts you want to install and run the script, everything should be OK.

$DEFAULT_DEST is the only distro-specific location. Technically, it can be any directory inside /usr/share/fonts/truetype (or it might be even more flexible--I haven't tried that), but I think that it's neater to put locally-installed fonts in a directory of their own.

---

### Post by emiphiste on 2006-10-12
I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)

---

### Post by eg-maverick on 2006-10-12
> **emiphiste said:**
> I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)


I wonder if using Nautilus would work for item 4. then you wouldn't have to type everyting out.

---

### Post by mssever on 2006-10-12
> **emiphiste said:**
> I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)

My script works fine for me in Dapper but I have no idea about Dapper. It's likely, though. I first made the script for Red Hat, and when I switched to Dapper, I had to modify it extensively.

I didn't know about the .fonts directory. You don't even have to run fc-cache? Cool.

The beauty of the command line is that you don't have to type all of that stuff all the time. Use wildcards. For example, lets say that you have your fonts in a directory called fonts. You could do something like ```
cp fonts/* .fonts
``` or ```
cp fonts/*.ttf fonts/*.TTF .fonts
``` or even ```
mv fonts .fonts
``` If you had 5,000 fonts (too many to fit on a single command line, do something like ```
for i in fonts/*.ttf fonts/*.TTF; do cp "$i" .fonts; done
```You could also do this from Nautilus, although if you take the time to learn the command line, you'll find that it's usually much faster and easier than using Nautilus (unless you need image thumbnails or something).

---

### Post by mssever on 2006-10-12
> **emiphiste said:**
> (By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)

Are there any error messages? What happens if you start up another program (such as OpenOffice)? You usually have to re-start programs for font changes to take effect. You could even log out and back in, although that shouldn't be necessary. If you can give me some information to work with, I'd be happy to help tweak the script.

---

### Post by SuperJETT on 2006-10-16
I did the .fonts directory approach, just copied fonts in there and they are installed, nothing else to do. 

Works nice.

---

### Post by Aleksandersen on 2006-10-17
When you drag fonts to the fonts:// directory the appear in the ~/.fonts/ directory only. It is kind of odd that you don't get any notification or indication that the font has been installed when you drag them to fonts://

---

### Post by mssever on 2006-10-17
Font installation is definitely an area that needs to be improved in Ubuntu. I don't know if this is fixed in Edgy. I hope so.

---

### Post by neil095 on 2006-10-24
Or you could just read the system help and just copy the font to /usr/share/fonts/ :D

---

### Post by mssever on 2006-10-24
> **neil095 said:**
> Or you could just read the system help and just copy the font to /usr/share/fonts/ :D
You also have to run ```
sudo fc-cache -fv
``` to cause the system to notice the changes. Hence my comment about this needing to be easier. In the ideal system, you should be able to accomplish any system task via either the command line or a graphical interface. sudo fc-cache -fv is hardly a GUI.

---

### Post by eg-maverick on 2006-10-25
> **mssever said:**
> You also have to run ```
sudo fc-cache -fv
``` to cause the system to notice the changes. Hence my comment about this needing to be easier. In the ideal system, you should be able to accomplish any system task via either the command line or a graphical interface. sudo fc-cache -fv is hardly a GUI.

Ah Ha!!! That's what I was missing! (of course how would I know?). I agree, it needs to be easier. 
Thanks for this though.

Craig

---

### Post by yellow beard on 2006-10-26
Awesome script. Cheers.

---

### Post by florizs on 2006-10-30
I know of the font installing problem, It would be real sweet if there was an option in the gnome-font-viewer (gfontview) that asked if you'd like to install the font.
Or would it be better as an option in nautilus?

I believe we should ask the gnome-desktop developers about it.

---

### Post by Billy Pilgrim on 2006-11-11
Thanks to all who contributed on this one.  I thought of using the wild card:

cp fonts/*.ttf fonts/*.TTF .fonts

but learned something on the command:

sudo fc-cache -fv

---

### Post by JeevesBond on 2006-12-10
Thanks to this thread I've been able to get a newly installed font working. Thanks for the help, especially the sudo fc-cache -fv bit ;)

---

### Post by deadly_paddooo on 2006-12-16
I have been looking around for some time on how to install fonts in ubuntu (edgy).

This post offers a good way, I looked at the script which is awesome...
Also the .fonts way as well.

So what I infer is that the easiest way is to copy the fonts to some directory over /usr/share/fonts or to the .fonts in the home dir.

However, I know there is a way to make you own directory somewhere like /usr/local/fonts/ttf/
and change the configuration in the config file for X server to look for that. I cannot find the config file, though I tried adding that dir in the xorg.config file and restarting, which apparently did not work. I read about chkfontpath doing that for us, but I could not find source or copy for chkfontpath.

Any ideas on how to do the above?

Thanks

---

### Post by John Fury on 2007-01-02
Why can't anything be simple with Linux. Like drag and drop. I'm trying to get this Elder Scrolls Daedric font and I am a noob and I don't know how to use nautilis.

---

### Post by handylinux on 2007-01-05
If anyone's still wondering about this, I found a page that seems to supply the necessary info: [**FontInstallHowto**]("https://help.ubuntu.com/community/FontInstallHowto").

---

### Post by gurnemanz on 2007-01-08
I can tell this is going to be a whole lotta fun once I get the major things up and running.

I notice the fonts references all seem to be to TrueType fonts. I'm not too crazy about TT. Does anyone use Type 1 fonts in Ubuntu?

BTW, a Pure Noob questions - do I want to load Mac fonts or PC fonts? Or is there a repository of purely Linux fonts?

Yes, this is how little I know about 'nix and 'nux. I'm here to remedy my ignorance, and your (plural and singular) help is a great gift. Thank you all.

g.   :-k

---

### Post by NULL712 on 2007-01-19
I'm pretty new to Linux but the way I installed my fonts was to hit (alt-F2) and then type in (gksudo nautilus) and hit enter then type your password go to file system then usr and then shared then fonts. it worked out fine for me. A proud user of ubuntu 6.10 edgy

---

### Post by Unterseeboot_234 on 2007-01-22
Fonts are a beast unto themselves. You can have copy of a bad font and another copy as a good, working font and both will have the same name. Me? I would encourage you to use a font management program like fonty python. Putting 2,000 fonts inside the files system won't help anything. In fact, having a bunch of fonts inside the system can use up RAM that doesn't need to always be tied up. fonty lets you categorize your fonts into folders that make sense to you, ie Christmas, Party, Customer1, etc.

[**fonty python**]("http://wiki.wxpython.org/index.cgi/FontyPython")
the limitation is fonty works only with TrueType.

> BTW, a Pure Noob questions - do I want to load Mac fonts or PC fonts? Or is there a repository of purely Linux fonts?

Mac files have that "fork" for file types. There is a forum discussion about extracting the font data portion of that fork. I've used PC versions of most of my TrueType fonts. Here is a HowTo:
[URL="http://www.ubuntuforums.org/showthread.php?t=314837"]
**Mac to Linux Fonts HowTo**[/URL]

As far as Type1 Fonts, I dunno. Type1 seems to be fading, I'm looking forward to the OpenType standard. Use something like FontForge to convert the fonts to the file formats you want.

---

### Post by gurnemanz on 2007-01-23
[QUOTE=Unterseeboot_234;2048071]Fonts are a beast unto themselves. <<SNIP!>>Here is a HowTo:
[URL="http://www.ubuntuforums.org/showthread.php?t=314837"]
**Mac to Linux Fonts HowTo**[/URL]/QUOTE]

Danke sehr! Es hilft mir sehr viel!

I can't offer you 7k Mac fonts, but I do have a fairly healthy collection I might well convert.

g.

---

### Post by projjalc on 2007-04-27
> **mssever said:**
> This is one of the best-kept secrets in Ubuntu. Open up Nautilus, hit Ctrl+L, and type fonts://<Enter>.

It's possible that you'll need a root nautilus for this: ```
gksudo nautilus
```

This seemed to work perfectly for me. Thanks.

---

### Post by Nightwalker07 on 2007-09-18
> **emiphiste said:**
> I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)Thanks for that! I preferred this method best.

---

### Post by tchslemur on 2007-10-05
> **mssever said:**
> You also have to run ```
sudo fc-cache -fv
``` to cause the system to notice the changes. Hence my comment about this needing to be easier. In the ideal system, you should be able to accomplish any system task via either the command line or a graphical interface. sudo fc-cache -fv is hardly a GUI.

this is probley the only time i will get to say this but this is where windows is somewhat better unless it freezes when you install the font lol:lolflag:

is there anyway that we can make a patch so you can just copy the fonts to /usr/shared/fonts and it will automatically recognize them cause then it would just be awesome lol

---

### Post by suchawato on 2007-10-18
I have a moral problem with this.
This is linux.
Not windows or Mac os.
If I am logged in as root, I should be able to do whatever I like, damaging or not.
That's the whole point of having lesser user accounts. 
If I want to cut and paste my entire file system to gibberish; I should be able to do that. This is not the first time I have run across this type of problem in Ubuntu.
The first was early on as a new user, when I wanted to log in as root in the first place. I found it was disabled, and had to find out how to un-disable it.
This is just damn annoying though. why doesnt cut and paste features work outside of the "home" folder???
It's MY damn computer!!! If I want to F*ck it up, That's my right!!! I shouldn't have the OS telling me what I can and can't do with it!
Especially not as Root.
Is there any way to disable this "feature" so that I can just cut and paste files?

---

### Post by Nightwalker07 on 2007-10-18
I agree to a certain extent, I dont like how by default ubuntu dosent allow you to live as a root acess account, but there are ways around it.

I think this might help:
```
sudo su
```This will log you into a session as root.

Then run:
```
passwd
```Change your root password at will.

Then go to:
System > Administration > Login Window

click the 'Security' tab and then tick 'Allow local system administrator login'. You may now login as root perminatly. I dont do this myself, but im sure thats a working method for it. Hope that helps.

---

### Post by suchawato on 2007-10-20
Thanks for that.
I don't log in as root often, but when I do, it's nice to have any easy way in , so that I don't have to waste unnessicary time.
I do understand that it is in my best security interests to not use root for regular use. It is nice to be able to quickly be as root if I need to change some settings or edit a paricular file for instance. Thanks for the help.

---

### Post by suchawato on 2007-10-20
By the way, I don't know if anybody accurately answered the OP.
But to install fonts in Ubuntu 7.4-7.10 (I cannot speak for previous versions) 

do the following:

* Log in as Root.

* Copy the fonts you want to install using the"copy"  command.

* Paste them into /user/share/fonts/(the appropreate folder, for instance truetype fonts will go in the 'truetype' folder)

* That's it.
Fonts added here will now be avalable system wide incl. openoffice and gimp.

* Log out as root, and log back in as your regular user.

---

### Post by smartboyathome on 2007-10-20
You can also install fonts by (putting them in or creating and putting them in) your ~/.fonts folder.

---

### Post by jupetsu on 2007-10-20
What I do is I go to Appearance -> Fonts -> Details -> Go to Fonts Folder

..then just paste my *.ttf files there. It's really easy and it works for me.:)

---

### Post by cchevy on 2007-11-09
I wanted to install some fonts from windows and i got my folder for install. quickly i figured that there was no way of installing them easy, so i read around and did this:

Alt-F2 to open the run dialog

**fonts://**
> 
The window that opens allows you to copy and paste new font files to install them.

as mentioned in [http://tombuntu.com/index.php/2007/10/15/how-to-install-fonts-in-ubuntu/](http://tombuntu.com/index.php/2007/10/15/how-to-install-fonts-in-ubuntu/)

and i did this and my pc froze. there weren't many fonts. i restarted and got nothing but wallpaper and NO menu. empty ubuntu...

please tell me i can fix this? why is it so hard to install new fonts?

can anybody tip me how to fix my system and install fonts ?

i am writing this post from xp and this is really embarrassing :(

---

### Post by mssever on 2007-11-09
> **cchevy said:**
> I wanted to install some fonts from windows and i got my folder for install. quickly i figured that there was no way of installing them easy, so i read around and did this:

Alt-F2 to open the run dialog

**fonts://**


as mentioned in [http://tombuntu.com/index.php/2007/10/15/how-to-install-fonts-in-ubuntu/](http://tombuntu.com/index.php/2007/10/15/how-to-install-fonts-in-ubuntu/)

and i did this and my pc froze. there weren't many fonts. i restarted and got nothing but wallpaper and NO menu. empty ubuntu...

please tell me i can fix this? why is it so hard to install new fonts?

can anybody tip me how to fix my system and install fonts ?

i am writing this post from xp and this is really embarrassing :(
Your problem with Gnome starting can't be related to installing fonts except that something apparently crashed at a bad time. What actually froze? Nautilus? Total system lockups are extremely rare, although the system might appear to be locked up if you don't know how to troubleshoot it.

First, try rebooting again. If that doesn't fix it, then you need to determine just what's crashing. At the login screen, hit F10 and select first the failsafe Gnome session to see if that works. If not, launch the failsafe terminal session.

Try starting gnome from the command line: ```
gnome-session &
```Post any errors you see. If that doesn't start things up properly (I'm guessing it won't), then log out again and return to the failsafe terminal. Now, run the following commands one at a time, noting any error messages: ```
gnome-settings-daemon &
gnome-panel &
nautilus &
```If something crashes, then you know that it's the culprit. If nothing does, then the culprit is probably one of your startup programs--but failsafe Gnome should have detected that already.


In addition to installing fonts the way you tried, you can also put them in ~/.fonts or create a directory for them under /usr/share/fonts/truetype and put them there. After either of these methods, you need to run ```
sudo fc-cache -fv
``` to tell the system about your changes.

---

### Post by cchevy on 2007-11-09
i just went in and deleted the fonts i installed 

that worked and i got my pc working

after a while...

i tried this: sudo fc-cache -fv right after i opened nautilus, made a myfonts folder in the truetypefonts and copied all my fonts.

/usr/share/fonts....

but the result was the same, so i had to  remove them manually from root, for the ubuntu to work again.

is there any other way except nautilus for fonts to be installed?

this is obviously not working for me

p.s. i tried at a friends place on fresh 7.10, it did the same crash....no menu, only wallpaper

---

### Post by mssever on 2007-11-10
> **cchevy said:**
> i just went in and deleted the fonts i installed 

that worked and i got my pc working

after a while...

i tried this: sudo fc-cache -fv right after i opened nautilus, made a myfonts folder in the truetypefonts and copied all my fonts.

/usr/share/fonts....

but the result was the same, so i had to  remove them manually from root, for the ubuntu to work again.

is there any other way except nautilus for fonts to be installed?

this is obviously not working for me

p.s. i tried at a friends place on fresh 7.10, it did the same crash....no menu, only wallpaper
It sounds like your fonts may be buggy--or at least some Gnome component doesn't like them. I don't really know how to solve that problem, but clearly there's a bug somewhere. If you can determine what's crashing, file a bug report on launchpad.net.

---

### Post by digitalis_vulgaris on 2007-11-12
I use links to have control over fonts on my system. I have fonts on my backup partition and in ~/.fonts put only link to the folder with fonts. This is also handy if you have windows and linux on same computer, and want to use windows fonts on linux.

You can create link with:
ln -s *destination** link_name*

To apply changes use:
fc-cache -f -v

---

### Post by cchevy on 2007-11-12
> **digitalis_vulgaris said:**
> I use links to have control over fonts on my system. I have fonts on my backup partition and in ~/.fonts put only link to the folder with fonts. This is also handy if you have windows and linux on same computer, and want to use windows fonts on linux.

You can create link with:
ln -s *destination** link_name*

To apply changes use:
fc-cache -f -v

can somebody please explain better this procedure of using fonts with a link?

i have xp on the disk, so i think it might work...

10x in advance

---

### Post by digitalis_vulgaris on 2007-11-12
1. For my metod you use terminal. Go in  folder ~/.fonts using cd command:
cd /home/name_of_your_folder/.fonts

2. Than create link to the folder with fonts:
ln -s destination link_name

Info:
destination is address of destination folder (/media/hdb1/Windows/Fonts)
link_name is some name (link_XP_fonts)

When Linux refresh font cache he will follow this link

3. Refresh font cache:
fc-cache -f -v

! never refresh font cache with sudo command because then Linux search for /home/root/.fonts instead for your personal .fonts

---

### Post by cchevy on 2007-11-12
thanks man, but i've tried all of this and it went fine, but no fonts showing in my apps (ooffice, abiword)

must be some nasty bug, i did almost everything to get this to work

---

### Post by apogee on 2007-11-13
Has anyone heard of or tried FontyPython?

A friend of mine wrote a python gui (front-end font-manager, for point-'n-click ppl like me)  that shows what fonts you have in your collection but are not installed. You can create "groups" (called "pogs") of fonts for a particular job, add selected fonts to a pog, install the pog and un-install the pog. The gui shows which fonts are installed and available and which pogs are installed and which aren't.

If Googling doesn't reveal the location of the newest version. The version I use is here:
[http://www.apogee.co.za/fontypython-0.2.0.tar.gz]("http://www.apogee.co.za/fontypython-0.2.0.tar.gz")
Read the readme for install and usage.

---

### Post by fedex1993 on 2007-11-17
is there like a crazy or cool font packages out there like microsoft core font package i know there is another one out there also where do yall get custom fonts at?(sorry for my texas acent)

---

### Post by apogee on 2007-11-19
> **fedex1993 said:**
> is there like a crazy or cool font packages out there like microsoft core font package i know there is another one out there also where do yall get custom fonts at?(sorry for my texas acent)
[http://www.dafont.com/](http://www.dafont.com/)
Check the licences for eh font. Some are free for peronal use, some are free for all uses etc.

---

### Post by injoy on 2007-11-22
> **jupetsu said:**
> What I do is I go to Appearance -> Fonts -> Details -> Go to Fonts Folder

..then just paste my *.ttf files there. It's really easy and it works for me.:)That worked for me, too!  Thanks!  :)

---

### Post by cchevy on 2007-11-23
> **injoy said:**
> That worked for me, too!  Thanks!  :)

OK...I did this...but now,  I am officially with no OS. It has happen all over again...I have no menu.

I placed the fonts as mentioned above...and now I need somebody's help to get them out of there manually in terminal(but only the ttf fonts).

Can somebody tell me where to look for this folder? 

**fonts:/// **?


Waiting for an answer (desperately)

---

### Post by Caro_CR on 2007-11-23
I cannot help you about that. I want to explain How you can do it without using terminal

Well if you want to do it the easy way... its very simple

For Feisty:
System>Preferences>Fonts>Details> and then you choose to go to the fonts file and paste the font there

(I use Ubuntu in spanish so the names may be different but I guess you'll manage)

in Gutsy:

system>preferences>appearance>fonts

---

### Post by wheezer on 2007-11-25
Yet one more thing I have to learn, just to get my work done.

Is there any kind of font manager to reduce this to a 2 minute exercise? I just want to manage my fonts, no spend an hour learning how to install them one at a time.

---

### Post by aeklabunde on 2007-11-25
> **cchevy said:**
> 

Can somebody tell me where to look for this folder? 

**fonts:/// **?


/var/lib/defoma/gs.d/dirs/fonts   ...This is where the font folder in system>preferences>appearence>fonts exists.

I pasted my fonts into the alphabetical folders in /var/lib/defoma/fontconfig.d because that's where Open Office seems to get them from, and that worked for me.  I used the sudo nautilus command to open root privilege file browsers (for adding and deleting fonts) since I don't speak "command line", or Klingon for that matter.

---

### Post by Wehrmacht on 2008-03-19
Wow... i'm about to gouge out one of my own eyes!

I open terminal.. sudo nautilus and ctl L to font page... this method will not allow me to copy the 4 fonts to the folder.

I navigate folder by folder down into the directory.. it will allow me to copy paste them into there this way... great... wait NO!

Although they are present, still not able to use the fonts.

What am I doing wrong here?  

Gutsy.  :confused:

---

### Post by AJB2K3 on 2008-03-19
Try the **Home\user\ .fonts** folder instead. Far easer.

Check the link in my sig \/\/---\/\/

---

### Post by Wehrmacht on 2008-03-19
Wow... ok that did it for me, thanks for the response sir!

strange how one terminal method will work, but another didn't, and all the GUI methods didn't work for me.

copying into the home/usr/fonts/ directory did it!

---

### Post by Cauda_Draconis on 2008-03-21
Yeah. A font manager would be spectacular. That's one of the biggest things I miss about KDE.

---

### Post by smartboyathome on 2008-03-21
There was a font manager before Nautilus's backend was remade. If you are on Gutsy, you can type fonts:/// to get a font manager.

---

### Post by nithin933 on 2008-03-30
Instead of copying every font one by one just type cp *.ttf /home/username/.Fonts (provided your current working directory is where you copied your fonts

---

### Post by smartboyathome on 2008-03-30
Make sure fonts is lowercase, or it won't work.

---

### Post by komputes on 2008-04-05
I just discovered kfontview, amazing little piece of free software, allows you to preview the fonts and then decide whether you want them installed locally or system wide. You can get it through add/remove.

Edit: kfontview is now part of the kdebase-workspace-bin package and is no longer in the repositories as its own package.

---

### Post by ogami on 2008-04-05
nevermind

---

### Post by Ghuloomo on 2008-05-30
You can just copy your ttf fonts to your home/user/.fonts (if .fonts doesnt exist, creat it), then open ur gimp and u'll see the fonts. If not go to your gimp preferences , folders, and in the fonts section browse for that .fonts directory and add it.
restart gimp, have fun

---

### Post by ekricyote on 2008-06-08
Looks like fonts:/// feature in nautilus was removed in Hardy.

Back to the old terminal way I guess...

---

### Post by ironhorse2008 on 2008-08-09
I got myanmar fonts in Ubuntu 8.04.

    * Open your home folder in Nautilus (GNOME) or Konqueror (KDE).
    * Since dot-folders are really hidden folders, you need to choose "Show Hidden Files" from the View menu.
    * Go to File -> Create Folder (GNOME), or right-click and choose Create New -> Folder (KDE).
    * Name the new folder " .fonts ".(be careful for dot before fonts)

Now double click on the folder to open it, and drag and drop your fonts into the folder. Restart computer again and then I got it. :)

---

### Post by Nanish on 2008-08-18
You don't need to restart, just update the font cache with 
sudo fc-cache -f -v

---

### Post by honkey on 2008-09-09
Can I remove the system fonts or are there problems after i removed
Can I get the system fonts anywhere after?

---

### Post by ktworks on 2008-09-09
Do you guys have any short and easy method so that a new bie can also take help from it.I am also having these kind of problems ...

---

### Post by mssever on 2008-09-09
> **honkey said:**
> Can I remove the system fonts or are there problems after i removed
Can I get the system fonts anywhere after?
There are a number of font packages installed. Fire up Synaptic and search for them. You can probably safely remove most of them. Just pay attention to what else might be removed as a consequence.
> **ktworks said:**
> Do you guys have any short and easy method so that a new bie can also take help from it.I am also having these kind of problems ...

[LIST=1]
[*]Make a directory for your fonts in /usr/share/fonts/truetype: ```
sudo mkdir -p /usr/share/fonts/truetype/my_fonts
```
[*]Copy your fonts to that directory:```
sudo cp /your/fonts/here /usr/share/fonts/truetype/my_fonts
```
[*]Run fc-cache:```
sudo fc-cache -fv
```
[*]Your fonts probably won't show up in your application until you restart it.
[/LIST]

---

### Post by tulen on 2008-09-10
just adding for microsoft font

> 
$ sudo apt-get install msttcorefonts


---

### Post by barratt_sab on 2008-09-11
One thing I have discovered - if you copy the font files as root (i.e. sudo cp or sudo nautilus and drag and drop) then the new font files have root as the owner and no access for anyone else.  When you then sudo fc-cache to update the font cache, everything works fine, because fc-cache is running as root.  However, when you then start an application (Gimp or OO, for example) as a normal user the new fonts are either found but not displayed (Gimp) or not found at all (OO).

The solution is to change the permissions on the new font files to make them world readable (you can sudo nautilus, navigate to the font directory select all, right-click properties and set the permissions).

---

### Post by Pro-reason on 2008-09-11
I had a terrible time installing fonts a few weeks back.

I thought I'd done it all right, but the system kept on screwing up with fonts failing to display.

I eventually realised that I just needed to do *sudo chmod +r* on them all.

---

### Post by IanW on 2008-09-11
I use a nautilus script I got at [Gnome Look](http://gnome-look.org/content/show.php/TTF+Font+Manager?content=82473)

---

### Post by skyttan on 2008-09-16
Thank you mssever! :D
This helped me installing the Calibri font!

---

### Post by mitchpc on 2008-09-16
After I changed themes back and forth in the "Preferecnes>Appearance
And in one instant I clicked "apply fonts" button that appeared, which made my fonts too big, So I went to fonts tab and decreased to 50 dpi. and everthing seem to go back to normal. but when I opened applications like Skype, Audacity K3b , terminal, etc,, their font sizes went to something like 9 points (instead of 18 points default for everything else). Applications like synaptic is in normal size as well as firefox.
I was able to fix skype with "q4 settings". And I even did the dpk-reconfig fonts, but nothing is changing.
Thank you.

---

### Post by stinger30au on 2008-09-16
this may interest you

[http://ubuntuforums.org/showthread.php?t=869626](http://ubuntuforums.org/showthread.php?t=869626)

---

### Post by mitchpc on 2008-09-16
I need to reset all my font sizes in Hardy ubuntu 8.4 LTS.
After a theme change some applications went to 9 points size.

---

### Post by dangermouse28 on 2008-09-17
There's 2 easy ways to install fonts.

1.  Create a new folder in your home folder called .fonts
    (the . will hide it from normal view)
    Copy all your .ttf fonts in here.
    Open a terminal and do:
    $ fc-cache -fv

    And that's it!

2.  Install Fontmatrix - a font manager for Linux. It lets you
    preview the fonts on your system and then install or remove
    as you like. The UI isn't fantastic but if you need help, PM
    me and I'll try!

---

### Post by Club17 on 2008-10-24
Well, I'm beginner.

But only want to report if you copy (as root) your TTF's to: /usr/share/fonts/truetype will be appear in GIMP & OpenOffice without refresh the cache in Ubuntu Hardy 8.04.1

Cheers.

---

### Post by AJB2K3 on 2008-10-25
> **Club17 said:**
> Well, I'm beginner.

But only want to report if you copy (as root) your TTF's to: /usr/share/fonts/truetype will be appear in GIMP & OpenOffice without refresh the cache in Ubuntu Hardy 8.04.1

Cheers.
If you copy them to the .fonts folder in your home directory it should also work without messing around.

---

### Post by Osborn on 2008-10-25
The easiest way to install fonts is to open your user folder (home).
Then press **view** and show hidden folders.
Now there will be alot folders named with a dot in the beginning.

Go to the folder **.fonts**
If you don't have the folder, just create it.
In this folder you can put your fonts. And when you are done, just close the window. Sometime it may require a restart before you start using the fonts.

---

### Post by zippytex on 2008-11-13
[COLOR="Black"][SIZE="4"][/SIZE][/COLOR]

Thanks!  Command line worked great and I don't even know what I am doing!!!:)

---

### Post by Kinetic_lord on 2008-11-28
I don't get it, why so complicated? I had to install KDE with Dolphin just to install some fonts on my computer. Once you select a font in dophin, on he right side of the screen a "install font" option appears. Well... smart people made it.

---

### Post by smartboyathome on 2008-11-28
> **Kinetic_lord said:**
> I don't get it, why so complicated? I had to install KDE with Dolphin just to install some fonts on my computer. Once you select a font in dophin, on he right side of the screen a "install font" option appears. Well... smart people made it.

You don't *need* to do that, just copy your fonts to ~/.fonts. Nautilus was able to do this, but lost the feature when they switched to gvfs.

---

### Post by SimonJohnes on 2008-12-05
you can download fonts from a lot of websites (just google it) and then put the downloaded .ttf files into /usr/share/fonts/truetype
It so easy:

1: Open Applications / Accesories / Console
2: sudo cp Desktop/downld_fnts/*.ttf /usr/share/fonts/truetype
3: Ready

This way is quite easy!

---

### Post by rin67630 on 2008-12-06
> **suchawato said:**
> I have a moral problem with this.
It's MY damn computer!!! If I want to F*ck it up, That's my right!!! I shouldn't have the OS telling me what I can and can't do with it!
Especially not as Root.
Is there any way to disable this "feature" so that I can just cut and paste files?

> gksudo nautilus 

...is the magic formula to let you screw up YOUR damn computer ad libitum.

Enjoy!

RIN

---

### Post by ax-ax on 2008-12-20
I love that script

---

### Post by alex.rayu on 2008-12-22
> **Kinetic_lord said:**
> I don't get it, why so complicated? I had to install KDE with Dolphin just to install some fonts on my computer. Once you select a font in dophin, on he right side of the screen a "install font" option appears. Well... smart people made it.

Yes, KDE does have lots of smart things that Gnome does not. I can't see how such smartness would make Gnome worse. Once again, it does seem to me more and more that Gnome is running out of steam. I wish I were a c++ programmer and could help. Which I most regretfully am not.

---

### Post by uknowyalovmeh on 2008-12-30
ok i have never used ubuntu before now and none of what your saying makes any sense to me. I dont know how to find those like apt source things or use the command lines or make scripts? Does anyone know or knows a guide that explains this step by step and in great detail? I feel like a complete retard. :P
im trying to install fonts so I can make the pretty images w/ GIMP that I did with windows

---

### Post by henriquemaia on 2009-01-01
> **uknowyalovmeh said:**
> ok i have never used ubuntu before now and none of what your saying makes any sense to me. I dont know how to find those like apt source things or use the command lines or make scripts? Does anyone know or knows a guide that explains this step by step and in great detail? I feel like a complete retard. :P
im trying to install fonts so I can make the pretty images w/ GIMP that I did with windows

Go to [B]Places
[/B]select [B]Home Folder
[/B]right click on the window that opens and select **C**[B]reate Folder
[/B]write its name as [B].fonts
[/B]Click on it
Now drop all the folders you have with fonts to this **.fonts **folder. 
The new fonts are installed.

if the .fonts folder disappears (its a hidden folder because of the . before its name), just press ctrl+h on the Home Folder and you'll see all the hidden folders.  .fonts will be there.

---

### Post by AJB2K3 on 2009-01-02
> **henriquemaia said:**
> Go to [B]Places
[/B]select [B]Home Folder
[/B]right click on the window that opens and select **C**[B]reate Folder
[/B]write its name as [B].fonts
[/B]Click on it
Now drop all the folders you have with fonts to this **.fonts **folder. 
The new fonts are installed.

if the .fonts folder disappears (its a hidden folder because of the . before its name), just press ctrl+h on the Home Folder and you'll see all the hidden folders.  .fonts will be there.
Also you may find that you don't have a .fonts folder, in this case press
**Shift+Ctrl+N** and type **.fonts** . the **.** and **s** is required in the folder name

---

### Post by adamkane on 2009-01-18
If 
control+l 
fonts:// 
doesn't work, the next easiest way is:

cd ~
mkdir .fonts

Copy ttf fonts to ~/.fonts

Reboot.

---

### Post by Bachstelze on 2009-01-18
> **adamkane said:**
> 
Reboot.

No need to reboot.

Also, fonts copied in the personal fonts directory of a user will only be available to that user. To make them available system-wide, copy them somewhere under [font="monospace"]/usr/share/fonts[/font].

---

### Post by AJB2K3 on 2009-01-19
Ok as I'm resurching and writing I found out about the 
```
fonts:///
```
Method and found out that.
1 fonts:/// is the same as /home/username/.fonts (the clue is in the 3 "/"
2 When using this method fonts don't show up immediatly and sometime require you to shut down the file manager, reopen and revisit fonts:///.

However when I try I get ```
cannot access .fonts
```
 in user mode and

```
Cannot handle /home/username/fonts
```

Ok solved it, the command is 
```
.fonts///
```as root
If multiple users use the computer then fonts need to be installed to 
```
/usr/share/fonts/
```

---

### Post by stankopp on 2009-01-19
This (/home/.fonts) does not appear to work in 8.10 while it did in 8.04LT

---

### Post by AJB2K3 on 2009-01-20
> **stankopp said:**
> This (/home/.fonts) does not appear to work in 8.10 while it did in 8.04LT

What do you mean? the .fonts folder doesn't exist untill it is created.
the .fonts/// on the other had seams to now be an admin tast.

---

### Post by keyboardslave on 2009-03-07
Thanks mate,

Worked fine for me,

Open terminal:

Mkdir ~/.fonts

then copy your fonts into that folder.

then run in terminal:

fc-cache -f -v

---

### Post by nmvictor on 2009-03-11
Thanks mssever for that helpful script.Are you a programmer or something?It good you are using your skills to make other users lives easier.It nice being part of the ubuntu community.I really appreciate the help one gets in this forums.Thanks all.:D

---

### Post by dhldhldhl on 2009-03-12
if I hit ctrl+l and I type in fonts:// it says either: Could not display "fonts:///" (not root), or Could not find "/home/daniel/fonts:". (root), can anyone help me out here?

---

### Post by Merk42 on 2009-03-12
> **dhldhldhl said:**
> if I hit ctrl+l and I type in fonts:// it says either: Could not display "fonts:///" (not root), or Could not find "/home/daniel/fonts:". (root), can anyone help me out here?

Does /home/daniel/.fonts (note the .) exist? If not create it and put the fonts in there.

Why isn't there some font menu thing in Preferences? It could show a preview of the fonts and have a nice drag and drop UI to install fonts.  At the very least just have it link to either the user or root fonts folder.

---

### Post by AJB2K3 on 2009-03-13
For more information on Installing follow my guide.
[Installing fonts.]("http://www.geocities.com/ajb2k305/tutorials/font.html")

---

### Post by spottedhyena on 2009-03-19
On the Add/Remove menu - there is an app called Fonty Python
Or use sudo apt-get install fontypython

Works wonderfully - does the job for you...Displays all the fonts in a folder and let's you pick the ones you want...awesome little program and really easy to use - Fonts showed up in OpenOffice straight away...no problems so far.

Here is a website with more info:
[http://otherwise.relics.co.za/wiki/Software/FontyPython/](http://otherwise.relics.co.za/wiki/Software/FontyPython/)

---

### Post by Ben Crisford on 2009-03-21
In kubuntu it is really simple, and regardless whether you run it or not, this might be useful for kubuntu users so i'll post it anyway.

***System> Install Fonts> Then browse to the .ttf file and ur done***

---

### Post by Ticketoride on 2009-04-15
> **barratt_sab said:**
> **Post: #72** One thing I have discovered - if you copy the font files as root (i.e. sudo cp or sudo nautilus and drag and drop) then the new font files have root as the owner and no access for anyone else.  When you then sudo fc-cache to update the font cache, everything works fine, because fc-cache is running as root.  However, when you then start an application (Gimp or OO, for example) as a normal user the new fonts are either found but not displayed (Gimp) or not found at all (OO).

The solution is to change the permissions on the new font files to make them world readable (you can sudo nautilus, navigate to the font directory select all, right-click properties and set the permissions).
That's the Ticket ... Fonts now show in Open Office 3.x under Jaunty 9.04

I also followed every Font-Copy Procedure on this Thread, so I have a half a dozen Font Folders all over the Place, and I have no Clue which one(s) did the Trick.

But none of those Instructs above works where the Font can actually be utilized (as opposed merely being shown as available to any given Application), and the Permissions mostly definitely need to be re-set.

Unfortunately it appears I have the nauseating Task ahead of me to change the Permissions on Hundreds of Fonts individually ... lol

Many Procedures on this Thread appear to no longer work in Jaunty 9.04, but the above mentioned ones do.

> **Kinetic_lord said:**
> **Post #84** I don't get it, why so complicated? I had to install KDE with Dolphin just to install some fonts on my computer. Once you select a font in dophin, on he right side of the screen a "install font" option appears. Well... smart people made it.
That works perfectly too, and probably the best Course of Action if Fonts will only be installed selectively.

> **spottedhyena said:**
> On the Add/Remove menu - there is an app called Fonty Python
Or use sudo apt-get install fontypython

Works wonderfully - does the job for you...Displays all the fonts in a folder and let's you pick the ones you want...awesome little program and really easy to use - Fonts showed up in OpenOffice straight away...no problems so far.
This Application false-reports that most Windows Type, as well as True Type Fonts cannot be drawn when various Programs under Ubuntu run them perfectly well. Caution.

---

### Post by Ticketoride on 2009-04-15
Making a */.Fonts* Folder under the Home Directory doesn't work under 9.04 Jaunty, at least not for all Applications. Even though I changed the Permissions, the Fonts would still not show up in OpenOffice 3.x after *sudo fc-cache -fv*

But those Fonts I had copied by means of *gksudo nautilus* to the /usr/share/fonts Directory showed up right away after I changed Permission from Root to the User Account by right-clicking the Properties Page Security Tab of the each Font, and then *sudo fc-cache -fv*.

This appears to be the Action that makes these Fonts completely available globally.

---

### Post by mssever on 2009-04-15
> **Ticketoride said:**
> Unfortunately it appears I have the nauseating Task ahead of me to change the Permissions on Hundreds of Fonts individually ... lol
Actually, that isn't necessary. Fonts technically *should* be owned by root. The key is to make them world-readable. The command ```
sudo chmod +r font_file
```will do the trick.

But you don't have to manually change them all. That's where the power of the command line becomes evident. Suppose your fonts are in three directories under /usr/share/fonts/truetype: foo, bar, and baz. You can do this:
```
cd /usr/share/fonts/truetype
sudo chmod +r foo/* bar/* baz/*
```Or, make a loop (useful if you have a lot more files and directories than my example):```
cd /usr/share/fonts/truetype
for i in foo bar baz; do
  sudo chmod +r "$i"/*
done
```

---

### Post by Ticketoride on 2009-04-16
> **mssever said:**
> ```
sudo chmod +r font_file
```
Just the usual Fare ---> **chmod: cannot access `font_file': No such file or directory**

> **mssever said:**
> 
```
cd /usr/share/fonts/truetype
sudo chmod +r foo/* bar/* baz/*
```

```
cd /usr/share/fonts/truetype
for i in foo bar baz; do
  sudo chmod +r "$i"/*
done
```
Unless it comes down "Gerber-Style" Baby-Steps 1,2,3 ... its all Pseudo-Klingon Greek to me.

Unless you have a specific Command that applies to the Fonts /usr/share/fonts Directory, I won't be able to do anything with it, since there is no Point placing the Fonts anywhere else, because I have shown in the Fashion in my Post above that this most definitely works. And since it does, There is no Point concentrating on other Directories at this Point. Maybe at some Point in the Future, but its over my Head now.

Nevertheless, I just found another Way ...

**Use Kubuntu's 9.04 Font Installer in Ubuntu 9.04**

Launch Synaptic and search for **systemsettings** and install.
Alternately run **sudo apt-get install systemsettings** in a Termnial Window.

Go to Applications "Add/Remove..." and search for "System Settings" and Checkbox it if not already so. Then hit "Apply Changes" at the Bottom.

Go to --> Applications ---> System Tools and hit "System Settings".

Click on the "Font Installer" Icon near the Bottom of the Page.

** ... also all the Fonts which were copied to the /usr/share/fonts Folder per my Post above and then had their Permission changed from Root to User, show up as being registered by Kubuntu's Font Installer.*

---

### Post by AJB2K3 on 2009-04-16
I take it nobody reads any of my posts with the link in my signature saying how to install fonts?
[http://www.geocities.com/ajb2k305/tutorials/font.html]("http://www.geocities.com/ajb2k305/tutorials/font.html")

---

### Post by Therion on 2009-04-16
Just tossing this out for any interested parties...

There are some .deb/source files on this site that will quickly and easily install a bunch of fonts for you. 

Just a few clicks and all the fonts are immediately available in Open Office and Appearance preferences and all other applications.

6,700 fonts in one .deb file if you really want a serious font-dump(!!!) or the "Lite" version will install 76 of the most popular fonts for you.  

All of the files are here:  [http://thelinuxbox.org/?page_id=3#fonts](http://thelinuxbox.org/?page_id=3#fonts)

---

### Post by Hilko on 2009-05-06
Thanks ! These fonts are really great. And easy to install, just click the .deb package that's all.

---

### Post by shameedp on 2009-05-14
> **eg-maverick said:**
> I wonder if using Nautilus would work for item 4. then you wouldn't have to type everyting out.

Thanks for the post dude


It really works

---

### Post by 0per4t0r on 2009-05-24
Thanks for this, now I can use my favorite font in GIMP!

---

### Post by alfalfa31 on 2009-06-10
Dude, this script rocks.  Thank you very much for sharing it...

---

### Post by Hozza on 2009-06-10
"fontmatrix" is really good and you dont need to mess around with terminal :)

---

### Post by Ian Clark on 2009-06-13
> **mssever said:**
> 
[LIST=1]
[*]Make a directory for your fonts in /usr/share/fonts/truetype: ```
sudo mkdir -p /usr/share/fonts/truetype/my_fonts
```
[*]Copy your fonts to that directory:```
sudo cp /your/fonts/here /usr/share/fonts/truetype/my_fonts
```
[*]Run fc-cache:```
sudo fc-cache -fv
```
[*]Your fonts probably won't show up in your application until you restart it.
[/LIST]
This would work for fonts that only have one .ttf file in the folder, but for others like [this]("http://www.nerfect.com/typecon.html") one or [this]("http://www.smeltery.net/fonts/justice") one, there are fonts that don't get installed.  Any suggestions?

---

### Post by Ian Clark on 2009-06-13
> **Hozza said:**
> "fontmatrix" is really good and you dont need to mess around with terminal :)
Fontmatrix can see the fonts that were mentioned in the last post, but enabling them still doesn't get OOO, Abiword or Gimp to see them.

---

### Post by ishmael2k on 2009-07-01
> **AJB2K3 said:**
> I take it nobody reads any of my posts with the link in my signature saying how to install fonts?
[http://www.geocities.com/ajb2k305/tutorials/font.html]("http://www.geocities.com/ajb2k305/tutorials/font.html")

I did, worked like charm. Very easy, pulled all my fonts from old pc and copied them to new folder. Open Office never knew what hit her. :lolflag:

---

### Post by labinnsw on 2009-08-21
> **mssever said:**
> I wrote a script a while back that installs fonts. Save the script somewhere in your $PATH and make it executable. Type ```
sudo mkdir -p /usr/share/fonts/truetype/font-install
```  Then, cd to the directory that the fonts you want to install are in, run the script from a terminal window, and follow the prompts. Remember that Linux is case-sensitive, so if some files have a ttf extension and some hava a TTF extension, you'll either need to rename them or run the script twice.

```
#!/bin/bash
#
# This script helps to install fonts
#
# Set your default font storage directory here
##DEFAULT_DIR="$HOME/fonts"
DEFAULT_DIR=`pwd`
# Set the default font installation directory here
DEFAULT_DEST="/usr/share/fonts/truetype/font-install"


# Don't edit anything below unless you know what you're doing.

echo "In which directory are the fonts?"
echo -n "[$DEFAULT_DIR] "
read DIR

echo
echo "What is the extention (without the dot) of the fonts?"
echo -n "[ttf] "
read EXT

echo
echo "Where should the fonts be installed?"
echo "DO NOT CHANGE THIS UNLESS YOU KNOW WHAT YOU'RE DOING!"
echo -n "[$DEFAULT_DEST] "
read DEST

if [ -z "$DIR" ]; then
    DIR="$DEFAULT_DIR"
fi

if [ -z "$EXT" ]; then
    EXT="ttf"
fi

if [ -z "$DEST" ]; then
    DEST="$DEFAULT_DEST"
fi

sudo -v
if [ $? != 0 ]; then
    echo "Unable to obtain the necessary privileges. Exiting..."
    echo -n "Press <Enter> to continue. "
    read WER
    exit $?
fi

echo
echo

if [ ! -d "$DIR" ]; then
    echo "Directory $DIR does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read SDF
    exit 2
fi

if [ ! -d "$DEST" ]; then
    echo "Directory $DEST does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read DFG
    exit 1
fi

echo "Copying fonts..."
cd "$DIR"

for i in *."$EXT"; do
    sudo cp -iv "$i" "$DEST"
done

echo
echo
echo "Updating the font cache..."
sudo fc-cache -fv

if [ $? != 0 ]; then
    echo "Error updating the font cache. Your fonts haven't been completely installed. Try running sudo fc-cache -fv manually. Exiting..."
    echo -n "Press <Enter> to continue."
    read FSF
    exit $?
fi

echo
echo
echo "Finished."
echo
echo "You will probably need to restart running programs to use the new fonts."
echo -n "Press <Enter> to exit. "
read WERT
exit 0
```

Useful even today. Too easy!!! (just remember: case sensitive)

---

### Post by russu52 on 2009-08-29
> **SuperJETT said:**
> I did the .fonts directory approach, just copied fonts in there and they are installed, nothing else to do. 

Works nice.

brilliant!!! never figured out that it was so easy! thanks!!

---

### Post by Catarina on 2009-09-01
> **emiphiste said:**
> I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)

Well, I just ended up using this method, after trying both the gksudo nautilus command and the script by [mssever]("http://ubuntuforums.org/member.php?u=126210").

Even though there are easier ways, especially when hadling multiple files, I found this one rather simple, though since I'm still a green user, I had some difficulties working it out at first (probably one of the reasons for my nautilus/script issue) but then I saw there were missing some really basic stuff.

In this example, I set /home/user/Documents as the original font location.

```

user@user-desktop:~$ sudo su
root@user-desktop:/home/user# cd /home/user/Documents
root@user-desktop:/home/user/Documents# cp /home/user/.fonts Font-Name.ttf
cp: folder omit `/home/user/.fonts'
root@user-desktop:/home/user/Documents# sudo fc-cache -fv

```

Notes: "user" should be your current session's username, "user-desktop" should be your computer's name and "/home/user/Documents" should have "Documents" replaced by the name of the folder containing the fonts to install.

Hope this turns out to be useful for someone in the future ;)

---

### Post by mssever on 2009-09-02
> **Catarina said:**
> Well, I just ended up using this method, after trying both the gksudo nautilus command and the script by [mssever]("http://ubuntuforums.org/member.php?u=126210").

Even though there are easier ways, especially when hadling multiple files, I found this one rather simple, though since I'm still a green user, I had some difficulties working it out at first (probably one of the reasons for my nautilus/script issue) but then I saw there were missing some really basic stuff.

In this example, I set /home/user/Documents as the original font location.
I've cleaned up your script:
```

$: sudo su # Omit this command. You should only use sudo when you need to be root. (In other words, try doing it first as a normal user.)
#: cd /home/user/Documents # Or, cd ~/Documents (or ~user/Documents if you want another user's home)
#: cp /home/user/.fonts Font-Name.ttf # This is backwards, hence the message below from cp.
cp: folder omit `/home/user/.fonts'
#: cp *.{ttf,TTF} ~/.fonts #Use this instead. You can modify the wildcard as appropriate.
#: sudo fc-cache -fv # Because of the first sudo, this sudo is unnecessary.

```

---

### Post by stephy123 on 2009-09-03
thinking of trying the solution.only one successful in getting it all right.anyone else?let me try it myself...lets see

---

### Post by AJB2K3 on 2009-09-03
> **stephy123 said:**
> thinking of trying the solution.only one successful in getting it all right.anyone else?let me try it myself...lets see
Try the link in my sig.

---

### Post by wirespot on 2009-09-04
People. What is all this about shell scripts and whatnot? It's very simple to add fonts to Ubuntu:

1. Copy your TTF files to ~/.fonts (create the dir if it doesn't exist). Yes, that's .fonts, with a dot.

2. Open a console and run **fc-cache -fv ~/.fonts**

That's ALL.

Long explanation:

Font handling in modern Linux systems is delegated to the "fontconfig" package. It's what gives you fc-cache. The system settings are in /etc/fonts but you're better off not touching that. You have a ~/.fonts.conf files which you can tweak (but be warned that System>Preferences>Appearance>Fonts will override it, so write-protect it if you customize it).

A simple tweak would be to add a <dir>~/multimedia/myfonts</dir> line inside the <fontconfig></fontconfig> block. Or several such entries. It helps if you want to keep you fonts organized in individual dirs. But I for one am perfectly happy throwing them all in ~/.fonts.

Hope this helps.

---

### Post by Nephiel on 2009-09-06
I just installed a bunch of ttf fonts by copying them in a folder inside /usr/share/fonts/ (to make them available to all users), gave them the proper permissions and ownership, and ran fc-cache -fv. The fonts installed fine and are available to OpenOffice and other apps.

But for some weird reason, the default system font has changed to "Segoe Print", one of the fonts I installed.

When any app tries to display a font and it's not available in my system, it falls back to displaying "Segoe Print".

 When I run OpenOffice Writer, the default font for a new document is now "Segoe Print" as well. I changed this to Arial through Tools->Options->OOoWriter->Basic Fonts, and after a restart, I went there again and clicked the "Default" button, sure enough, the default was again "Segoe Print".

Uninstalling "Segoe Print" simply sets the next one, "Segoe Script", as default.

I'm not running Gnome nor gnome-settings-daemon (I use Fluxbox) but the default Gnome UI font is set to Arial. The GTK theme is set to Arial as well.

I've already checked all the fontconfig files (/etc/fonts/fonts.conf and local.conf). I have no ~/.fonts.conf file.

Might be related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/125949](https://bugs.launchpad.net/ubuntu/+bug/125949)

Is there some other way to set the default fallback font?

---

### Post by davyman913 on 2009-09-09
> **wirespot said:**
> People. What is all this about shell scripts and whatnot? It's very simple to add fonts to Ubuntu:

1. Copy your TTF files to ~/.fonts (create the dir if it doesn't exist). Yes, that's .fonts, with a dot.

2. Open a console and run **fc-cache -fv ~/.fonts**


I just ran this in terminal step by step and got it to copy and everything, I run fc-cache and it appears to find the files and succeed to do whatever it does. But the fonts are still unavailable to GIMP and OpenOffice. Can anyone help me out? I didn't do anything with permissions, but I don't have any clue what I would need to change with those to get it working.

---

### Post by smr1lk on 2009-10-05
I also had this issue. But I found an easy way out. Do the following steps.

1. copy all new founts to a folder (any folder name)
2. use the command line terminal to go to the folder.
3. within the folder type this:
       chmod 644 *.*
4.go to an existing folder like "thai" as follows:
      cd /usr/share/fonts/truetype/thai
5. then copy the new fonst to this folder.
     cp  /replace with your full folder path/*.* .

NOTE: DO NOT IGNORE THE LAST DOT IN THE ABOVE COMMAND.

THAT'S IT. OPEN THE WORD PROCESSOR. THE FONTS ARE THERE.:)

---

### Post by Exodist on 2009-10-05
> **Aleksandersen said:**
> Hi,

I have a .ttf font file here and I am wondering how I install it into the system?

In  you home folder just make a folder called .fonts and drop them in there. That simple.

---

### Post by sharma567 on 2009-10-06
You can still drag and drop to install fonts using a different folder: .fonts in your home folder. This folder may not exist by default. Open your home folder in the file browser, and select View->Show Hidden Files. If you canâ€™t find the .fonts folder, create it.
 You can copy any TTF font file into this folder and it will become available immediately to applications after they are restarted. You can get TTF fonts from the Internet, or even a Windows system.
____________________________________________
[business opportunity directory](http://www.giblink.com/site/Businesses/)  [humor blog](http://www.davepye.com)

---

### Post by akolahi on 2009-11-20
Yep that worked for me :)

Not all fonts are showing up in OpenOffice, but i think that's another issue.

> **sharma567 said:**
> You can still drag and drop to install fonts using a different folder: .fonts in your home folder. This folder may not exist by default. Open your home folder in the file browser, and select View->Show Hidden Files. If you canâ€™t find the .fonts folder, create it.
 You can copy any TTF font file into this folder and it will become available immediately to applications after they are restarted. You can get TTF fonts from the Internet, or even a Windows system.
____________________________________________
[business opportunity directory]("http://www.giblink.com/site/Businesses/")  [humor blog]("http://www.davepye.com")

---

### Post by AJB2K3 on 2009-11-22
Is my tutorial not of use anymore?
I sure I've explained it as well as I can.
[http://www.ajb2k3.co.uk/tutorials/font.html]("http://www.ajb2k3.co.uk/tutorials/font.html")

Arg never finished the system wide section.

---

### Post by alex.rayu on 2009-11-22
How to install fonts? You must be kidding! Select the fonts, right click - and there will be a bold-faced "Install Fonts" menu item. Everything for a user! Oh drats, I forgot, that's in Windows!

---

### Post by Merk42 on 2009-11-22
> **alex.rayu said:**
> How to install fonts? You must be kidding! Select the fonts, right click - and there will be a bold-faced "Install Fonts" menu item. Everything for a user! Oh drats, I forgot, that's in Windows!

**Thank God** font installation is finally self explanatory in Karmic
Double Click (opens up a preview) then click "install"

---

### Post by alex.rayu on 2009-11-22
God has nothing to do with it. He had his chance to insert that function all that time. But he didn't. Thanks to the developers!

---

### Post by Joe Casadonte on 2010-01-01
Hi,

Running 9.10, just tried the "Install Font" from the Font Viewer and the fonts fail to show up in OO.  Also, the .fonts & fc-cache -fv method didn't work, either.  :(

---

### Post by Exodist on 2010-01-01
> **Joe Casadonte said:**
> Hi,

Running 9.10, just tried the "Install Font" from the Font Viewer and the fonts fail to show up in OO.  Also, the .fonts & fc-cache -fv method didn't work, either.  :(
In your home folder, like mine is /home/exodist, you will have a .fonts folder. Just like that ".fonts". From the the entire directory will look like this /home/exodist/.fonts

If you put your true type fonts in the .fonts folder, they will show up. You may have to log out and back in just in case there is a bug, but they will work. Make sure its .fonts, not .Fonts or .font or .FONTS. Only .fonts

Cheers,
Exo

---

### Post by alex.rayu on 2010-01-04
Yeah if you have 300 fonts to install - opening each of them in a preview and clicking an Install button does not make one with thanking God for it. It is great to have a button there. BUT, a context Install menu item in a context menu is a MUST.

---

### Post by Joe Casadonte on 2010-01-04
> **Exodist said:**
> You may have to log out and back in just in case there is a bug, but they will work.

Indeed, that was it. -- thanks!

---

### Post by Exodist on 2010-01-04
> **Joe Casadonte said:**
> Indeed, that was it. -- thanks!
Not a problem. When making gnome themes, now and then I have to log out and log back in for GNOME to update from the theme code. Then sometimes it doesn't, its just quirky from time to time.

---

### Post by AlexanderDGreat on 2010-02-03
I don't know if there's anything wrong with my method, can you please comment on it? Tried on 3 Karmic computers and 2 Jaunty, works well! I'm using a .ttf fonts.

NOTE: I have a MS Office 2007. I just went to C:\Windows\Fonts\ and got all the .ttf fonts there.

1. To browse your system files with root permissions

```
sudo nautilus
```

2. Create a folder **myfonts** under:

> /usr/share/fonts/

Copy & Paste your fonts in your newly created folder:

3. Make sure you set permissions to:

```
sudo chmod -R 755 /usr/share/fonts/myfonts/
```

4. Finally, restart your fonts

```
sudo fc-cache -fv
```

5. If you're curious:

```
man fc-cache
```

6. Open OOP - and fonts like cambria, calibri, etc... will be there...

---

### Post by blackhawkover on 2010-02-04
I was having same prob as some, clicking on the preview and pushing install, which changed the button to install failed. So, I opened /home in root and went to .fonts and that font was there, double clicked and clicked install and it worked. I'm not sure if it will work in openoffice without logging out or something, but we are closer. 

thanks for the tip.

---

### Post by mssever on 2010-02-05
> **blackhawkover said:**
> I was having same prob as some, clicking on the preview and pushing install, which changed the button to install failed. So, I opened /home in root and went to .fonts and that font was there, double clicked and clicked install and it worked. I'm not sure if it will work in openoffice without logging out or something, but we are closer. 

thanks for the tip.

Editing stuff in your home directory as root is virtually always unnecessary if your system is properly configured. Files under your home dir should be owned by your user, and of course your user has control over the files it owns.

Messing about as root can leave root-owned files around, which can cause various problems. Save root for only system-level stuff.

---

### Post by Allwynd on 2010-02-18
i personally got interested in the Diablo II Lord of Destruction font, so i easily found it and downloaded it and i wanted to install it but didnt know how, so i searched around the forum a bit, the first responce didnt work, maybe i was doing it wrong
then i opened the font with something like font viewer similar to the one in windoze.. and there was a button [Install] .. the font was .ttf
now i have the font ^_^
i hope this helps out someone

---

### Post by airtonix on 2010-02-18
> **alex.rayu said:**
> Yeah if you have 300 fonts to install - opening each of them in a preview and clicking an Install button does not make one with thanking God for it. It is great to have a button there. BUT, a context Install menu item in a context menu is a MUST.

You mean copy & paste is too hard? 

1. select font(s)
2. press ctrl + c
3. press ctrl + l
4. type ~/.fonts
5. press ctrl + v

---

### Post by dfwsupergeek on 2010-03-14
I see that this is a VERY old thread, but I just wanted to say that the install script worked like a dream in Karmic, so Thanks! :)

---

### Post by trixa_13 on 2010-03-25
> **Aleksandersen said:**
> Hi,

I have a .ttf font file here and I am wondering how I install it into the system?


You just have to double-click it and it will open a new window. At the right of the window, there is an option, "Install Font". Click on it and it will install the font. You can see it in your Home Folder but first, you have to select "Show Hidden Files" on View Menu and double-click the folder, ".fonts". And voila! The font is installed!:KS

---

### Post by Jimmy Goal on 2010-03-29
For me it worked: under Ubuntu 9.10 default distro


create folder "/home/USERNAME/.fonts"
copied all the font files to that folder
typed "sudo fc-cache fv" in terminal

It was done   :D

Thanks all

---

### Post by Bloodsmith on 2010-04-02
Heeeyyyy, first post, awesome.
Does any of this translate over to Kubuntu? And if so, anyone know where I may be able to find extra fonts to download? If possible, from a trusted source. Thanks!

---

### Post by LaurenJadeTaylor on 2010-04-04
Hi friends this is the way to install fonts in ubuntu:- 



This section describes two ways for how to install new fonts in Ubuntu. 



The first uses the[COLOR=Black] [Synaptic Package Manager]("https://wiki.ubuntu.com/SynapticHowto")[/COLOR] to install fonts from the Ubuntu repositories. As new fonts get added to the archive, this method offers fonts suitable for an increasing number of users, and is very easy. 



The second method is useful if you have downloaded fonts from the web, bought them, or acquired them from other sources. It is a bit more manual, but allows you to use fonts (including restricted fonts when you can't find a free/libre/open font equivalent) from a wide range of sources. 



Finally, at the end of this page, there are some links for further information on fonts on GNU/Linux.

---

### Post by adzidzor on 2010-05-03
> **Jimmy Goal said:**
> For me it worked: under Ubuntu 9.10 default distro


create folder "/home/USERNAME/.fonts"
copied all the font files to that folder
typed "sudo fc-cache fv" in terminal

It was done   :D

Thanks all


Worked perfectly for me in Lucid! Thanks

---

### Post by Davidmark on 2010-05-03
1
**Move all your fonts to the ~/ Directory**. The ~/ Directory is your home folder. So if you were logged in as cruddpuppet, the directory would be /home/cruddpuppet/ .2
**Open up the terminal**. I'm assuming you've already extracted the font to the ~/ directory. Type: "cd /usr/local/share/fonts/truetype" without the quotes (the path is "/usr/share/fonts/truetype" on some distros). What this does is changes the directory to the truetype fonts directory.3
**Type in "sudo mkdir myfonts" also without quotes**. Assuming you're not logged in as root, this will ask you for your password. Anything you type will not be seen, but it is there. Just type in your password, press enter, and the directory 'myfonts' will be created.4
**Type in "cd myfonts" **. Then type in "sudo cp ~/fontname.ttf ." . These will get your font in the /myfonts directory.5
**In order to install the font, ownership has to belong to root, so type in "sudo chown root**.root fontname.ttf" and after that "sudo mkfontdir" which makes a directory for your font.6
**Now your font is installed, but it will disappear the next time ubuntu starts up, so you just need to type "cd **.." and after that "fc-cache" .

---

### Post by .Daniel on 2010-05-13
Likewise, this definitely works in Lucid Linux - thanks very much :grin:

'create folder "/home/USERNAME/.fonts"
copied all the font files to that folder
typed "sudo fc-cache fv" in terminal'

---

### Post by cadaverousmob on 2010-06-02
> **.Daniel said:**
> Likewise, this definitely works in Lucid Linux - thanks very much :grin:

'create folder "/home/USERNAME/.fonts"
copied all the font files to that folder
typed "sudo fc-cache fv" in terminal'

+1

Go Lucid!

---

### Post by mssever on 2010-06-05
> **gaconden said:**
> **Move all your fonts to the ~/ Directory**. The ~/ Directory is your home folder. So if you were logged in as cruddpuppet, the directory would be /home/cruddpuppet/
These instructions are a difficult way to operate. Unless you only have one font to install, it'll be awkward to dump the fonts in your home directory. Just skip this step and leave your fonts wherever they are now. But if you put all your fonts in a single directory which contains only fonts, your life will be easier if you have a large number of fonts to install.
> **Open up the terminal**. I'm assuming you've already extracted the font to the ~/ directory. Type: "cd /usr/local/share/fonts/truetype" without the quotes (the path is "/usr/share/fonts/truetype" on some distros). What this does is changes the directory to the truetype fonts directory.
Open up a terminal. Skip everything else here; it's a waste of time.
> **Type in "sudo mkdir myfonts" also without quotes**. Assuming you're not logged in as root, this will ask you for your password. Anything you type will not be seen, but it is there. Just type in your password, press enter, and the directory 'myfonts' will be created.
Try this command instead: ```
sudo mkdir -p /usr/local/share/fonts/truetype/myfonts
```We didn't need to cd earlier because we can just as easily make the directory from wherever we are. And remember to use the tab key to autocomplete directory names and speed along. The -p argument to mkdir tells mkdir to create any additional directories that may be necessary. It's probably unnecessary in this case, but it doesn't hurt.

> **Type in "cd myfonts" **. Then type in "sudo cp ~/fontname.ttf ." . These will get your font in the /myfonts directory.
Assuming you put your fonts in ~/fonts (adjust this as necessary for your situation) and that there are only fonts in tht directory, type ```
sudo cp ~/fonts/* /usr/local/share/fonts/truetype/myfonts
```
> **In order to install the font, ownership has to belong to root, so type in "sudo chown root**.root fontname.ttf" and after that "sudo mkfontdir" which makes a directory for your font.This step is unnecessary. You used sudo with your cp command, so of course the files you copied are already owned by root. Also, the mkfontdir command is unnecessary unless you're using old .pcf, .snf, or .bdf fonts. Chances are, you're not.
> **Now your font is installed, but it will disappear the next time ubuntu starts up, so you just need to type "cd **.." and after that "fc-cache" .Actually, the font isn't installed yet. Just type ```
sudo fc-cache -fv
``` and you're good to go, with no worries about rebooting.

---

### Post by AlexanderDGreat on 2010-06-06
@mssever - You mentioned to put your fonts in this folder:

```
/usr/local/share/fonts/truetype/myfonts
```

BUT... I put mine in:

```
/usr/share/fonts/myfonts
```

notice, it's not in LOCAL, nor in TRUETYPE folders - Is this OK? What's the difference? Yet my fonts are working great, is that normal?

**PS Anyone tried to rename a FONT for example, sudo mv cambria.ttf cam.ttf - and notice it doesn't work after that, even after restart?**

Try it on OPENOFFICE or A CSS file.

---

### Post by mssever on 2010-06-07
> **AlexanderDGreat said:**
> @mssever - You mentioned to put your fonts in this folder:

```
/usr/local/share/fonts/truetype/myfonts
```

BUT... I put mine in:

```
/usr/share/fonts/myfonts
```

notice, it's not in LOCAL, nor in TRUETYPE folders - Is this OK? What's the difference? Yet my fonts are working great, is that normal?I don't know exactly, but often there are several possible places where you can put fonts. /usr/local is traditionally for stuff you add yourself while /usr is for stuff that's part of the distro.

> **PS Anyone tried to rename a FONT for example, sudo mv cambria.ttf cam.ttf - and notice it doesn't work after that, even after restart?**

Try it on OPENOFFICE or A CSS file.
Apparently for some reason fonts require that they have a certain filename.

---

### Post by Girideepa on 2010-08-29
Dear All,
thanks for nice tutorial,
simply copied ttf fonts to .font folder,
that's it,

---

### Post by apacheuk on 2010-09-07
This maybe just me... I don't normally haven bother with the command line stuff

just right click on a .ttf file (where ever I've downloaded it to) and click "open with font viewer". Once that happens there is an "install" button in the bottom right.

Have only checked this with .ttf files, but seems to work.

---

### Post by shivertone on 2010-09-07
**How to Install Fonts on Ubuntu**


     **       Running a few simple commands helps you to install fonts in Ubuntu.     **


                       [FONT=Verdana][SIZE=2]The different ways of installing Fonts on Ubuntu[/SIZE][/FONT][FONT=Verdana][SIZE=2]are described below.[/SIZE][/FONT][FONT=Verdana][B][SIZE=2]
[/SIZE][/B][/FONT]
 
[LIST=1]
[*]     [FONT=Verdana][SIZE=2]Installing fonts for single use[/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]Installing fonts for systemwide use[/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]Installing Microsoft Windows Fonts (eg Times New Roman)[/SIZE][/FONT][FONT=Verdana][B][SIZE=2]
    [/SIZE][/B][/FONT]
[/LIST]
 
 [FONT=Verdana]**[SIZE=2]Installing fonts for single use[/SIZE]**[/FONT]
 [FONT=Verdana][SIZE=2]    1) Using **kfontview**[/SIZE][/FONT][FONT=Verdana]
[/FONT] 
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]An easy way to install fonts is using **kfontview. **Run the command given from command line. 
    [/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]Go to **Applications **> **Accessories **> **Terminal**
    [/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]          [IMG]http://www.zolved.com/UserFiles/Image/27984/terminal%281%29.jpg[/IMG]
[/SIZE][/FONT] 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Run the command[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        **apt-get install kcontrol**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]         [IMG]http://www.zolved.com/UserFiles/Image/28550/jpgfont.jpg[/IMG][/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]After the installation process is completed, run command $kfontview.[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]    **kfontview**[/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]From the **kfontview **window, open the font you have downloaded.[/SIZE][/FONT]
     [FONT=Verdana][SIZE=2] Click on the "Install" button[/SIZE][/FONT]
     [FONT=Verdana][SIZE=2] NOTICE: You will probably need to resize the window to see the "Install" button which is in the lower right hand corner.[/SIZE][/FONT]
     [FONT=Verdana][SIZE=2] Click on the "**Personal**" button[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]    2) By hand
[/SIZE][/FONT] 
[LIST]
[*]     [FONT=Verdana][SIZE=2]If a font doesn't exist create it. First create a font's directory[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]    **mkdir ~/.fonts**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana][SIZE=2]To copy font from command line[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana]**[SIZE=2]cp [font file] ~/.fonts[/SIZE]**[/FONT]
 
[LIST]
[*][FONT=Verdana][SIZE=2]To copy all fonts from myfonts folder 
    [/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]         **fc-cache -f -v ~/.fonts**

[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Installing fonts for systemwide use**[/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Make a root directory[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]**mkdir /usr/share/fonts/truetype/myfonts**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana] Copy the font(s) into the newly created directory[/FONT]
[/LIST]
 [FONT=Verdana]                 **[SIZE=2]cp [fonts] /usr/share/fonts/truetype/myfonts[/SIZE]**[/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]To Run[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        [B]fc-cache -f -v
[/B][/SIZE][/FONT]
 [FONT=Verdana]**[SIZE=2]Installing Microsoft Windows Fonts (eg Times New Roman)[/SIZE]**[/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Make sure you have the "universe"  repository added. If not, as root, modify your /etc/apt/sources.list and  uncomment the deb line which will look something like this[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
[/SIZE][/FONT] 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Updata apt-get[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]          **apt-get update**[/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]To Install run the following[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]          **apt-get install msttcorefonts**[/SIZE][/FONT][FONT=Verdana]
[/FONT]

---

### Post by monet.hart on 2010-09-07
it worked for me too.  Thanks

---

### Post by commodianus on 2010-09-17
> **Aleksandersen said:**
> Hi,

I have a .ttf font file here and I am wondering how I install it into the system?

1. If you don't have it, create /home/**user**/.fonts (**user** being your username).

```
mkdir ~/.fonts
```2. Extract the fonts to that directory.

2.a Alternatively use nautilus (check View>Show Hidden Files or hit ctrl+H) and copy / paste them in (as .fonts is a hidden directory).

2.b Alternatively copy the fonts using the terminal:

cp /path/to/font.tff /home/**<user>**/.fonts

3. Profit.

---

### Post by syed.rakib.al.hasan on 2010-10-17
> **commodianus said:**
> 1. If you don't have it, create /home/**user**/.fonts (**user** being your username).

```
mkdir ~/.fonts
```2. Extract the fonts to that directory.

2.a Alternatively use nautilus (check View>Show Hidden Files or hit ctrl+H) and copy / paste them in (as .fonts is a hidden directory).

2.b Alternatively copy the fonts using the terminal:

cp /path/to/font.tff /home/**<user>**/.fonts

3. Profit.


Awesome.......... simply awesome....... i like using method 2.

---

### Post by baditaflorin on 2010-11-01
> **shivertone said:**
> **How to Install Fonts on Ubuntu**


     **       Running a few simple commands helps you to install fonts in Ubuntu.     **


                       [FONT=Verdana][SIZE=2]The different ways of installing Fonts on Ubuntu[/SIZE][/FONT][FONT=Verdana][SIZE=2]are described below.[/SIZE][/FONT][FONT=Verdana][B][SIZE=2]
[/SIZE][/B][/FONT]
 
[LIST=1]
[*]     [FONT=Verdana][SIZE=2]Installing fonts for single use[/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]Installing fonts for systemwide use[/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]Installing Microsoft Windows Fonts (eg Times New Roman)[/SIZE][/FONT][FONT=Verdana][B][SIZE=2]
    [/SIZE][/B][/FONT]
[/LIST]
 
 [FONT=Verdana]**[SIZE=2]Installing fonts for single use[/SIZE]**[/FONT]
 [FONT=Verdana][SIZE=2]    1) Using **kfontview**[/SIZE][/FONT][FONT=Verdana]
[/FONT] 
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]An easy way to install fonts is using **kfontview. **Run the command given from command line. 
    [/SIZE][/FONT]
[*]     [FONT=Verdana][SIZE=2]Go to **Applications **> **Accessories **> **Terminal**
    [/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]          [IMG]http://www.zolved.com/UserFiles/Image/27984/terminal%281%29.jpg[/IMG]
[/SIZE][/FONT] 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Run the command[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        **apt-get install kcontrol**[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]         [IMG]http://www.zolved.com/UserFiles/Image/28550/jpgfont.jpg[/IMG][/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]After the installation process is completed, run command $kfontview.[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]    **kfontview**[/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]From the **kfontview **window, open the font you have downloaded.[/SIZE][/FONT]
     [FONT=Verdana][SIZE=2] Click on the "Install" button[/SIZE][/FONT]
     [FONT=Verdana][SIZE=2] NOTICE: You will probably need to resize the window to see the "Install" button which is in the lower right hand corner.[/SIZE][/FONT]
     [FONT=Verdana][SIZE=2] Click on the "**Personal**" button[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]    2) By hand
[/SIZE][/FONT] 
[LIST]
[*]     [FONT=Verdana][SIZE=2]If a font doesn't exist create it. First create a font's directory[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]    **mkdir ~/.fonts**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana][SIZE=2]To copy font from command line[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana]**[SIZE=2]cp [font file] ~/.fonts[/SIZE]**[/FONT]
 
[LIST]
[*][FONT=Verdana][SIZE=2]To copy all fonts from myfonts folder 
    [/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]         **fc-cache -f -v ~/.fonts**

[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**Installing fonts for systemwide use**[/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Make a root directory[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]**mkdir /usr/share/fonts/truetype/myfonts**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana] Copy the font(s) into the newly created directory[/FONT]
[/LIST]
 [FONT=Verdana]                 **[SIZE=2]cp [fonts] /usr/share/fonts/truetype/myfonts[/SIZE]**[/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]To Run[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        [B]fc-cache -f -v
[/B][/SIZE][/FONT]
 [FONT=Verdana]**[SIZE=2]Installing Microsoft Windows Fonts (eg Times New Roman)[/SIZE]**[/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Make sure you have the "universe"  repository added. If not, as root, modify your /etc/apt/sources.list and  uncomment the deb line which will look something like this[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]        deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
[/SIZE][/FONT] 
[LIST]
[*]     [FONT=Verdana][SIZE=2]Updata apt-get[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]          **apt-get update**[/SIZE][/FONT]
 
[LIST]
[*]     [FONT=Verdana][SIZE=2]To Install run the following[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]          **apt-get install msttcorefonts**[/SIZE][/FONT][FONT=Verdana]
[/FONT]

In ubuntu 10.10 

```
sudo apt-get install kcontrol
[sudo] password for badita: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2a kdebase-runtime kdebase-workspace-bin

E: Package 'kcontrol' has no installation candidate
badita@badita-P35-Platinum-MS-7345:~$ 


```

---

### Post by flitbee on 2010-11-29
> **emiphiste said:**
> I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)

This is the most easiest method I've found so far! Thank you..

---

### Post by MrGreenTea on 2011-01-11
[SIZE=5]Thanks. After read all the messages, I figure out that all you need is:
1. create a folder
2.dump all your fonts in it
3.right click the folder, rename it to .fonts
4.right click it again, cut
5.go to /home/user/ and paste it.

At least it worked for me. You can try
[/SIZE]

---

### Post by prokoudine on 2011-01-11
> **MrGreenTea said:**
> Thanks. After read all the messages, I figure out that all you need is:
1. create a folder
2.dump all your fonts in it
3.right click the folder, rename it to .fonts
4.right click it again, cut
5.go to /home/user/ and paste it.

At least it worked for me. You can try
I wonder why people go through pains like this when there are tools like Fontmatrix to manage fonts collections.

---

### Post by ganeshbhatbams on 2011-01-29
"gksudo nautilus" worked nicely in ubuntu 9.10 i copied file easily
thank you
Dr.ganesh:popcorn:

---

### Post by Copper Bezel on 2011-01-29
> I wonder why people go through pains like this when there are tools like Fontmatrix to manage fonts collections.Pains like putting the files you downloaded into a *different folder*? I just don't understand why anyone would feel the need to use the terminal.

I'm disturbed at the possibility that there might be anything simpler than drag and drop.

---

### Post by PTZ on 2011-02-10
There is a real simple way of installing a font (10.04) - 

1.  Open the folder containing the font.
2.  Right-click the font file.
3.  Select "Open with Font Viewer" from the menu.
4.  Click the INSTALL FONT button in the lower right corner of Font Viewer.

---

### Post by psnegi on 2011-02-12
The simplest way is download the font you want to install. Double click on it. At the right bottom corner you will see the option 'install font'. Click on it and it will be installed. You can check in Open Office word and it will be there. (Ubuntu 10.1)

---

### Post by AlexanderDGreat on 2011-02-20
Hi, I'm so confused when assigning fonts to my design because there are A LOT OF FONTS, out there!

Example when I type in OpenOffice, use GIMP, I'm overwhelmed with the LOTS of fonts out there, even when I was still in Windows.

Is there a tutorial where I can:

1. Remove All Pre-Installed Fonts?
2. Create or paste only the ones I want in /home/user/.fonts? or /usr/share/fonts/myfonts/ ?

If I can do this, I'll be faster and can only CHOOSE FONTS I Actually USE and NEED.

Thanks a lot.

---

### Post by rvchari on 2011-02-20
> **Aleksandersen said:**
> Hi,

I have a .ttf font file here and I am wondering how I install it into the system?

i usually take the straight steps...
i download all the ttf i need. then copy to ~/.fonts folder in hme or if you need systemwide application, move the *.ttf fonts to /usr/share/fonts/TTF
if TTF folder isnt there then create one.

```
sudo mv ~/FONTS.ttf /usr/share/fonts/TTF
```

if TTF folder isnt there in /usr/share/fonts, then create...

```
sudo mkdir /usr/share/fonts/TTF
```

---

### Post by prokoudine on 2011-02-21
> **Copper Bezel said:**
> Pains like putting the files you downloaded into a *different folder*?

Pains like having to manually manage fonts collection instead of using perfectly reasonable interfaces with tags and whatnot.

> **AlexanderDGreat said:**
> Hi, I'm so confused when assigning fonts to my design because there are A LOT OF FONTS, out there!

Example when I type in OpenOffice, use GIMP, I'm overwhelmed with the LOTS of fonts out there, even when I was still in Windows.

Use font managers. They make it easy to decide what you don't need that can be hidden for while. I'll see about a tutorial.

---

### Post by swiftarrow on 2011-07-24
Hi people,

If, like most, you are on a single-user system, then font installation is dead simple.

Of course, there are a billion different ways (read above) but here's my favourite:

create a directory called ```
.fonts
``` in your home directory.
Put your new fonts in that
run ```
sudo fc-cache -fv
```

That's it!:guitar:

---

### Post by AJLChase on 2011-07-30
I'm using ubuntu 11.04 and am trying all of the different ways to install fonts into existing and new folders, but a lot of these folders im finding that after i make them it won't allow me to modify or change permissions to install anything into them. Getting kind of frustrated as I would just assume it would be pretty straight forward. When I use GIMP 2.6 to select a font I keep getting Invalid UTF-8 data in file '/home/ajlchase/.font/BROKEN_GHOST.ttf no matter which way I locate it....help this noob out please!

---

### Post by Rhys L on 2011-09-05
Hi I'm a noob too but to have the max permissions i would open a terminal window then at eh prompt type 

sudo nautilus 

This opens a file browser as root i think that should give you whatever permissions you want

---

### Post by w.saharut on 2011-10-08
[SIZE=1]> **emiphiste said:**
> I tried using the script, and it looked like it copied the fonts over fine; however, when I opened the GIMP to make sure I had the fonts, they were all defaulted to look like one of the monotypes. This may or may not be a unique issue - just thought I'd let you know (though the most likely reason is that I'm doing something wrong).

After some research on ubuntuforums.org, I've located a really simple way to install fonts (just to add on to the thread in case you're only looking to install maybe a few fonts at a time).

1) Download any/all fonts into one location (I'm using /home/"USERNAME"/ttffonts).

2) Navigate back to your home directory and create a folder called ".fonts". (This directory will disappear from view; don't worry about it, it's still there.)

3) In terminal, cd to /home/"USERNAME"/ttffonts.

4) cp all fonts in ttffonts to /home/"USERNAME"/.fonts (The only minor inconvenience about this is that, unlike using the script, you have to type out all fonts by hand - which may suck quite heartily if you're trying to install thousands of fonts from a server.)

5) Installation complete! (Source: [http://ubuntuforums.org/showthread.php?t=263689](http://ubuntuforums.org/showthread.php?t=263689))


(By the way, if you can help me get the script to work 100%, that would be awesome. It looks to be a very handy and well-written tool. I thought it might be because I'm using Breezy Badger instead of Dapper - could that be the culprit?)[/SIZE]

[SIZE=3][COLOR=Blue]it's work 100%. i ever have problem in fonts format between ms office and ununtu.
but now it's ok.
Thank so much.[/COLOR][/SIZE]

---

### Post by monsterzero on 2011-10-11
> **psnegi said:**
> The simplest way is download the font you want to install. Double click on it. At the right bottom corner you will see the option 'install font'. Click on it and it will be installed. You can check in Open Office word and it will be there. (Ubuntu 10.1)This worked great for me and it took about five seconds.  Thank you!

(Running Ubuntu 10.04)

---

### Post by robot_chicken_parm on 2011-10-26
the easiest way to install a new font is to download the font file of your choice, from for example [http://www.fontcenter.com/fonts/zero_threes.html]("http://www.fontcenter.com/fonts/zero_threes.html").  Font Center has a lot of goodies, and that particular one, zero threes, is one of my favs.  With this particular site, or any for that matter, it doesnt matter if it says the font is for mac or pc, as it is a *.TTF file anyway.  Download the file, open it.  Without even extracting it, from within the zip program, just open the tff file.  It will show an example of the file and a button that says install.  It is that simple.  Enjoy!

---

### Post by xtremo on 2011-10-26
Thanks for the tip.....been puzzled on this for a while!

---

### Post by nowashburn on 2012-10-24
I know this is an old thread, but it was the first one that came up when searching. Anyhow, my 2 cents..

I have three machines, 2 running 12.10 and one running 12.04. No matter what when clicking on the font and selecting "Install Font" in font viewer, I get the Install Failed message. Instead I have to copy the font to the .fonts directory manually. Not a huge deal but kind of annoying and well, there does seem to be an issue here because if not, it wouldn't fail. 

What is the purpose of the install font option in font viewer if it doesn't seem to work for so many people?

---

### Post by GreatDanton on 2012-10-24
Simplicity I believe. I prefer installing fonts via terminal anyway.

---

### Post by legendbb on 2012-11-12
Came up with this thread when trying to add fonts to Ubuntu 10.10

Found a quick summary quick concise and complete: [http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu](http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu)

Just one point to add, please do make sure minimum user has read access to your newly added fonts.

And try to avoid using font viewer's "install fonts" button, because it install fonts to ~/.fonts/ can be good for yourself, but confuse others at later time.

Thanks for all efforts.

---

### Post by matega on 2012-12-12
> **eg-maverick said:**
> I wonder if using Nautilus would work for item 4. then you wouldn't have to type everyting out.

Yes, it would. '.fonts' is a hidden directory, all you have to do is tell Nautilus you want to view hidden files as well. Either do it in the settings or press Ctrl-H (H as Hidden). It works in pretty much any file manager, not just Nautilus. Once you get to see the directory, simply copy the fonts into it. They will only be available to the current user though.

---

### Post by Random20210831 on 2012-12-13
**1st way:**
1) Open Terminal **(Ctrl + Alt + T)**
2) **(for root privilegies)**```
sudo su -
```
3) **(for nautilus start)** ```
nautilus
```
4) Find font archive and extract it in **/usr/share/fonts/truetype/**

**[COLOR="DarkRed"]NOTE: Don't extract fonts in /home/user/.fonts or /root/.fonts. For system-wide (for all in system) installation extract it in /usr/share/fonts/truetype/.[/COLOR]**

**2nd way:**
1) Open nautilus
2) Double-click on desired font archive
3) That will open Font Manager
4) Simple click on "Install" button

That's all! :D

---

