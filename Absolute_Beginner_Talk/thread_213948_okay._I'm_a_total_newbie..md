---
title: "okay. I'm a total newbie."
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-07-12
and I need some serious help! I actually like using windows, but I installed ubuntu to see what the hype was all about. I've been extremely frustrated in getting started. there's all this talk about partitions and code and command lines. I'm not familiar with any of this. I cannot change the screen size (resolution?), and whenever I try to type in code, it asks me for my password. I try to put my password in, but it won't accept it. Ubuntu accepts this same password when I start up.

I want to learn, but most beginner threads I see just jump into all this computer language. I can't see my files that were put on my hardrive from windows!

any help would be appreciated. will I ever figure linux out?

---

### Post by not_yet on 2006-07-12
welcome:) 

screen resolution      system / preferences  / screen resolution

re: your password 

changing to root can do big damage so use with care

lets say you wanted to edit a file that required root (admin) privilage

from the terminal ( applications / assessories / terminal)

sudo gedit  (press enter)

now it will ask you for your password, giv it and press enter 

hth a little ;)

---

### Post by slimdog360 on 2006-07-12
You cant see the windows files because they are written in a different way, just like you wont be able to see the Ubuntu files in windows.
Dont worry about this at the moment but I believe there is a way to use them.

about the password hmm, did you create another account by any chance?? One different to that which you used when you installed Ubuntu. 
If you didnt do that I cant think of a reason why it wouldnt accept it.

About the screen resolution. Are you not sure how to change it? or have you tried to change it but it didnt work?
If its the first one then you go to System(up the top)-->Preferences-->Screen resolution.

---

### Post by friedokra on 2006-07-12
I tried changing the screen resolution, but when I change it and hit "apply"...ubuntu just starts over. Maybe I am trying to change the screen size. the desktop for example is too wide, like this:

<--------------------------------------------------------------------------->

I want it to be more narrow (horizontally) like this:
     <-------------------------------------------------------------->

I have no idea how to change this. My password seemed to work when I installed "easyubuntu" using the terminal, but earlier when it looked like this whenever I would type a command into the terminal:

Password: (and when I tried to type something in here, it wouldn't let me. I could only press 'enter' and then it would say password denied as if it thinks I was trying to use the enter key as my password.)

---

### Post by friedokra on 2006-07-12
like, everything (images and text) looks squished.

---

### Post by Dr. Nick on 2006-07-12
look here for some info about seeing windows
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

specifically here
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

When Ubuntu "restarts" it is probably just logging out to apply changes, If your monitor looks streched then set the res to 1024x768 or something similar and then use the controls on the monitor itself to make the image look correct.

---

### Post by babyhewy on 2006-07-12
Did you install it by clicking on install on the desktop, or did you just put the cd in the drive and reboot the computer to get to ubuntu.

---

### Post by bikeboy on 2006-07-12
> **not_yet said:**
> welcome:) 

changing to root can do big damage so use with care

lets say you wanted to edit a file that required root (admin) privilage

from the terminal ( applications / assessories / terminal)

sudo gedit  (press enter)

now it will ask you for your password, giv it and press enter 

hth a little ;)

For graphical apps that should be gksudo rather than plain sudo :)

---

### Post by Malac on 2006-07-12
Well as far as the password goes you won't see anything in a terminal while you are typing it in. 
You just type it in at the ```
Password:
``` prompt but you won't see the characters you are typing in or any asterisks either.
If you are launching a gui application(i.e. one with it's own window) it is better IMHO to use "gksudo" instead of "sudo" as this gives you a nice GUI that will show a "*" for every letter you type in and also there are some user enviroment issues if using GUI apps but command line sudo, apparently.

---

### Post by candtalan on 2006-07-12
friedokra said:
I tried changing the screen resolution, but when I change it and hit "apply"...ubuntu just starts over. Maybe I am trying to change the screen size. the desktop for example is too wide, like this:

<--------------------------------------------------------------->

I want it to be more narrow (horizontally) like this:
<---------------------------------------------------->

reply:
This sounds more like the screen width and may be adjusted by settings on your monitor. Sometimes there are buttons on th efront of the monitor, one for a menu, then, say, + and -

---

### Post by friedokra on 2006-07-12
there is no button on my notebook to change screen size. I have an acer aspire 5000 notebook. on my desktop there is such a button. but alas, I search in vain for this elusive screen changing button on my notebook comp.

---

### Post by Tom Brokaw on 2006-07-12
> **friedokra said:**
> and I need some serious help! I actually like using windows, but I installed ubuntu to see what the hype was all about. I've been extremely frustrated in getting started. there's all this talk about partitions and code and command lines. I'm not familiar with any of this. I cannot change the screen size (resolution?), and whenever I try to type in code, it asks me for my password. I try to put my password in, but it won't accept it. Ubuntu accepts this same password when I start up.

I want to learn, but most beginner threads I see just jump into all this computer language. I can't see my files that were put on my hardrive from windows!

any help would be appreciated. will I ever figure linux out?

Hi, friedokra.

I had a similar problem with my LCD desktop screen, couldn't get the 1280x1024.  Someone advised me to type this

```
sudo dpkg-reconfigure xserver-xorg
```

in the console.  I do not know if there is any difference between the terminal (the graphic window that comes up) or the console (the screen that looks like DOS), but I don't think there is.

What this did was allow me to reset all my configurations.  For most of them I just entered the default, but for one, it let me choose the resolutions I wanted.  Enter them with the space bar.

Doing this may not fix your problem but if you don't change anything else, it shouldn't break it either.

I also had/have a problem where Windows and Ubuntu "move" my display on my monitor, so Ubuntu is too far right and if I correct it, Windows is too far left.

I get around this by pressing the button that says "auto" on my screen.  However, since mine is a desktop, it's made to be used with many different computers, whereas your lappy is not,so that's probably why you can't find the magic auto-detect button.

---

### Post by friedokra on 2006-07-12
and why are there only three options for the screen resolution under "preferences". the only options on the list are:

1024 x 768
800 x 600 and
640 x 480

and when I click on one of these dismal options....ubuntu restarts and asks for my username and password again. when it loads, nothing is changed. it doesn't matter which resolution I choose. all three are the same. it's annoying looking at squished images that are too long horizontally..

---

### Post by Tom Brokaw on 2006-07-12
Those were the same three options I had, and typing that command fixed it for me.

The terminal is in Applications > Accessories > Terminal.  If you right-click it you can add it to the desktop.

---

### Post by slimdog360 on 2006-07-12
I done a little googling on 'acer aspire 5000 notebook' to see if it was widescreen but couldnt find anythign conclusive, some said it was others said it wasnt??go figure.
So my question is, is your notebook a widescreen. Which could explain why you are getting a funny resolution. Im pretty sure you can fix this problem if it is widescreen.
edit: do you know what the natural resolution of the screen is?

---

### Post by friedokra on 2006-07-12
Tom: thanks for the help. I tried typing in that command and it brought me to the screen with the resolution options. however I clicked on one and hit 'enter' and it went to the next screen. nothing changed.

slimdog: yes, this notebook is a widescreen and I have no idea what it's original resolution is.

---

### Post by friedokra on 2006-07-12
and I used the spacebar to select a resolution.

---

### Post by friedokra on 2006-07-12
okay, I got it to where it will let me type in some type of horizontal and vertical parameters? but nothing has changed since I typed in some numbers. I didn't even know what numbers to type in. as I said, I'm not used to any kind of code or manual input on computers.

---

### Post by friedokra on 2006-07-12
I don't know how I managed to do it, but now ubuntu won't even start. something about the screen not being able to show up at all. maybe I put in some unreadable parameters. how do I remove ubuntu from my system entirely? when I load ubuntu now just the terminal screen comes up. no icons, no browsers, and me who doesnt know any code. I just see a black screen with prompts now. something about an "x" or something. maybe I need to totally uninstall and start over.

---

### Post by slimdog360 on 2006-07-12
Okay I know how to fix this but Ive got to go out for a couple of hours. Unless someone else can fix this Ill help you later. 
Note you have to change the vertrefesh and horizsynch in the xorg.conf file. Though Id have to find what they are for a wide screen which is why I'll have to do it later.

---

### Post by slimdog360 on 2006-07-12
> **friedokra said:**
> I don't know how I managed to do it, but now ubuntu won't even start. something about the screen not being able to show up at all. maybe I put in some unreadable parameters. how do I remove ubuntu from my system entirely? when I load ubuntu now just the terminal screen comes up. no icons, no browsers, and me who doesnt know any code. I just see a black screen with prompts now. something about an "x" or something. maybe I need to totally uninstall and start over.

argh, try typing into that screen
```
sudo update-rc.d gdm defaults
```

---

### Post by slimdog360 on 2006-07-12
okay im back. Did you get your desktop back?

Can you check the manual for your notebook and see what the natural screen resolution is. I had a look and found that it should be 1280x800, but I want to make sure.

First if you didnt get your desktop back and really want to reinstall Ubuntu you will just have to whack back in the cd and install it how you did the first time.

Second to get your monitor working properly you can follow these instructions and hopefully it should work(dont worry its easier than it looks).

open a terminal and enter one line at a time

```
sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```
scroll down till you find something that looks like

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       XXXXXX
    VertRefresh     XXXXXX
    Option         "DPMS"
EndSection

replace the XXXXXX bit (you will have numbers obviously) so it looks like.

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       **28.0 - 64.0**
    VertRefresh     **43.0 - 60.0**
    Option         "DPMS"
EndSection

then scroll down a little further
you will see something with the header 
Section "Screen"
then there will be some more writing and under that you will see something which looks like
   
SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400"  "640x480"
    EndSubSection

thats mine so yours will looks a little different. This should repeat a few times each with different depths.
tack onto the end of the mode bits "1280x800" (including the quotes) so that it should look similar to 

Modes      "1024x768" "800x600" "720x400"  "640x480" "1280x800"

do this for all of them.

Then save the file and restart X by pressing ctrl+alt+backspace.
You should then be able to select your screen resolution the way I said to start with System-->Preferences-->screen resolution.
Hope that works for you, if not its a matter of changing the HorizSync and VertRefresh parts.

---

### Post by manicka on 2006-07-12
Probably should add that if the changes to your xorg file completely stuff the xserver, then 

sudo cp etc/X11/xorg.conf_backup /etc/X11/xorg.conf 

will get you back up and running with your old settings

---

### Post by friedokra on 2006-07-12
okay. I can't get away from this black terminal screen whenever I start ubuntu up. I tried typing in "sudo gedit/etc/x11/xorg.conf
and it doesn't recognize this command. It is also saying "the x server is now DISABLED - restart gdm when it is configured correctly." But the thing is - I don't know how to configure it correctly if I can't even get to the screen where I first configured it.

---

### Post by Tom Brokaw on 2006-07-12
That *sounds* like the problem I had when I had to type in the command I posted earlier.  But if you aren't sure what the parameters need to be, it probably won't help to go through all that config again.

If it were my computer, I'd find out the native resolution ( I think someone said 1280 x 800) and the acceptable refresh rates. The manufacturer should be able to help with this.

Then I would post back here with that info.

It's frustrating getting past this stuff, but I'm really enjoying ubuntu now that I've got it running.  Stick with it.

---

### Post by manicka on 2006-07-12
> **friedokra said:**
> okay. I can't get away from this black terminal screen whenever I start ubuntu up. I tried typing in "sudo gedit/etc/x11/xorg.conf
and it doesn't recognize this command. It is also saying "the x server is now DISABLED - restart gdm when it is configured correctly." But the thing is - I don't know how to configure it correctly if I can't even get to the screen where I first configured it.

did you back up the xorg file as recommended, if so type


sudo cp etc/X11/xorg.conf_backup /etc/X11/xorg.conf 


or you can try to edit the xorg file with nano


sudo nano /etc/X11/xorg.conf

you can't use gedit because it needs a graphical interface (the xserver) to operate, which won't happen when your xserver fails and you are thrown back into  command line

hth

---

### Post by Towncivilian on 2006-07-12
When you fix xorg.conf, type sudo init 1 and when that finishes, type sudo init 3 and Ubuntu should start up if you configured it properly.

"X" is the user interface. You can restart X by pressing Ctrl+alt+backspace. Be sure you've saved all your files beforehand, though.

I was a newbie yesterday too, but it isn't that hard... you'll learn if you follow some howtos and just play around. If you break something, it's not hard to just reinstall Ubuntu. I had to reinstall twice already, but hopefully this install will be with me for a while. :)

Good luck.

Oh, one more thing, the command line is case sensitive (e.g. if you're going into \etc\X11, you have to type it "\etc\X11" not "\etc\x11" (without quotes of course). If you press the up arrow, the text of the last command comes up.

---

### Post by friedokra on 2006-07-12
alright. I had to put the cd back in and install again. are there two ubunbtus on my computer eating up my hard drive? do I have 3 operating systems now (2 ubuntus and a windows?) or when I installed again (using the cd) did the old defunct ubuntu, in which I managed to destroy my 'x' (whatever that is), stick around?   I am totally confused. what are partitions and sudos?

---

### Post by friedokra on 2006-07-12
> **slimdog360 said:**
> okay im back. Did you get your desktop back?

Can you check the manual for your notebook and see what the natural screen resolution is. I had a look and found that it should be 1280x800, but I want to make sure.

First if you didnt get your desktop back and really want to reinstall Ubuntu you will just have to whack back in the cd and install it how you did the first time.

Second to get your monitor working properly you can follow these instructions and hopefully it should work(dont worry its easier than it looks).

open a terminal and enter one line at a time

```
sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```
scroll down till you find something that looks like

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       XXXXXX
    VertRefresh     XXXXXX
    Option         "DPMS"
EndSection

replace the XXXXXX bit (you will have numbers obviously) so it looks like.

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       **28.0 - 64.0**
    VertRefresh     **43.0 - 60.0**
    Option         "DPMS"
EndSection

then scroll down a little further
you will see something with the header 
Section "Screen"
then there will be some more writing and under that you will see something which looks like
   
SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400"  "640x480"
    EndSubSection

thats mine so yours will looks a little different. This should repeat a few times each with different depths.
tack onto the end of the mode bits "1280x800" (including the quotes) so that it should look similar to 

Modes      "1024x768" "800x600" "720x400"  "640x480" "1280x800"

do this for all of them.

Then save the file and restart X by pressing ctrl+alt+backspace.
You should then be able to select your screen resolution the way I said to start with System-->Preferences-->screen resolution.
Hope that works for you, if not its a matter of changing the HorizSync and VertRefresh parts.

okay, I did the thing with the quotes and "1280x800" and nothing happened. yes I saved. how do I change the horizsync and vertfresh? what do I change them to?

---

### Post by friedokra on 2006-07-12
I just tried to change the horisync? 

after getting out of xconfig I see this in the terminal -

c"lay@clay-laptop:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060712202834"

---

### Post by friedokra on 2006-07-12
PROBLEM SOLVED!!!!!! okay. cool. my problem is solved for now. this problem anyways. the resolution is looking much better. thanks. but my next questions are: what is a sudo? what is a partition? and also, when I installed ubuntu for the second time from the live cd (using the same name and password), did it delete the other ubuntu install? do I have 3 operating systems on my laptop now (2 ubuntus with 1 being defunct and Windows XP [which I'm not going to delete anytime soon])????

---

### Post by slimdog360 on 2006-07-12
Sudo gives you root privliges, which means you can modify certain files, files which are usually critical to Ubutnu. 
Partion = google
Third, yep it sounds like you have Ubutnu installed twice. Umm you could give installing another go, there is a couple of good guides from that [psycocats]("http://psychocats.net/ubuntu/index.php") page
On the left hand side of that page there is a number of good guides. One of which relates to partioning your hard drive and another on installation.

---

### Post by ncappel1 on 2006-07-12
I would like to add that getting the bugs out of the computer, working to solve these kinds of problems is like a puzzle. It can be very fun. The frustration is simply a lack of patience. read the forums, try different solutions, *always backup your files*, and have fun! You'll feel like Mcguyver in no time.

---

### Post by Tom Brokaw on 2006-07-12
> **ncappel1 said:**
> I would like to add that getting the bugs out of the computer, working to solve these kinds of problems is like a puzzle. It can be very fun. The frustration is simply a lack of patience. read the forums, try different solutions, *always backup your files*, and have fun! You'll feel like Mcguyver in no time.

Well put.  My first resolution problems were very frustrating because I wanted them fixed right away.  When I took a step back and relaxed, it was a lot easier to explain my problem and get some help.  

This week is killing me, I have to focus on getting a new job, and all I want to do is learn Ubuntu stuff and PS new avatars.

---

### Post by candtalan on 2006-07-13
> **friedokra said:**
> PROBLEM SOLVED!!!!!! okay. cool. my problem is solved for now. this problem anyways. the resolution is looking much better. thanks. but my next questions are: what is a sudo? what is a partition? and also, when I installed ubuntu for the second time from the live cd (using the same name and password), did it delete the other ubuntu install? do I have 3 operating systems on my laptop now (2 ubuntus with 1 being defunct and Windows XP [which I'm not going to delete anytime soon])????

Well done! Did you sort it out by following one etc of these messages - what did you do, do you recall?

sudo is short for Super User Do (it) or something similar. It means you have to use a password and you will get promoted to root (maximum) privilidges temporarily for the task in hand.

Partitions are parts of a hard drive which are areas allocated by the user, and which are quite separated and independant, and can be used as if they themselves are different hard drives. In a simple case, a hard drive (HD) is entirely one partition only. HDs are so large now that it is easy to have several partitions happily coexisting. My demonstration pc has about 15 partitions.......most of them are about 5 GB. One has windows on it.

If a partition is deleted, then the partitions next to it are not affected. The space which is left is called unpartitioned space. Subsequently the adjacent partitions can be expanded to take some space up, or a new partition can be put into the gap. A partiton does not have to be formatted with a file system (fs), but you cannot do much with it unless it has a fs. If you find you have got ubuntu twice, you might also find that the second one intelligently used the 'swap' partition created by the fisrst ubuntu. The linux swap partition might be shared. On my demo pc one swap file is used by a number of distros - they run one at a time anyway.

hth

---

### Post by Brunellus on 2006-07-13
just to add:  you can have no more than 4 *primary* (physical) partitions on a single hard drive.  That is, you can only divide a hard drive into 4 phsyically-distinct parts.  You can instruct your computer to treat any one of those 4 primary partitions as its own little virtual hard drive, including cutting it up into sub-partitions (*logical* partitions).  There's no limit on logical partitioning.

---

### Post by friedokra on 2006-07-15
"Well done! Did you sort it out by following one etc of these messages - what did you do, do you recall?"

I had to do it about five times because I kept having to load ubuntu over and over (long story). The commands that Tom Brokaw and Slimdog posted about changing the horisync in my x config is what helped. I also had to change my video card info in the x server (I think that is what it's called). I also had to type in "sudo gedit /etc/X11/xorg.conf" and manually add "1280x800" to the screen display options.

In short: sudo gedit /etc/X11/xorg.conf
and
sudo dpkg-reconfigure xserver-xorg

are what worked. along with knowing my screen resolution and the horisync I needed to use. thanks ppl.

---

