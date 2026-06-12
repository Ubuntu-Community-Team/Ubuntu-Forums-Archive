---
title: "How to install files into 7.04 Feisty Fawn, AMD desktop version"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by scrapmetal on 2007-09-15
How to install these files into:
7.04 Feisty Fawn, AMD desktop version
Tried on line lessons, forum searches etc, just don't seem to get it.
(I'm old and gray, my eye's are dim.)

Have experience from MS dos 5 prompt(terminal use) to xp-pro, "so many years wasted, so much useless obsolete knowledge in brain". At least I can still physically build computers.

May have unpacked msttcorefonts.tar.gz to "/" directory by mistake.
How do I check to see if I have?
How do I fix mistake if I have?
Does installing massive amounts of fonts slow the operating system, as it does in Microsoft?
Large font collection prefered as am ex commercial graphic artist and the correct font for the correct project is important to me.

Downloaded these files, how to install them?.

skype-debian_1.4.0.99-1_i386.deb
fonts.tar.gz
msttcorefonts.tar.gz

Placed them here:
/home/vaughan/Downloads/skype-debian_1.4.0.99-1_i386.deb
/home/vaughan/Downloads/fonts.tar.gz
/home/vaughan/Downloads/msttcorefonts.tar.gz

Any Help Greatly Appreciated, from this great global community.
Many thanks.

---

### Post by Maestro23 on 2007-09-15
Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

.deb = sudo dpkg -i packagename

The others are tarballs.  Must use the** tar** command.

---

### Post by scrapmetal on 2007-09-16
16/09/07 15:40:38 Australian.

Thank the powers that be Ubuntu is not windows.
Yes Ubuntu is for me, and after I learn enough, the charity and volunteer workers in my community.

Been to these sites, thanks.
Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Will try [http://ubuntuguide.org/wiki/Ubuntu:F...eryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:F...eryl_.28ATI.29) , as I have not known about this one, thanks.

All files placed in vaughan directory prior to commands executed
Results were as follows.

vaughan@scrapmetal-vaughan:~$ sudo dpkg -i  skype-debian_1.4.0.99-1_i386.deb
dpkg: error processing skype-debian_1.4.0.99-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 skype-debian_1.4.0.99-1_i386.deb

sudo tar -i msttcorefonts.tar.gz
vaughan@scrapmetal-vaughan:~$ sudo tar -i msttcorefonts.tar.gz
tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.

sudo tar -i fonts.tar.gz
vaughan@scrapmetal-vaughan:~$ sudo tar -i msttcorefonts.tar.gz
tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.

Obviously have to learn a lot more. My mild brain injury dose not help.
Many thanks, will advise further progress or lack of later.

---

### Post by Maestro23 on 2007-09-16
You can always get the syntax for a command by looking at its "man" page.  Example, in a terminal:

> man tar

Brings up everything about the **tar** command.

Also here's a link to the Feisty starter's guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Working_with_archives_and_packages](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Working_with_archives_and_packages)

LinuxCommand.org(Basic Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

RootSudo (Ubuntu's root, so to speak): RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Remember man, baby steps... baby steps.:)

---

### Post by sumguy231 on 2007-09-16
> vaughan@scrapmetal-vaughan:~$ sudo dpkg -i skype-debian_1.4.0.99-1_i386.deb
dpkg: error processing skype-debian_1.4.0.99-1_i386.deb (--install):
package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
skype-debian_1.4.0.99-1_i386.deb
You need to dowload the x86-64 versions of those (if available) rather than the 386 ones. Barring that, there is a way to install 32-bit stuff, but I don't know anything about 64-bit systems.

---

### Post by AnRa on 2007-09-16
You may install msttcorefonts like this:```
sudo apt-get install msttcorefonts
```;)

---

### Post by mocoloco on 2007-09-16
I'm all for learning command-line tools and it sounds like you're not afraid of the blinking cursor :), just wanted to make you aware that you can also do these things graphically.
Install .deb file - double click it.
.tar.gz, right click, select "extract here".  Files will be extracted in new folder

The fonts should go in /usr/share/fonts.  If you just browse to that folder your user doesn't have rights to copy to it, so you can run Nautilus (the file browser) using sudo (hit Alt+F2, type "gksudo nautilus"), just be aware you'll have all access and can mess things up if you go deleting stuff left and right!  Then you can drag and drop into that folder.

Or of course just copy the files using the cp command in the terminal.

---

### Post by scrapmetal on 2007-09-16
16/09/07 18:17:01 Little place in big Australia

Thanks for the learning resources on line (I now have Broadband) as they are hard to find in the local library, unless real old Unix books are to your liking.

Do not rename skype-debian_1.4.0.99-1_i386.deb to skype-debian_1.4.0.99-1_amd64.deb
and run this: It dose **_NOT_** work.

sudo dpkg -i  skype-debian_1.4.0.99-1_amd64.deb

Obviously have to learn a hell of a lot more. My mild brain injury dose not help.
Little steps, I will try my best. To banish ms/xp/vista from their world of hurt is my goal.
Many thanks, will advise further progress or lack of later.

---

### Post by Soarer on 2007-09-16
You're making life more difficult for yourself by thinking in the 'Windows Way' :)

Generally, we don't download binaries & install them on Linux. We use repositories, which contain thousands of programs already formatted & tested (usually) for Ubuntu.

For example, msttcorefonts are in the 'Multiverse' repository. Just select (from the menu top right) System, then Administration, then Synaptic Package Manager. Search for msttcorefonts, right click & install. Click apply & it will do it for you :)

Skype is in the Medibuntu repository, which you will have to add for yourself. Instructions are [here]("https://help.ubuntu.com/community/Medibuntu#head-129d92fb96c7303897b120c1e0948e766bb21400")

A bonus, for 64 bit users like us, is that Synaptic will choose the right architecture for our systems. Not sure is there is a 64 bit Skype - should be).

Give Synaptic a try - I MUCH prefer it to the 'download & double-click' method (and I have a few years on me too :) )

---

### Post by scrapmetal on 2007-09-16
Thanks, AnRa, did msttcorefonts terminal way. Perfect.

Will try fonts.tar.gz as mocoloco suggested.

Skype after that.

Have to get the windows way out of my head.
How do you re-format a biological hard drive?

Huge thanks to All.
will advise of further progress later.

---

### Post by scrapmetal on 2007-09-16
16/09/07 22:27:48 Little place in big Australia

Have tried fonts.tar.gz as mocoloco suggested.

Access to usr/share/fonts worked perfectly.:)

Looks like I had a fault in downloading.:confused:
Reported:
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

But I now know for next time!

Thanks from, Happy Ubuntu User.:KS

---

### Post by scrapmetal on 2007-09-16
16/09/07 23:58:47 Australia E.S.T.

Hi Soarer,
Thank you for the help:), bellow are the results::(

Medibuntu repository, added as bellow. 

Followed instructions in "terminal window" for "Ubuntu 7.04 "Feisty Fawn" as bellow:

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Terminal window confirmed successful operation.:popcorn:
Opened synaptic package manager, and the following occurred.

Synaptic showed no entry for Skype. :confused:
Did search for skype, and produced no results.:confused:
So it may be there is no 64 bit skype available.
Can I install a 32 bit version?:)

(I remember 8 inch floppy drives and hard drive platters bigger than dinner plate's)

Thanks from, Semi Happy Ubuntu User.

---

### Post by scrapmetal on 2007-09-16
17/09/07 00:48:44  Time to sleep.

More feed back.

Synaptic Package Manager:
Reload activated.
The following happened;

An Error Occured::mad:
The following detail are provided.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Synaptic package manager returned to normal.

Back to the drawing board.:confused:

---

### Post by Soarer on 2007-09-16
There seems to be no 64 bit version of Skype (surprise, surprise).

However,[ this thread]("http://ubuntuforums.org/showthread.php?t=77069&highlight=skype")  shows a way to run the 32 bit version on 64 bit. I haven't tried it yet, but some people have got it to work.

No idea about Medibuntu (I run Gutsy) but the key is wrong. Maybe try again tomorrow to add that or send them a mail.

I remember punch tapes, me :)

---

### Post by Kilz on 2007-09-16
> **scrapmetal said:**
> 17/09/07 00:48:44  Time to sleep.

More feed back.

Synaptic Package Manager:
Reload activated.
The following happened;

An Error Occured::mad:
The following detail are provided.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Synaptic package manager returned to normal.

Back to the drawing board.:confused:

You may want to post questions about your Ubuntu amd64 install in the [64bit section of the forum.]("http://ubuntuforums.org/forumdisplay.php?f=134") There are also sticky posts there with links to other posts helpful to people running the 64bit version.

---

### Post by Soarer on 2007-09-16
Further to my last post re Skype.

I found some more instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=432295").

I did the Fiesty 64 install (I have Gutsy, and very wonderful it is too) and it just worked.

Superb job by Cappy (make sure you spell that right :))

HTH

---

### Post by scrapmetal on 2007-09-16
17/09/07 04:26:32   Australian. Time to sleep.:KS

More feed back.

Synaptic Package Manager:
Reload activated.
The following happened;

An Error Occured:confused:
The following detail are provided.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Synaptic package manager returned to normal.:confused:

google earth worked in Synaptic Packet Manager - no restrictions
libdvdcss2 worked in Synaptic Packet Manager - no restrictions
Back to the learning board soon, will try skype after sleeep.:)

Thanks one and all, learning lots.:)

---

### Post by scrapmetal on 2007-09-19
Thank you Kilz for directions to the 64 bit section of forum.
A big thank you to Soarer for both links, the second one led me to cappy,
truly a fantastic place for solving skype issues,

The following may help the next searcher.

(video use in skype for amd 64 is reported to be ready in 2007, end of ?)
Copy and pasted Feisty Fawn 64 amd selection into my terminal and ran.
Partial load, probably because I was not logged in as administrator, but as normal user.
Broke terminal commands into sections so load password could be typed in, and then the next, etc.
Outcome was library's were installed, icon for skype installed but would not run.

THIS WORKED. 
If you read posting from start to finish, you will find in cappys an entry from craigsn on page 8 that only uses the commands for a new load of skype, once * lines are removed. Copy and paste into terminal, run. and it worked PERFECTLY for me.

A MONSTER THANKS TO ALL, 
learn t three different ways to install software properly. Once you get the hang of it, it is relatively easy. Will recommend 606.1 i386 Edgy Elf LTS on other computers.

An apple does not FALL to the ground, it avoids floating pointlessly around in space.

---

