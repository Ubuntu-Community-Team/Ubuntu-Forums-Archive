---
title: "OpenOffice 2.4 Upgrade"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-27
I am currently running Kubuntu Gutsy with Open Office 2.3, but found out today on slashdot that OOo just released version 2.4. Is there a quick way to upgrade it to the new version? If it makes a difference, I will be upgrading to Hardy for KDE when the new OS is released (might wait about a month or so to make sure the basic bugs are worked out).

---

### Post by forrestcupp on 2008-03-27
If it doesn't make a difference, just wait until you get Hardy and you will have 2.4.

---

### Post by Joeb454 on 2008-03-27
Well Hardy still has OOo 2.3

When did you say 2.4 was released?

---

### Post by sarixe on 2008-03-27
no, if you check here: [http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu) , hardy has 2.4.0rc2

---

### Post by tekDragon on 2008-03-28
Well...  that still doesnt answer the OP's question.

In any case right now the .deb package for 2.4 is down on the OO site. I guess you could use the tar.gz, but I wouldnt be able to tell you which commands to input.

---

### Post by Joeb454 on 2008-03-28
**sarixe** I'm running Hardy :) It might be in the daily build, but if so they've not pushed it through the updates yet :p

---

### Post by spacefreak86 on 2008-03-28
I noticed it on slashdot, but yeah, the .tar.gz file is out on OOo, but I don't know how to compile from source, which is why I prefer the .deb or .rpm packages (makes it much easier). Unfortunately, I cannot figure out how to uninstall something that I installed via this method, so I suppose wait until it comes out on the normal Adept updates?

---

### Post by fourscore on 2008-03-28
To rephrase the  OP's question :     Will  OpenOffice 2.4 be made available for Gutsy  or do we have to upgrade to Hardy to get it ?

---

### Post by waspbr on 2008-03-28
just checked on hardy, I got version 2.4.

---

### Post by ramjet_1953 on 2008-03-28
Here's a Bit Torrent link that may work to download the .deb:

[http://borft.student.utwente.nl/~adrian/torrentphp/torrent.php/OOo_2.4.0_LinuxIntel_install_en-US_deb.tar.gz.torrent](http://borft.student.utwente.nl/~adrian/torrentphp/torrent.php/OOo_2.4.0_LinuxIntel_install_en-US_deb.tar.gz.torrent)

Regards,
Roger :cool:

---

### Post by PmDematagoda on 2008-03-28
> **fourscore said:**
> To rephrase the  OP's question :     Will  OpenOffice 2.4 be made available for Gutsy  or do we have to upgrade to Hardy to get it ?

No it will not unless OpenOffice 2.4 has significant advantages over OpenOffice 2.3 in terms of security and if OpenOffice 2.3 cannot be patched with those updates without upgrading to 2.4.

But upgrading OpenOffice should not be too hard, just download the archive from the website, unpack it and run:-
```
sudo dpkg -i *.deb
```
after that is done you may install the gnome package to get better integration.

---

### Post by waspbr on 2008-03-28
check'em out for yourself:

[http://www.oooninja.com/2008/03/new-features-openofficeorg-240.html]("http://www.oooninja.com/2008/03/new-features-openofficeorg-240.html")

treat your self to a nice cold and crisp beer while you read...

---

### Post by hasinasi on 2008-03-28
I just downloaded the torrent for the deb file.
If you unpack it, you do not get one deb file, but several ones. There is a script "update" that one can be executed. However, it fails with many errors (several dependency problems).
Trying to run some of the debs in the DEB folder (which is created after extraction) fails as well. 
Any ideas what to do?

---

### Post by Anubisxian on 2008-03-28
> **hasinasi said:**
> I just downloaded the torrent for the deb file.
If you unpack it, you do not get one deb file, but several ones. There is a script "update" that one can be executed. However, it fails with many errors (several dependency problems).
Trying to run some of the debs in the DEB folder (which is created after extraction) fails as well. 
Any ideas what to do?

I'm getting the same thing as well. I'd very much like to upgrade from 2.3 to take advantage of the tasty new features that 2.4 has to offer...

---

### Post by kool_kat_os on 2008-03-28
i didnt notice that it was release....they also changed the style of their website

---

### Post by Joeb454 on 2008-03-28
I'm hoping OpenOffice.org 3.0 will be in Intrepid (8.10) :)

It looks like a promising release, and I'm sure I'm not the only one who is wanting Office 2007 file format support :)

---

### Post by randcoop on 2008-03-29
I haven't tried, but the simplest way to install it should be to download the deb archive from here [http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0"), unpack it, change into the debs directory, and run ```
sudo dpkg -i *.deb
```

---

### Post by cOzAtS on 2008-03-29
yet it gets a lot of dependency errors...:( 

plus the ./updte script gives error about conflict with bundled Oo... :(

---

### Post by mister_pink on 2008-03-29
You could manually add the hardy repo, install it from there, ignoring all the other updates, and then remove them again. I can't vouch for this being a great idea but it's one way to do it...

---

### Post by cOzAtS on 2008-03-29
Would that be safe for the rest of my system? or would it demand dependencies for kernel and stuff?

---

### Post by randcoop on 2008-03-29
I wouldn't use the Hardy version, unless you decide to upgrade to Hardy.

You should not have run the update program, since that assumed that you had installed 2.3 from OpenOffice and not from Ubuntu.  I suspect that the problems you're now having with the dependencies arose because you first tried to run update, instead of just installing the deb packages.

Although it's drastic, at this point, you might want to consider completely removing OpenOffice in order to cleanse your system prior to a re-installation of the program.  Apt-get is hard to clean up in these circumstances and sometimes a purge is the only way.  If you remove both 2.3 and 2.4, you should be able to install 2.4, since it will be a fresh install at that point.  Of course, you'd also be free instead to reinstall 2.3 from the Ubuntu repositories.  

But if you clean things up, I think the the sudo dpkg -i *.deb will work with 2.4.

CAUTION AND NOTE: I am NOT telling you to remove documents.  Removing programs with apt-get will not remove your documents.  DO NOT just try to remove directories on your own.  

DOUBLE CAUTION: There are no promises associated with the idea of removing programs.  These are suggestions and they don't come with any guarantees.

---

### Post by spacefreak86 on 2008-03-29
Okay, so download the .tar.gz files, go to add/remove programs (in Kubuntu), remove OpenOffice, install OpenOffice from .tar.gz files. Does anyone know how to actually install the program,, or is there a single .deb file to run that will install it for me?

---

### Post by Unstuck on 2008-03-30
> Okay, so download the .tar.gz files, go to add/remove programs (in Kubuntu), remove OpenOffice, install OpenOffice from .tar.gz files. Does anyone know how to actually install the program,, or is there a single .deb file to run that will install it for me?

Make sure you download the .tar.gz file for Linux DEB.  You can get it here. [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

The directions below are very good.  In step 3, you can unpack .tar.gz with Archive Manager if you don't feel like messing with the terminal.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Good luck!

---

### Post by spacefreak86 on 2008-03-30
Grr. I got dumb and installed the package over the existing OpenOffice, then uninstalled the old one. Now 2.4 won't load. I then tried re-installing it, then purging it from system using Adept Manager, now trying to reinstall over existing 2.4. Is there a way to completely purge all versions of OOo and then just install 2.4?

---

### Post by Bubba64 on 2008-03-30
I upgraded to Hardy the Saturday after they Beta release and have done all the updates and now have 2.4 installed it is much faster coming on the screen, but I haven't used it for anything other than a presentation display from an email.

---

### Post by spacefreak86 on 2008-03-30
Okay, so I've somehow purged OO 2.3, now have 2.4 installed. But it won't load at all. I click the shortcut on the K-menu for it, the icon bounces around (as though the program is loading), and then nothing happens. um, help?

---

### Post by Joeb454 on 2008-03-30
Hmm...strange. I'm runing Hardy, and I don't have OOo 2.4 :(

---

### Post by Bubba64 on 2008-03-30
> **Joeb454 said:**
> Hmm...strange. I'm runing Hardy, and I don't have OOo 2.4 :(
I am quite surprised I have made a few tries at the straight debian downloads and purges but was never able to get anything installed so I would just reinstall the program from synaptic or the terminal. All I know is when I open this down loaded presentation from a original MM power point it opens in 2.4 weird stuff. When I downloaded Hardy originally it also kept FF 2.0 installed, nobody else seemed to have this, but I think on that I had reinstalled it straight from FF. I due check for updates to Hardy about every 4 hours and install, and I also have source code checked in the repositories.

---

### Post by spacefreak86 on 2008-03-30
Alright, I'm having major problems with it now. Long story short, right now I have 2.4 purged from the system, with 2.3 re-installed, but it won't load at all. I'm trying to re-install Java from the repositories after removing them, thinking that the error might be in Java and not the program itself. If someone could walk me through this in just getting Open Office 2.3 to work, I'll skip the 2.4 and wait for Hardy or OpenOffice 3.0 to come out and hope that things work that time around. I like the installer feature of 2.4 that it comes with, but if I can't get the program to load at all, it doesn't help too much.

---

### Post by Bubba64 on 2008-03-30
I reference to my claim of having 2.4 inatslled check this out
mark@mark-desktop:~$ sudo apt-get install open office
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package open is a virtual package provided by:
  kbd 1.12-19ubuntu2
  console-tools 1:0.2.3dbs-65ubuntu7
You should explicitly select one to install.
E: Package open has no installation candidate
When I wanted to save a MM Power Point I chose a presentation save but was told it it couldn't be saved and do I want the latest which would save it I said yes and got this virtual version. So after trying to open the original in it opened in 2.3 but I was able to save it in 2.4 format, really weird, although I have been using systray, due to being a college student and wanting open office to come up faster.

---

### Post by spacefreak86 on 2008-03-30
Alright, finally got it working for OpenOffice 2.3. Out of curiosity, what is the advantage of 2.4 over 2.3?

---

### Post by Bubba64 on 2008-03-30
> **spacefreak86 said:**
> Alright, finally got it working for OpenOffice 2.3. Out of curiosity, what is the advantage of 2.4 over 2.3?
Open the terminal and paste in this command  
sudo apt-get install openoffice.org
hopefully that will get every thing back in shape. Sorry I just noticed that you edited your post and that you have it working. Open Office 2.3 has been a pain in the @ for me but, I am not a GEEK it seemed to need that touch, it was also slow in starting up, and I have seen numerous complaints on the forum. Like any program though we run them on individual computers with individual impressions.

---

### Post by spacefreak86 on 2008-03-30
Mostly I ask to see if it is worth the hassle that I am having to upgrade it, or should I wait until Hardy comes out and hope it has OpenOffice 2.4 automatically installed with it (since it just came out after the beta, I'm not expecting the beta to have it). 2.3 seems to handle most issues, although graphing in excel, support for math functions that were created in Equation Editor, and an increased spell-check / thesaurus would be really nice.

---

### Post by Joeb454 on 2008-03-30
You might as well wait until Hardy...I mean, it's only 24 days now, so you might as well.

I'm actually waiting for OpenOffice 3.0 ;)

---

### Post by Bubba64 on 2008-03-30
I just found this link   [http://tombuntu.com/index.php/2008/03/28/openofficeorg-24-released-already-included-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/28/openofficeorg-24-released-already-included-in-ubuntu-804/)

---

### Post by calc on 2008-03-31
OpenOffice.org 2.4.0 (final release) debs should be in Hardy in the next few days and yes OpenOffice.org 3.0.0 should make it into Ubuntu 8.10 barring any release schedule slippage on the part of OpenOffice.org. The current version of OOo 2.4.0~rc2 in Hardy has the wrong splash screens which is why it appears to be 2.3.

---

### Post by fourscore on 2008-03-31
> **PmDematagoda said:**
> No it will not unless OpenOffice 2.4 has significant advantages over OpenOffice 2.3 in terms of security and if OpenOffice 2.3 cannot be patched with those updates without upgrading to 2.4.


This is a joke.   Why can't  OO2.4 be made available  in the Gutsy repositories.  Why should you force people to upgrade to Hardy.  From the comments  I note that  to upgrade later to  OO3.0  we will have to ditch Hardy and upgrade to 8.10.     I had a similar issue  when  OO2.3 was released last yr and  forced me to upgrade from Fiesty to  Gutsy.

Pls note OO2.4  is  a significant upgrade  over  OO2.3.1  else  it would have been  labeled as  OO2.3.2

I also note from some comments that   FF3.0 will also not be made available for Gutsy.

What is the point of  having  a 18 month support window and having softwares in repositories  if  version upgrades will not be provided.     Pls dont tell me to download  directly from   OO website and install.  It is ducking the issue at hand.

It is so easy to upgrade the OO version in Windws for eg.  I  moved from OO2.3.1 to  OO2.4 within an hour  in windows without having to upgrade the OS.

---

### Post by cotcot on 2008-03-31
joke

---

### Post by Bubba64 on 2008-03-31
> **fourscore said:**
> This is a joke.   Why can't  OO2.4 be made available  in the Gutsy repositories.  Why should you force people to upgrade to Hardy.  From the comments  I note that  to upgrade later to  OO3.0  we will have to ditch Hardy and upgrade to 8.10.     I had a similar issue  when  OO2.3 was released last yr and  forced me to upgrade from Fiesty to  Gutsy.

Pls note OO2.4  is  a significant upgrade  over  OO2.3.1  else  it would have been  labeled as  OO2.3.2

I also note from some comments that   FF3.0 will also not be made available for Gutsy.

What is the point of  having  a 18 month support window and having softwares in repositories  if  version upgrades will not be provided.     Pls dont tell me to download  directly from   OO website and install.  It is ducking the issue at hand.

It is so easy to upgrade the OO version in Windws for eg.  I  moved from OO2.3.1 to  OO2.4 within an hour  in windows without having to upgrade the OS.

Firefox 3 is in synaptic in Gutsy I installed it. By the way Linux is not Windows I don't care if you use that analogy I have never used Windows but you will draw a lot of negative comment.

---

### Post by mister_pink on 2008-03-31
There's a support window for the software in which they continue to provide important security and bug updates, they do not provide new functionality. They do this to try and keep the older but still supported versions stable.

The difference between this and windows is that to upgrade windows you have to go out and buy a new os, to upgrade ubuntu you press a button. Its hardly a massive problem. Additionally ubuntu is updated every 6 months, not every 6 or 7 years. 

Finally, in windows you have to manually install it anyway, its no harder to do this in ubuntu really, you just have to do it right. 

Finally finally, it might go in the backports repo at some point anyway.

---

### Post by hasinasi on 2008-03-31
> **Bubba64 said:**
> Firefox 3 is in synaptic in Gutsy I installed it. By the way Linux is not Windows I don't care if you use that analogy I have never used Windows but you will draw a lot of negative comment.

So bragging about the advantages of Linux over Windows is allowed but Windows becomes off-limits when it may be better here and there? 
Yeah, that's truly the spirit of free software which made me switch away from Windows! 
Or putting it from another angle: do you think ignoring its weaknesses is really going to help make Linux/Ubuntu the superior OS?

I just did the manual upgrade from 2.3 to 2.4 and I found it quite rough. I am sorry, but I have to agree that doing this in Windows would have been much easier, and it is something that could/should be improved in Linux/Ubuntu.

---

### Post by mister_pink on 2008-03-31
As I said before, in due time it will go into the official backports repo. I think is important again to say this: linux is not windows. The people that sort out the backports repo are not paid, they do so in their spare time. If you want things to happen more quickly, do it yourself. This is open software after all.

That said, I do think when it comes to installing things manually ubuntu could do with some improvements. Its rare that you should have to do it, making installing things in general much less painful than Windows, but when you do need to do it it is more difficult for some users than it needs to be.

---

### Post by Oldsoldier2003 on 2008-03-31
> **Joeb454 said:**
> **sarixe** I'm running Hardy :) It might be in the daily build, but if so they've not pushed it through the updates yet :p

look at the about box in an OOo app.Iit says 2.3 in bold print at the top- but in the fine print its says 2.4.0rc2

---

### Post by stchman on 2008-03-31
> **spacefreak86 said:**
> I am currently running Kubuntu Gutsy with Open Office 2.3, but found out today on slashdot that OOo just released version 2.4. Is there a quick way to upgrade it to the new version? If it makes a difference, I will be upgrading to Hardy for KDE when the new OS is released (might wait about a month or so to make sure the basic bugs are worked out).

Go to [www.openoffice.org](www.openoffice.org) and download the Linux DEB version.

You will need to untar the archive and do the following on all .deb files.

```
sudo dpkg -i *.deb
```

After that you will need to install the debian menus package.

Before you install the new OO make sure you uninstall the old OO completely.  The following command will remove OO off your system.

```
sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

---

### Post by tomsa on 2008-03-31
The following is copied from (I don't want to take credit for this- I still have to look it up): [http://www.tuxfiles.org/linuxhelp/softinstall.html]("http://www.tuxfiles.org/linuxhelp/softinstall.html") and should help you when you want to install packages from source.


< Installing software from source in Linux - 1.2 >

So you've downloaded a software package with tar.gz or tar.bz2 extension and have no idea what to do with it. Or perhaps you already know that it's most likely the source code of the program you want to install and you have to compile it, but don't know how. Don't worry, compiling and installing software from source in Linux isn't as hard as it may sound!

Author: Nana Långstedt < nana.langstedt at gmail.com >
tuXfile created: 13 July 2002
Last modified: 22 September 2005

contents

    * The procedure
    * Step 1. Unpacking
    * Step 2. Configuring
    * Step 3. Building
    * Step 4. Installing
    * Cleaning up the mess
    * Uninstalling


< The procedure >

The installation procedure for software that comes in tar.gz and tar.bz2 packages isn't always the same, but usually it's like this:

# tar xvzf package.tar.gz (or tar xvjf package.tar.bz2)
# cd package
# ./configure
# make
# make install

If you're lucky, by issuing these simple commands you unpack, configure, compile, and install the software package and you don't even have to know what you're doing. However, it's healthy to take a closer look at the installation procedure and see what these steps mean.

< Step 1. Unpacking >

Maybe you've already noticed that the package containing the source code of the program has a tar.gz or a tar.bz2 extension. This means that the package is a compressed tar archive, also known as a tarball. When making the package, the source code and the other needed files were piled together in a single tar archive, hence the tar extension. After piling them all together in the tar archive, the archive was compressed with gzip, hence the gz extension.

Some people want to compress the tar archive with bzip2 instead of gzip. In these cases the package has a tar.bz2 extension. You install these packages exactly the same way as tar.gz packages, but you use a bit different command when unpacking.

It doesn't matter where you put the tarballs you download from the internet but I suggest creating a special directory for downloaded tarballs. In this tutorial I assume you keep tarballs in a directory called dls that you've created under your home directory. However, the dls directory is just an example. You can put your downloaded tar.gz or tar.bz2 software packages into any directory you want. In this example I assume your username is me and you've downloaded a package called pkg.tar.gz into the dls directory you've created (/home/me/dls).

Ok, finally on to unpacking the tarball. After downloading the package, you unpack it with this command:

me@puter: ~/dls$ tar xvzf pkg.tar.gz

As you can see, you use the tar command with the appropriate options (xvzf) for unpacking the tarball. If you have a package with tar.bz2 extension instead, you must tell tar that this isn't a gzipped tar archive. You do so by using the j option instead of z, like this:

me@puter: ~/dls$ tar xvjf pkg.tar.bz2

What happens after unpacking, depends on the package, but in most cases a directory with the package's name is created. The newly created directory goes under the directory where you are right now. To be sure, you can give the ls command:

me@puter: ~/dls$ ls
pkg pkg.tar.gz
me@puter: ~/dls$

In our example unpacking our package pkg.tar.gz did what expected and created a directory with the package's name. Now you must cd into that newly created directory:

me@puter: ~/dls$ cd pkg
me@puter: ~/dls/pkg$

Read any documentation you find in this directory, like README or INSTALL files, before continuing!

< Step 2. Configuring >

Now, after we've changed into the package's directory (and done a little RTFM'ing), it's time to configure the package. Usually, but not always (that's why you need to check out the README and INSTALL files) it's done by running the configure script.

You run the script with this command:

me@puter: ~/dls/pkg$ ./configure

When you run the configure script, you don't actually compile anything yet. configure just checks your system and assigns values for system-dependent variables. These values are used for generating a Makefile. The Makefile in turn is used for generating the actual binary.

When you run the configure script, you'll see a bunch of weird messages scrolling on your screen. This is normal and you shouldn't worry about it. If configure finds an error, it complains about it and exits. However, if everything works like it should, configure doesn't complain about anything, exits, and shuts up.

If configure exited without errors, it's time to move on to the next step.

< Step 3. Building >

It's finally time to actually build the binary, the executable program, from the source code. This is done by running the make command:

me@puter: ~/dls/pkg$ make

Note that make needs the Makefile for building the program. Otherwise it doesn't know what to do. This is why it's so important to run the configure script successfully, or generate the Makefile some other way.

When you run make, you'll see again a bunch of strange messages filling your screen. This is also perfectly normal and nothing you should worry about. This step may take some time, depending on how big the program is and how fast your computer is. If you're doing this on an old dementic rig with a snail processor, go grab yourself some coffee. At this point I usually lose my patience completely.

If all goes as it should, your executable is finished and ready to run after make has done its job. Now, the final step is to install the program.

< Step 4. Installing >

Now it's finally time to install the program. When doing this you must be root. If you've done things as a normal user, you can become root with the su command. It'll ask you the root password and then you're ready for the final step!

me@puter: ~/dls/pkg$ su
Password:
root@puter: /home/me/dls/pkg#

Now when you're root, you can install the program with the make install command:

root@puter: /home/me/dls/pkg# make install

Again, you'll get some weird messages scrolling on the screen. After it's stopped, congrats: you've installed the software and you're ready to run it!

Because in this example we didn't change the behavior of the configure script, the program was installed in the default place. In many cases it's /usr/local/bin. If /usr/local/bin (or whatever place your program was installed in) is already in your PATH, you can just run the program by typing its name.

And one more thing: if you became root with su, you'd better get back your normal user privileges before you do something stupid. Type exit to become a normal user again:

root@puter: /home/me/dls/pkg# exit
exit
me@puter: ~/dls/pkg$

< Cleaning up the mess >

I bet you want to save some disk space. If this is the case, you'll want to get rid of some files you don't need. When you ran make it created all sorts of files that were needed during the build process but are useless now and are just taking up disk space. This is why you'll want to make clean:

me@puter: ~/dls/pkg$ make clean

However, make sure you keep your Makefile. It's needed if you later decide to uninstall the program and want to do it as painlessly as possible!

< Uninstalling >

So, you decided you didn't like the program after all? Uninstalling the programs you've compiled yourself isn't as easy as uninstalling programs you've installed with a package manager, like rpm.

If you want to uninstall the software you've compiled yourself, do the obvious: do some old-fashioned RTFM'ig. Read the documentation that came with your software package and see if it says anything about uninstalling. If it doesn't, you can start pulling your hair out.

If you didn't delete your Makefile, you may be able to remove the program by doing a make uninstall:

root@puter: /home/me/dls/pkg# make uninstall

If you see weird text scrolling on your screen (but at this point you've probably got used to weird text filling the screen? :-) that's a good sign. If make starts complaining at you, that's a bad sign. Then you'll have to remove the program files manually.

If you know where the program was installed, you'll have to manually delete the installed files or the directory where your program is. If you have no idea where all the files are, you'll have to read the Makefile and see where all the files got installed, and then delete them.


Hope this helps!
:guitar:

---

### Post by Bubba64 on 2008-04-01
> **hasinasi said:**
> So bragging about the advantages of Linux over Windows is allowed but Windows becomes off-limits when it may be better here and there? 
Yeah, that's truly the spirit of free software which made me switch away from Windows! 
Or putting it from another angle: do you think ignoring its weaknesses is really going to help make Linux/Ubuntu the superior OS?

I just did the manual upgrade from 2.3 to 2.4 and I found it quite rough. I am sorry, but I have to agree that doing this in Windows would have been much easier, and it is something that could/should be improved in Linux/Ubuntu.

Thanks for reading my mind like Karnak, GEEEEEEEEEEEE thats exactly what I meant to do restrict you from free speech. I was only pointing out the obvious, personally I don't care what you say or what system you run, but I was just trying to warn of the backlash I have seen at times when somebody RANTS. I have only used Linux because I didn't own a computer until a year and a half ago, and I got a computer from a computer from a re cycler that sells computers with Dapper. Personally wouldn't know if it is superior it is the only thing I have used, which by the way cost 30$.

---

### Post by kneewax on 2008-04-01
If we could avoid flamers here for a second.  Guys we just need to think about the way we type stuff - the written word can come across a lot harsher than we mean it too.  However I think you have unfortunately hit a nerve here.  There is an element in the Linux communities that cannot stand any mention of windows and the old chestnut that we shouldn't compare OS's comes out.  Well the thing is if folk didn't compare the OS's then ex-Windoze users would never switch.

Bubba64 you are an exception - and a lucky one at that! - most folk here have at some point migrated from one version of Windoze or other.  Linux and in my opinion Ubuntu distros in particular are superior to Windoze - However there are one or two elements where Windoze is, if not superior, then at least more user friendly and one of those very few areas is manual installation of software.  Now I actually find the package management system very helpful, because if it is in the packages then I don't generally have the computability worries I would have had in Windoze.  But there are times when you might want to install software that isn't in the repos or before it gets to the repos and I am afraid that in Windoze - for good or for bad - that is a lot easier - lets face it clicking on a self-executing installer is easier for most users than fumbling around with the command line - even if actually using the shell is more efficient.

What bothers me is that it is getting to the stage that no-one can mention anything the Windoze might do well or at least more easily without being flamed.  We need to acknowledge that most users here are here because they already prefer Linux to Windoze - Linux is not Windoze - and thank goodness for it - BUT remember you are most likely preaching to the converted.  If someone mentions that a particular task appears easier or more efficient in Windoze maybe we should be prepared to acknowledge that - not flame them for mentioning it.

The challenge facing the community is to overcome these areas and improve the way Linux does stuff - not so it becomes a Windows clone, but so the user experience of Linux is more friendly.  No one wants Linux to be Windows, but there are times when we could learn from other OS's no matter who builds them.

</rant>

Please no-one take these comments personally, I am just making comment on the board behaviour I have witnessed over the past year or so.

Kneewax

---

### Post by ImpressMe on 2008-04-01
> **forrestcupp said:**
> If it doesn't make a difference, just wait until you get Hardy and you will have 2.4.

And why would we upgrade the entire OS to get a bugfix release? Look at the polls about Gutsy... 20-30% had major problems after updating to Gutsy.

---

### Post by ImpressMe on 2008-04-01
> **Bubba64 said:**
> Firefox 3 is in synaptic in Gutsy I installed it. By the way Linux is not Windows I don't care if you use that analogy I have never used Windows but you will draw a lot of negative comment.

So what? This phenomenon is called discussion.

---

### Post by spacefreak86 on 2008-04-01
Gah, can we get back to the original topic?

---

### Post by ImpressMe on 2008-04-01
[COLOR=Black]Indeed. The debs from openoffice.org did not work. Nothing happens when launching the icons. No error messages from the console.

I downloaded the RPM's instead , converted them to debs with 'alien' and then installed these debs. 

EDIT: Never mind, it works when running the programs BUT now Synaptic wants to downgrade the packages. Not worth the trouble. Back to Windows and productivity.
[/COLOR]

---

### Post by mister_pink on 2008-04-01
Sorry that you decided to go back to windows. I guess linux isn't for everyone, but I thought I should let you know that linux does provide simple ways round these problems - all you need to do to stop it downgrading is tell it the force the version. Find it in synaptic and its in the menus.

---

### Post by noisygecko on 2008-04-01
I figured out how to go through all the steps to install 2.4 on my Ubuntu 7.10 only to notice that Ubuntu changed the version numbers by putting 1: in front of the packages.  That means the Update Manager keeps wanting to "upgrade" to the old 2.3 version (as just mentioned by ImpressMe).

Does anyone know how to stop the downgrade from happening?  And I don't mean just ignoring the Update Manager icon.

I don't know how to change the version numbers or names of the RPM to Debian packages I converted with alien, or how to tell the Update Manager to quit worrying about the openoffice.org packages.

I have to agree with several people in this discussion -- this shouldn't be so hard.  If the Ubuntu package managers/packagers don't want to bother updating things, then they should at least make it possible for others to do it.

-Sim

---

### Post by mister_pink on 2008-04-02
Just like I said above, you need to lock the version. By default its configured to favour software from the repos. Open synaptic (System-> Admin -> Synaptic package manager) and search for openoffice. Select the installed openoffice packages and then click Package -> Lock version

---

### Post by noisygecko on 2008-04-02
> **mister_pink said:**
> Just like I said above, you need to lock the version. By default its configured to favour software from the repos. Open synaptic (System-> Admin -> Synaptic package manager) and search for openoffice. Select the installed openoffice packages and then click Package -> Lock version

Thanks for the tip about locking the packages with Synaptic.  I missed you saying that when I read through the rather long thread to catch up, and don't find the word "lock" when I search the thread...

-Sim

---

### Post by randcoop on 2008-04-07
This thread has turned a fairly basic question (how to install OpenOffice 2.4) into a repetitive discussion about the pros and cons of Linux and Windows.

First, then, a quick word about the latter: Ubuntu and its various guises comes out every six months.  The expectation is that it is a rare situation indeed for a user to need to have updated versions of software more frequently than that.  In the case in point, the question that seems not to be asked is, why do you HAVE to have version 2.4 of OpenOffice?

Okay.  Here's the how-to for installing OpenOffice 2.4 on (K)Ubuntu:

First, use synaptic, adept or whatever other GUI apt program you like to remove OpenOffice 2.3 from your system.  Simply run a search for openoffice and remove anything that's installed.

Second, visit the OpenOffice site and download the deb file for OpenOffice 2.4 (here: [http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0]("http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0").

Third, open a terminal and navigate to the directory where you downloaded the file.  The command is ```
cd
``` follow by a space and the name of the directory.

Fourth, unzip the tar.gz file you downloaded.  The command is ```
tar -xvzf [FileName]
```

Fifth. change into the new DEBS directory you just created: ```
cd OOH680_m12_native_packed-1_en-US.9286/DEBS
```.

Sixth, install the files: ```
sudo dpkg -i *.deb
```

Seventh, change into the desktop-integration file: ```
cd desktop-integration
```

Eight, install the files there: ```
sudo dpkg -i *.deb
```

You should now be done.  And your menus should list the new OpenOffice 2.4 (if not, log out and in again).  

A couple of notes that may be helpful:

Your OpenOffice is now located in /opt, which is not where Ubuntu's version was installed.  So if you're looking for the executable files, look in /opt/openoffice.org2.4/program.

If your updater (Adept or Synaptic) continues to suggest that upgrades are available, it's because you didn't install an Ubuntu version of OpenOffice.  You can change get it to stop listing the upgrades by following the instructions here: [http://ubuntuforums.org/showthread.php?t=747470]("http://ubuntuforums.org/showthread.php?t=747470")

---

### Post by rod40cool on 2008-04-15
Thanks randcoop and others for this discussion about manually upgrading to OO2.4. I now have a better appreciation of the process of how Ubuntu versions of Linux software get into the repositories for installation of applications by us users using the very easy Synaptic Package Manager. Manual upgrading of software in Ubuntu is an area that could do with some addressing, but I am grateful to those community contributors who put hours of effort into producing this wonderful free open source operating system. Thanks for the instructions to upgrade but I look forward also to upgrading Gutsy to Hardy which upgrades every other piece of Ubuntu supported software I have installed at the same time.:):):)

---

### Post by maddentim on 2008-04-17
@randcoop,

Thanks for the solid step by step guide.  One follow up question.  After I upgrade in a month or so to Hardy, I think I am going to want to have the "official" ubuntu version of Openoffice installed.  That way, it stays maintained and all.  Will I be able uninstall this version of ooo from synaptic and install the ubuntu version?

EDIT: I did the randcoop process and looked at the post that he references and now see how it can be managed.  Thanks anyhow...

---

### Post by philinux on 2008-04-17
2.4 updates came through yesterday for hardy and everyone is saying it's much faster.

---

### Post by Joeb454 on 2008-04-17
I had OpenOffice 2.4 on Hardy a couple of weeks ago now..though more updates yesterday yes :)

---

### Post by randcoop on 2008-04-17
> **maddentim said:**
> @randcoop,

Thanks for the solid step by step guide.  One follow up question.  After I upgrade in a month or so to Hardy, I think I am going to want to have the "official" ubuntu version of Openoffice installed.  That way, it stays maintained and all.  Will I be able uninstall this version of ooo from synaptic and install the ubuntu version?

You should be able to uninstall using synaptic.  Once you install any deb file using dpkg, the apt system knows that it's there.  That's why I mentioned that you would get update notifications from update manager programs.  Because those programs see your installation and think that the ubuntu version is is upgrade.

Anyhow, again, the short answer is yes, you can uninstall the 2.4 version you have and then install the Ubuntu version.

But it may not be necessary.  Once you have Hardy installed, synaptic should look at your 2.4 version and compare it to the 2.4 version of Ubuntu and tell you that Ubuntu is an upgrade.  At that point, you can just upgrade to the Ubuntu version, without uninstalling.

Hope this is clear, but if not, let me know and I'll try again.

---

