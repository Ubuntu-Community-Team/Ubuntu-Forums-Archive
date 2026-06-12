---
title: "What is the Best Dvd ripper available?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-03
I want the best dvd-ripper application for ubuntu that has an **option** to copy not only the movie itself but the "main menu", "behind the scenes", "extra footage" and all that jazz. **Literally** making an **exact** **replica** of the dvd. 

Thanks in advance to anyone :]

---

### Post by riptreeper on 2007-04-03
That would be sweet to have that I would like to know about that as well I have an Lg external burner

---

### Post by Maestro23 on 2007-04-03
You guys can read up on diffrent programs here: [http://linuxappfinder.com/multimedia](http://linuxappfinder.com/multimedia)

---

### Post by newlinux on 2007-04-03
I usually do this in Myth, but I'm pretty sure k3b can do what you want at least with DVD5s...

You can use dvd::rip as well... (search for dvdrip, k3b, acidrip, dvd ripping in the forums - you'll find what you need). You can also do it command line if you are interested...

---

### Post by handy on 2007-04-03
I just run DVDshrink in Wine, it installs under Wine really easily, it is simple to use & incredibly reliable.  You can even edit what you want in or out of the backup DVD.  

It's legally free software as well.  Google for it, because it has been made illegal to host in the USA, or some such rubbish.

---

### Post by antoz on 2007-04-03
I have used shrink in windows, tried K3b in Ubuntu could not get it to work, any sugestions from someone who is using it?

---

### Post by newlinux on 2007-04-03
I have used K3b in the past. Could help you more if you told me what you did and what didn't work.  Tools->Copy DVD then check only create iso image... are you able to view dvds at all?

---

### Post by handy on 2007-04-04
I've tried a few different native solutions in Ubuntu, none of them have worked for me.

Admittedly I haven't tried too hard because DVDshrink does the job so easily for me.

---

### Post by TheMono on 2007-04-04
Have you tried k9copy 

sudo apt-get install k9copy

I haven't used it myself, as I don't want to do what you want to do, but I have heard it is excellent.

---

### Post by MockY on 2007-04-04
> **handy said:**
> I just run DVDshrink in Wine, it installs under Wine really easily, it is simple to use & incredibly reliable.  You can even edit what you want in or out of the backup DVD.  

It's legally free software as well.  Google for it, because it has been made illegal to host in the USA, or some such rubbish.

Thank you for that. It works perfectly and I am using it as we speak. *thumbs up *\\:D/

---

### Post by handy on 2007-04-04
> **TheMono said:**
> Have you tried k9copy 

sudo apt-get install k9copy

I haven't used it myself, as I don't want to do what you want to do, but I have heard it is excellent.

It probably is excellent, but it didn't work for me some months ago.  Maybe it's better now, & as I said in the previous post, I didn't try too hard... :)

---

### Post by splendid on 2007-04-06
I tried installing k9 and get the following message:

rob@basement:~$ sudo apt-get install k9copy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package k9copy

---

### Post by yabbadabbadont on 2007-04-06
And for discs that dvdshrink and dvddecrypter can't handle (newer ones mostly), there is dvdfabdecrypter.  I believe that the latest version runs under wine, but I dual boot so I haven't tested it that way yet.

---

### Post by yabbadabbadont on 2007-04-06
> **splendid said:**
> I tried installing k9 and get the following message:

rob@basement:~$ sudo apt-get install k9copy
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package k9copy

Make sure that you have the universe and multiverse repositories enabled.

---

### Post by bruenig on 2007-04-06
xdvdshrink is good. You should try that. It is native.

---

### Post by splendid on 2007-04-06
Any primers for installing xdvdshrink

---

### Post by yabbadabbadont on 2007-04-06
> **splendid said:**
> Any primers for installing xdvdshrink

[http://doc.gwos.org/index.php/Xdvdshrink](http://doc.gwos.org/index.php/Xdvdshrink)

The page was last updated a year ago, so let the buyer beware.  ;)

---

### Post by richbarna on 2007-04-06
> **splendid said:**
> Any primers for installing xdvdshrink

This is some info that I found at [Sourceforge]("http://dvdshrink.sourceforge.net/dvdshrink.html"):-


[FONT=Verdana,Arial,Helvetica][SIZE=16]**Required Software**[/SIZE][/FONT]   The following software MUST be installed and functioning for the DVDShrink to do it's job: [LIST]
[*]The transcode package and it's required codecs (ripping etc),
[*]the mjpegtools package (re-multiplexing),
[*]the mkisofs package (creating ISO images),
[*]the subtitleripper package (converting subtitles),
[*]the gocr package (for subtitles),
[*]the dvd+rw-tools package (burning), and
[*]the dvdauthor package (authoring DVDs).[/LIST]     The script also makes calls to 'cat', 'stat' and a few other standard Linux tools. You'll want to make sure that they are in your toolset (coreutils package). 

    If you want to run the GUI front-end you'll need to have perl and perl-GTK2 installed. 

I still think that you would be better off with [k9copy]("https://help.ubuntu.com/community/K9Copy"), I am running Feisty and it has worked flawlessly for me.

If you fancy playing around with some other distros, SAM Linux has dvdshrink native in the repos.

---

### Post by splendid on 2007-04-06
Following the guide.  Having problems converting to .deb   Get message

sudo alien dvdshrink-2.6.1-6mdk.noarch.rpm
File "dvdshrink-2.6.1-6mdk.noarch.rpm" not found.
rob@basement:~$ sudo alien dvdshrink-2.6.1-6mdk.noarch.rpm
File "dvdshrink-2.6.1-6mdk.noarch.rpm" not found.
rob@basement:~$ sudo alien dvdshrink -2.6.1-6mdk.noarch.rpm
Unknown option: 2
Unknown option: .
Unknown option: 6
Unknown option: .
Unknown option: 1
Unknown option: 6

---

### Post by DreamcastJack on 2007-04-06
I really dig AcidRip!  it does what I want.

---

### Post by splendid on 2007-04-06
Any links on how to install AcidRip?

---

### Post by bruenig on 2007-04-06
splendid, don't alien it, use the .tar.gz.

The dependencies can be installed with
```
sudo apt-get install transcode mjpegtools subtitleripper mkisofs dvdauthor dvd+rw-tools gocr libgtk2-perl
```
Then just extract the .tar.gz and run the install.sh with
```
sudo ./install.sh
```

I have created a .deb in which I added a menu entry and is very easy to install, but I don't know where exactly to put it since it is too big to attach here and I am not really a packager or anything so I can't get it in the repos.

---

### Post by kpkeerthi on 2007-04-06
I'm more than happy with AcidRip.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#CD_.26_DVD_burning_.26_ripping](http://ubuntuguide.org/wiki/Ubuntu_Edgy#CD_.26_DVD_burning_.26_ripping)

---

### Post by nonewmsgs on 2007-04-06
the dvd decyptors that are for linux havent been able to be able to beat the new copy protection schemes.  if anyone knows of any linux will crack the tougher ones like saw3, give me a hollar please, because i would prefer that.

both of these are under WINE

dvdfab under wine gives me a rip that looks like it isn't decrypting it.

i love ripit4me.  it automatically makes a PSL file and sends it to dvd decryptor and then opens dvdshrink for you.  ah the 1 click button.  'nuff said.

---

### Post by handy on 2007-04-12
I could not get ***[DvdFab Decrypter]("http://www.dvdfab.com/free.htm")*** to install with Wine, has anyone else got it to work?

---

### Post by ramjet_1953 on 2007-04-12
I use K9 copy on a regular basis and it does a good job of converting a DV9 to DVD5 without any problems.

However, I have found in my particular instance that when I have the auto-burn option enabled, when it comes time to burn K9 copy crashes and as a parting shot, deletes the iso as well!

I overcome this by disabling the auto-burn option and just have it save the iso. I then use K3b to burn the disk.

I am running both programs under GNOME, and as they are actually KDE apps, that may be my problem with auto-burn.

With these programs, you need to make sure that writing permissions are set-up properly.

Regards,
Roger 8-)

---

### Post by eric p on 2007-04-13
I would also say k9copy is the way to go. I was even able to backup discs that I couldn't using dvdshrink and anydvd. DVD backup was the last hurdle for me ,other than gaming I only boot into windowz now to play games.

---

### Post by pkh106 on 2007-04-25
After some intensive research, i found this (haven't tested it), but apparently, it'll get DVDFab working under wine in Ubuntu.

(Begin Paste - As of 04/09/2007) - so it's pretty recent, taken from WineHQ

Running DVDFab Decrypter 3.0.9.6 on wine 0.9.34 compiled from source under Ubuntu Feisty.

[https://home.comcast.net/~elijah1718/WineDLLS.tar.gz](https://home.comcast.net/~elijah1718/WineDLLS.tar.gz)

That's a package of Windows XP dlls I gathered together to get everything working as intended.

Okay... after you get that copy them to /home/username/.wine/drive_c/windows/system32

Then run sudo winecfg

Set it to run as Windows XP then drives click autodetect then advance.. make sure your cdrom is set to cd-rom.

After that click Libraries tab and then add mfc42.dll to override.. it should be set to (native,bultin).

Then run winecfg and do the same thing over again.

Then make sure to restart your entire pc.

This is how I got mine working on the latest dvd decrypter 3.0.9.6.

I am not sure if that is EVERYTHING... if not, add a comment with anything I missed... if everything did work.. congrats.

---

### Post by Cerny on 2007-06-20
I'm quite a fame of acidrip. It works really well and does amazing quality of placing the video in avi formant.

---

### Post by BrokeBody on 2007-06-20
I use AcidRip. It does the job.

---

### Post by rf186 on 2007-06-25
I have managed to get DVD Shrink & DVD Decrypter running under Wine, without much hassel & they seem to work fine on most DVD's, but some newer DVD's require more up to date software, So I also have a copy of DVDFab Platinum 3.0.8.0 which seems to install using Wine, but then I get an error message that "burning engine failed to initialize" I seems to rip DVD's OK, but it won't burn them?
Anyone have any ideas on how I could possibly fix this (DVDFab is setup to run in a Wine-WinXP environment)

---

### Post by patsimon12 on 2007-06-25
Have you tried something else actually native to linux (like k3b)?

---

### Post by yabbadabbadont on 2007-06-25
> **rf186 said:**
> I have managed to get DVD Shrink & DVD Decrypter running under Wine, without much hassel & they seem to work fine on most DVD's, but some newer DVD's require more up to date software, So I also have a copy of DVDFab Platinum 3.0.8.0 which seems to install using Wine, but then I get an error message that "burning engine failed to initialize" I seems to rip DVD's OK, but it won't burn them?
Anyone have any ideas on how I could possibly fix this (DVDFab is setup to run in a Wine-WinXP environment)

I wonder if it needs the Nero back end to be installed?  That is what the other two use to do the actual burning.

---

### Post by kevdog on 2007-06-25
Good that DVD Decryptor and Shrink run under wine.  The bad news is that anyDVD does not.  Despite what I read and tried so far, the best tools for the job are still windows based.  Its a bummer!

---

### Post by Sunflower1970 on 2007-07-01
Got DVDFab HD Decrypter (the newest version) working well with Feisty and Wine 0.9.39, I found that as long as a real DVD is in the player before the program is started, it'll recognize the drive and make a perfect copy. I then burned it with K3b. 

I didn't have to do anything special at all. I already had Wine installed, so I just downloaded DVDFab, then double clicked to install the .exe under wine. It installed, I started the program and that's all I had to do for it to start to rip the DVD...When I checked my winecfg, it's set to Windows 2000....and everything works great....

:)

---

### Post by yabbadabbadont on 2007-07-01
> **kevdog said:**
> Good that DVD Decryptor and Shrink run under wine.  The bad news is that anyDVD does not.  Despite what I read and tried so far, the best tools for the job are still windows based.  Its a bummer!
You can always run windows inside of vmware or virtualbox and do this.  You just have to be sure to make your virtual drive large enough.

> **Sunflower1970 said:**
> Got DVDFab HD Decrypter (the newest version) working well with Feisty and Wine 0.9.39, I found that as long as a real DVD is in the player before the program is started, it'll recognize the drive and make a perfect copy. I then burned it with K3b. 

I didn't have to do anything special at all. I already had Wine installed, so I just downloaded DVDFab, then double clicked to install the .exe under wine. It installed, I started the program and that's all I had to do for it to start to rip the DVD...When I checked my winecfg, it's set to Windows 2000....and everything works great....

:)

Thank you for the information, that is good to know.

---

### Post by kens8 on 2007-07-17
> **Parasitesss said:**
> I want the best dvd-ripper application for ubuntu that has an **option** to copy not only the movie itself but the "main menu", "behind the scenes", "extra footage" and all that jazz. **Literally** making an **exact** **replica** of the dvd. 

Thanks in advance to anyone :]

If that's what you want, honestly the best option is to drop to the command line:

dd if=/dev/dvd of=dvd.iso

That'll create an .iso in fairly short order and it'll run exactly as your dvd would in most media players.  Just rename "dvd.iso" with whatever you want (ex. "Clerks.iso").

---

### Post by yabbadabbadont on 2007-07-17
> **kens8 said:**
> If that's what you want, honestly the best option is to drop to the command line:

dd if=/dev/dvd of=dvd.iso

That'll create an .iso in fairly short order and it'll run exactly as your dvd would in most media players.  Just rename "dvd.iso" with whatever you want (ex. "Clerks.iso").

Doesn't work for movie DVDs that use the new Sony copy protection scheme.  DVDFabdecrypter is the only thing that I have found that will backup such discs.

---

### Post by C.S.Cameron on 2007-07-17
I haven't found anything better than DVDDecrypeter followed by DVDShrink in Windows or Umbuntu
Cork

---

### Post by loyeyoung on 2007-07-28
Antoz

"I have used shrink in windows, tried K3b in Ubuntu could not get it to work, any sugestions from someone who is using it?"

You must install libdvdcss2 from the medibuntu repository. ([http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/))

---

### Post by yogo on 2007-07-28
> **handy said:**
> I could not get ***[DvdFab Decrypter]("http://www.dvdfab.com/free.htm")*** to install with Wine, has anyone else got it to work?


Handy, 

I noticed you got DVD Shink going in Wine.  Can you give me a basic step by step for dummies on how to do this. Once I get one app to work, then I will be able to get more things up and running I just do not understand what to do to get Wine going.

I have read the FAQ's etc but I am not sure what to do....Ubuntu newbie


TIA


Well I found one way to get apps to run in Ubuntu, I am not sure this is the right way. When I open up my winecfg, I have no programs showing up so I locate my program files folder and navigate to what program I want to run and I choose to open with Wine, it works but probably is not the right way. Why don't my programs show up in Wine, the program files folder is there but empty as for my programs...?

---

### Post by clint1010 on 2007-08-14
we don't need native windoze apps ;)

While reading through this thread I installed k9copy and made an *.iso image of a new DVD I purchased, and successfully completed. As I type this k3b has just finished writing the *.iso to a blank DVD, now I'm off to test it ..... ..... ..... sweet, the backup DVD works a treat :)



nothing goes better with movies than :popcorn:

---

### Post by Blutack on 2007-08-14
I'm a fan of acid::rip personally.

---

### Post by jocheem67 on 2007-11-23
The latest DVDFab combining with wine works very well at the moment, whereas in the past it would give some bad results.
The advantage is that DVDFab beats the latest protectionschemes...

For DVDFab, just make sure you've got a mfc42.dll in your wine system32 folder. As stated earlier. When put to yor harddrive you can just use DVDShrink to create an iso.

Really this is the most reliable method at the moment, linux native apps. just don't do well on the latest protections...

---

### Post by asmiller-ke6seh on 2007-11-23
I think that K9Copy is terrific. Works great for me, including transcoding down from DVD9 to DVD5. It even has an MPG4 out option.

---

### Post by Bakhman on 2007-12-13
Can someone tell me how to install K9copy? I DLed it, but when I copy/paste the .gz file to "/usr/local/bin" (so that I can use the "make install" command) it doesn't let me paste there. I don't know what other method to use..

---

### Post by yabbadabbadont on 2007-12-13
> **Bakhman said:**
> Can someone tell me how to install K9copy? I DLed it, but when I copy/paste the .gz file to "/usr/local/bin" (so that I can use the "make install" command) it doesn't let me paste there. I don't know what other method to use..

System->Administration->Synaptic Package Manager.

Then Settings->Repositories.  Make sure that the line with (multiverse) at the end is checked.  Close the dialog and hit the Reload button.  Now search for k9copy and select it for installation.

:D

---

### Post by fenian on 2007-12-13
To install k9copy open a terminal and enter...

> sudo apt-get install k9copy

---

### Post by yabbadabbadont on 2007-12-13
> **fenian said:**
> To install k9copy open a terminal and enter...

But only if you have already enabled the multiverse repository first....

---

### Post by fenian on 2007-12-13
These are the steps for installing a newer version of k9copy.

1-First remove old version with the command...

  >   sudo apt-get remove k9copy

2-Then install the dependencies with these commands...

    > sudo aptitude install dvdauthor libdvdread3 mencoder mplayer libhal1 libdbus0 libdbus-qt-1-1

and...

>     sudo aptitude install libdvdread3-dev libqt3-headers libqt3-mt-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall libhal-dev libdbus-qt-1-dev libhal-storage-dev

3-Download the source file from (download the file to the desktop)...

    [http://downloads.sourceforge.net/k9copy/k9copy-1.1.1-3.tar.gz](http://downloads.sourceforge.net/k9copy/k9copy-1.1.1-3.tar.gz)

4-Extract the source file to the Desktop (right click & choose extract here)

5-Navigate to the k9copy-1.1.1-3 folder...

  >   cd ~/Desktop/k9copy-1.1.1-3

6-Configure and build the source with the commands...

   >  ./configure

then...

   >  make

then...

   >  sudo checkinstall --install=no

(this creates a DEB file which is cleaner then just running sudo install)

7-Install the DEB file with the command...

   >  sudo dpkg -i  k9copy-1.1.1_3-1_i386.deb

8-Because the program gets installed in the directory usr/local/kde/bin/k9copy you want to symlink (symbolic link) that to /usr/bin/ k9copy.Do that with this ommand...

    > sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy

9-Create a menu shortcut so k9copy appear under the applications>sound & video menu.First open the text editor...

   >  gksudo gedit /usr/share/applications/k9copy.desktop

an epty document will open copy and paste the following text...
> 
[Desktop Entry]
Name=k9copy
Comment=DVD ripper
Exec=k9copy
Icon=/usr/local/kde/share/icons/hicolor/48x48/apps/k9copy.png
Type=Application
Categories=Application;AudioVideo;

save and exit.

You should now have the latest version of k9copy.

---

### Post by ctyc on 2007-12-13
Handbrake is the best:  [http://handbrake.m0k.org/](http://handbrake.m0k.org/)

CLI usage example:

HandBrakeCLI -f avi -e ffmpeg -E lame -S 1400 -i /dev/cdrom -t 1 -o movie.avi

---

