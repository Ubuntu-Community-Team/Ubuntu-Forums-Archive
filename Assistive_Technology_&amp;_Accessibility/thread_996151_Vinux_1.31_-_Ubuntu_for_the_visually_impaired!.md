---
title: "Vinux 1.31 - Ubuntu for the visually impaired!"
date: 2008-11-28
forum: Assistive Technology &amp; Accessibility
---

### Post by drbongo on 2008-11-28
I am happy to announce the release of Vinux 1.4!

NB: If you have any questions about Vinux please ask them on the Vinux Mailing list not
here as while the moderators of this mailing list are prepared to tolerate occasional
announcements about Orca related Linux releases it is not the right place to discuss
these packages and/or distributions!

Vinux a free and open source operating system which has been optimised for visually impaired
users. It is based on the popular Ubuntu Linux distribution and built around the Orca 
screen-reader/magnifier. It is designed to boot your computer, log you in automatically
and then start up the Orca screen-reader with Braille support. Full-screen 
magnification can then be activated with a simple keystroke.

New Features for 1.4!

Security: Unlike previous versions Vinux 1.4 has been built from scratch
using the Ubuntu 'mini.iso' 10MB network installation which means it 
contains all of the latest packages and security patches as of the day of 
release.

Audible Boot Prompt: The Live CD now sounds the system bell three times
when the boot prompt appears on the screen, which then gives you thirty 
seconds to type in any cheatcodes or boot options you require. 
e.g. typing 'textonly' will boot into console only mode, you can then
type 'yasr' to start a console based screen-reader.

Braille Displays: The Live CD now supports a wide variety of serial Braille 
displays in edition to the automatic detection of USB Braille displays. 
In order to use a serial Braille display or a USB Braille display with a 
different language table you simply have to type in a short code at the 
boot prompt. e.g. 'alde' for an Alva Serial display using the German 
language table, or 'alude' for an Alva USB  display using the german 
language table. There are a full list of cheatcodes included in the 
'cheatcodes_braille_displays.txt' on the CD. By default Vinux supports
USB Braille displays using the en_uk language table.

Talking Login Screen: Once installed espeak will now ask you to enter
your username and password when the login screen is loaded providing you 
do not enable autologin during the installation process. It will not 
however echo what you type, but if you enter the wrong username and/or
password you will be asked to enter them again. It is important that you
should not enable autologin if you are using a wifi connection as the keyring
manager workaround detailed below depends upon a manual login to work!

Keyring Manager Workaround: Vinux now includes a workaround of sorts for the 
keyring manager which is currently inaccessible with Orca. We have set up a 
pre-configured keyring password 'vinux' which is retained on both the Live CD
and a full install. This means that when you try to connect to a wifi
network and Orca stops speaking when the keyring manager password dialog box
opens, you simply have to type 'vinux' into this box and as long as
autologin is not enabled you will never have to enter the keyring password
again.

Lynx Fix: Lynx, Netrik and Firefox now use a local copy of the vinux.org.uk
homepage as their starting URL's by default which means that you can 
open the broswers without problems whether you have an active internet
connection or not.

Menu Entries for Console Applications: I have added menu entries for some
of the extra console based applications provided in Vinux. This is to enable
beginners who may not know the names of these applications or their way around
the console to find and experiment with them more easily.

Download Vinux 1.4 - [http://vinux.org.uk/downloads/old/1.4/Vinux-1.4.iso](http://vinux.org.uk/downloads/old/1.4/Vinux-1.4.iso)
Check md5sum - [http://vinux.org.uk/downloads/old/1.4/Vinux-1.4.iso.md5sum.txt](http://vinux.org.uk/downloads/old/1.4/Vinux-1.4.iso.md5sum.txt)
Vinux Homepage - [http://vinux.org.uk/index.php](http://vinux.org.uk/index.php)

Full lists of all of the Keybindings for Vinux, Orca, Gnome and Yasr can be found 
in the Vinux folder in the the home directory.

Credits: I would like to thank Osvaldo La Rosa for all his hard work
in providing the audible beeps and the Braille display cheatcodes, 
and David Knight for suggesting the workaround for the keyring 
manager bug!


drbongo 24/03/2009 

UPDATE: Vinux - The new name for Vibuntu!

I am happy to announce that we have now rebranded Vibuntu as Vinux after
discussion with Canonical about the use of the 'buntu' suffix. They were
happy to let us call it the Ubuntu VI Remix but we decided to go with Vinux
which now recursively stands for Vinux Is Not Ubuntu but gnu/Linux! We have
been busy creating a new website, mailing list and development blog and hope
to have a new release out soon - Vinux 1.3! The URL's are:

Homepage: [http://vinux.org.uk/](http://vinux.org.uk/)
Development Forum/Mailing List:
[http://groups.google.com/group/vinux-development](http://groups.google.com/group/vinux-development)
Development Blog: [http://vinux-development.blogspot.com/](http://vinux-development.blogspot.com/)

There are already threads created on the forum/mailing list for bugs reports,
suggestions, help and advice and user profiles, but you are free to start new
threads on different topics if appropriate. We do not expect there to be very
high traffic initially and we will still post significant new release
annoucements on other related mailing lists. The development team currently
consists of myself, Tony Sales (aka drbongo) as the main developer and
Osvaldo La Rosa (aka ald0) who is responsible for web administration etc. We
would of course welcome support from people who would like to contribute to
the project in any way at all. I will be posting a list of small modular
tasks which people might like to take on board as needs arise. Ideally I
would like to have a core development team of 3 to 6 individuals, with
specific responsibilities and a looser collection of individuals who would
contribute on an adhoc basis when required.

The project is still very much in its infancy and there is plenty of scope
for evolution...

Hope to hear from you soon, drbongo and ald0.




Vibuntu 1.2 Released!

I am happy to formally announce the realease of Vibuntu 1.2 and I feel that this is a significant release because I have now resolved the problem of Orca beong unable to read admin apps launched from the menus and activated USB Braille Display autoprobing. This was achieved by simply changing the entries in the admin menu so they launched as an ‘application in terminal’ using the sudo or gksu command when necessary. This simply opens a terminal, asks for the admin password if required and then runs the gui application. When you close the application the terminal closes automatically and focus is returned to the Orca window.  The only exception to this is remastersys gui which for some reason does not retain focus, you have to alt+tab to move from the terminal to the remastersys gui. (This is a problem with remastersys rather than Orca/Gnome etc).  Sighted or partially sighted users are advised to open the admin apps using the desktop icons which will run the admin applications in the standard way. (Thanks to Luke Davies for this suggestion) Of course this solution only works on top of the changes recommended on the Orca SysAdmin page.

The download  URL’s are:

[http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.2.zip](http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.2.zip) 
(This is a zip file containing iso and md5sum)

[http://vibuntu.blinuxman.net/](http://vibuntu.blinuxman.net/)  and [http://blinuxman.net/vibuntu/](http://blinuxman.net/vibuntu/)
(These are standard iso downloads)

The homepage is here:

[http://blinuxman.net/projects/vibuntu.php](http://blinuxman.net/projects/vibuntu.php)

The Development Blog is here:

[http://www.vibuntu.blogspot.com/](http://www.vibuntu.blogspot.com/)

I would like to thank everyone who has contributed to this project by offering feedback, suggestions and criticisms. I would especially like to thank Osvaldo La Rosa who has enthusiastically taken on the responsibility for hosting a Vibuntu webpage and mirroring the images. This will in all probability be the last release of the year as I now want to take stock of what has been done, make available a list of  features/changes,  instructions on how to create Vibuntu from scratch and a wishlist of possible new features divided into easy, difficult and impossible! 

As ever I would appreciate continued feedback and suggestions. I will set up a thread on the Ubuntu Assistive Technology and Accessibility section for people to post their suggestions!

drbongo

Vibuntu 1.1 is ready!

The new release of Vibuntu is ready for download! It incorporates several significant improvements over the first version and a handful of small changes. Vibuntu is a remaster of the Ubuntu 8.10 'Intrepid Ibex' live CD customised to the needs of blind and partially sighted users! It is designed to boot from a live cd or USB memory stick, log you in automatically and then start up the Orca screen-reader. Full-screen magnification can then be activated with a simple keystroke.

IMPROVEMENTS...

Firstly I have resolved the problem of Orca not working with applications run with root permissions by following the recommendations posted on the official Orca website: i.e. I created an .orbitrc file for the root user, disabled the gksu keyboard grab and edited the sudoers file. This allows Orca to work with applications like the Ubiquity installer and the Synaptic Package Manager etc. However, the recommended way to launch these applications is to open a terminal by pressing 'Ctrl+Shift+t' and then typing the name of the application e.g. 'sudo ubiquity'. The reason for this is that launching these applications from the panel menus or desktop icons produces inconsistent results. In other words sometimes Orca works and sometimes it doesn't. Finding a way to solve this problem is still my top priority.

Secondly I have now merged the 2D and 3D versions of Vibuntu into a single .iso image. Vibuntu will now boot into the standard 2D magnification mode by default, however you can enable/disable the 3D magnification by simply clicking on a 
desktop icon or menu entry. This means that you can try the 3D version without any risk of major problems because if it doesn't work or crashes the display you can simply disable the 3D effects or restart your xserver by pressing Ctrl+Alt+Backspace'.

Some minor improvements include Braille support being enabled at boot, a slightly larger red mouse pointer to enhance its visibility on both dark and light backgrounds, some new keybindings to open a terminal 'Ctrl+Shift+t', to open the home directory 'Ctrl+Shift+h', to toggle window maximisation 'Ctrl+Shift+m' and to toggle fullscreen mode 'Ctrl+Shift+f'.

DOWNLOAD...

The new release is available from the following URL:

[http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.1.zip](http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.1.zip)

Inside the zip file you will find iso image and a text file containing the md5sum of the iso image (not the zip file).

The image should also be available at Osvaldo La Rosa's blinuxman.net mirror within the next 24 hours:

[http://vibuntu.blinuxman.net/](http://vibuntu.blinuxman.net/) or [http://blinuxman.net/vibuntu/](http://blinuxman.net/vibuntu/)

Osvaldo has also kindly set up a homepage for Vibuntu at:

[http://blinuxman.net/projects/vibuntu.php](http://blinuxman.net/projects/vibuntu.php)

INFORMATION...

You can use Vibuntu as a live CD, a portable operating system on a USB memory stick (Using Unetbootin) or you can install it 
to your hard drive either alongside or as a replacement for Windows. In order to fit all of the accessibility settings on the CD I have had to remove some applications including: The GIMP graphical image manipulation program, the F-Spot photo-manager, Gnome Games and the Ekiga voice over IP package. You can easily reinstall these and many more open-source applications if you choose to install it on your hard-drive. I used the RemasterSys package to create Vibuntu and I have included this package on the CD in case you want to make your own customised live CD. N.B. The default username and password is 'orca', and this will be retained even if you install it to your hard-drive, no matter what you type in during the installation process. (You can change this by typing 'sudo passwd orca' into a terminal and then typing the new password twice)

As always I would of course appreciate any feedback on Vibuntu.  Post any feedback: good, bad or just plain ugly on this thread.

KEYSTROKES...

What follows is a list of keystrokes you can use to control the screen-reader and magnification software. I will only provide a few basic keystrokes for Orca to get you started as they are all listed in the preferences window and are unchanged from the default settings. I have provided an exaustive list of the magnification/display keystrokes as I have customised them to make them easier to remember!

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

GNOME...

Open a Terminal: ctrl+shift+t
Open the Home Directory: ctrl+shift+h
Toggle Window Maximisation: ctrl+shift+m
Toggle Full-screen Mode: ctrl+shift+f

This list of keystrokes will automatically load into Gedit when Vibuntu boots!

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

### Post by drbongo on 2008-11-29
Installing Vibuntu...

At the moment the Orca Screen-Reader does not support the Ubuntu Installer GUI (Ubiquity). Therefore for the time being to install Vibuntu to the hard-drive of your computer you will either need sighted assistance or you can try the following step by step instructions. N.B. These instructions will wipe your hard-drive and install Vibuntu with the English language, USA keyboard settings and the New York time zone.

1. Press Alt+F2 to open the Run dialogue
2. Type 'ubiquity' then press Enter
3. Type in the password 'orca' then press Enter
4. Press Alt+F to accept the default language (English)
5. Press Alt+F again to accept the default time zone (New York)
6. Press Alt+F again to accept the default keyboard layout (USA)
7. Press Down twice then Alt+F to partition the whole disk
8. Type in your name then press Tab
9. Type in your username then press Tab
10. Type in your password then press Tab
11. Type in your password again and then press Tab
12. Type in the name of the computer then press Tab
13. Press space bar to select automatic login then press Alt+F
14. Press enter to start the installation.

N.B. You can press Alt+B to go back a step at any time, or Alt+F4 to abandon the process.

The installation will take 10-20 minutes to complete
When the CD and Hard-Drive has stopped spinning press Enter to restart the computer
When the CD ejects remove it from the drive and press Enter again to restart the computer.

If you have any problems please port in the Vibuntu thread on the Ubuntu Forums.

drbongo

---

### Post by drbongo on 2008-11-29
If you want to connect to a wireless network using Orca, you need to press Alt+F2, type nm-connection-editor and fill in the network name and any WEP/WPA keys etc. I will add a menu entry for this in the next version.

drbongo

---

### Post by drbongo on 2008-11-29
I have just discovered that the reason Orca doesn't work with Ubiquity is that for some reason the Orca settings only work for the user who logged in, thus when you open any app as root Orca stops working in those windows. I have managed to work around this by setting up a root password, logging in as root, starting Orca and then running ubiquity! It looks like the only way around this is to log in as root when you want to perform root admin tasks. I will investigate more tomorrow, I might be able to set up a root login account with a Orca setup and include it on the live CD. I will post a more detailed work around for ubiquity and connecting to a wireless network tomorrow using Orca.

And before I get lambasted for suggesting someone log in as root, I know this is risky, but if you are blind and there is no other way to perform these tasks independently what would you do?

drbongo :guitar:

---

### Post by drbongo on 2008-11-29
I have just discovered that the reason Orca doesn't work with Ubiquity is that for some reason the Orca settings only work for the user who logged in, thus when you open any app as root Orca stops working in those windows. I have managed to work around this by setting up a root password, logging in as root, starting Orca and then running ubiquity! It looks like the only way around this is to log in as root when you want to perform root admin tasks. I will investigate more tomorrow, I might be able to set up a root login account with a Orca setup and include it on the live CD. I will post a more detailed work around for ubiquity and connecting to a wireless network tomorrow using Orca.

And before I get lambasted for suggesting someone log in as root, I know this is risky, but if you are blind and there is no other way to perform these tasks independently what would you do?

drbongo :guitar:

---

### Post by drbongo on 2008-11-29
I have just discovered that the reason Orca doesn't work with Ubiquity is that for some reason the Orca settings only work for the user who logged in, thus when you open any app as root Orca stops working in those windows. I have managed to work around this by setting up a root password, logging in as root, starting Orca and then running ubiquity! It looks like the only way around this is to log in as root when you want to perform root admin tasks. I will investigate more tomorrow, I might be able to set up a root login account with a Orca setup and include it on the live CD. I will post a more detailed work around for ubiquity and connecting to a wireless network tomorrow using Orca.

And before I get lambasted for suggesting someone log in as root, I know this is risky, but if you are blind and there is no other way to perform these tasks independently what would you do?

drbongo :guitar:

---

### Post by drbongo on 2008-11-29
Sorry, previous message got posted three times - I got an error message when I clicked on submit three times in a row - then suddenly it uploaded three times! Sorry...

drbongo

---

### Post by djringjr on 2008-11-29
drbongo, is it possible to install the vibuntu files on top of an existing Ubuntu 8.10 installation, and when at the log in screen choose Vibuntu?

Also please tell us what 3D cards are supported and if there is any minimum requirements.  I have an old Nvidia card, a GE Force2 - MX/MX 400 card which is about 10 years old now.

Keep up that crazy beat on those bongos!

DR

---

### Post by drbongo on 2008-11-30
All the packages you need to create a Vibuntu setup are installed by default in the Ubuntu 8.10 Live CD. All I have done is to set up an Orca configuration so it is on the highest verbosity settings (i.e. it reads out everything it can) and added three key bindings so that the Orca magnifier can be enabled and disabled with a keystroke. I have also set up some customised key bindings to take advantage of the Advanced Desktop Zoom settings provided by Compiz, but this will only work with a newish graphics cards. I then remastered the CD using Remastersys and installed it to a USB stick using Netbootin.

I have actually tested the mx400 and it doesn't support Compiz. I believe you would need an ATI Radeon 9550 or newer and/or an Nvidia Geforce 8 Series or newer. It works on some laptops e.g. a Sony Vaio NR11M and TX3XP but not on a Toshiba Satellite A100 or A300. Obviously the 3D version offers much more advanced features but the 2D version works perfectly well - but I would recommend using keystrokes to navigate rather than the mouse as it results in a much smoother display.

So the answer to your question is yes - you can choose a Vibuntu setup at login by creating two user accounts, one normal and one with accessibility functions. The easiest way to do this would be to download and install Vibuntu and then simple create a new user account which would have the normal Ubuntu looks and settings!

Let me know if you want any more help!

drbongo:guitar:

---

### Post by djringjr on 2008-11-30
Dr. Bongo,

Is this Vibuntu 1.0 a Command Line Interface (CLI) Linux with optional X server?  Perhaps I had misunderstood.  A CLI program for the blind is much more desirable as it is difficult - and often impossible - to locate X Windows and read them as it is really a "hunting game" with a mouse on a screen that is black and unreadable to the blind!

Best

DR

---

### Post by cmay on 2008-11-30
> I would of course appreciate any feedback on Vibuntu. What do you think of the name? Is it corny enough? Would Vinux be better? Post any feedback good or bad on this thread.thanks for this. i have been following a distro once that was called blinux but it died out. 
i am so happy that there is something like this now. thanks. if you need any help translating from english to danish ever i will be happy to help as much as i can. i am not that much affected yet by my eyes being bad as they are but it will maybe come . so i am very grateful for something like this. 
thanks.

oh , and vibuntu sounds just great. if the name should turn out be too much alike ubuntu for some reason then  vinux is also a very good name. 

anyway i am going to try this out. 
thanks again. :)

---

### Post by drbongo on 2008-12-01
> **djringjr said:**
> Dr. Bongo,

Is this Vibuntu 1.0 a Command Line Interface (CLI) Linux with optional X server?  Perhaps I had misunderstood.  A CLI program for the blind is much more desirable as it is difficult - and often impossible - to locate X Windows and read them as it is really a "hunting game" with a mouse on a screen that is black and unreadable to the blind!

Best

DR

Vibuntu uses the same Gnome desktop as the Ubuntu 8.10 release but with the preconfiguration of accessibility software. Although using a command line is probably easier than navigating GUI's for someone who is a fairly competant IT user, beginners and people moving over from windows find it very confusing. Also from an educational point of view, having a GUI makes it much easier for someone to teach a VI learner how to use a computer because they can see where the focus is and where the learner needs to get to etc. There is nothing to stop you using Vibuntu completely from the terminal of course. But I will try to include a terminal based screen-reader like yasr or speakup in the next version so you can spend the whole session in a virtual terminal setup by pressing Ctrl+Alt+(F1-F6) once Vibuntu is running.(Press Ctrl+Alt+F7 to return to the GUI session)

The rationale behind Vibuntu is to create a single OS that both sighted and visually impaired users can use rather than expecting VI users to use an OS and/or applications that are unfamiliar to the general population and therefore only serve to further ostracise the visually impaired from the community at large. 

Thanks for the feedback, I completely understand your point of view, because some of the VI learners I work with are competent hackers at the command line. However the vast majority are not and just want to do simple things like write text, send e-mails and browse the net which isn't that difficult using a GUI based screen-reader and a few keyboard shortcuts etc.


drbongo:guitar:

---

### Post by drbongo on 2008-12-01
Update: I am now working on a bash script that will enable Orca to work during installation. It kills the existing orca session, restarts it using sudo so it works with the root user account and then starts ubuiquity. This allows you to install ubuntu using Orca and then restart the computer with the original Orca settings.

I have managed to get it to work but it still needs a few tweaks to make it work smoothly such that the user doesn't even notice the change. I am hoping that I will then be able to modify this script so it runs anytime a user uses sudo to run applications as root.

drbongo

---

### Post by drbongo on 2008-12-01
I have only just started this project, but there seems to be a reasonable amount of interest, and I intend this to be a long term commitment. There is certainly a niche for a mainstream distro which is accessible for VI users. 

I would like to know if there is anyone who might like to contribute to the project in whatever way they can.  I intend to do most of the work but I would appreciate having a small group of people I can call on when needed as I will be doing most of this work in my own time.

You do not have to be an elite hacker, I certainly am not, all I want is enthusiasm and reliability. I envisage asking people to perform small modular tasks which do not involve anyone having to make a major commitment to the project.

For example I would be happy to hear from people who would occasionally be willing to test pre-releases and identify bugs, write (or recording) short how-to's on performing certain tasks with access technology, designing a logo, desktop backgrounds or themes, recording short audio messages to provide` users with audio feedback when a screen-reader is unavailable, writing small scripts to improve accessibility, testing apps for accessibility, hosting or  mirroring the distro, providing technical advice and guidance to users and even just providing suggestions for improvements.

Having a visual impairment is not necessary, but would be an advantage to at least know or work with someone who has a visual impairment so you have an understanding of the issues involved.

I envisage Vibuntu (or Vinux - haven't decided yet!) being a simple to use OS which makes it as easy as possible for visually impaired users to get the Linux experience and give up using expensive commercial software running on an expensive commercial operating system. However I want it to be just as attractive to sighted users by keeping the standard Gnome desktop and apps instead of tailoring it exclusively for the visually impaired. I envisage it being used in schools and colleges with VI learners, as a flexible OS on a family computer, or as an easy introduction to computing for older people who are losing their sight. Thats the ideal - but it is going to take quite a bit of work to get it there...

Does anyone share my vision?

Can't wait to hear from you! Please provide an e-mail address and an idea of what you would be willing to do, and a link to anything you have already done (if applicable).

I will not reveal any of this information if you want to remain anonymous.

Please send me a private message and I will send you my email
drbongo:guitar:

---

### Post by drbongo on 2008-12-02
Update: From information gleaned from Orca mailing list it seems that there is a relatively simple fix for the orca/administrator problem which involves creating an orbitrc file for the root user. I have not tested this yet, I am sure it will work, but I am not certain whether remastersys will retain this file or not! If it works that will be a major improvement and I will release the second version as soon as I have remastered it.

It seems that the idea of setting up a root account has already been used successfully, and other uses have manually done what I was going to do with a simple bash script, so there are two fairly safe backup options if the orbitrc hack doesn't work with remastersys.

drbongo:guitar:

---

### Post by drbongo on 2008-12-04
UPDATE: Vibuntu 1.0 is now also available from the following mirrors* 

[http://vibuntu.blinuxman.net/](http://vibuntu.blinuxman.net/)
[http://blinuxman.net/vibuntu/](http://blinuxman.net/vibuntu/)

*Special thanks to Osvaldo La Rosa (aka Ald0) for this generous offer!

---

### Post by Arrakeen on 2008-12-05
Hi,
    I found this thread just a couple of days ago after searching for a distro for my Mother - she's suffering from AMD and has reached the end of the road as far as simply making the fonts bigger on the screen.

   She's been looking at a commercial system and when she said it was a £1000+ I started to think I should look for a more open solution.

    I'm sure she'd be a willing tester - I've downloaded both the 2d & 3d version and will see which works better on her setup.

    I'm more than willing to help - but must admit that while I work in IT networking and am pretty fluent in Linux I'm not a coder (well not for the last 16 years) and get kind of lost when asked to do installs that don't use a package manager.

    I've PMd my email address and would be happy to help in anyway I can.

Keep up the good work.

Phil.

---

### Post by drbongo on 2008-12-08
Vibuntu 1.1 is ready! (I have replaced original first post with this announcement)

The new release of Vibuntu is ready for download! It incorporates several significant improvements over the first version and a handful of small changes. Vibuntu is a remaster of the Ubuntu 8.10 'Intrepid Ibex' live CD customised to the needs of blind and partially sighted users! It is designed to boot from a live cd or USB memory stick, log you in automatically and then start up the Orca screen-reader. Full-screen magnification can then be activated with a simple keystroke.

IMPROVEMENTS...

Firstly I have resolved the problem of Orca not working with applications run with root permissions by following the recommendations posted on the official Orca website: i.e. I created an .orbitrc file for the root user, disabled the gksu keyboard grab and edited the sudoers file. This allows Orca to work with applications like the Ubiquity installer and the Synaptic Package Manager etc. However, the recommended way to launch these applications is to open a terminal by pressing 'Ctrl+Shift+t' and then typing the name of the application e.g. 'sudo ubiquity'. The reason for this is that launching these applications from the panel menus or desktop icons produces inconsistent results. In other words sometimes Orca works and sometimes it doesn't. Finding a way to solve this problem is still my top priority.

Secondly I have now merged the 2D and 3D versions of Vibuntu into a single .iso image. Vibuntu will now boot into the standard 2D magnification mode by default, however you can enable/disable the 3D magnification by simply clicking on a 
desktop icon or menu entry. This means that you can try the 3D version without any risk of major problems because if it doesn't work or crashes the display you can simply disable the 3D effects or restart your xserver by pressing Ctrl+Alt+Backspace'.

Some minor improvements include Braille support being enabled at boot, a slightly larger red mouse pointer to enhance its visibility on both dark and light backgrounds, some new keybindings to open a terminal 'Ctrl+Shift+t', to open the home directory 'Ctrl+Shift+h', to toggle window maximisation 'Ctrl+Shift+m' and to toggle fullscreen mode 'Ctrl+Shift+f'.

DOWNLOAD...

The new release is available from the following URL:

[http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.1.zip](http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.1.zip)

Inside the zip file you will find iso image and a text file containing the md5sum of the iso image (not the zip file).

The image should also be available at Osvaldo La Rosa's blinuxman.net mirror within the next 24 hours:

[http://vibuntu.blinuxman.net/](http://vibuntu.blinuxman.net/) or [http://blinuxman.net/vibuntu/](http://blinuxman.net/vibuntu/)

Osvaldo has also kindly set up a homepage for Vibuntu at:

[http://blinuxman.net/projects/vibuntu.php](http://blinuxman.net/projects/vibuntu.php)

---

### Post by drbongo on 2008-12-12
Vibuntu 1.2 Released!

I am happy to formally announce the realease of Vibuntu 1.2 and I feel that this is a significant release because I have now resolved the problem of Orca beong unable to read admin apps launched from the menus and activated USB Braille Display autoprobing. This was achieved by simply changing the entries in the admin menu so they launched as an &#8216;application in terminal&#8217; using the sudo or gksu command when necessary. This simply opens a terminal, asks for the admin password if required and then runs the gui application. When you close the application the terminal closes automatically and focus is returned to the Orca window.  The only exception to this is remastersys gui which for some reason does not retain focus, you have to alt+tab to move from the terminal to the remastersys gui. (This is a problem with remastersys rather than Orca/Gnome etc).  Sighted or partially sighted users are advised to open the admin apps using the desktop icons which will run the admin applications in the standard way. (Thanks to Luke Davies for this suggestion) Of course this solution only works on top of the changes recommended on the Orca SysAdmin page.

The download  URL&#8217;s are:

[http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.2.zip](http://www.rnc.ac.uk/mct/linux/vibuntu/Vibuntu-1.2.zip) 
(This is a zip file containing iso and md5sum)

[http://vibuntu.blinuxman.net/](http://vibuntu.blinuxman.net/)  and [http://blinuxman.net/vibuntu/](http://blinuxman.net/vibuntu/)
(These are standard iso downloads)

The homepage is here:

[http://blinuxman.net/projects/vibuntu.php](http://blinuxman.net/projects/vibuntu.php)

I would like to thank everyone who has contributed to this project by offering feedback, suggestions and criticisms. I would especially like to thank Osvaldo La Rosa who has enthusiastically taken on the responsibility for hosting a Vibuntu webpage and mirroring the images. This will in all probability be the last release of the year as I now want to take stock of what has been done, make available a list of  features/changes,  instructions on how to create Vibuntu from scratch and a wishlist of possible new features divided into easy, difficult and impossible! 

As ever I would appreciate continued feedback and suggestions. I will set up a thread on the Ubuntu Assistive Technology and Accessibility section for people to post their suggestions!

drbongo

---

### Post by drbongo on 2008-12-12
I have written a short press release aimed at VI users who may not know about
Linux. I would be grateful if you could post it on any general
accessibility/software sites/forums you use if you think it would be a good
way of getting the uninitiated to give Linux a try! If we manage to get
enough interest from a few institutions, charities or government agencies it
may be possible to obtain some funding for a few developers to work on the
project full or part-time! Thanks for all the support. I hope people on the
mailing lists don't think I just a self-promoting megalomaniac, I really do
want to help VI users and I believe (perhaps naively) that Vibuntu is a step
in the right direction. Please feel free to shoot me down in flames! <straps
on his asbestos wings and applies liberal amounts of sun-block> The press
release follows!


Vibuntu - The first Linux distro to be fully accessible to blind and
partially sighted users out of the box!



Vibuntu is a customised version of the popular Ubuntu Linux distribution
optimised to meet the needs of visually impaired users by default. Vibuntu
comes in the form of a live CD  which you place in the CD drive and then
restart your computer. Once it boots a screen-reader is activated, USB
Braille displays are automatically detected and full screen magnification can
be turned on/off with a simple keystroke. Vibuntu also provides an attractive
visual interface which makes it suitable for sighted, partially sighted and
blind users. You can navigate the menus and applications using the
screen-reader and/or Braille display or switch this support off and use the
full screen magnification. This is an ideal way of introducing visually
impaired users to the Linux operating system which offers a free and
open-source alternative to expensive proprietary software. This is very safe
and secure way to let someone experience Linux and experiment without taking
any risks or making any changes to your computer. You can continue to use
Vibuntu as a live CD or install it to your hard drive either alongside
Windows or as a complete desktop replacement. It is also possible to install
and run Vibuntu from a USB memory stick if your computer supports USB
booting. If you are interested in trying Vibuntu or would just like to know
more about it please visit the project website at
[http://blinuxman.net/projects/vibuntu.php](http://blinuxman.net/projects/vibuntu.php)

---

### Post by drbongo on 2008-12-12
I had a message today from a large charity organisation who want to fund the development of a nvda-compatible full-screen magnifier  to run on windows from a USB pendrive for third world countries etc. They where thinking of basing it on python. Is this something you would be interested in working on either yourself or together. It looks like there would be funding available to do this either as an individual or through the college. I suggested that if you took a python/SDL approach you could probably use the graphics engine to send the screen to a virtual display and then use the real display to focus on smaller areas of the virtual screen (like compiz) however the tricky bit would be getting good quality font smoothing and caret tracking. I also suggested that it might make more sense to try and port/adapt an existing linux magnifier like gnome-magnifier or the accessibility modules of compiz. A penny for your thoughts!

drbongo

---

### Post by drbongo on 2008-12-13
Because Vibuntu uses a pre-configured user account, the username and password
are retained after an install. This has confused a few people. You can change
both your user name and password after install using the terminal.

To change your password type 'sudo passwd orca', enter the password orca,
then enter the new password twice.

To change your username type 'sudo usermod -l newname oldname' into a
terminal, enter your password, press enter and then log out and back in again
using the new username.

I will include the username change command in the help file in the next
version of Vibuntu.

drbongo

---

### Post by linuxguymarshall on 2008-12-13
Most people who are visually impaired and need to use a computer already paid $150 for a GeekSquad lame-*** to come to their house, another $1500 for a computer that is more than they need, $250 more for in-home setup and $250 more for software and hardware geek squad said they "needed"

in other words, they wont switch.

---

### Post by drbongo on 2008-12-14
Hi, unfortunately I think you are correct! But it is just because of this that I want to make Vibuntu. I hope in the future that we can avoid people falling into this expensive trap in the first place, or at least show them that there is an alternative to paying for yet another expensive upgrades to their operating system and accessibility software.

drbongo

---

### Post by drbongo on 2008-12-15
I have now posted a rough guide to how I made Vibuntu 1.2 from a default
install of Ubuntu 8.10 (Intrepid Ibex) on the Vibuntu Development Blog for
anyone who is interested - [http://vibuntu.blogspot.com/](http://vibuntu.blogspot.com/)

---

### Post by jonathonblake on 2008-12-18
> **linuxguymarshall said:**
> 
another $1500 for a computer that is more than they need, 

Before suggesting that a US$1,500 is more than they need, I'd suggest you price the cost of the hardware that blind users utilize.    (I'd love to see a used Braille Display unit in working condition,  for US$1,500.)

> in other words, they wont switch.

The entire ecosystem of a11y services revolves around the party that provides the product/service being paid by a party other than the one that receives the product/service. And, as usual with such ecosystems, there are no "checks and balances{", and the market place is distorted by the economics required to justify higher budgets each year.   

The entire ecosystem is predicated on maximization of revenue, and minimization of real, actual,viable  services that are provided. (Freedom Scientific is on record for stating that they will never provide support for software that is not distributed by, or authorized by Microsoft.  They aren't the only company to publicly admit that their applications, by design, do not, and will not function with specific programs, because "defective by design", is their method of creating software.)

Since both distribution,and support  are unavailable, there is no rational reason to switch to Linux.    Currently, the amount of support for Linux, that the average individual with a11y needs can receive, is less than zero.  

Vibuntu is for a niche market ---  blind people who have a linux tech on 7/24 call. I hope it is successful. 

Given the history of Linux distros for the blind, I doubt that Vibuntu will be around in two years.   However, I would be surprised if the a11y tools that it introduces are not migrated to other distributions.


jonathon

---

### Post by drbongo on 2008-12-18
You may be right, but I hope you are wrong and the only way to find out is to try and that isn't going to do anyone any harm. With the proliferation of netbooks, linux if getting used by more and more people who are not technically inclined and will just use it if it works. If it does get more popular on the desktop then inevitably there will be VI users who want to try it and perhaps the greatest incentive is the extortionate price of commercial accessibility software etc. The Wright brothers were told on a regular basis that they were wasting their time and only a few eccentrics would ever want to fly in an aeroplane. But they persisted and the sky is now full of aeroplanes containing people :guitar:who don't know anything about how they work!

Maybe I should have called it 'Pigs Will Fly Linux'!

drbongo

---

### Post by jonathonblake on 2008-12-18
> **drbongo said:**
> the only way to find out is to try and that isn't going to do anyone any harm. 

The virtue of projects like ViBuntu is in the tools that they create, that are migrated to other distributions.   

> With the proliferation of netbooks, linux if getting used by more and more people who are not technically inclined and will just use it if it works. 

For blind individuals, the major limiting factor for notebooks is the absence of a Braille display screen.  Arguably, the lack of a Perkins keyboard is another limitation of netbooks.  

>  perhaps the greatest incentive is the extortionate price of commercial accessibility software etc. 

A11y support vendors are _not_ paid by the people who utilize their offerings, but,instead, are paid by third parties.  Those third parties are either government agencies, or non-profits.  In either instance, they need to justify having a higher budget each year. Even when the FLOSS product outperforms the commercial offering, the commercial product will be utilized, because that does not threaten their revenue stream, whereas the FLOSS product does.

IOW, under the current a11y ecology, it doesn't matter what FLOSS solutions are presented, because the organizations that allegedly help those who have a11y issues, get more revenue from rejecting FLOSS, than embracing it


jonathon

---

### Post by Sef on 2008-12-18
> A11y support vendors are _not_ paid by the people who utilize their offerings, but,instead, are paid by third parties. Those third parties are either government agencies, or non-profits. In either instance, they need to justify having a higher budget each year. Even when the FLOSS product outperforms the commercial offering, the commercial product will be utilized, because that does not threaten their revenue stream, whereas the FLOSS product does.

IOW, under the current a11y ecology, it doesn't matter what FLOSS solutions are presented, because the organizations that allegedly help those who have a11y issues, get more revenue from rejecting FLOSS, than embracing it


One has to have faith that things will change.  The change will not come fast, but slowly.

---

### Post by LaPingvino on 2009-01-04
Hello!

I read this thread with a lot of interest, as I know several blind Esperantists and I'm the computer specialist for quite some people (and luckily for them having a lot of interest in accessibility, sourcing from writing accessible websites) and luckily enough the Esperanto voice (and Braille? need to find out that...) works quite nice.

This efforts should make it easier and easier to get blind Esperantists an operating system in their favorite language. I am planning to get an Esperanto-only disc of ubuntu some day, and with the efforts of Vibuntu it will be easier to make such a disc of use for all Esperantists. If some other languages should be included in such a release, or for some other reason, please contact me! :)

Yours,

Joop Kiefte (LaPingvino), admin of the Esperanto Ubuntu-translation team in Launchpad
ubuntu-eo.org (coming "soon")

---

### Post by drbongo on 2009-01-18
I am happy to announce that we have now rebranded Vibuntu as Vinux after
discussion with Canonical about the use of the 'buntu' suffix. They were
happy to let us call it the Ubuntu VI Remix but we decided to go with Vinux
which now recursively stands for Vinux Is Not Ubuntu but gnu/Linux! We have
been busy creating a new website, mailing list and development blog and hope
to have a new release out soon - Vinux 1.3! The URL's are:

Homepage: [http://vinux.org.uk/](http://vinux.org.uk/)
Development Forum/Mailing List:
[http://groups.google.com/group/vinux-development](http://groups.google.com/group/vinux-development)
Development Blog: [http://vinux-development.blogspot.com/](http://vinux-development.blogspot.com/)

There are already threads created on the forum/mailing list for bugs reports,
suggestions, help and advice and user profiles, but you are free to start new
threads on different topics if appropriate. We do not expect there to be very
high traffic initially and we will still post significant new release
annoucements on other related mailing lists. The development team currently
consists of myself, Tony Sales (aka drbongo) as the main developer and
Osvaldo La Rosa (aka ald0) who is responsible for web administration etc. We
would of course welcome support from people who would like to contribute to
the project in any way at all. I will be posting a list of small modular
tasks which people might like to take on board as needs arise. Ideally I
would like to have a core development team of 3 to 6 individuals, with
specific responsibilities and a looser collection of individuals who would
contribute on an adhoc basis when required.

The project is still very much in its infancy and there is plenty of scope
for evolution...

Hope to hear from you soon, drbongo and ald0.

---

### Post by LoveSponge on 2009-01-29
I'm downloading the ISO now and I'll work with it.  I agree with the point that having the GUI allows the Sighted to help the VI user.  See my post: Helping a friend with Orca and Streaming.

---

### Post by LoveSponge on 2009-01-29
> **linuxguymarshall said:**
> Most people who are visually impaired and need to use a computer already paid $150 for a GeekSquad lame-*** to come to their house, another $1500 for a computer that is more than they need, $250 more for in-home setup and $250 more for software and hardware geek squad said they "needed"

in other words, they wont switch.

There are many blind people who are working with hand-me-down windows based JAWS software/hardware systems.  Given the economic climate, and the state of affairs for the VI, I would say there is a need for free.

My general observation is that, even in College Towns like mine, people still don't know about the quality of Open Source. The "if it's free it must be inferior" mindset prevails.

I feel that is about to change given:

1) the economic climate
2) the new American Administration's willingness to adopt new tech

---

### Post by vividia on 2009-01-30
Its projects like these that keep me learning more.  As is I don't think I know enough to help.

But Awesome!!

---

### Post by drbongo on 2009-02-23
Vinux 1.3 Released!

drbongo and ald0 are proud to announce the new release of Vinux - Linux for the Visually Impaired!

This release includes a variety of new packages and features, as well as solutions for bugs in earlier versions:

It includes a range of useful console applications and the yasr screen-reader, a selection of forensic/recovery tools so it can be used as an accessible recovery CD/USB pendrive by more experienced users. You can now install it straight to a USB pendrive using the Ubuntu USB installer, from the live CD or the ISO image once installed to hard drive. The username and password entered during the installation process is now retained and of course Orca, a full-screen magnifier and Braille support are all available out of the box! If you would like to try it out or read more details then please follow these links:

Vinux 1.3 ISO image - [http://vinux.org.uk/downloads/latest_(1.3).iso](http://vinux.org.uk/downloads/latest_(1.3).iso)

Vinux 1.3 MD5SUM - [http://vinux.org.uk/downloads/latest_md5sum-1.3.txt](http://vinux.org.uk/downloads/latest_md5sum-1.3.txt)

Vinux 1.3 Release Announcement - [http://vinux.org.uk/downloads/latest_release_announcement-1.3.txt](http://vinux.org.uk/downloads/latest_release_announcement-1.3.txt)

Vinux 1.3 Keybindings etc - [http://vinux.org.uk/downloads/1.3/](http://vinux.org.uk/downloads/1.3/)

There is one known issue in this release, the cups server does not work when you install it to a hard drive, although it works fine from the live CD or a USB pendrive install. There is a very simple fix for this which you can implement once you have installed it if you want to print out any documents. There is a script which will do this for you, or you can simply type the four lines into the terminal using the sudo command!

Vinux Cups Fix Script [http://vinux.org.uk/downloads/old/1.3/cupsfix.sh](http://vinux.org.uk/downloads/old/1.3/cupsfix.sh)

If you have any questions or would like to give us feedback, please register on the Vinux Forum/Mailing List so as not to clog up these mailing lists with posts which may not be relevant to this mailing list.

Vinux Forum/Mailing List: [http://groups.google.com/group/vinux-development](http://groups.google.com/group/vinux-development)

have fun,

drbongo and ald0

---

### Post by drbongo on 2009-02-23
Osvaldo la Rosa has made audio versions of all the Vinux 1.3
documentation available in .ogg format. They can be downloaded from
the following URL's:

[http://vinux.org.uk/downloads/old/1.3/Release-Announcement-Vinux-1.3.ogg](http://vinux.org.uk/downloads/old/1.3/Release-Announcement-Vinux-1.3.ogg)

[http://vinux.org.uk/downloads/old/1.3/Vinux-1.3-New-Features.ogg](http://vinux.org.uk/downloads/old/1.3/Vinux-1.3-New-Features.ogg)

[http://vinux.org.uk/downloads/old/1.3/Vinux-Keybindings.ogg](http://vinux.org.uk/downloads/old/1.3/Vinux-Keybindings.ogg)

[http://vinux.org.uk/downloads/old/1.3/gnome-keybindings.ogg](http://vinux.org.uk/downloads/old/1.3/gnome-keybindings.ogg)

[http://vinux.org.uk/downloads/old/1.3/orca-desktop-keybindings.ogg](http://vinux.org.uk/downloads/old/1.3/orca-desktop-keybindings.ogg)

[http://vinux.org.uk/downloads/old/1.3/orca-laptop-keybindings.ogg](http://vinux.org.uk/downloads/old/1.3/orca-laptop-keybindings.ogg)

[http://vinux.org.uk/downloads/old/1.3/roll-your-own-vinux.ogg](http://vinux.org.uk/downloads/old/1.3/roll-your-own-vinux.ogg)

[http://vinux.org.uk/downloads/old/1.3/welcome-to-vinux.ogg](http://vinux.org.uk/downloads/old/1.3/welcome-to-vinux.ogg)

[http://vinux.org.uk/downloads/old/1.3/yasr-keybindings.ogg](http://vinux.org.uk/downloads/old/1.3/yasr-keybindings.ogg)

Thanks for this ald0!

---

### Post by drbongo on 2009-02-26
Vinux 1.31 - Release Notes.

This release contains a fix for the cups server problem which
was still present in the 1.3 release.

Direct Link - [http://vinux.org.uk/downloads/old/1.31/Vinux-1.31.iso](http://vinux.org.uk/downloads/old/1.31/Vinux-1.31.iso)

md5sum - 5dfff403a9e8a6d9ae5a550198483207  Vinux-1.31.iso

We believe it was caused by the presence of two ssl keys Ubuntu added
to beef up the security when using a cups server on an unprotected
network, and after discussions with frag the developer of 
remastersys, we came up with a solution which will be included
in the next version of remastersys. If you have already downloaded 
version 1.3 and installed it there is no reason to download this 
release as you can fix the cups server issue with three simple 
terminal commands after installation:

sudo rm /etc/cups/ssl/server.crt
sudo rm /etc/cups/ssl/server.key
sudo /etc/init.d/cups start

This issue does not effect the 1.3 Live CD itself or a USB pendrive 
install. Sorry for any inconvenience caused!

drbongo and ald0

---

