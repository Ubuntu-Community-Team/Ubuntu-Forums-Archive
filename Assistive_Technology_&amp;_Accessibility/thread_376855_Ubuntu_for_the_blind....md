---
title: "Ubuntu for the blind..."
date: 2007-03-05
forum: Assistive Technology &amp; Accessibility
---

### Post by diablo75 on 2007-03-05
I have a friend who uses Windows XP with JAWS to make his way around the computer.  JAWS is a text to speech application that reads menus, buttons, and other stuff off so the user can hear what they have their cursor or mouse over, etc.

I am wanting to know if there is a program out there that does this in a similar fashion that runs on Ubuntu.  I think he'd be willing to give it a shot if I installed in on his laptop for him.

---

### Post by jaustin19 on 2007-03-05
If you haven't been swamped with replies, Gnopernicus has a screen reader similar to Jaws.  It requires the Gnome interface and at present I can not make it start on boot.  The accessibility features must be turned on, (note on the screen " changes on this screen will not take effect until you logout" )  By futsing with default speech and startup settings then logout/login will usually start the speech function.  It can usually be maintained on Hibernate.  Sometimes it will come up from a cold boot, but not reliably as a blind person needs.  This appears to be a very comprehensive effort so far as utility and documentation.  But it is not trouble free for a novice or a blind person.  Any thoughts

---

### Post by Pipistrelle on 2007-03-09
I am totally blind and use both operating systems. Ubuntu accessibility is still in the early stages, and getting better all the time, but I don't think it would be a good idea to switch over to it just yet. Web accessibility is minimal, but email with evolution and media players work great. I believe that Firefox 3.0 will be working soon, so stay tuned. Also, I find that Orca works best with Gnome, and it can be loaded by pressing alt+f2, then typing orca.

Teresa

---

### Post by Pipistrelle on 2007-03-10
Well, seems I was a little hasty in my judgment, there. It looks like there are updates to both Firefox and Orca that make it work well. I haven't tried it yet myself, but it looks promising. The only thing I'm unsure of is whether I need to update it manually or whether the updates are included in Add/Remove or other update utilities. (I know just enough about command-line stuff to make me dangerous.)

Anyhow, here's a useful link on Firefox and Orca:
[http://live.gnome.org/Orca/Firefox#details](http://live.gnome.org/Orca/Firefox#details)

Teresa

---

### Post by sedition on 2007-04-04
I'm actually working on putting together a live CD for my long-time friend, who wasn't born blind, but now is. After a lot of frustration with XP and JAWS he asked about test driving my OS of choice, Ubuntu. After reading up on Linux accessibility, I decided to use the text-install as a base. Since he only uses his laptop for email, intarwebs, music and playing MUDs, then I don't see him really needing a GUI.  I'm a firm believer in Occam's Razor and it's simply more efficient (once you learn the commands) to use the CLI and enable speakup->speech-dispatcher->espeak for TTS. Sort of along the lines of Oralux, but without Emacspeak. He's a friggin' brilliant guy and he'll pick everything up via the customization I've been adding and reading man pages in no time. A good place to start doing some research on how far along accessibility is and the problems users encounter would be the BLinux mailing list. There are numerous tools out there, but you really won't know how effective they are until you unplug your monitor and try to actually use them.

---

### Post by Rkgoboom on 2007-04-25
I would be very interested in a copy of that live CD. Please could you maybe torrent the .iso? I am a linux newb and am not up to the task of making one yet.

---

### Post by w9fyi on 2007-06-30
I'm having difficulty using firefox, and evolution in ubuntu 7.04.  When I'm browzing the webusing firefox, I'm unable to determine different elements of a page.  Also in evolution, i'm having difficulty gettinng in to my inbox.  I can finally see messages in the list, when I'm in my inbox, but when i press enter or ctrl-o to ppen the message, I can't read it.  I can however see the headers if I'm pressing tab.  Any help would be appreciated.

---

### Post by djringjr on 2008-02-17
We are also trying to get a keyboard driven distro for the blind!

[http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b](http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b)

Any help is requested especially from those who have brailler terminals.

Best

David Ring

---

### Post by sedition on 2008-02-19
Still working on the live cd version, but I threw together a quick how to on a TTS text-only install of 6.10 here:
[http://ubuntuforums.org/showthread.php?t=634272](http://ubuntuforums.org/showthread.php?t=634272)

---

### Post by drbongo on 2008-11-28
I am happy to announce the release of Vibuntu 1.0 (aka Vinux) a remaster of the Intrepid Ibex live CD customised to the needs of blind and partially sighted users! It is designed to boot from a live cd or USB memory stick, log you in automatically and then start up the Orca screen-reader. Full-screen magnification can then be activated with a simple keystroke.

The type of magnification on offer depends upon whether you downloaded the 2D or 3D version of Vibuntu. The 2D version only offers basic options but will run on any computer, while the 3D version offers advanced features but requires a powerful 3D graphics card. If you are in any doubt as to which version is best for you or do not require magnification at all I recommend you download the safer 2D version. Vibuntu is available from the following URL's:

[http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-2D-1.0.zip](http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-2D-1.0.zip)

[http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-3D-1.0.zip](http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-3D-1.0.zip)

Inside the zip file you will find iso image and a text file containing the md5sum of the iso image (not the zip file).

You can use Vibuntu as a live CD, a portable operating system on a USB memory stick* or you can install it to your hard drive either alongside or as a replacement for Windows. In order to fit all of the accessibility settings on the CD I have had to remove some applications including: The GIMP graphical image manipulation program, the F-Spot photo-manager and the Ekiga voice over IP package. You can easily reinstall these and many more open-source applications if you choose to install it on your hard-drive. I used the RemasterSys package to create Vibuntu and I have included this package on the CD incase you want to make your own customised live CD. N.B. The default username and password is 'orca', and this will be retained even if you install it to your hard-drive, no matter what you type in during the installation process.

(*Using Unetbootin)

I would of course appreciate any feedback on Vibuntu. What do you think of the name? Is it corny enough? Would Vinux be better? Post any feedback good or bad on this thread.


Enjoy yourself,

drbongo

P.S. What follows is a list of keystrokes you can use to control the screen-reader and magnification software. I will only provide a few basic keystrokes for Orca to get you started as they are all listed in the preferences window and are unchanged from the default settings. I have provided an exaustive list of the magnification keystrokes as I have customised them to make them easier to remember!

ORCA...

Open Preferences Window: insert+space
Open Main Menu: alt+F1
Move Through Menu/Text: up, down, left and right
Move Through Form: tab, shift+tab
Toggle Voice On/Off: insert+s
Quit Orca: insert+q

BASIC 2D MAGNIFICATION...

Toggle Magnification On/Off: insert+m
Increase Magnification: insert+(plus)
Decrease Magnification: insert+(minus)

ADVANCED 3D MAGNIFICATION...

Zoom In: win+z (win+left-mouse)
Zoom Out: win+x (win+right-mouse)

Zoom x1: win+1
Zoom x2: win+2
Zoom x4: win+3

Toggle Magnifier Box: win+m
Zoom In Magnifier Box: ctrl+left-mouse
Zoom Out Magnifier Box: ctrl+right-mouse

Resize Window: win+r
Zoom To Window: win+w

ADVANCED 3D MOVEMENT...

Pan Right: win+right
Pan Left: win+left
Pan Up: win+up
Pan Down: win+down

Lock Zoomed Window: win+l

Centre Mouse Pointer: win+c
Toggle Highlight Mouse Pointer: win+h

ADVANCED 3D COLOURS...

Toggle Invert Colours: win+i
Toggle Invert Window Colours: shift+win+i

Toggle Filter Colours: win+f
Toggle Window Filter Colours: shift+win+f
Switch Filter Colours: win+s

Decrease Window Brightness: win+(minus)
Increase Window Brightness: win+(plus)

Decrease Window Saturation: shift+win+(plus)
Increase Window Saturation: shift+win+(minus)

Toggle Dim Inactive Windows: win+d

This list of keystrokes will automatically load into Gedit when Vibuntu boots!

---

### Post by drbongo on 2008-11-29
Installing Vibuntu...

At the moment the Orca Screen-Reader does not support the Ubuntu Installer GUI (Ubiquity). Therefore for the time being to install Vibuntu to the hard-drive of your computer you will either need sighted assistance or you can try the following step by step instructions. N.B. These instructions will wipe your hard-drive and install Vibuntu with the English language, USA keyboard settings and the New York time zone.

1. Press Alt+F2 to open the Run dialogue
2. Type in the password 'orca' then press Enter
2. Type 'ubiquity' then press Enter
3. Press Alt+F to accept the default language (English)
4. Press Alt+F again to accept the default time zone (New York)
5. Press Alt+F again to accept the default keyboard layout (USA)
6. Press Down twice then Alt+F to partition the whole disk
7. Type in your name then press Tab
8. Type in your username the press Tab
9. Type in your password then press Tab
10. Type in your password again and then press Tab
11. Type in the name of the computer then press Tab
12. Press space bar to select automatic login then press Alt+F
13. Press enter to start the installation.

N.B. You can press Alt+B to go back a step at any time, or Alt+F4 to abandon the process.

The installation will take 10-20 minutes to complete
When the CD and Hard-Drive has stopped spinning press Enter to restart the computer
When the CD ejects remove it from the drive and press Enter again to restart the computer.

If you have any problems please port in the Vibuntu thread on the Ubuntu Forums.

drbongo

---

### Post by djringjr on 2008-11-29
drbongo, greetings.  Word reached me by the Coconut Wireless that Vibuntu 1.0 was released.  Congratulations.

Could you post to the Vibuntu thread the required 3D card that is needed or supported for the 3D version?

For those who wish to find the Vibuntu thread with ease, the message on the coconut wireless contained the following link:  [Vibuntu 1.0]("http://ubuntuforums.org/showthread.php?t=996151&highlight=Vibuntu")

The coconut wireless also mentioned that it was responsible for the hiccup that caused three postings and apologized for the problem and added that you could delete the two duplicate posts.

My very best wishes to you,

DR

---

### Post by drbongo on 2008-11-30
Thanks I will attempt to delete the extra posts and check out the coconut website.

drbongo

---

### Post by Entwicklung Medizinproduk on 2009-01-18
> **djringjr said:**
> We are also trying to get a keyboard driven distro for the blind!

[http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b](http://www.murga-linux.com/puppy/viewtopic.php?t=24571&sid=284fe90df919d1327ce503b6dd35f63b)

Any help is requested especially from those who have brailler terminals.

Best

David Ring

Well, technology always find a solution to make work easier and to help people. A keyboard for blind is nice.

---

### Post by seboo on 2009-02-01
Hi,
i'd like to try your ubuntu distribution with orca.
which are the voices included?
eloquence sapi, real speak?
french voice?
if eloquence sapi are not included is it possible to add new voices easily.
is the default keyboard US?

sorry for the newby questions, but i'm blind and and it will be my first try on a linux system.
i use to work with window-eyes on windows xp.
thanks in advance
best regards
seb

---

### Post by Sarai the Geek on 2009-02-14
This might go without saying, but before you install ubuntu on a computer that's going to be using any sort of text-to-speech software, don't forget to run a live CD to ensure that audio will work. 
In most cases, even if it doesn't work out of the box it can be fixed with some work, but not all. It took me a week to get my computer to even produce any sound, and I've never been able to get headsets to work. Apparently it's a known problem with my audio card but no one seems to have a fix. For me, it's *c'est la vie*, but if I was using a screen reader it would be incredibly frustrating.

---

