---
title: "Finding what I've &quot;installed&quot;"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by geekchicohio on 2007-01-31
I've got a couple weeks of Ubuntu experience, but recently decided (read: was forced) to switch completely (from WinXP) and start off with a freshly formatted drive and a fresh installation of Dapper.

**My problem is this:**
Ubuntu doesn't seem to be doing what it did the first time around. I keep installing, or thinking I'm installing packages and then being unable to find the programs. I've used Add/Remove..., I've used apt-get, and I've used synaptec at various times to try to install a few different programs and they're just disappearing. I have little-to-no knowledge of the basics of the Linux filesystem (I'm used to a "Programs" folder), and I'm used to the programs I install placing themselves in the start menu.
Even programs I installed in my previous experience with Ubuntu 'just worked' then and seem not to now.

What I can't figure out is where the things I've installed are, and how to access them so that I can use them now. Where can I find them to (if need be?) create launchers for them. Why don't they immediately begin to go to work as they did before? Why aren't they being added to my Applications menu as I install them?

Some do. But many (ntfs-3g, beagle, gnome deskbar-applet, checkgmail, tovid, fuse2) have just vanished without my being able to find them again to actually USE them since installation.

Some of these programs I've even attempted to re-install in the terminal or using add/remove, and I'm told they're already installed and newest version. Now if only I can find them...

**(not part of my question, but a bit of background on me:)**
I've been using Ubuntu 'recreationally' for a couple weeks now after several years as being the guy who understood Windows better than any of his friends. I'm reeling after going from a Windows Power User to a complete Linux n00b overnight.
I had a dual-boot setup for awhile and managed to recently kill WinXP and am now facing the reality that I'm a full-time Ubuntu user. I'm stoked about it, I was planning on leaving MS behind in the Vista switch anyway, but I'm still just scratching my head at the way things seem to be going for me...

---

### Post by ComplexNumber on 2007-01-31
> ntfs-3g, beagle, gnome deskbar-applet, checkgmail, tovid, fuse2apart from beagle(this will be in the menu, but you probably haven't found it yet) and deksbar applet(you will find this in your list of applets), none of them are graphical applications.....so i'm not surprised that they don't appear in the menu.

---

### Post by kolinab on 2007-01-31
I've had similar problems to what you're describing. 

A couple of things I have done that have helped. I installed the Debian menu in Automatix2. It shows you lots of programs that don't automatically show up in the applications menu. If you're looking for automatix2, I think the link to use is [www.getautomatix.com](www.getautomatix.com). It's easy to find anyway.

The other thing that I realised a few times is that a program I installed doesn't necessarily have a graphical front end. Sometimes punching the program's name into a terminal window has opened a graphical front end for me and other times I have realised the program I installed runs only from the command line. I'm learing the command line slowly, but tend to stick to the pretty looking programs for now . . .

Anyway, I don't know if I've actually told you anything you don't already know. In that case I just share in your linux learning . . . I myself just rid myself of XP and moved to ubuntu just over a month ago. I didn't bother with a transition phase with a dual boot - I don't NEED my computer for work so just did a clean install of ubuntu on a formatted drive and have been having fun. Sink or swim!

K

---

### Post by geekchicohio on 2007-01-31
Here's the kicker, the part I forgot to mention before.
Through Automatix I installed the debian menu. I've gone to the Alacarte Menu Editor to turn the debian menu on, having read on various FAQs it's the best way to find things...and it doesn't work. The checkbox next to it won't allow itself to be checked. Soo...I'm at a loss.

---

### Post by seshomaru samma on 2007-01-31
Open a terminal and run those programmes from there . It usually works. 
You can then create a desktop/panel shortcut by right clicking anywhere and choosing 'create launcher'(on the desktop) or 'add to panel' (on the panel)

---

### Post by kolinab on 2007-02-01
Weird about the Debian menu. I don't remember having to check any checkboxes to get mine working. I just installed it with automatix and boom, there it was in my apps menu. Maybe there is some larger problem with your menu that is causing you these problems? I dunno - hopefully someone can help.

---

### Post by s26c.sayan on 2007-02-01
Use the Terminal!!
E.G. to run the 'checkgmail' app, just type 'checkgmail' in a terminal and press RETURN!!! You can even type in the first few letters of the app name and use the autocomplete feature by presssing TAB.



To find out where an installed app is, issue the command
```
whereis <appname>
```The following command will generate a list of all installed apps (just found it on the net) !!
```
dpkg --get-selections | grep -v deinstall > ubuntu-files

```You can then view the list by opening the file 'ubuntu-files' using any text-editor.
_Reference_: [http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

And as a 6 months old Ubuntite ;) , my advice to you will be to try mastering the CLI as much as you can...its real FUN!!! :)

---

### Post by 3rdalbum on 2007-02-01
Tovid does have a GUI, but it doesn't automatically put itself into your menus (lazy developers!). You can create a launcher for "tovidgui" and that will launch Tovid.

Beagle isn't a program that appears under your Applications menu either; it's really just the "backend" for Nautilus' Search function and the Deskbar.

---

### Post by geekchicohio on 2007-02-01
Okay, so with your wonderful help I've managed to get CheckGmail up and running.
I just used automatix to uninstall and then re-install the Debian Menu. Still no dice on that one.
The thing that is really leaving me scratching my head is the fact that this is the second time I've had a fresh copy of Ubuntu on my system. After I killed WinXP I decided (puzzlingly) to start with a fresh copy of Ubuntu and go from the ground up. Some of the programs that I'm not able to get working are programs that 'just worked' in Ubuntu's previous incarnation. Most notably, deskbar-applet. The last time I installed that, BAM, it was up and running (and I could search for things using beagle from there). This time around, I just can't find it.
I'm going to play in the Terminal some more (that worked for CheckGmail and the ToVid GUI), after all) but I'm just at a loss for why doing the exact same thing to the exact same Operating System (I used the same LiveCD for install both time for chrissakes) is producing a different result this time.
So...more headscratching for me, and a lot more fiddling I'm sure... but thanks everyone for all the advice so far. (And I hope you don't mind that my posts always tend to be so long-winded).
((Also, also, apologies that the unfortunate colon-parenthases combo in my first post turned into that godawful emoticon. That's not my style.)

---

### Post by ComplexNumber on 2007-02-01
[quote=3rdalbum]Beagle isn't a program that appears under your Applications menu either; it's really just the "backend" for Nautilus' Search function and the Deskbar.[/quote]
it does appear in the menu (you're thinking of libbeagle). its circled in red in the 1st screenshot screenshot. also, its not just  a backend for nautilus search - its a gui as well (see 2nd screenshot)

---

### Post by Falconi on 2007-02-01
Thanks a lot to all of you for all your tips and to geekchicohio for popping the question: Finding what I've "installed" :confused: . 

A couple of weeks ago I decided to get some Linux-knowledge, after having used Windows a lot for several years. Having visited several Linux-forums it seems like I'm not the only one who's leaving Windows and turning into a Linux-user.

I installed an old version of SUSE (9.2) and tried Mandriva Live-disk, and I must say, that I'm sure that I'll dump my XP as soon as possible.

With my SUSE I have exactly the same problem "Finding what I've installed". I've put the question on a Danish Linux-Forum, but haven't got any answers yet. Therefore reading this thread has been exstremely useful to me, especially because I'm going to download and install UBUNTU in a couple of days.

Maybe the UBUNTU will help me solve my problems with my Lexmark printer and WinFasts 2000 xp TV-card, which I'm having using SUSE 9.2.

Once again - thanks for your help - and sure I'll be back in this forum. :D 

Regards
Falconi

---

### Post by jackrobinson on 2007-02-01
> **geekchicohio said:**
> I just used automatix to uninstall and then re-install the Debian Menu. Still no dice on that one.

after you install the debian menu, 
do this:
```
sudo update-menu
```
then enable it from alacarte.

---

### Post by funky^munky on 2007-04-01
Hi all

What is alacarte?

---

### Post by funky^munky on 2007-04-01
Hi all

I am very very new to ubuntu/linux i only installed ubuntu v6.10 a few days ago in an attempt to free myself of microsnots cracked windows. I have to say so far i am not impressed I know its  early days and a steep learning curve etc and i should be patient but so far many programs have crashed/frozen eg.

The first thing i did was update my system with the update manager, since then every time i boot up i have 2 ubuntu systems on my PC in the login window 

first ubuntu 6:11
       ubuntu 6:11 safe mode
       ubuntu 6:10 
       ubuntu 6:10 safe mode 
       etc.........
       etc...........
      windows XP

or something along those lines cant remember exact phrases used, anyhow it certainly wasnt me all i did was use update manager it did the rest.

secondl
 :vlc player freezes the whole OS when I change skini! please dont tell me its user error :(

and i have encountered many problems some of my own doing I fully admit, others simply because they dont work. 

Which brings me somewhat slowly to the point of my post in this thread I too have encountered the very same problems with missing apps/programs including the very same problem with debian menu installed from automatix2. This must be a bug not a user issue. Its there in system>preferences>menu layout,  but it wont allow me to check the box to  show it on applications menu!

Plus when I use the sudo commands suggested. I receive this message

: sudo: update-menu: command not found

I do get that message frequently when I type commands suggested on various websites

furthermore many other progs have just disappeared for example i installed avast4worksation ( i know they say linux doesnt suffer virii, but i felt naked without a trusted anti-vir) anywayi have found the app installed in synaptic but how do i launch it? and how do i put it on my desktop etc?

Thank you for suffering my rant, I appreciate ubuntu is FREE, its a work in progress, and it has probably taken many many people hundreds of hours of their own free time making this OS for whiners like myself, but its so frustrating when things dont work properly and everyone wants to point the finger at the user all the time :_(

I will continue to persevere with ubuntu cos the only other option is windows and thats getting more and more restrictive to the point i have to wonder who owns my PC me or microsnot.

---

