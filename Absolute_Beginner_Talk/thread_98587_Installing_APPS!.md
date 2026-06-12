---
title: "Installing APPS!"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by surfoutsider on 2005-12-03
I have just recently made the switch to Breezy 5.10 from Windows XP but have already been met with difficulties.  Minus my hardware issues, I cannot understand how to install programs from the internet.  For instance, I would like to install the newer version of Firefox, Thunderbird and RealPlayer 10.  Every how-to guide refers to Synaptic but they never specify how to have Synaptic recognize the newly-downloaded programs that are on my desktop.  What needs to be done to move programs from downloaded on my desktop to active in-use programs?  Another frustration with this "for humans" how-to documentation:

Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x RealPlayer10GOLD.bin


To install Real Player 10, run the downloaded file. Type

sudo ./RealPlayer10GOLD.bin


For starters, how do I "change to the directory"?  Also, if the downloaded file is managed through the Archive Manager where is the directory?  Do I have to manually type commands in terminal windows to install RealPlayer?--I thought OS improved upon that over a decade ago.  I understand that this is probably a very easy task; yet for someone with no linux experience the help and how-to pages do a horrible job at explaining the basic necessary tasks of their seemingly "for humans" linux.  Any simplified help (from professional to novice) would be greatly appreciated.

---

### Post by d1337 on 2005-12-03
Easy slick...don't get frustrated yet.  From what I understand, Ubuntu builds of apps are supported by Ubuntu and sometimes take a little while before the upgrade is available as officially Ubuntu supported.  Your biggest challenge will be patience while you learn how things are done Linux style as opposed to MS style.  It's all relatively similar, but the slight differences will drive you nuts.  I'm actually now to the point that I'm more confident in Linux as opposed to MS...but it's taken me over a year to get there.

If you really want the newest Firefox, Thunderbird etc., there are ways, but there is also a learning curve combined with some research.  My questions would be...Why?  Is the stock Firefox install or Thunderbird missing some functionality that you desperately need?  Personally, I stick with mostly supported apps for the big deals like mail/calendar, webbrowser, etc.

As far as changing to directory, have you opened a terminal window yet or switched to a terminal via ctrl-alt-f* (*=1-6)?  Commands are similar to MS or DOS.  If I wanted to change to my Desktop from a command line, I would

cd /home/d1337/Desktop

of course the d1337 part is mine.  When you try this, type the first letter or two and hit tab for completion.  Once you are in a directory, try:

ls -la

to see all files & directories.  You may need to spend some time familiarizing yourself with how to navigate the filesystem before you dive in to installing bleeding edge apps that aren't part of the Ubuntu packages.

d1337

---

### Post by cwaldbieser on 2005-12-03
[QUOTE=surfoutsider]I have just recently made the switch to Breezy 5.10 from Windows XP but have already been met with difficulties.  Minus my hardware issues, I cannot understand how to install programs from the internet.  For instance, I would like to install the newer version of Firefox, Thunderbird and RealPlayer 10.  Every how-to guide refers to Synaptic but they never specify how to have Synaptic recognize the newly-downloaded programs that are on my desktop.  What needs to be done to move programs from downloaded on my desktop to active in-use programs?  Another frustration with this "for humans" how-to documentation:

Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x RealPlayer10GOLD.bin


To install Real Player 10, run the downloaded file. Type

sudo ./RealPlayer10GOLD.bin


For starters, how do I "change to the directory"?  Also, if the downloaded file is managed through the Archive Manager where is the directory?  Do I have to manually type commands in terminal windows to install RealPlayer?--I thought OS improved upon that over a decade ago.  I understand that this is probably a very easy task; yet for someone with no linux experience the help and how-to pages do a horrible job at explaining the basic necessary tasks of their seemingly "for humans" linux.  Any simplified help (from professional to novice) would be greatly appreciated.[/QUOTE]

Basically, Ubuntu maintainers take all the software officially maintained for the system an store it in big software repositories on the Internet.  Programs like Synaptic download software from the repositories and install it automatically for you.

If you are just starting out with GNU/Linux, it is probably better that you don't start out trying to manually install software.  That should come later, when you are more familiar with how to accomplish basic tasks.

The reason this can be difficult for someone new to the environment is because the software for GNU/Linux systems is often distributed as program source code.  Those files often have ".tar.gz" extensions.  The reason they are distributed that way is because the software is meant to run on many different types of machines.

It would be like if you were using Windows, and you wanted to get the new Word, and you bought the CD and when you popped it in the drive, there was no InstallShield-- instead you would have to copy the files to where they were supposed to go, and maybe you would have to install and run VC++ to compile parts of it.  

The process for installing souce programs in Ubuntu is a little more automatic than that, but that is why it is best to stick with Synaptic to start with.

Concerning Realplayer, Synaptic can't just install that software for you because Real does not package their software in a way that it recognizes.  Instead, it downloads the installed program Real wrote, and gives you their directions on how to run the installer.  These instructions do require you to open a terminal to run the installer program.

---

### Post by aysiu on 2005-12-03
Read this: [All four ways to install software in Ubuntu](http://www.psychocats.net/linux/installingsoftware.php)

---

