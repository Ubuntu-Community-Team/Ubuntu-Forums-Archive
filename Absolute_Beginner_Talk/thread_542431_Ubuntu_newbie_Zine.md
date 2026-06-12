---
title: "Ubuntu newbie Zine"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by tyggna1 on 2007-09-03
Before you read anything else, switch to hybrid view in the forum.   This is done by clicking on "Display Modes" off to the left, and selecting "Switch to Hybrid Mode"
[B]
***If you'd like to post comments about the zine, please post them [here]("http://ubuntuforums.org/showthread.php?t=544581")  to keep this as uncluttered as possible.  Thanks.***[/B]

That's right, I want to write a zine--or an online magazine in the forum!  I want this to be especially for newbies.  A lot of people aren't friendly to new people, and don't really feel obligated to help them--after all, it isn't really their problem.  I have a different belief, though.  The Ubuntu community is Ubuntu's greatest asset.  As a computer user, I look and see roughly 6000 people online, and I can't help but think, "At least 100 of those people know the answer to my question, maybe one of them will share it."

Still, it takes two or three posts to really get noticed.  This can be frustrating--as there isn't a one-stop source for linux, and every guide, help, and how-to is just as valid as any other one.

In this thread, I'm going to post a number of articles over time.  For the experienced user who happens upon this--I need to be edited.  I'm not perfect, and I am likely to make mistakes, but if you are willing to politely point those out to me, then I will edit the post and make it better than it was on my own.  Also, if you want to contribute to this zine, please pm me about what you want to add, just so I have a heads-up before you post.

To the new user, I shake your hand and say, "Welcome to Ubuntu!  Here's what you need to know.  You'll probably want to subscribe to this thread, as it could be the most valuable learning resource to you."

My articles will include my 12 years of computer hard-ware and windows experience, some common challenges that many people face when first switching over, and methods of learning how to use your soon-to-be favorite Operating System.  There will also be some basic how-to guides


At the end of this post, I will add links to threads that give good how-tos and valuable information.  If you feel like I've missed something that every newbie should know, pm me and I'll edit my post.  Please don't post, "Wow, that was great!  Thanks!"  or "You're an idiot and here's why" in this thread, as I want this to be as concise of a resource as it can be.  I'll title my replies to this thread differently, so the hybrid view will be extremely valuable.

Thank you, and I hope that we can work together to make Ubuntu a better place.


Tyggna

---

### Post by Yasumoto on 2007-09-04
Sweet! Sounds like a great idea. I'm really excited to see how this turns out.

My first contribution will be Christer Edwards site, which I've learned a lot of good stuff from: > [http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)


btw, nice forum quote :D

---

### Post by tyggna1 on 2007-09-04
This is a point of much confusion for many people who are tech-savvy in windows, and think that their knowledge of drivers will apply to linux.  This guide is written for newbies to computers, so I'll start with the basics.


What is a driver?
    A driver is software that controls a piece of hardware directly.  A video card has drivers that teach your computer how to run your games.  A USB port has drivers that tell the processor how to use your digital camera.  Every circuit board in your computer needs a driver to run it.  

 How is a driver used?
    A driver needs to work through a program called a kernel.  A kernel is really just that, a commander of the computer.   It is the first things that loads up into memory, and is the last thing that leaves when shutting down.  It manages the processor, it handles all the basic compute functions.  Drivers need to communicate to the hardware through the kernel.

What's the difference between a linux kernel, and a windows kernel?
   A very good question.  Windows was designed to be a modular kernel in order to accommodate all the hardware that was out there.  This means that the windows kernel lets each driver snap onto it like a lego (commonly in the form of a .dll file) so that the kernel can fit any set of hardware you throw at it--so long as you have a bit of code from your hardware manufacturer.
   Linux does things very differently.  Linus Torvald (the disputed inventor of Linux) wrote his thesis in computer science around the question. "what if I just put everything in the kernel?"  He experimented with this idea, and thus, with a lot of help from a lot of people, they made the very first linux!  It had all the drivers written right into the kernel itself, and the results were very surprising.  Linus' machine would compute faster and better than it did when it utilized a modular kernel--or one similar to DOS.  The kernel didn't have to pull things off the hard drive constantly to run things,  it had it all right there in RAM, and the result was a much sleeker operating system.  After compacting his code to a bare minimum--I believe he got an A on his thesis.
   But there was a problem.  Linus' operating system only worked on a computer that was identical to his in every aspect.  If you're looking to distribute and operating system, that's not very practical.  Just because it ran better, doesn't mean that all the hardware manufacturers in the world were going to bow down to a superior set of code and make all their products uniform.  So, Linus, being a very smart man, decided to give his code to the public and said, "Here it is,  thanks for your help!  If you can make it better, feel free to."
   What do I share the history of Linux with you?  What on earth does this have to do with drivers?  Well, releasing his code to the public made a lot of hackers and software developers started looking at it and thinking, "maybe I can change just a few things in the code to make this work for me."  Back in those days, a single megahertz added onto clock speed was a huge advantage, and something that would use your processor better meant having a huge edge over your competition.  This, until recently, has been the only motivation behind writing a Linux driver.
  This meant that the hacker or developer who used that particular piece of hardware would write his code to make it push his hardware as hard as it could be pushed without damaging it--but it also meant that new users had to get the same (or very similar) card as a hacker or software developer.   A lot of people argue (my own father, who works at Intel, included) that this is the primary shortcoming of Linux--but this heritage also has done much to emphasize Linux's strengths.  It makes for very tight code that runs very effectively, but also means that you will have to manually tweak your driver to make the most out it.
   As a side note for the tech-wise:  This isn't a very different concept from what you do in windows, Nvidia has its own control panel that is designed to do just that, there are certain steps you'll have to take to get your network card running at full-duplex, and there are certain things you'll have to change in Linux to get the most out of it.  So, let's dig into that.

How does linux use a "Driver?"
   The answers are:  programs and configuration files. 

Programs: 
   Often, these take the form of commands.  For you old DOSers, dir was actually a program, delete was actually a program, and mkdir (or md for short) was a program.  It was a very small program, usually only one or two functions big, but it was built right into the kernel so it would run fast.  Now, for those of us who appreciate vintage software and history, it's time to get excited:  The text-based interface is not dead!  Linux actually runs natively in a text-based environment.  We call it the CLI (short for command line interface).   Believe it or not, but you can actually do everything in the CLI that you can do in the GUI (means Graphical User Interface, or what you're looking at right now).   The GUI runs on top of the CLI in Linux, and if you feel so inclined, try typing in the name of your favorite program in the terminal (in my case, tremulous).
   Now that you see that the two are inseparably connected, I must share one sad fact of Linux--every program can run from the text-based interface, but not every program can run from the GUI.  I know, I know, it is sad, for the new user--but once you get comfortable with that fact, it won't bother you.  After a while, you'll probably learn to enjoy it.  For more info, see the (upcoming) article in this thread entitled--Text-base interface.

  Back to drivers.  There are really only a few relevant programs to drivers.  The one that first comes to mind is:

**modprobe**

modprobe is a program that runs only in the CLI (it's also called the terminal) that will allow you to install drivers directly into your kernel!  This 8-character long command can even tell your computer what drivers to use, and which ones you want removed, and list all of the drivers that are installed on your computer. 
all you have to do is type in:
```
modprobe -l  
```
#(that's a lower case -L)
and you'll get a very verbose list of all the drivers currently available to your kernel.  Typing a -i at the end, followed by the exact name of a driver, and you'll install that driver into your kernel.  
For listing the drivers most people prefer to type in:
```
lsmod
```
instead of modprobe -l because it gives a more human-readable output.  
    The kernel also uses programs, such as ifconfig, in order to run other pieces of hardware.  
    So, for the time being, you're going to have to step away from your pictures and sounds to edit your drivers.  Who knows, some developer might get fed up with the CLI and write a program that will do the exact same thing as modprobe in a GUI (hey, that sounds like fun!  maybe I'll give it a try!), but for now, we need to use the sleek, precise, and oh-so-fast command line.

Now that we know where to edit/change drivers, how do we do that?
   Short answer: with caution and backups.  
   Someone on this forum probably has some of your specific hardware, and knows what driver to put on to get it to work right.  Even if they don't, I'll help you know what you need to do, and there are thousands of others who can give you very valuable ideas, and help you know where to start.   This forum is your greatest asset for detailed support, but you need to know how to use those details, and understand the language of Linux for that to be useful.
    Often, you can find a how-to guide simply by typing in the name of your piece of hardware.  Sometimes, you can only find some information that mentions your hardware briefly.  After reading this, both will be valuable too you.
    Your best bet is in gathering some information from your system about what hardware you're using.  Try checking out:
> lspci
in the terminal.
If you're new to linux, anything with ls in the command name is going to be your new best friend. ls is short for "list," and it does just that.  In the terminal, it lists all the information about what is attached to your computer.  This will include information like:
          *What modem is installed
          *The name of your video card
          *How linux is using your USB ports
          *What audio hardware linux detects
          *The name--given by the hardware itself-of everything that is physically plugged in to your computer
        
Try typing in the exact name listed under lspci in the forum search, and you'll probably find quite a bit of relevant information.
If you don't, check out google, and run a search for the exact name plus linux drivers.
Filtering through the google search results can be a headache, and will likely only be useful for new leads.  Your looking for a driver name, specifically.  From there, you can find what you need in linux itself--you just need to know how.

Okay, I've found my driver name, how do I install it?

   This changes depending on what device you're using.  modprobe is a good universal utility for installing a driver, but not very handing for usage.  This is where we get into the really fun and cool part of Linux.
   If the driver is installed, the first thing you'll need to know is "what other drivers are loaded for this device?"  Unlike windows, it's possible to have more than one driver for a single device.  Almost always, it is not a good idea to use two drivers at once.  So, before you get that driver working, make sure nothing is working against it.
  
   You do this by blacklisting.  Blacklist is a configuration file that specifically tells your kernel what drivers not to load into memory.  An odd way of doing things?  maybe, but all you have to do is type the exact name of your driver into the blacklist configuration file, and then you're done.  You can get to your blacklist--which is a literal file by typing in:
```
sudo gedit /etc/modprobe.d/blacklist
```

   If you've already installed the right driver in modprobe--and it isn't a video driver--then you're done.  Video drivers are tricky, and I'll make an article designed specifically for them later.

 Just learn to do research, and to dig deep for the information you need.  You've heard the phrase, "knowledge is power" right?  In linux, knowledge directly translates to compute power.

And that's a general use guide for linux drivers.  Sorry for the really long article--I'll break it up to make it more managable/readable.

This article was designed to be an overview of the driver system in linux, and to give a basic knowledge of how they function.  Such a concept is difficult to cover in a single sitting--but this article will be edited for clarity and continuity, and accuracy.  Please re-read in a few days from the original post.

---

### Post by RomeReactor on 2007-09-04
Hi. I think you have a good idea going on here! Many times we forget to explain ourselves when trying to offer help, and some of those times we end up causing more confusion for a new user.

As a suggestion, you could try to touch on some of the solutions offered by UbuntuGuide, and explain some of the more obscure commands in more detail. Also you could try helping [nanotube]("http://ubuntuforums.org/member.php?u=66474") with his [Linux Console wiki]("http://ubuntuzilla.wiki.sourceforge.net/Using_The_Linux_Console"); I've been meaning to help him add links to the sites related to the programs mentioned and a more in-depth explanation of some of the commands, but I just haven't had time yet. Just send him a PM and let him know.

There's also Full Circle Magazine ([site here]("http://www.fullcirclemagazine.org/"), section of these forums [here]("http://ubuntuforums.org/forumdisplay.php?f=270")). You could try helping them with a few tutorials.

---

### Post by tyggna1 on 2007-09-04
This is just a short list of links that I have personally found to be newbie friendly.


[12 things to do with a brand-new feisty install]("http://ubuntuforums.org/showthread.php?t=515582")

[A wiki-pedia style site with a lot of good information, great for how-to's]("http://learn.clemsonlinux.org/wiki/Main_Page")

[This thread is stickied for a reason: namely, it's a great link-hub around the forums.]("http://ubuntuforums.org/showthread.php?t=232059")
[URL="http://ubuntuforums.org/showthread.php?t=510812"]
A great article that compares security of windows and Ubuntu in detail[/URL]

---

### Post by tyggna1 on 2007-09-05
**This article is an overview for the CLI.**

    If Ubuntu has ever crashed on you, or you selected "recovery"  option in your Grub boot loader, you probably found yourself in a dark and scary place with no pictures--just white letters and a flashing cursor.  For the faint-of-heart user, this likely terrified you, and compelled you to unplug your computer and go cry in a corner.   Okay, maybe not that extreme, but most people I've met who are annoyed (at first) with this text-based environment the first time they try to use it.

   This dark and scary place isn't as scary as you might think.  It's called the Command Line Interface--or CLI for short.  If you ever selected "terminal" under your applications menu, then you've been here before.
   You might be wondering,  "why is this even here?"  especially, if you've never used an old operating system or had to do a large amount of network troubleshooting in windows.  Well, this might come as a suprise, but this CLI is actually Linux.  Yes, that's right, that loginname$computername:  is actually Linux--not the graphics that you usually see.
    Linux runs natively in a text-based environment.  This is *very* different than windows XP and on, and all the Mac OSes.  Those operating systems are based on a graphical system (more commonly called a GUI).  Oh, sure, Linux has a GUI--it's called X (or X-server), but what you're seeing now is really running on top of the CLI.

    Now, lets have a look around the CLI, since computers can break, and you may need to know this some day.   First point:  to run any program, simply type in its name.   If you're a gamer, like me, and you play tremulous, all you have to do is type in:
> tremulous
in the terminal, and it'll run your game for you--you'll also notice that it'll give you a great deal more information about *how* it is running your game--which can be great for debugging and tweaking games to work the way you want them to.  (As a side note, say "hi" to me if you see a player named either Tyggna, or You won a corndog! in game)
   Second point:  moving around in a CLI takes a little bit more doing.  You always have an active or working directory--where you are at is printed in this format:
>  name@computer:/active/directory$
This means that you're on your own computer, in a specific directory.  If no /active/directory is printed, but you see a ~, that means you're in your home folder.  If it just prints a /, then you're at the base of your drive.
    You'll need to be able to move and look around the CLI to access any files.  Here's a list of basic commands and what they do--you'll want to memorize these, and try using them in a terminal.  

**This first set of commands is designed to help you get around.**
> ls - means list.  This will list everything in your active directory, files and folders.  In the terminal--black text means that it's just straight data.  Dark Blue means it's a folder that you can move to.  Red means its a file that is used by crucial system program.  Green means that it can be used by a program you've installed.  Light Blue means that it links to somewhere else 
> cd - change directory.  Type this in followed by the directory name to move around.  To go down a directory, type in two periods  (examples:  cd ..   cd / cd /home/guest)
> mkdir - make directory.  You can make any directory you want.  If you type in mkdir and then a name, then it will make it in that folder.  You can also make a directory in a folder other than the one you're in i.e. mkdir /bin/mygames/fungame
> sudo - use this before a program to run as the root user.  The root user has control over everything on the computer--and is therefore protected with your password for security reasons.
> rm - means remove.  This will delete files, to delete a directory, it's rmdir 

**This set is a bunch of useful programs and commands that will help you learn more about your computer.  These are only usable from the CLI.**> man - short for manual.  Type this in before any command name, program name, or driver name and it'll give you the manual for how to use it.  This is possibly the best learning resource in linux--since the manual was often written by the same people who programmed it.
> vim - vi improved.  This is a program that allows you to do text editing in the CLI.  It's confusing at first, but powerful.  Check out a [tutorial]("http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html") before using.  There's another text-editor called pico, but I've never used it personally
> ifconfig - this lists everything about your network adapters.  It will give you a lot of valuable troubleshooting information --such as your hardware address, if you have an active connection, your ip address, and other details about how your adapter is being used

**These last few are just to help you with troubleshooting and tweaking:**
> lsmod - lists every driver in modprobe
> lspci - lists all hardware physically attached to your computer
> iwconfig - like ifconfig, but designed for wireless cards
> grep - this is used to distinguish patterns in Linux. 
>  using a | on one line will allow you to separate two commands--this is sometimes needed
> apt-get - check the manual pages for this one.  You'll need to use sudo in front of it, as this is the CLI application installer
> wget - type in a url after this and it will let you add a website to your repository list
And while I haven't tried this one myself, I hear that it can be extremely useful
> dpkg-reconfigure xserver-xorg - (I'll try this when I get home to see what it does, but I suspect it'll help repair a broken GUI)


    Here's the big question, why should you care about this?  98% of the time you will never have to use the command-line.  Why bother with it, then?  I'll make my case by telling you what your computer has to go through.
    Right now, every single pixel on your screen needs to be sent through the processor 60 some odd times a second.  For your monitor alone--it needs to process the color of that pixel (which takes about 32 bits of data per pixel), the position (which is roughly another 32 bits of data per pixel), and the intensity of that pixel (usually about 8 bits of data per pixel).  Now, for a GUI, it has to load, first, the desktop, if you have a picture on it, it stores it in RAM and calls the information for that.  Then, it calls all the graphics for each program (like the start menus, and the buttons you can click on), after it calls the basic graphics for each item, then it calls for the window size, and any other relevant data associated with it.  When your computer isn't doing anything at all, that adds up to be roughly 102 million bits.  A modern processor handles 32bits per cycle, and can do roughly 2 billion cycles in a second (or 2Ghz as you've heard it called).  Given that, it takes about 
3 to 4 Mhz to run something in a GUI when idling.  
    Now, lets compare to a CLI.  A CLI runs at a lower resolution natively (800x600 at most, usually less), so already less has to go through the processor.  Next, it doesn't need to process every pixel on the screen, it does this last.  It needs to call your location, and what peices of text are being displayed on the system.  To do this, it refers to a table that has all the pixels for each letter assigned (typically about 600 bits each character) that's in RAM.  So, even if you are typing up a regular command, about 30 letters, the total operating system overhead will rarely get above 100Khz.  i.e. a CLI will take less than 1/400th of your processor power to run actively!--and this can be very important in a server applications, and other power-computing applications.

I hope this has been helpful in explaining a vast new world of powerful computing.  It is impossible to cover all the commands in the text-based environment--as every new program adds a new command.  Some programs are designed exclusively for the command line.  I hope this has been helpful in dispelling your fears or concerns about using it.  Please PM me if you feel like I've missed some absolutely essential commands.

---

### Post by tyggna1 on 2007-09-07
So many converts to Ubuntu are either gamers, or former gamers.  I'm a bit of both.  I play old games :D.   To do this, most people want their graphics card to work, and to work properly--but there's so many different types out there.  Some of us are tied down to an 8Mb integrated card--others have the newest GeForce with SLI, GPUs, and a 633Mhz  FSB, with all the bells and whistles and a bunch of other things that make us all say, "PCMCIA" (that's People Can't Memorize Computer Industry Acronyms).   Whatever your card--this article will teach you how to push its limits in Ubuntu, and get it to work right.
[B]
The First step:[/B]
     Make sure you're using the right driver.  You'll have to do a bit of digging around the forums to find out what that is--and you might be unlucky enough to not find anything.   Whether someone else knows for a fact that a certain driver works well with your card--or you have to dig to get a list of drivers that might work with your card--you're going to have to experiment and play around with settings to get this to work right for you.  
     Most of this tutorial will involve a file named xorg.conf.  This is the configuration file for all the graphics that Linux uses (which is a program named X)--from games to menus, xorg.conf is your computer's one-stop shopping place for all graphic capabilities.  
     Before doing anything, make a backup, and write down the second command given here on paper.  The command to make a backup is:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

     If something goes wrong, and your X-server (Graphical interface) crashes, you can restore it to the way it is now by typing in:
```
sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf 
```

     Now that the important thing is out of the way, get ready to roll up your sleeves, and, as Ms. Frizzle from the Magic School Bus series says, "take chances, make mistakes, and get messy!"

**Finding your driver, and learning how to use it:**
     Whatever your graphics card, you're going to have to edit xorg.conf.  The easiest way to do this is to press alt-F2 (the X run command) and type in:
```
sudo gedit /etc/X11/xorg.conf
```
For a regular Ubuntu install.  For Kubuntu, replace the gedit with a kedit.
     This will bring up xorg.conf.  It's just a text document.  It's divided into sections, and each section represents a part of your computer that X needs to use.  Look for> section "device"  That's your graphics card.  Lets break up what it says underneath it, shall we?

> 
Section "Device"
	Identifier	"The name of your graphics card"
	Driver		"driverYou'reUsing"
	BusID		"PCI:1:0:0"  #Where this is card is physically located on your motherboard
#a pound means "comment,"  anything after a pound won't be read.  
#These are notes for yourself, so you can understand what you changed
#and why you changed it
	Option		"something" "argument"

The first three are pretty self explanatory--as I put the explanation in the names.  The one that will let us really tweak our card and push it to its limits is the fourth one.  These options are specific to your driver.  Each driver was designed to use different features on your card.   The next paragraph is solely examples to help you better understand, and is optional.

    Some graphics cards use SLI--which means that you can have two graphics cards share the work load.  This option needs to be enabled--once the proper driver is installed for your SLI-capable cards.  Really nice graphics cards have their own processor on them, and the speed of that processor might be an option that you can set in your file.  Onboard memory (in Mb) will often need to be set to be utilized.  Other cards have two ports on the back, and to use both at the same time, you'll need to set a certain option to enable dual-monitor support.

     So, how do I know what these options *are* for my driver, and know what they do?  Fortunately, the guys who wrote the programming code for the driver also included an instruction manual.  To make this easier to program in, they just wrote a text file.  This file can only be accessed from the terminal.  If you press alt-F2, and type in:
```
man driverNameFoundInXorg.Conf
```
and then click the button that says:
[ ] Run in terminal

    Then you'll get to read the documentation for your specific driver!   Believe it or not, but nearly all the options are listed right there in the manual, *and* they tell you exactly what they do, and what they're used for!  Some just make 3D games go faster, others are absolutely necessary to make X work and look nice.  In either case, it's a very good idea to read through the driver manual for your own card.  
    After all, it's like the user manual that comes with your car--and there are very few professional mechanics in Ubuntu.  You might be surprised to find that you'll go an extra 40 miles (or 64km) just by putting in one fuel-grade higher--like the manual suggests.  
    Remember: As smart as some people here are, no one knows your computer like you--because it's there with you.  A lot of "high bean" users know how to work the tools, but they don't know your engine block in the same way you can.  Read the manual--since you're the mechanic.
    
**Pushing your card:**
    Once you're comfortable with the other two steps, the last one is the easiest.  Just remember to backup every time after you've changed something--and it still works.  
     All you have to do now is copy and paste the options that look like they're what you want underneath the BusID.  You literally just type into xorg.conf:

```

       BusID "1:0:0"
       Option "NameOfOption" "on"
#or  
       Option "OnboardRam" "32"
```

Sometimes the option will call for an "on/off" a "true/false" an "integer (or whole number)" or something else--these will be specified in the manual (though not always clearly).  Just remember, if it says, _boolean_ it's a one or the other option, and if it's _real_ it can be any number at all.

That's it for tweaking your drivers.  The next portion of this article is all about Video Card Hardware.  Read this to understand more of what some of your Options will say.








Video Cards:
**Ports**
     There are 4 common ports that modern Video Cards can come on.  
     *PCI-e.  PCI-e (x16) is by far the fastest port, and allows for the smoothest communication between your CPU and your video card.  Unfortunately, ATI's drivers will use PCI-e as if it wer e PCI, which greatly hinders preformance of an ATI card. 
      *AGP (stands for Advanced Graphics Port).  These have different speeds, 8x being the highest.  Any motherboard made after 2002 would be 8x.  These are really just the front-end on your motherboard, and get their own special channel with the CPU--other than that, they aren't too different than PCI cards.
      *Integrated-- enough said, these are integrated into the motherboard.  I'd use them like AGP--as that is likely to give the most stable preformance.
     *PCI -- by far the slowest of all these.  PCI is the same kind of port that you'd plug an audio card into.  Most people don't have these--unless they really want to game on an older computer and don't have $40 to spend on a new motherboard that has AGP on it.


**Video Card Components**
     Most video cards have enough physical components on them to rival most early 90s computers!  Video Card manufacturers do this so that you can have smooth video performance--and so that your graphics don't get mixed in with all the other stuff your computer is running.  They come equipped with:
     --A special processor of their own, called a Graphical Processing Unit (GPU).  This processor is especially designed for 3D functions.  Most graphics cards actually just use a whole bunch of little ones to get the job done--so there's less blips and visual glitches.  
     --Onboard RAM:  This is just the main buffer zone for the GPU to do its thing.  
     --A Core Clock:  Similar to the clock speed for your CPU--this is the "tick" or heart beat of the video card.  Its measured in Mhz--meaning millions of cycles per second.
     --Memory clock: how fast the GPUs can talk with the RAM.  
     --Ports:  They have to let the monitor plug in somewhere.  DVI is the most common High-definition port available.  SVGA is an older one (often blue), and it gives a pretty solid transfer rate.  Some will also have S-Video--this is designed to let you use a TV or a Television Projector with your video card.

---

### Post by jlambeth1 on 2007-09-07
I agree that this sounds like a great idea as I have got my system tweaked just right for me but still feel very much like a noobie.  I would like to add that every question (minus one question regarding obsolete equipment) that I have posted has been answered with the utmost professionalism.  This is the best forum I have ever participated in and it is what makes me more of an Ubuntu convert everyday.

---

### Post by Shaktipwr on 2007-09-07
I haven't read everything but, thank you.  You f**king ROCK!!!!  I just posted (without seeing your post) that I am intimidated by posting cause everyone "knows so much"  I am an absolute linux noob and a totally intrigued, excited and enthralled by it.  I have also just recieved a Feisty Fawn machine.  I thank you for looking out for the rest of us!

---

### Post by tyggna1 on 2007-09-08
I'm an over vocal Ubuntu Zealot.  I carry a copy of the Live CD with me where ever I go, and offer to give a copy to anyone as soon as I learn that they use a computer.  I'm not yet to the point where I'd hand out them out at the airport in an orange robe--but who knows how far I'll go with it.  After all, I've only been using Ubuntu for a few months now.

For a lot of people who are new, they find this new operating system exciting, and even enchanting.  Others quickly become disenfranchised and drop the idea all together.  In this article, I want to share some facts about Ubuntu in order to give you--the new user--the firepower you need to make Ubuntu appealing.  Not all of this will be pretty, and not all of them will make Ubuntu   out to be "the best operating system of all time!" but they will help educate you, so you will know the "selling points" of Ubuntu and be armed to spread the Open-Source joy abroad.


_**Business**_

Linux, as a whole, has always had a stranglehold over the server market.  Steve Ballmer knows this, and it probably keeps him up at night.  There are two extremely good reasons why Linux takes the server market--and why Ubuntu should take the business market within the next few years.  Here are the points that appeal to businesses.

**1.   Free**  - Windows is not free for a business.  Litigation, started by a single pirated copy, can be extremely costly to a business.  I hear business men say all the time, "I just can't afford to upgrade everything to Vista--it would cost me over $5000, and my computers work fine the way they are now."
    My dad (a manager in Intel's chipset architecture department) commented, upon first seeing Ubuntu,  "Intel would save, literally, millions of dollars in licensing fees if we all worked on Ubuntu machines."  The Licensing fees alone make Ubuntu extremely appealing on the business end.  The main reason why they won't change right away is because you can't turn the Titanic on a dime, and switching all the computer systems of a corporation is, often, just too costly--even though the software is free.
     That's the downside on this selling point.  It isn't actually free.  All there employees will need to spend a few hours learning this operating system.  At an average wage of $15 per hour, you're looking at an average of $60 per person to make an effective switch.  It is a one-time cost, and after that, all software is either free--or extremely costly to have it produced yourself.

**2.  Security**
   A lot of businessmen are very prejudice when it comes to security.  After all, their data is their livelyhood.  Saying that Ubuntu can't contract a virus (with proper user-restrictions in place) is a definite selling point there.  Also--the fact that the core of Linux has been designed and developed by hackers--who also have a bit of security fetish, can sweeten the pot.  This won't be enough to sell them on the security point, I'm afraid.  I've tried.  And the reason is, again, with the new users.
   You just can't make an operating system dummy proof.  I take phone calls for 6-hours everyday to help people fix there computer, and I can tell you that 4/5 calls will effectively prove that point.  Heck, I crashed my Linux machine twice in the first week!  A system that you don't know how to use won't be as secure because you'll have to learn--by experience--how to secure it.
    There is hope, however.  Ubuntu can implement a cure-all policy.  It comes with a fire-wall built in, or a list of IP-tables.  The only way that a malicious program can access your data, is if you install something, and then give it your password to do so.  For a business administrator, simply install Ubuntu, and then don't give *anyone* the root password.  They won't believe you at first, that they can simply put in one password, never speak of it again, and that their system will stay as secure as Maid-Marian's virtue in Robin Hood, Men in Tights  (it's an everlast!).  
     Just explain, clearly and consciously that the root user is the only one that is allowed to change anything.  To install a program--or run a program that can affect the way your computer runs, Ubuntu needs that password.  In reality, a human being would sooner grow feathers spontaneously and learn to fly than a malicious program would be able to do any damage without you inputing your password.    Don't give that password to the end-user, and there won't be any trouble.  :D

**3.  Long life**
    This is a surprising fact, but Ubuntu will extend your battery life on a portable computer.  It wasn't until the late 90s that Microsoft implemented battery-saving measures--but Linux has had those built into it since the 80s.  Most people find, when switching from Vista, that their battery life will double.   This goes for desktops too, Ubuntu will cut down on your energy bill.
    There are two main reasons for this.  Ubuntu just schedules your system resources more efficiently.  This is why you won't notice much difference in loading time when opening three or four programs at once.  It sets your CPU at a steady pace that changes gradually according to your usage.   When you take all those jumps out of processor usage--the whole processor will run warmer--but it will take less juice over time to keep it running.
     The second is RAM.  RAM is the energy hog of your computer.  It takes about 10W to keep 128Mg of RAM powered.  So, for 1Gb of Ram, you need 80W!   Vista uses 512Mb of RAM when it isn't doing anything.   Ubuntu uses about 40Mb.  Hmm, 40W, or 3W--what's gonna make your battery last longer?   Oh, and one other thing,  Windows has a memory leak.  That means that your RAM will fill up gradually over time.  Junk gets stored there and doesn't clean out.  For you Windows Server admins, have you ever wondered why your server needs to be rebooted once a month?  That's why.  Ubuntu has no gunky RAM build up.
      The last point will explain why it was designed this way.
[B]
4.  Scalable[/B]

Your Ubuntu machine will run just as well with 400 hard drives put into it, as it would with 1.  Windows won't--things will get bogged down.
Not only that, but with Ubuntu you can actually add a hard drive to your computer while it is still on!  Yeah, no joke!  It'll take a moment to read it, and then all you have to do is mount it--or format it if it isn't formated yet.  This is why Linux has taken the server market.
Ubuntu --along with any Linux distribution-- was designed around a, "no preset limits" policy.  The Ubuntu on your machine, unlike windows, can actually handle more than 4Gb of RAM--in fact, it can handle all the RAM you can stuff onto your motherboard.   

     Here's the selling point with this:  Upgrades are cheap and easy!  No limits, except for the physical limitations.  

      Take, for example, adding a new hard drive on a windows machine.  You'll have to shut everything down, plug it in right, set it to "master" or "slave" (or newer machines will do "cable select," and then make sure you're booting off the right hard drive, and then go into windows and take anywhere from 1/2  to three hours to preform either a quick format or a full format.   
     In Ubuntu, while your machine is still on, you can plug in the new hard drive--it doesn't care about masters and slaves, really, GRUB takes care of all that.  Go to System, administration, and the GNOME partition editor, and you can have that drive formated and mounted in less than 10 minutes.   No rebooting required :D

Also--upgrades to Ubuntu and to your installed software, happen automatically.  You've already noticed that this happens--and it happens so smoothly that, after a while, you won't even think about it.  So, not only can you actively do a lot to make your computer better, but it will upgrade itself naturally.   Free, quick, painless, and endless upgrades?  Try taking that to your boss.


***Home usage***

**Usage:**
98% of all computers are being used to browse the internet right now, as we speak.  If the world were a better place, then 80% of that wouldn't be there (as that's how many searches are pornographic in nature)--but the fact remains that internet browsing is the main reason for owning a computer. 
    There's only one reason why Ubuntu wouldn't have Windows beat in every aspect on this point:  most people don't like change.   Sad, but true.  Change is the driving force behind economies, evolution, and putting new clothes on.  If you're like me, then you really hate that last one.  People won't change unless it's easier to change than to stay the same.  
     The biggest selling point here will only come at an opportunity.  When someone gets a really nasty virus that hasn't been cleaned off yet.  Offer Ubuntu as a solution.  If they aren't tech-savvy, then just say that the fix will require a "slight change in the interface."  Just tell them their menus will move around a bit--and a few things will look different.  Most of them will be just fine with that.  Just take the time to install Ubuntu--and 98% of the time, they'll never know the difference--after all, if they don't know how to do something with their new "interface," then they probably already come to you for computer advice anyway.  Also, you can then direct them to the forums and just say, "this is where all the tech geeks hang out, they can fix your computer."  And we can.
[B]
Speed:[/B]

It took me a solid 6 minutes to boot into windows XP pro and get full control.  I usually got a snack while it was booting up.  Ubuntu--2 minutes and 15 seconds flat.  Now, I can turn my computer on, check my e-mail, and go in less than 5 minutes total.  It's pretty sweet.   That extra 5 minutes a day really adds up.  Even if their 5.1 surround sound doesn't work at first--saving those 3 minutes at start up every time they want to use their computer will make their experience with technology much more enjoyable.
Heres why:   The absolute bare bonez of Ubuntu is about 60Mb.   The barest form of Windows XP is 140Mb.  You have less than half to load volume there.  Also, Windows is based off services.  Services just do little things, like let your anti-virus start up, manage your file sharing, and, oh yeah, use the bulk of your hardware.  Each service averages about 2Mb of space.  Given that XP has about 100 services that it needs to start on boot up, you can tac on about 200Mb to their bare-bone kernel.
Ubuntu has, on average, less than 20 items that start-up in addition to the bare-bonez (which we call the kernel).   Only about 5 of these are absolutely necessary.  Again, compare up to 100Mb needed to load and run on bootup, or a minimum of 300Mb.  It's really a no-brainer which one most people (and computers) would prefer.  Oh, yeah, and because it requires less work from your hardware--your computer will last longer.

**Free:**
   Around the forums, we often say that "windows is free."  Read [here]("http://articles.tlug.jp/Windows_Is_Free") if you want to know why.  Yes, for most people, you didn't actually go out to the store and pay $200 for windows, did you?   You got it from a friend, or from school, or it came preloaded on your system, and you never really saw the cost of it.  Ya know what, yeah, it's true, Windows is free if you want it to be--so don't try to sell Ubuntu on the "it's free" point.

     Have you ever tried recording music in Windows?  If you haven't, then don't bother.  If you try to record more than one track--things get really messy.  Also, to get the software you need to really use your computer for recording costs about $40--in windows.  In Ubuntu, it's free.
     Say you want software that will help teach your kid a new language.  Windows: $20, Ubuntu--free :D.   A new Office Suite--Windows: $120, Ubuntu--free.  You get my point.  Windows itself is free--but if you want to do more than pluck around your file-system all day, then  you'll have to pay for it.  This is where Ubuntu really shines.



***My selling point to you:***

Here's why we want to sell Ubuntu.  Ubuntu's primary shortcoming is that it can't support all the hardware that's out there.  The people who make the hardware don't see any money in making it "Linux-friendly."  This goes for a lot of good software too.  I know people who would eat a bag of worms if it meant getting a Linux version of StarCraft 2.  
We want to sell Ubuntu--because then other people will sell to us.  The more of us, the more companies in the computer industry will cater to us.  If my sister used Ubuntu, and all her friends and so on and so forth, I wouldn't have to worry about tweaking and changing so many things in Ubuntu--the manufacturers would do it for me.

So, go forth, and spread the joy of Open-Source!

---

### Post by tyggna1 on 2007-09-11
I've posted this elsewhere, but I think it's good enough now to make my zine:

I love Ubuntu, and I'm at the point now with feisty fawn, that I don't believe I'll ever go back to windows.  I killed my windows partition, because Ubuntu has become comfortable for me.  It sure wasn't this way when I first installed it though.  I was new to Linux, and didn't know a lot of basic things.

I had used windows for so long, that I think that really handicapped me for the first week or two I had Ubuntu installed.  If I would've just not assumed some things, I could've been a lot happier with my new OS from the get-go.  Here's my top ten things that I wish I would've known when I first used Ubuntu.

**10.  Don't be a jerk.**
I didn't have to learn this one the hard way.  However, I've seen enough people who feel like they will "win friends and influence people" by belittling them, or by demanding something from them.  To set the record straight for everyone that is out there:  You are not smarter than anyone else, you are not stupid or "computer illiterate," and nobody else in this forum is either.  You may happen to know a little bit more about how to implement a wireless driver using modprobe--but not know anything about GIMP, or how to use it.  We share both code and knowledge here, so dig up those preschool manners and learn that sharing is caring (but keep all viruses to yourself please). 

**9. Scoreboard:**
Windows:  We're the best.  Linux: Isn't that swell?

Linux really isn't out there to compete in the same way that windows is.  If we can make your computer run better, and you can get what you want your computer to do out of Ubuntu, then you'll find a lot of friends here at the forums.  If you think that Linux has any kind of need or desire to measure up to windows, or any other OS for that matter, than you'll be sorely disappointed with Ubuntu.  The dominant attitude with Ubuntu seems to be:  Yeah, we're better than windows, but windows has it's uses too.  We *want* Ubuntu to be a windows killer/competitor, simply because it'll make computers cheaper and more efficient.
[B]
8.  Previous OS is incompatible[/B]
I switched from windows.  What I knew in windows doesn't apply to Linux.  I'm a newbie here.  I really do need to learn, and I really do need to take some initiative if I'm going to have the experience I want to have with my computer.  In a single phrase--only assume that you know nothing.

**7. Doing more with less**
That's Ubuntu.  It's small, it's quick, and there's it takes less space than a lot of other OSes.  Oh sure, you can change that, and you can add features and change settings until your heart's content--but it comes small for a reason.  Think of how different every computer is.  Now think of how different every computer user is.  Kinda a large pool of differences, huh?  Ubuntu will come with exactly what you need for 95% of the time you use your computer--and it'll be small and quick.  To get that other 5%, you'll have to keep reading.   Also, Ubuntu will better utilize just about everything on your computer better for that very reason--it's customized to your system--and doesn't follow the mentality "one size fits all."    Hence, with less money/hard drive space/systems specs, you'll be able to do more than you could with other OSes.  Occassionally, Ubuntu may require you to actually get a new part for your system.  This is rare--but, even if you just do word-processing, it'll be cheaper than the $140 for the new Microsoft Office 2007.

**6.  Learn how to backup and restore key files in a number of ways.**
Nobody likes OS reinstalls--and it's so easy to prevent them in Linux.  If you just backup a key file before you try to edit it (like backing up xorg.conf before attempt to use dual monitors) then you can completely avoid an operating system reinstall all together.  For some, you'll need to know what to put in on the command-line only--and won't be able to rely on a graphical interface.  For others, pressing alt-F2 and typing in gksudo nautilus will be enough--but be warned, if you don't write down how to replace the edited file with the backup, then you might not ever remember where it was on your hard drive, and whether the copied file comes first or second in the cp command.
[B]
5.  Experiment until you've got the mad scientists beat[/B]
Fiddle.  Poke.  Tweak.  Look.  Dissect.  Record.  Conclude.  Enjoy!  The more you experiment, the more room there is for reward--just remember #6.

**4.  Blue, pink, or chartreuse?**
You can make linux into anything you want.  Programmers:  This could be the best development environment you've ever seen--but you'll have to customize it yourself.  Media enthusiasts:  Make the iMac eat its heart out!- but you'll have to customize it yourself.   Gamers:  You can push your hardware harder than you could before (if only game developers understood that <sigh>)  but in all cases:  You need to customize it yourself!  Rosegarden won't record well without a low-latency kernel attached to it.   Anjunta needs a lot of dependant packages installed for you to get the best out of your C++ experience, and video drivers need to have some of their extra features added into xorg.conf to get some sweet eye-candy going.  

**3.  Ubuntu comes in pieces**
Remember legos?  Erector sets?  Mega blocks?  Guess what!?  That's what Linux is like too!  Ubuntu comes with all the essential pieces (in most cases) so you can build off the skeleton.  RoseGarden, Amarok, Wine, are all blocks that you add on to your OS to make it run in the exact way that is perfect for you.

**2.  Getting help takes time, and a plate of cookies**
Ubuntu says that it's provided with ABSOLUTELY NO WARRANTY -- this is only kinda true.  It comes with a culture that is based off of respect and concern for other people.  We respect those who know, and we're concerned about those who need help.  The only motivation that the "experts" have is out of the goodness of their hearts.  You can't demand anything, but the promise of being a friend to a person who will help you is often reward enough.  Be friendly in your posts.


And the most important thing I wish I knew when I started using Ubuntu:
**1.  Learn how to learn**
Reading is a part of life now.  You want something to work, expect to do a bit of reading.  It takes a bit of research to get something working exactly the way it should in some cases.  Be prepared to dig, discover, and learn.  You no longer watch the news at night, you read the paper.  Linux is for a more educated user base, so learn how to learn.


That's my top 10, maybe one or two will help you love your new OS even more ^.^

---

### Post by tyggna1 on 2007-10-15
Sorry it's been a few weeks since my last article--but I have a good excuse.  I'm a dad now!  Well, I'm used to little to no sleep, and I'm ready to share some Ubuntu wisdom.

This article is dedicated to those people who have tried to find a program online, downloaded a linux version of it, and then pulled out a lot of hair as they tried to get it to work in Ubuntu.  

Let me tell you now, there's an easier way--heck, it's easier than it was in Windows.   All you have to do is click on Applications->add/remove and then find the piece of software you want, click the check box next to it, and hit apply.   Ubuntu will install it, and do everything it needs to do for that software to work.   It's that easy!  Go on, try it!  I recommend something called beryl for nicer computers--it's definitely worth a try.  

If the application isn't there, don't worry, there's still a good chance that we can make this easy for you--but you'll have to read through a bit and type a few things in--it still isn't too bad.

**The basics of repositories**

    The answer to gLife, the Universe, and everything Linux is: Repositories.   Repositories are an online collection of software that is pre-packaged and ready to install in Ubuntu.   Add/remove is just a list of software that is available from the main Ubuntu repository.  Be warned--though, not all repositories have the ability to install from the add/remove menu.   

All repositories (relevant to Ubuntu) come in this format:

```
deb http://the.repository.url/ **<software type> <install type>**  
```

deb - means debian.  Debian is what Ubuntu is based off of--hence, what we use.
[http://the.repository.url/](http://the.repository.url/) -  where the repository is located online.
<software type>  - this is usually the short name of the version of Ubuntu that you use.  For me, feisty.   For others, edgy, and soon to be gutsy.  This tells the repository that you only want software for your specific distribution.  You can try adding an edgy repository to your feisty install--if you'd like, but the results aren't always favorable.
<install type> -- describes what legal category the software is under.  examples are non-free and main.
You can also add what type of repository it is, like multiverse or universe.  

There are three programs associated with installing software from repositories.   They are add/remove, synaptic package manager, and aptitude.
Add/remove you should know, and synaptic package manager lets you install software piece by piece (though, we call the pieces packages).
Aptitude is simply the text-based version of these two.  As most people are lazy, and making a graphical interface for everything takes quite a bit of time, you'll find a lot more programs simply by typing in ```
aptitude search <program name> 
```
than you would under add/remove programs.  

**_Adding a repository in the command line_**
(see a previous article, "Text-based interface" for more info).

If you're absolutely opposed to using the command line, or greatly prefer using the mouse, skip down--but trust me, this is easier than the alternative.

You can access the command line by clicking Applications -> Accessories -> Terminal.   That brings up the command line.   For adding repositories, we're going to use two commands  
```

echo <repository in proper format> | sudo tee -a /etc/apt/sources.list 
```

and
```
wget <url of key> -O- | sudo apt-key add -
```

I can already hear the comments:  What do you mean this is the easiest way!?  That's a lot of stuff to learn/remember.
Yeah, you're right, but you'll only have to learn this once, and then you're done--and it's only a three-step process every time afterwards.   So, sit down, put on some thinking caps--eat some fish, and let's wade through this once so you won't have to fret every time you want to add a repository.  

first in the command listed is echo.   echo just means, print this text. 
```
echo your face is dirty
```
prints the text: your face is dirty.  That's not too bad.

```
| sudo tee -a
```
sudo means --use elevated privileges. You're changing something that Ubuntu considers essential, so you need to use the elevated privileges.  
tee -a   means write with standard input--i.e. input text.

and /etc/apt/sources.list is your existing list of repositories.  Put all that together and you are just telling the computer:   Put this repository into my list of repositories.   Again, that command is:  
```

echo <repository in above format> | sudo tee -a /etc/apt/sources.list 
```

See, that isn't so bad.   Once we have our repository added, we need to get permission--from the repository--to use it.   That's where our second command comes into play.

Repositories use a set of keys.  Keys determine what you can do on a repository.   All you need is a key that gives you "download and install" permissions, which is commonly called the public key.   They're just files with a security code in them (typically in the .grp or .pub format).   Remember that command we use?
```
wget <url of key> -O- | sudo apt-key add -
```

wget simply downloads files from the internet,  the -O- says that it's a text file.  | says that we want that previous command to be added to this next command.  sudo is the same.  apt-key is the Ubuntu program that provides authorization to install, and add - means to use the downloaded file.  So, put it all together, and we're telling the computer:  get the authorization to use this repository, and then us it.   Not too hard, and worth memorizing the commands for.  


**_adding a repository in the graphical interface_**

If you absolutely must use the graphical interface, here's how to add a repository, but you'll quickly see that using the command line is much quicker.  

System -> Administration -> software sources

This is a graphical list of repositories.  As you can see by playing around here, there are a few different types of repositories.  The check boxes involve the repositories that are specific to your version of Ubuntu.   The next tab is probably blank--these are custom repositories you can add.   This is what we're interested in.
First, find a repository that suits you.    [Go here for instructions on adding the google repository]("http://www.google.com/linuxrepositories/ubuntu704.html")

If you skipped the command line section, the rest is what you missed.  

To explain:   Most repositories require a "key."   That key is there to keep people from changing the repository.   So, you need a key that will allow you to download--or a public key.  This key is provided by the vendor, and you'll need to save it onto your computer somewhere.   Import that key under the "authentication" tab in software sources.
     After that, add the URL given to you by the vendor in "Third Party Software"tab.   To do this, type it in the proper repository format:
```
deb [http://the.repository.url/](http://the.repository.url/) **<software type> <install type>**  
```

     Close out of software sources, and it should ask you to refresh your resources list.  That's it.  The google guide--with pictures, describes it best, so just learn that 5 step process, and do it every time.

**_alternative methods of adding repositories_**

Here's a sort of hybrid that will help with repository troubleshooting.   You can edit your repository list directly by pressing alt+f2 and typing in
```
sudo gedit /etc/apt/sources.list
```
*note, for kubuntu, it's kedit instead of gedit, and xubuntu is mousepad.

This brings up a text file of all your repositories.  You can type in the repository you want with a formal format here, and then add the key using one of the previous two methods.
# note, you may want to uncomment out the universe repositories for Ubuntu (by deleting the # before them), if it's legal to do so in your country (but if you're reading this and English is your native tongue, then you probably can).


**_The second hardest way to install_**
      This is probably what you tried when you first converted to Ubuntu:  download from a website and double click on the install file.   You probably got a bit frustrated when you double-clicked on it and nothing happened.  Well, to do this, you'll need to understand the following concepts:

1.Permissions
2.Install file types
3.What else might need to be installed along with it
4.How to add it to your menu/as a shortcut

1.Permissions:
       Linux security philosophy is exactly the opposite of Window's:  namely, Linux states, &#8220;if we haven't said you can use it, you can't.&#8221;
       That's why it never ran, you never gave it permission to run.   You can give it permission to run in one of two ways.   The easiest is right-clicking on the file, selecting &#8220;properties,&#8221; clicking the permissions tab, and clicking the box that says &#8220;allow executing file as program&#8221;   Then you can double click on it, and it'll run.   I'll warn you, though, you might run into some additional difficulties afterwards though.
        The other way uses the command line (For the rest of your Linux career, just learn to accept the phrase, &#8220;Anything you can do, the command line can do better&#8221;).  The command is ```
sudo chmod -C 777 filename
```
That just gives full access (read, write, and alter) to everyone.   You can read more about that on the forums if you're interested.  


2.Install file types
  Here's the five main catagories:   .deb, .rpm, .pkg, .run, and scripts.

.deb is a group of packages for a debian-based version of Linux (Ubuntu is debian-based)

.rpm means runtime package.  These are mostly used in Red-hat Linux (and similar distros), and will need to be converted to .deb by installing and using alien.

.pkg is a single package, and will need to be installed using aptitude anyway.

.run is a binary-based installer, it is self executable&#8212;just give it permission to run and it'll usually do the rest.   Developers use these when they want to be able to scan what distribution you're using&#8212;and will often confirm it with you during the install.   Other than that, you can expect these to behave like commercial installers.

script is unique to Linux.  Text can be executed&#8212;as Linux sort of has it's own programming language, so some installs are just scripts that allow you to do some fun stuff in Linux.

if it's .deb, .run, all you need to do is give it permissions, and then deal with the windows that pop up, and it'll take care of the rest.   .pkg is installed by typing in

```
sudo aptitude -S filename.pkg
```
in the command line.

	For a script, allow it to execute, and then &#8220;run in terminal&#8221; when it prompts you.
	
     .rpm is much trickier.   First, you need to install a CLI (command line) program called alien.   You can do that by typing 
```
sudo apt-get install alien
```
     Then you need to convert it to a debian package system (read the manual pages for alien first, though, you'll thank yourself later).   The command to do so is
```
sudo alien -d filename.rpm
``` 
     And that will convert it to a .deb package system&#8212;then treat it like a .deb, and don't be too surprised if it doesn't work.

3. What else might be installed along with it
      Linux cares about packages.  Think of packages like building blocks for software.  You need to build them one on top of the other.  That's referred to as a dependency.   If you install some packages in the method listed in this section, you'll find out what you're missing when you go to run it.  After that, it's just playing with legos to get everything you need.

4.How to add it to your menu/as a shortcut
      This is so that you keep your sanity later.   To make a desktop shortcut is the easiest.   Just right-click on the desktop -> create launcher.   When that window pops up, pick a name for it, and if the program installed itself in the /usr/ directory, then just type the name of it under command, and create it.   Not so bad.   
      To add it to a menu, just go to System -> Preference -> main menu, and that will let you edit/add menu items, and then it's much the same process as making a launcher on your desktop.


So, that's how you install anything you want in Ubuntu&#8212;from easiest to hardest.   There is one key method left out of this article, and that is compiling source code&#8212;but I'm saving that for a later article.

As always, please post comments on the [comment thread]("http://ubuntuforums.org/showthread.php?t=544581") and try to keep this one clean.

---

### Post by stinger30au on 2007-10-15
[a great Ubuntu PDF ezine is Ubuntu Full Circle]("http://fullcirclemagazine.org/")

---

### Post by tyggna1 on 2007-11-17
This is the *hardest* way of installing programs in Ubuntu.   It's not too bad--unless you're doing it for the first time.   Here are some tips to get you started:

Get the tools first.   
```
sudo aptitude install apt-file build-essential cvs subversion
```
Then follow these three steps:
1:   You have to build your own dependencies
         Remember how Linux is like Legos?  You have to put all the pieces together.   With aptitude and add/remove, all the pieces come together neatly packaged and put together.   When compiling from source, that's not the case.   Most advanced programs rely on other programs to run.   Tremulous needs OpenGL, GIMP needs a newer version of glib (graphics library),  and every program relies on a number of compilers to work.   It's enough to give you a headache three times over.
         Fortunately--most programmers make this easy for you.  Download the source code, unzip it, navigate to the new folder and then type in ```
sudo ./configure
```

        That lets you check the dependencies needed for the source code you're trying to install.  If ./configure doesn't finish--it'll stop on whatever dependency you're missing.  You might also want to read the INSTALL text file that comes with a lot of source code--this can help you identify missing dependencies.   

2:    The computer has to build the software
         Once you've got all dependencies in place, you need to transform the source code into a program.   This can take a long time for your computer to process.   Simply type ```
sudo make
``` once you're done with ./configure, and you're computer will run at full processing capability until it's done.   

3:    You need to install the software
          The code is built, but other programs might depend on it later--so they need to know where to find it, and Ubuntu wants to know where it's at too.   Type ```
sudo make install
```  when make is finished to accomplish this.

And you're done.   Doesn't sound too bad, right?  Well, try it.   My first compiling project was GIMP 2.4 on feisty fawn.  Took me about an hour to figure out.  The difficulty of this method is the time that it takes.   Once you know about ./configure, INSTALL, and the "make" commands, you have everything you need to change linux source code into linux software.  Use at your own risk.

[Here's the community docs on this]("https://help.ubuntu.com/community/CompilingEasyHowTo?highlight=%28compiling%29").  They go into much more detail, and is worth the read.

---

