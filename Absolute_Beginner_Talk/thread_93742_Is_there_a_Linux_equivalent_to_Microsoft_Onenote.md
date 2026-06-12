---
title: "Is there a Linux equivalent to Microsoft Onenote?"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by DevilsRejection on 2005-11-22
I do not use the tablet functionality since well... I do not have a tablet lol. But I do enjoy the many features that one note brings me as an application for taking down notes in class, jotting random thoughts, and a clipboard on steroids.

So is there anything remotely similar to OneNote for Linux?

BTW: This is my first time messing around with Linux so expect to see a lot of me in this forum :) I'm still downloading the Ubuntu 5.10 DVD, going to throw it on my IBM Thinkpad X40 tonight.

---

### Post by suRoot on 2005-11-22
I don't think you'll find anything quite linke onenote, however you may want to try tomboy.  I've found it to be an acceptable replacement on my desktop.

```
sudo apt-get install tomboy
```

---

### Post by DevilsRejection on 2005-11-22
[QUOTE=suRoot]I don't think you'll find anything quite linke onenote, however you may want to try tomboy.  I've found it to be an acceptable replacement on my desktop.

```
sudo apt-get install tomboy
```[/QUOTE]

I see that all the time, the sudo apt-get install XXX

Where do I type that in? Where does the program install to? Will there be a shortcut created for me somewhere? How do I launch the application from there?

I googled TomBoy, and it definitly doesn't look like it would satisfy my needs.

---

### Post by suRoot on 2005-11-22
You run apt-get from a console.  Main Menu -> Accessories -> Terminal

sudo = gives you administrative (root) rights which you need to install software

apt-get = the debian package management system

install = duh!

XXXX = package name

Installation varies by program, but generally things get thrown in to /usr/bin/ (or /bin or /usr/local/bin).

Menu entries, again, vary by program.  If you look through the sub-menus under the main menu you should be able to find it.  If all else fails, you can run programs from the terminal by entering their name, eg. tomboy.

---

### Post by darknuala on 2005-11-22
tomboy is definitely not One Note.

Here's a couple of ideas

[www.wordpress.org](www.wordpress.org)
[http://hnb.sourceforge.net/](http://hnb.sourceforge.net/)
[http://knowit.sourceforge.net/](http://knowit.sourceforge.net/)

But nothing compares to One Note in that area

---

### Post by matthewstory on 2005-11-22
Ubuntu provides a GUI (Graphical User Interface) for the Debian apt-get protocal, called synaptic, if you're not familiar with Command Line Interface (CLI) it might be easier to use the Synaptic GUI to get a handle on how apt-get works before jumping into CLI apt-get.

you can find synaptic here:
SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER

Once you've opened synaptic you can access the synaptic users guide through 
HELP > CONTENTS
and there are also plenty of other how-to and documents in the wiki and on various other parts of the ubuntu website.  And for more information on apt-get CLI and apt-get in general visit the debian site on it at: [http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

I would eventually get used to CLI, so many of the best programs for linux don't come with a GUI, and if a particular program you need doesn't come wrapped in a debian package, then the command line is the only way to compile the source and build the program.  CLI is our friend.

cheers,
matt

---

### Post by DevilsRejection on 2005-11-22
Let me get my feet wet first before I start downloading and compiling source. After all, I am getting Ubuntu because it is supposed to be a friendly distro.

---

### Post by 23meg on 2005-11-22
The closest app to Onenote for tablets that I've found is Gournal.

---

### Post by DevilsRejection on 2005-11-22
Well can you use a keyboard with it tho?

EDIT: Just went to the website. And I quote: "It's designed for usage with a stylus, not a mouse or keyboard."

---

### Post by 23meg on 2005-11-23
You can still enter text into it but it's really designed with tablet use in mind. Other things you should check out: NoteMeister, Gnome Vazaar, BasKet, Newton Desktop Wiki.

---

### Post by Bharath on 2006-09-04
Hi,

Check out [http://memoranda.sourceforge.net/](http://memoranda.sourceforge.net/) for Onenote replacement. Memoranda has more than 50% of the functionalities of OneNote.

Bharath

---

### Post by Karl S. on 2006-09-05
> **Bharath said:**
> Hi,

Check out [http://memoranda.sourceforge.net/](http://memoranda.sourceforge.net/) for Onenote replacement. Memoranda has more than 50% of the functionalities of OneNote.

Bharath

I've checked it out, but I'm not sure what to do now. Downloading and installing Memoranda is not exactly idiot-proof, as it's not available on the Synaptic Package Manager.

I'd love to try it, though, as I just tried, and rejected, Basket. My OneNote needs are immense and peculiar (I have 4 years' worth of dissertation notes on it + all the materials for the classes I've taught, and I expect I'll keep adding information), so I'm not sure Memoranda is going to do the trick. I'd love to try something, though, since the lack of OneNote is just about the only thing keeping me from switching to Ubuntu entirely.

So what do I do when I get to Memoranda download page?

---

### Post by Karl S. on 2006-09-07
> **Karl S. said:**
> So what do I do when I get to Memoranda download page?

Well, since there's been no answer forthcoming, I tried doing something. Didn't work, in part because there's been indication of which file I should download.

Here's my output:

> karl@karl:~/Desktop/memoranda1.0a-20031204$ sh memoranda.sh
: command not found2:
memoranda.sh: line 3: /home/karl/Desktop/memoranda1.0a-20031204/lib/kde/systray4jd: Permission denied
memoranda.sh: line 3: exec: /home/karl/Desktop/memoranda1.0a-20031204/lib/kde/systray4jd: cannot execute: Success
: command not found3:
System tray icon is disabled
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.JFrame.<init>(libgcj.so.7)
   at net.sf.memoranda.ui.App.showSplash(Unknown Source)
   at net.sf.memoranda.ui.App.<init>(Unknown Source)
   at net.sf.memoranda.Start.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...7 more
karl@karl:~/Desktop/memoranda1.0a-20031204$

---

### Post by StickyStyle on 2006-09-08
It looks like you need to install the sun java JRE first as memoranda is a java app.
Follow this guide to install it...
[B][https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)

[/B]You can probably skip the demo, jdk, and source packages mentioned in step 15, unless your a java coder.

---

### Post by Karl S. on 2006-09-08
Thanks for the help. I have Java installed now, but Memoranda still didn't install.

I think I'm going to give up on it, though, as it doesn't look as though it's going to serve my needs, anyhow. Just have to hope that Evernote does a Linux version. And, haha, that I can get my wireless working, which just isn't happening.... back to Windows until Edgy comes out.

---

### Post by Bharath on 2006-09-24
Check out memoranda.sourceforge.net memoranda has 50% of OneNote functionalities

/Bharath

---

### Post by jjhart on 2006-11-13
Bharath,
I see on a few posts that you recommend memoranda. Is there a deb package for it, or does someone have to build it? I'm new and don't really comprehend building packages or installing from source, I just need a deb package if possible.

---

### Post by blendmaster on 2006-11-13
Have you tried running onenote under wine? I assume that it isn't too graphics intensive, so it may work.

```
sudo apt-get install wine
```

Then bring out the executable file for Onenote, and use:

```
sudo wine <file>
```

While under that directory.

Hope that helps!

---

### Post by ryu kun on 2006-11-18
AFAIK there isn't any deb package for Memoranda. But it isn't hard to install. Click [here]("http://www.ubuntuforums.org/showthread.php?t=269425") to see how.

---

### Post by alexeya on 2006-11-28
> **Karl S. said:**
> Well, since there's been no answer forthcoming, I tried doing something. Didn't work, in part because there's been indication of which file I should download.

Here's my output:

Memoranda will not work with GNU Classpath JRE due to its limitations (incomplete implementation of the Swing libraries). You need the "original" Sun's JRE from java.sun.com (1.4.x and 1.5.x has been tested).

In Gnome, it's recommended to comment a line in memoranda.sh which starts systray4jd - it's a KDE stuff.

---

### Post by alexeya on 2006-11-28
> **jjhart said:**
> Bharath,
I see on a few posts that you recommend memoranda. Is there a deb package for it, or does someone have to build it? I'm new and don't really comprehend building packages or installing from source, I just need a deb package if possible.

You do not need to build the sources, as the latest releases include the prebuilt version. Just unzip the distribution and run 'memoranda.sh'.

I have no idea who is going to build the deb package and put it into repository but I'd be glad if it's happened.

---

### Post by bailout on 2006-11-28
Have you tried Basket? [http://basket.kde.org/](http://basket.kde.org/)

I only discovered it myself a short while ago and haven't really played with it much but it sounds good. Version 0.5 is in the edgy repos but v0.6 is on the site for download.

---

### Post by Karl S. on 2006-12-03
Still in Windows...I just transferred all my notes from OneNote to [Keynote]("http://www.tranglos.com/free/keynote.html"). For my purposes--keeping all the notes for my dissertation--it seems much superior to OneNote. It's a smaller app, takes up a lot less memory, and is much, much more flexible. Unfortunately, there's no Linux version, and I haven't tried running it under Wine: but someone might want to give it a shot.

---

### Post by magicmike on 2007-04-17
Karl S.  I just installed Keynote with Wine and seems to work fine.

---

### Post by chakkaradeep on 2007-04-17
Tried Memoranda, the GUI is not as good as I expect and I hate Java :( 

Trying basket now :guitar:

---

### Post by cstrippie on 2007-04-17
I'm also a Onenote fanatic, but I just run a small windows install in an emulater (VMware Server, but there are several others).  I use Tomboy notes for "quick & dirty" notes that, if important, I later copy to onenote.  VMware server can be set up to boot the VM at startup (of Ubuntu), so it's always available.

---

### Post by mjukr on 2007-04-29
OneNote is my one "killer app" that I use extensively. I'm playing around with BasKet, which is nice, but not nearly as nice as OneNote (doesn't preserve formatting when dragging/pasting "objects," etc.). 

And there don't seem to be any comparable Gnome versions at the moment.

I think many people mistakenly assume that these are mainly for tablet users, which isn't true! I don't even own a tablet :P

---

### Post by pyros on 2007-05-09
> **mjukr said:**
> OneNote is my one "killer app" that I use extensively....
I think many people mistakenly assume that these are mainly for tablet users, which isn't true! I don't even own a tablet :P

I second that. I have found at least three note-taking programs that work with a stylus, but nothing for keyboard input. What I ended up using suites my purposes quite well, but obviously isn't for everyone. I have been using google notebook with quite a bit of success.  it has an added bonus of exporting to google docs as well, so you can save a notebook in any of the formats supported by docs/writely

if you already have a google account (through gmail, a customized home page, etc) you can go right to [http://www.google.com/notebook/](http://www.google.com/notebook/) and sign in. It has a handy firefox plugin as well which can be found here: [http://www.google.com/notebook/download](http://www.google.com/notebook/download)

Like I said, not a solution for everyone, but it's working for me.

---

### Post by venik212 on 2007-05-20
Can you run OneNote under Wine?

---

### Post by mjukr on 2007-05-20
I haven't tried that... maybe I'll take a look. Generally I avoid running MS apps under Linux. I have to use Windows enough at work! If I *must* use a windows app, I will generally RDP into my Windows box.

But I supposed Wine is an option if no alternatives pan out.

---

### Post by zorkerz on 2007-09-02
so i installed basket and now my theme looks like kde instead of gnome. if i go to system -> prefrences -> appearance it says that
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

so what can I do or what can i uninstall to get ride of this.
elias

---

### Post by helliewm on 2007-09-02
Go to [www.getdeb.net](www.getdeb.net) and try JARNAL. It is very similar to OneNote. Its a deb file so all you do is download and click on it (literally) to install it.:)

Helen

---

### Post by zorkerz on 2007-09-02
Hmm did not do anything but on this last restart my normal gnome icons returned. 

I am currently using BasKet which is pretty nice. I would like to try memoranda but have not found a deb for it. Seems like other people are having the same problem if anyone knows where one can be found it would be much appreciated.
elias

---

### Post by helliewm on 2007-09-02
You need java installed. Go to the Menu top left side/CORNER  of your PC Applications, Accessories, Jarnal should be in the Accessories Menu.

The Jarnal DEb will tell you if you need to install Java. Watch the DEB closely as Jarnal installs if its not in your Acessories Menu .

Helen

---

### Post by zorkerz on 2007-09-04
So i gave basket a chance and thought i was going to use it. Then in class today I realized there is no built in spell checker in basket. im using tomboy now. Im actually pretty happy with tomboy. 

What I don't know is how to get ride of all the kde packages that installed in order to allow the basket to work. I don't have a list of what was installed with it and they did not get ununstalled. I don't have any other kde apps i think so i should not need them at all.

any ideas?

---

### Post by _Stevie_ on 2008-01-09
im reluctant installing basket, since its a KDE app, but i gotta say, its very tempting.
i wish there was a gnome-only version.

---

### Post by ByteJuggler on 2008-01-09
> **_Stevie_ said:**
> im reluctant installing basket, since its a KDE app, but i gotta say, its very tempting.
i wish there was a gnome-only version.

KDE apps mostly work seamlessly on Gnome desktops and vice versa, I wouldn't worry about it.

---

### Post by _Stevie_ on 2008-01-09
im actually only worried about KDE taking over my gnome desktop :)
i read something like this in a post in this thread.

---

### Post by ByteJuggler on 2008-01-09
> **_Stevie_ said:**
> im actually only worried about KDE taking over my gnome desktop :)
i read something like this in a post in this thread.

Nah.  You can have both desktops installed at the same time.  (In fact you can have several other installed as well.)  You then select which you want at logon by clicking on that "Session" selector thing (or whatever it's called.)  I have both KDE and Gnome installed, usually I use Gnome but sometimes I log into KDE.  They co-exist peacefully.

---

### Post by _Stevie_ on 2008-01-09
ah wonderful, that doesnt sound as nasty as i first thought :D
just one question, its a bit off-topic, but also refering to "trying stuff".
i noticed that, when uninstalling external debs, the package dependencies arent
removed anymore. i suspect this is due to the fact that it is an external package.
is there a way to *safely* remove packages (as BasKet) without having all the 
unused clutter on the hd?

i already installed many packages and when uninstalling, i noticed that most of the dependent
libs arent uninstalled.
also synaptic doesnt "log" those package-events, means i cant have a look at the history and
just remove the packages manually. also  GTKorphan doesnt find any leftover packages,
although there are some! is there a solution for that?

---

### Post by dansen926 on 2008-05-01
I have found Basket to be a simply wonderful alternative to OneNote

[http://basket.kde.org/](http://basket.kde.org/)

---

### Post by _Stevie_ on 2008-05-01
yep, i can fully acknowledge that. basket is very cool.
too bad there isnt a gnome-like alternative.

---

### Post by funkydan2 on 2008-05-06
I'm using Zim - [http://zim-wiki.org/](http://zim-wiki.org/).  A fairly up-to-date version is in the universe repository, so you can install it through synaptic.

I don't think it's quite as powerful as Basket, but it's doing the trick for me.  (It would be really nice if it was able to preserve the formatting that I copy in from OpenOffice, but with the stuff I'm using it's not to hard to work with.)

---

### Post by Aearenda on 2008-05-06
I use xournal - it's in the universe repository.

---

### Post by jcanino20 on 2008-07-10
> **DevilsRejection said:**
> I do not use the tablet functionality since well... I do not have a tablet lol. But I do enjoy the many features that one note brings me as an application for taking down notes in class, jotting random thoughts, and a clipboard on steroids.

So is there anything remotely similar to OneNote for Linux?

BTW: This is my first time messing around with Linux so expect to see a lot of me in this forum :) I'm still downloading the Ubuntu 5.10 DVD, going to throw it on my IBM Thinkpad X40 tonight.
Another option to consider in Zoho Notebook, on [www.zoho.com](www.zoho.com). This is basically free Office Suite software that only exists online. I use other zoho tools, and am seriously considering Notebook because I want to be able to use it at work and at home (read as on Windows *and *Linux). 

To my knowledge, this kind of setup is the only one that would accomodate access on either linux, windows or a mac. I should confess I have *not * tried some of the other alternatives yet. Although, a quick look at Basket seems to suggest that I cannot sync between Windows and Linux.

Given the choice, I'd be in a linux only environment. Unfortunately, the world hasn't caught up with that enlightened way of thinking yet! ;-)

Hope this info is useful.

---

### Post by supersako on 2008-07-18
Unfortunately, there is nothing on Linux or even Mac that will compete with OneNote. I know this is an old post, but I was in the same predicament and needed OneNote for taking notes in class. I decided to get VMWare, this way I can use Adobe CS3 and Visual Studio 2008(I know it sucks! I need it for school :(  ) as well.. Just an idea, you can always go the virtualization route, and I can attest that OneNote works beautifully in VMWare with a Windows XP guest.

---

