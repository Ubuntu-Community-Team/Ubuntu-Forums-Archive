---
title: "Few Questions from a New User"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by kc0eak on 2006-06-03
Hello,

I am fairly new to Ubuntu and I have some questions that I've come up with as I've been exploring it.  If you can help me with any of them, it would be greatly appreciated.  I'll list the questions first, then go into a little more detail if I need to.

- How do I get my wireless card to work?
- What are some common commands used in the linux terminal?
- Are there startup items in Ubuntu?
- How do I compress / extract files through the terminal?
- How do I delete an old kernel?
- How do I update firefox?
- How do I keep a device unmounted?
- How do I network with Windows XP?
- How do I uninstall some games?
- Where's the program files directory?
- Is there anything such as Defragmenting in Ubuntu?
- What are some good linux programs?
- How do I create a shortcut?
- How do I play Windows media files?
- How does linux handle spaces?

How do I get my wireless card to work?
- I've got a Netgear WPN111 USB wireless adapter.  I believe it has the Atheros chipset.  How do I get this to work with Ubuntu?

What are some common commands in the linux terminal?
- Pretty much self-explanatory.  Just wondering what others use the most.

Are there startup items in Ubuntu?
- Is there a way to start a program at startup (mainly an instant messenging program), similar to the Windows Startup folder?

How do I compress / extract files through the terminal?
- How do I make or extract a tarball?  I've downloaded some files that are tarballs, both plain and compressed (in gz or bz2 format), but I haven't figured out how to open them or extract them through the Archive Manager.  How would I do these 2 things through the terminal?

How do I delete an old kernel?
- After installing Ubuntu, I downloaded updates.  One of the things it did was to update the kernel.  Now when I boot up, I get the GRUB boot loader, and in addition to the current version of the kernel and Windows XP, I have the option to boot with the old kernel.  Is there a way to uninstall this so that the option is gone, or is the old kernel kept there for a reason?

How do I update firefox?
- The version of firefox that came with Ubuntu (at least at the time I downloaded it) was v1.0.8.  I want to update this to the current v1.5.0.3.  How do I do this?

How do I keep a device unmounted?
- Whenever I boot Ubuntu, it mounts hda1.  It's been a while since I looked at it (normally I just unmount it right away), but I think it's mounting my NTFS drive.  I can't actually read anything when I try opening it.  How do I keep this unmounted so it doesn't show up on my desktop every time I boot up?

How do I network with Windows XP?
- At my parents home, they are running Windows XP.  I connect to the router when I am there to access the internet.  That part works fine, but I can't figure out how to access our desktop computer.  How do I get the 2 computers networked so that I can transfer files between them through the router?

How do I uninstall some games?
- I have no desire to play some of the games that came with Ubuntu.  When I go into the Add Applications section to try and uninstall them, like I have done with some other programs, I get told that they are part of the system and can't be uninstalled.  I get the same message with some other programs I try to uninstall as well (I think the exact message says something about dependencies).  Is there any way to "strip down" the programs that came with Ubuntu, or will this mess up the dependencies of other programs?

Where's the program files directory?
- What directory is the "linux equivelant" of the Windows Program Files folder?

Is there anything such as Defragmenting in Ubuntu?
- Windows has the Disk Defragmenter utility to optimize the drive.  Is there any utility like this in Ubuntu?

What are some good linux programs?
- I've seen lists of the "best Windows freeware programs" or "Windows programs you can't live with out".  Does anyone know of any lists such as these about what some of the better programs for linux are?

How do I create a shortcut?
- I've tried making a shortcut to a text file I have on my FAT32 partition, but every time I try to open it, a box pops up with some options about running the file (or something like that.  This is being typed from the Windows side of my computer, so I can't look for sure right now).

How do I play Windows media files?
- I have a lot of video files in Windows Media format.  How can I play these (and other Windows media files) in linux?

How does linux handle spaces?
- I've had some problems in the terminal with file names with spaces.  How can I enter these into linux, or do I need to eliminate the spaces in order to enter them into the terminal?

Thanks again for all the help.  It is very much appreciated as I continue to learn about this amazing OS.

---

### Post by nalmeth on 2006-06-03
A lot questions, but I'll bite. Please point out anything I missed or anything that's still unclear.
- How do I get my wireless card to work?
Didn't work out of the box? If your up for some reading and learning, click the Wireless Help link in my signature.

- What are some common commands used in the linux terminal?
This is a tough one to answer, not knowing your priorities, and what you would like to use the terminal for. Ubuntu is trying to become a distro that depends on the terminal as *little* as possible. Elaborate on what you'd like to do with the terminal. Check the Learn the Terminal link in my signature.

- Are there startup items in Ubuntu?
Using the Gnome Desktop Environment? Go to SYSTEM -> PREFERENCES -> SESSION'S. You'll be able to add item's there. Just add the command for whatever you want. I.E. gaim (lower-case)

- How do I compress / extract files through the terminal?
You'll find that information in the Learn the Terminal guides, but you can really do this easier with-out the terminal. The Archive Manager should behave much like the window's application's you use. Try browsing to the archive in nautilus (file manager), right clicking on it, and hit Extract Here.

- How do I delete an old kernel?
You may want to hold off on this, unless you're sure you've got the right one. I'm pretty sure you can just use synaptic to uninstall them, or in the terminal,
sudo apt-get remove linux-kernel-yada-yada-yada
You may need to remove the entry on GRUB, but apt probably does that for you.

- How do I update firefox?
You must be using breezy. You can use automatix to install firefox 1.5 easily, again see my signature. You may want to install fresh or upgrade to the new Ubuntu Dapper Drake release. It is in stable condition. I've been using it for month's, but it's ready for the public now.

- How do I keep a device unmounted?
Don't need to use the device ever? One way to go about it would be (command line, just for fun :) )
sudo nano /etc/fstab

add a comment (##) to the start of the line you don't want mounted.
For example:
/dev/hda1 /media/hda1 yada yada yada
change to:
##    /dev/hda1      /media/hda1    yada yada yada

- How do I network with Windows XP?
Use samba. Not sure if it's installed by default. Search in synaptic for it, or via terminal:
sudo apt-get install samba
You can configure your shared folder's through Gnome.
Samba will work with your MSHOME network.

- How do I uninstall some games?
To tell you the truth I've never pursued this. I would guess that these are part of meta-packages, that would require uninstalling other programs to delete them. I could very easily be wrong. They probably take up little to no space, so if you'd like you can just remove them from the menu.

- Where's the program files directory?
This is a little complicated. I assume you want to go find the games folder's and delete them manually. You should know even from window's this is not good practice. It won't be that easy anyway. Essentially, the configuration files for each program are stored in your /home folder. They are hidden from regular sight. I think most of the application data is stored somewhere in the /usr folder, or /usr/share. Libraries are stored in /lib. DON'T try to uninstall like this unless you really know what you're doing. You could mess some thing's up.

- Is there anything such as Defragmenting in Ubuntu?
Not needed. EXT3 fragment's to such an insignificant amount that the effect's of any defragmenting is unnoticable.

- What are some good linux programs?
Where to start?
Please give some elaboration as to what you're looking for, there are about 16,000 packages in the repositories.

- How do I create a shortcut?
What kind? To an application? Drag it from the menu to the desktop, or right-click the desktop. Create Shortcut.

- How do I play Windows media files?
Use automatix to install restricted codecs, read [here]("https://wiki.ubuntu.com/RestrictedFormats") for information on why you need to do this, and why they are not included.

- How does linux handle spaces?
In the terminal? If your folder is called "Shared Folder" and you want to change to that directory, you *could* type it out completely like so:
cd Shared\ Folder
Notice the backslash. For explanation, read through the terminal guides I refered to you.
To make it easier though, just type some of the directory's name, and hit TAB to let the terminal finish it for you.

cd Sh TAB becomes cd Shared\ Folder

this work's with anything, including file-names, binaries, executable's, packages, anything.


I would really recommend upgrading to dapper before using automatix, if you are interested. Sometimes the app's and other "stuff" it installs can cause upgrade problem's.

Please post back with anything I missed, as I surely missed something.

---

### Post by Denis on 2006-06-03
[edit]There's always someone faster :D[/edit]

Those are a lot of questions. I'll try to answer some of them. 
You may also find it interesting to learn some things from the following websites about Ubuntu: 

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

These are the most important ones I know. And the forums of course. 

> What are some common commands used in the linux terminal?
A very nice guide about the terminal: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

> - How do I compress / extract files through the terminal?
Compress: tar -cf package.tar /path/to/directory
Extract: tar xvzf package.tar
you can find more information about the "tar" program in the manual: type "man tar" in the terminal to see all the options of tar. (you'll have to study it a bit, but it's a useful source of information)

> - How do I delete an old kernel?
I find it the easiest way to start synaptic ( system > admin. > synaptic ) and to search for  "linux-image". You'll get a list of installed kernels, right click to remove a package. The grub menu will be updated automatically. 

> - How do I update firefox?
The easy way is to wait untill it is updated in the next release of Ubuntu. If you really want the latest version, you'll find some info on the forum. Any security updates will also be done for the current release, but that won't change the version of Firefox. 

> - How do I keep a device unmounted?
Devices are mounted when they are in "fstab". Open this file in the terminal "sudo gedit /etc/fstab"

remove the _line_ of the device you don't want to mount: like /dev/hda1 e.g. Save the file and the device will no longer be mounted next time. 

> - How do I uninstall some games?
Again, open synaptic. Search "gnome-games". If you remove this package all games will be gone. It looks like they can't be uninstalled seperatly. You can however disable the items in the menu, look for Alacarte (the menu editor)

> - Where's the program files directory?
Read about the directory tree in Linux here:  [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

In short: there isn't really a program files directory, the different parts of the programs are installed in seperate directory's, all in different locations. 
Read some of the help files on the internet, it will make things more clear. 

> Is there anything such as Defragmenting in Ubuntu?
Fragmentation on Linux filesystems is much less than in Windows. Besides, the effect of fragmentation is also less. So there is no need to do a defragmentation on Linux filesystems. 

However there is a program to do that (don't remember the name). But as I said it is not necessary, and can even be dangerous. 

An easy way to get the fragmentation away is to move the files to an other filesystem and then move them back. But again, normally that's really not necessary. 
> - What are some good linux programs?Here you can find some amazing lists. 
[http://ubuntuforums.org/showthread.php?t=33183&highlight=windows+linux+programs+list](http://ubuntuforums.org/showthread.php?t=33183&highlight=windows+linux+programs+list)

> - How do I create a shortcut?
I guess you did a right click on a file and chose "make link". If it is a text file Ubuntu may want to execute it, which isn't wat you want. Isn't there an option to just open the file?

> How do I play Windows media files?
Read this page about restricted formats: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

> How does linux handle spaces?Add a backspace (\) in front of them: "some file" will look like: "some\ file"


That will be all for today, I hope this helps. Sorry about any mistyped words, it's late you see :)

Look some things up on the forums, there's a lot of information to find here too!

---

### Post by nalmeth on 2006-06-03
@ Denis 
beat ya to it! :D

But you did answer a couple question's I didn't know. Also those documentation pages are sites that *every person who install's ubuntu should know about.* If I had known about them when I first installed, I could have saved myself a world of trouble.

Just to reduce confusion for OP:

Denis recommended 
sudo gedit /etc/fstab

I recommended 
sudo nano /etc/fstab

gedit and nano are just different text editors. You could use many other's, people just have their own preferences. 

I would recommend commenting the line in fstab rather than deleting it however, in case you want it back, it's just a matter of then "uncommenting" it. Then you don't have to look up what option's the drive should have.

---

### Post by CompShrink on 2006-06-03
Some very good answers to your questions, I would deffinately read through the three replies above me, but I bet you already did.

As mentioned, Automatix can be dangerous, it does a lot of stuff... but it can also be really useful.

I would suggest first trying this:

Go to Applications > Accessories > Terminal
and copy and paste in (including the "s!):

gksudo "gedit /etc/apt/sources.list" 


Add to the bottom the following line:

deb [http://tikal26.net/ubuntu/apt](http://tikal26.net/ubuntu/apt) breezy main

Close that, open Synaptic (Which will be your friend for installing/uninstalling almost everything). It's in System > Administration > Synaptic Package Manager

First click the reload button at the top, then search for **ubuntuplus** . I would suggest installing **ubuntuplus-recommended**, which will give you firefox 1.5, along with more media apps, which should let you play WMV etc. and a few other useful things, a download manager, etc.

---

### Post by kc0eak on 2006-06-04
Thanks for all the replys.  I'll have to look over some of that as soon as I can.  I had to post all of my questions, rather than just searching for them because I'm working at a Boy Scout camp, and our internet time is limited as we have to work some of the time.  Thank you for all the help and I'll reply if I need anything else.

---

