---
title: "Xbox Live Notifications"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by TheSe7enthSin on 2007-08-07
**Archive notice:** This thread will no longer be updated; the archive is closed. Stay tuned for updates on [https://launchpad.net/xblstatus](https://launchpad.net/xblstatus) *--jacobmp92*

I'm not sure where I should have created this thread. Please move to the appropriate board if necessary.

I wanted to know if there is a program for Ubuntu that lets me view my friends on Xbox Live & see their status, get notifications, etc.. I have seen such programs for Windows & Mac. If anyone knows if a program exists or is being worked on, please pass the info.

Here are a couple of examples of what I'm searching for.

Program for the Mac (One like this I would like on Ubuntu):
[http://99lives.org/2007/02/11/xbox-live-mac-maclive/](http://99lives.org/2007/02/11/xbox-live-mac-maclive/)

Program on Windows:
[http://brh.numbera.com/software/xblist/](http://brh.numbera.com/software/xblist/)

[U][B]Update:
[/B][/U]twisted_steel has taken over this project & has written up a program. Click [here]("http://ubuntuforums.org/showthread.php?t=520113#51") for the latest post containing his instructions & release.

---

### Post by TheSe7enthSin on 2007-08-07
I kept looking through and saw that Maclive has the source code at their Google Code page. Would this allow someone to port this to Linux/Ubuntu?

[http://code.google.com/p/maclive/source](http://code.google.com/p/maclive/source)

---

### Post by twisted_steel on 2007-08-07
I was trying to figure that out as well.  I think the main code could be reused and it's just a question of changing the notification code; as far as I know Growl is Mac-only.  I haven't done any Mac programming myself, so I'm not sure what is involved.

However, I would definitely be interested in a Xbox Live notification system for Linux.

---

### Post by TheSe7enthSin on 2007-08-07
Yea, I saw that Growl is Mac only.
I have been using a program, Mumbles, that gives me notifications for Rhythmbox & Pidgin ( [http://www.mumbles-project.org/](http://www.mumbles-project.org/) ). Could the source of the MacLive program be reused using the kind of method that enables Mumbles to give you these Growl-like notifications?

---

### Post by Frak on 2007-08-07
Absolutely it could, thats the beauty of Open Source, the only thing now is to find someone who is willing to not only convert the code, but also to merge interfaces.
I would try to find a developer who is an XboX-Live fanatic, and mention this to him/her. Necessity is the mother of invention :)

---

### Post by twisted_steel on 2007-08-07
I wonder if the maclive developer has an interest in this?  It might be worth changing the code in general to abstract things like drawing notifications (Growl vs. Linux app) and drawing windows (Mac toolkit vs. Gtk/Qt/etc).  Otherwise, I think the Linux rewrite is definitely doable.

Edit: I finally realized why the code looked a little off to me.  It's written in Objective-C versus C or C++.

---

### Post by Kralizec on 2007-08-07
I found this, [Specto]("http://specto.sourceforge.net/"), after running a google search for 'xbox live notifications linux'. I don't have an xbox live account to test it though, sorry.

P.S. I've realized the other day how much of a hypocrite I (we) are for hating windows and yet loving to play the 360...because oh boy do I love the 360. Any one else notice this?

---

### Post by TheSe7enthSin on 2007-08-07
> **Frak said:**
> Absolutely it could, thats the beauty of Open Source, the only thing now is to find someone who is willing to not only convert the code, but also to merge interfaces.
I would try to find a developer who is an XboX-Live fanatic, and mention this to him/her. Necessity is the mother of invention :)

=)
I hope someone wouldn't mind taking the task of getting this up and running for Ubuntu.

---

### Post by Frak on 2007-08-07
I don't hate Windows, and the 360 is actually built more like a Mac than a Windows box.

---

### Post by TheSe7enthSin on 2007-08-09
Oh yea? I don't have any programming skills, so I wouldn't know if the 360 is more like a Mac than a Windows Box. You sure it isn't just the color? =P

But yea, just bumping this up so others who are up for making this possible can see...

---

### Post by Frak on 2007-08-09
The Xbox 360 has a Custom IBM PowerPC with 3 symmetrical cores running at 3.2 GHz each.
Custom ATi Card running at 500MHz & 10MB of embedded DRAM
Memory, 512MB GDDR3, 700MHz, Unified memory architecture
Memory Bandwidth
22.4 GB/s memory interface bus bandwidth
256 GB/s memory bandwidth to EDRAM
21.6 GB/s front-side bus
Disks
Detachable and upgradeable 20 GB hard drive
12X dual-layer DVD-ROM
Memory unit support starting at 64 MB
Support for up to 4 wireless game controllers
3 USB 2.0 ports
2 memory unit slots
Built in Ethernet Port
Wi-Fi Ready: 802.11 A, B and G
Video Camera Ready


    * Support for DVD-Video, DVD-ROM, DVD-R/RW, DVD+R/RW, CD-DA, CD-ROM, CD-R, CD-RW, WMA CD, MP3 CD, JPEG Photo CD
Stream media from portable music devices, digital cameras, Windows XP PCs
Rip music to Xbox 360 hard drive
Custom playlists in every game
Windows Media Center Extender built in
Interactive, full screen 3D visualizers
Stands vertically or horizontally
Face Plates are Interchangeable to personalize the console

Just to name a few points ;)

---

### Post by TheSe7enthSin on 2007-08-25
There has to be someone here who would be interested in making this available for linux...
=[

---

### Post by Crafty Kisses on 2007-08-25
> **TheSe7enthSin said:**
> I'm not sure where I should have created this thread. Please move to the appropriate board if necessary.

I wanted to know if there is a program for Ubuntu that lets me view my friends on Xbox Live & see their status, get notifications, etc.. I have seen such programs for Windows & Mac. If anyone knows if a program exists or is being worked on, please pass the info.

Here are a couple of examples of what I'm searching for.

Program for the Mac (One like this I would like on Ubuntu):
[http://99lives.org/2007/02/11/xbox-live-mac-maclive/](http://99lives.org/2007/02/11/xbox-live-mac-maclive/)

Program on Windows:
[http://brh.numbera.com/software/xblist/](http://brh.numbera.com/software/xblist/)

Someone will do it, guaranteed.

---

### Post by twisted_steel on 2007-08-27
I've been looking into it off and on, and it doesn't look like it would be that bad, especially with python.  I just haven't had time to sit down and figure out the HTML scraping part of it.

The notification part is easy with pynotify.  I imagine it would be easy enough to support the mumbles program that was posted earlier.  The bulk of the work would be in authenticating with the web site and grabbing the necessary information out.

Here is a link to a HTML parser for python:
[http://www.crummy.com/software/BeautifulSoup/documentation.html](http://www.crummy.com/software/BeautifulSoup/documentation.html)

Maybe we can get something started over in the Programming section of this site?

---

### Post by Joeb454 on 2007-08-30
Well given that a LOT of people have 360's...you'd think that a fair few programmers that use Ubuntu / Linux in general would like to see this on their linux boxes

---

### Post by jms830 on 2007-09-08
Can't you link your xbox gamertag to an msn account or something, and then somehow see your friends through gaim/pidgin?

---

### Post by TheSe7enthSin on 2007-09-08
My Gamertag is linked, but Gaim/Pidgin does not support Xbox Live. Just MSN contacts.

---

### Post by NickD-NLUG on 2007-12-18
So.... anyone get anywhere with this?  I'd be interested in updates too, without having to leave Firefox logged in and screen scraping.

Meanwhile do note with the introduction of MSN to the Xbox you might be able to get somewhere using an MSN client....

---

### Post by twisted_steel on 2007-12-18
No, I unfortunately moved on to other things, but the method I started on was more or less screen scraping.  I'm still refreshing Firefox as necessary in the meanwhile.  Is this what you're talking about with the MSN Messenger integration?

[http://www.flickr.com/photos/majornelson/191961417/](http://www.flickr.com/photos/majornelson/191961417/)

I haven't linked my MSN and Xbox Live accounts together yet because I am using different Passport accounts.

---

### Post by NickD-NLUG on 2007-12-19
With the MSN, yes, that's what I'm talking about.  We'll see if I can make something useful out of that facility with the various and nasty linux and console based ways I use to access IM.

Alternatively there might be some value in working with the xbox_live.py code that's part of this:

[http://damonkohler.blogspot.com/2007/10/pertelian-pypert-and-xbox-live.html](http://damonkohler.blogspot.com/2007/10/pertelian-pypert-and-xbox-live.html)

I tried last night, but I have no python experience at all.  I expect that this code and five minutes of a python programmer's time would be enough to get it to print the output to stdout.

Thanks for the reply.

---

### Post by twisted_steel on 2007-12-19
Wow, this is a lot cleaner than what I was trying to do to log in to live.xbox.com.  I already have some code that I was running on a saved version of the friends page to grab their gamertag, gamerpicture, their online/offline status, and the description of the game they are playing.  I'll take a look tonight when I actually have friends on, but this is what the sample output was of my code before (note the date):

Gamertag:  Friend
Gamerpicture:  [http://tiles.xbox.com/tiles/TK/5Q/0Gdsb2JgbC9ECFZXV0oAGAFdL3RpbGUvMC8xMTAyMAAAAQAAAAD-f65s.jpg](http://tiles.xbox.com/tiles/TK/5Q/0Gdsb2JgbC9ECFZXV0oAGAFdL3RpbGUvMC8xMTAyMAAAAQAAAAD-f65s.jpg)
Status:  Offline
Description:  Last seen 07/29/07 playing Xbox 360 Dashboard

Yes, I changed the gamertag :)

---

### Post by NickD-NLUG on 2007-12-19
Cool.  Please get in touch if you want someone to test the code for you at all.

---

### Post by twisted_steel on 2007-12-20
Did you have any success running any of the sample code the other night?  I tried stripping down part of it, but kept getting an error about maximum recursion depth.

This is my post in the Programming Talk forum: [http://ubuntuforums.org/showthread.php?t=645283](http://ubuntuforums.org/showthread.php?t=645283)

I also sent an email to the author.  It might be a problem with the version of mechanize I have on my laptop because it looks like it did work from the photos on the blog.

---

### Post by NickD-NLUG on 2007-12-20
I had the same problem with maximum recursion depth.

If you added some debugging lines to the code I'd be interested to see what you did.  As stated, my python knowledge is *very* limited.

---

### Post by twisted_steel on 2007-12-20
I actually haven't really done that much Python programming in a few years, so I'm trying to get myself back on track.  When I was debugging the sample code, I added in print statements before several lines and ran it to see how far it was getting before bombing out.

I haven't heard anything on why the simplified version isn't working at all, so I went ahead and just wrote the authentication part from scratch using a combination of urllib2 and ClientForm, with cookielib to store the cookies and to make the login process faster.  The code is really rough at this point and needs a decent amount of error checking added in, but I'm really happy to have gotten this far.  Looking at the login page source, you might think you could just provide the form with the username and password, but there is unfortunately more going on behind the scenes.  Once the login form is submitted in a browser, JavaScript code is executed which actually ends up manipulating some of the variables before they are sent off to the server.  One of them, strangely enough, has a value of "IfYouAreReadingThisYouHaveTooMuchFreeTime" and its length gets modified based on the length of your password.

I'm going on vacation next week with good old dial-up, so I'll see what I can get done in my spare time.  If I have something decent, and more importantly, legible, I'll send it your way to get some feedback and also so you can get an idea of what is going on.

---

### Post by NickD-NLUG on 2008-01-15
Let me know how you're getting on with this, we'll see if we can get anywhere.  I wondered if I could use another program to snaffle the page, something like wget, using the cookies created when you'd logged in already.

However, like you say, some cookie variables are written on the fly and so you need to emulate whatever the javascript is doing to get the page each time.

---

### Post by twisted_steel on 2008-01-15
I can send you what I have now if you like.  I currently have two python classes for the backend - one for the connection itself and one for friend objects.  There is an example console program at the moment that prints out the current friends online and will refresh again in 30 seconds.  I would like to make a front end using pygtk and have something started with a treeview.  The one thing I haven't done is combine the two.

The backend supports the following at this point:[LIST]
[*]Connect to the Xbox Live site using cookies (a few redirects involved)
[*]Grab the friends list, including name, online/offline/away status, picture, and current game played
[*]Cache the friends' pictures locally on disk (this is good for loading it into a frontend)[/LIST]I would to eventually add in more error checking and the ability to see your messages and send messages to friends.  I will toss it up on my site at some point, but I would like to get more of it finalized.

---

### Post by Strawp on 2008-02-16
> **twisted_steel said:**
> I can send you what I have now if you like.  I currently have two python classes for the backend - one for the connection itself and one for friend objects.  There is an example console program at the moment that prints out the current friends online and will refresh again in 30 seconds.  I would like to make a front end using pygtk and have something started with a treeview.  The one thing I haven't done is combine the two.

The backend supports the following at this point:[LIST]
[*]Connect to the Xbox Live site using cookies (a few redirects involved)
[*]Grab the friends list, including name, online/offline/away status, picture, and current game played
[*]Cache the friends' pictures locally on disk (this is good for loading it into a frontend)[/LIST]I would to eventually add in more error checking and the ability to see your messages and send messages to friends.  I will toss it up on my site at some point, but I would like to get more of it finalized.

Could you post a copy of this online somewhere? I'd be interested in trying it out.

---

### Post by Gouki on 2008-02-17
Could you paste the code somewhere? Or even attach it. 

I would be interest in continuing your work.

---

### Post by twisted_steel on 2008-02-18
Sorry about the delay.  I'll try to clean it up a bit and get something up within the next few days.

---

### Post by TheSe7enthSin on 2008-02-18
Awesome. I'm glad this is moving somewhere. =]

---

### Post by twisted_steel on 2008-02-23
While I was adding in some error checking and contemplating releasing a sample GUI that didn't really do much, I decided to make a GUI that worked reasonably well.  I still need to add in some threading because at the moment menu functions block the GUI from redrawing until they complete.  It definitely looks a lot better than it did when it was just a command line program.

I've attached a screenshot of the current state.  I have no idea on a name, so it's just LiveStatus for the moment.

---

### Post by TheSe7enthSin on 2008-02-24
Looks great so far. =]

---

### Post by Duffkiligan on 2008-02-24
off subject, but my friend has linux on his 360. I believe it's Feisty but I could be wrong.

---

### Post by Crafty Kisses on 2008-02-24
I'm actually excited about this, can't wait until this actually gets out there.

---

### Post by DocHoliday52090 on 2008-03-01
I too am awaiting this. Keep up with the good work, twisted_steel!

---

### Post by twisted_steel on 2008-03-09
I've finally reached a point where the program works well enough for an initial release.  I copied the following from several files that are included in the archive.  Be sure to read beforehand :).  I think I have all the prerequisites right, but let me know if I missed something.  Also, if you have any ideas about features you would like or problems that could be fixed, let me know.  Is the GUI too big, too small?  Would you like to have more information displayed?  The same is true if you want to help work on it.

_Download_:
Get version 0.1 (the initial release) -> [here]("http://www.hollec.com/projects/livestatus/") <-.
[U]
Prerequisites[/U]:
Install python-beautiful-soup, python-clientform, python-glade2, python-gtk2

Extract the archive into a folder of your choice.  Edit the livestatus.py script and fill in your correct username (e-mail address) and password.  The program saves your settings (a cookie and a cache of the gamer pictures) in ~/.livestatus/

Give the script executable permissions by running the following from the
terminal:
    chmod u+x ./livestatus.py
[U]
Usage[/U]:
Run the program from the terminal:
    cd /path/to/livestatus
    ./livestatus
    
You should also be able to double-click the livestatus.py file in the
file manager and select Run if prompted.

_Todo_:
Clean up debug print statements.  They are there right now to help troubleshoot if anyone runs into a problem.

Implement support for sending and receiving messages through the Xbox Live
site.

Add in notifications with libnotify or one of the other notification libraries over DBus.

Add in sorting for the tree.  Currently, a friend that is moved from one
status to another will be placed at the end of the list, rather than in
alphabetical order with the rest of the friends.

I experienced a random bug where a friend was moved from Online to Offline, but disappeared from the tree view.  It was, however, still in the dictionary of offline users.  Let me know if you see anything like this or have a fix for it.

Fix the following known issues:

    The File->Disconnect menu item has not been implemented.

    The Edit->Preferences menu item has not been implemented.

    Clicking the 'x' in the corner of the about box will prevent it from being
    opened again if selecting Help->About.

---

### Post by TheSe7enthSin on 2008-03-10
Great, its working well for me. =]
One thing I noticed, when you click the tab to show all offline friends, it extends the window vrtically past the desktop. A scrollbar isnt made.

But again, great job.

---

### Post by twisted_steel on 2008-03-10
I've been hoping I could get a scrollbar in there similar to Pidgin, but I haven't done anything yet.  My desktop display is 1680x1050, and it even looks large on there if I view my offline friends.  I have 12 total in my list, so my situation might not be as bad as yours.

Actually, it looks like a [gtk.ScrolledWindow]("http://www.pygtk.org/pygtk2reference/class-gtkscrolledwindow.html") might do the trick.  I'll have to look into it later.

---

### Post by twisted_steel on 2008-03-10
That was a little too easy :mrgreen:.  I opened up the .glade file with Glade (install glade-3), selected the treeview and hit Cut.  I dropped in a scrolledwindow, selected that, and then hit Paste.  All I had to do was save and re-run the program to get the scroll bars in.  I can send you the glade file if you like.

I was thinking that the friends list might look a lot cleaner if the categories were removed.  Instead of Online, Away, Busy, and Offline all having there own sections, there would just be one list.  There could be an option in Preferences (which still has to be made) that would allow you to toggle viewing Offline friends.  If they were shown, the gamer picture would be changed to a grayscale version.  Any friends that were Away or Busy could have the info section under the name updated to reflect that.

---

### Post by twisted_steel on 2008-03-10
This is a quick mockup of what I was talking about in my previous post.  I lost two friends during editing, but if they were still in the list, there would also be a scrollbar in the right.  It might also be useful to add in the offline time that is seen on the live page (e.g. Last seen 10 minutes ago playing The Orange Box).  That might be better for something to show in a tooltip or some sort of separate info area because some of the descriptions can get quite long, forcing you to either increase the window size or scroll over.

---

### Post by blasteryui on 2008-03-10
> **TheSe7enthSin said:**
> I'm not sure where I should have created this thread. Please move to the appropriate board if necessary.

I wanted to know if there is a program for Ubuntu that lets me view my friends on Xbox Live & see their status, get notifications, etc.. I have seen such programs for Windows & Mac. If anyone knows if a program exists or is being worked on, please pass the info.

Here are a couple of examples of what I'm searching for.

Program for the Mac (One like this I would like on Ubuntu):
[http://99lives.org/2007/02/11/xbox-live-mac-maclive/](http://99lives.org/2007/02/11/xbox-live-mac-maclive/)

Program on Windows:
[http://brh.numbera.com/software/xblist/](http://brh.numbera.com/software/xblist/)

[U][B]Update:
[/B][/U]twisted_steel has taken over this project & has written up a program. Click [here]("http://ubuntuforums.org/showthread.php?t=520113#37") for the latest post containing his instructions & release.

Use Wine to run the Windows one, "xblist" wine should run it.

---

### Post by TheSe7enthSin on 2008-03-10
I've tried to run it with Wine before, hence the creation of the topic. ;)
Edit: Oh yea. It doesn't seem to work on Wine because XBList requires .NET Framework 2.0. I saw somewhere that the framework doesn't work yet. But that was a long time ago, not sure about now.

---

### Post by blasteryui on 2008-03-10
> **TheSe7enthSin said:**
> I've tried to run it with Wine before, hence the creation of the topic. ;)
Edit: Oh yea. It doesn't seem to work on Wine because XBList requires .NET Framework 2.0. I saw somewhere that the framework doesn't work yet. But that was a long time ago, not sure about now.

.net Framework 2.0 does work my friend =]
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)
there ya go, now XBlist should work :D.

---

### Post by twisted_steel on 2008-03-13
The next version (0.2) is almost ready with a revamped friends list.  I think it looks a lot cleaner.  I haven't added in the grayscale conversion for offline friends, so that may come in a later version depending on the time.  After this one gets out, the next focus will be on adding in notification support (libnotfiy and mumbles).  Are there any other notification programs/libraries that anyone uses all the time?

There are two preview screenshots with the offline friends shown in the first and hidden in the second.  Note that only offline friends will be hidden.  If any friends are logged into Live, but set to Away or Busy, they would still show up in the second preview.

---

### Post by Joeb454 on 2008-03-13
It's looking good :) I'd like to contribute, but I have too much Uni work on my hands :(

---

### Post by G|N| on 2008-03-14
> **twisted_steel said:**
>  Are there any other notification programs/libraries that anyone uses all the time?

Don't forget about specto ;)
I looked at your code and it seems i could easily add a watch for xbox notifications myself.
Thank you for your work! :)

---

### Post by twisted_steel on 2008-03-14
> **Joeb454 said:**
> It's looking good :) I'd like to contribute, but I have too much Uni work on my hands :(

No problem - I've been through that before.:p

> **G|N| said:**
> Don't forget about specto :wink:
I looked at your code and it seems i could easily add a watch for xbox notifications myself.

Cool.  The code has changed slightly in the latest version with a variable added to the friend class that is updated when an online friend's description has changed (e.g. "Playing Lego Star Wars" when it was "Playing Halo 3" before).  The previous status (Online/Away/Busy/Offline) is also held onto for quick checking.

I'm going to try to get this all into a Launchpad project so it's easier to contribute and get at the code.

Does anyone have ideas on a better name?  I looked around and there is some old Java class called LiveStatus.

---

### Post by mozetti on 2008-03-14
LiveSeer/360Seer

LiveCensus

LiveDrone/360Drone

LivePegger/360Pegger

---

### Post by TheSe7enthSin on 2008-03-14
XBLStatus?
That doesn't seem to show much hits on google.

---

### Post by twisted_steel on 2008-03-16
I just uploaded the latest version (0.2) of XBL Status (formerly LiveStatus).  The URL on my site also changed, but the old URL has a link to the new page.  The new version uses ~/.xblstatus/ to store cache files and a cookie, so you can delete the old directory ~/.livestatus/ if you had the previous version installed.

[http://www.hollec.com/projects/xblstatus/](http://www.hollec.com/projects/xblstatus/)

---

### Post by twisted_steel on 2008-03-17
I created a project page on Launchpad and added the latest code from my computer (version 0.2 as of this writing).  It is the same code that was released in the package on my site.

[https://launchpad.net/xblstatus](https://launchpad.net/xblstatus)

---

### Post by twisted_steel on 2008-03-30
Notification support using libnotify is now in [trunk on Launchpad]("https://code.launchpad.net/xblstatus").  I'm going to wait until mumbles support is added before releasing 0.3.  Hopefully that will be soon ;-)

---

### Post by Gouki on 2008-03-31
Good work. Just a small thing:

On the readme, you mention that that the software requires python-beautiful-soup. The correct package name is: python-beautifulsoup 

Not something a search wouldn't fix, but just wanted to give you the heads up.

Great work so far!

---

### Post by twisted_steel on 2008-03-31
Thanks.  I'll fix the readme.

---

### Post by TheSe7enthSin on 2008-04-02
I like that you added it to LaunchPad. Easy updates. ^_^

So what are your feature update plans? Do you have a list you're working on or are you working on things as they come to mind?

---

### Post by twisted_steel on 2008-04-02
I have DBus notification support built into the code on my dev box that I was testing with a mumbles plugin yesterday.  I just got back, so I was going to try to get that out tonight.  The mumbles developer has been helping me with debugging the mumbles plugin, so I was just going to see if dot_j had any recommendations before it was pushed out.  Once I do that, that should make a 0.3 release, which will include DBus support and the Libnotify support that is currently in trunk on Launchpad.

As for the future, I really want to get a local configuration file squared away, and would probably just incorporate that into whatever the next release would include.  That would make it easier to install the program on the system-wide (read: deb/rpm package) instead of hand-editing the file every time you install it.  I also want to see if I can incorporate sending/receiving messages and just do some fixes in general.  For example, I had a friend suggest including the time the friend was offline in the "Offline" status - e.g. "Offline - 7 hours."  Eventully I would also like to move the control code out of the GUI.

---

### Post by Crafty Kisses on 2008-04-02
This is looking pretty sick, thanks man!

---

### Post by MadMax08 on 2008-04-04
great little app you have here. the only thing i noticed is that if a user is playing an orginal xbox game on their 360, it shows them as 'offline'. i'm not sure if there's anything that can be done about that, i also dont know if it shows up as 'online playing xxxxx' in Live messenger or on your 360 dashboard under the same conditions...

maybe a "minimize to tray" option?

just a thought

keep up the good work.

:)

---

### Post by smurphster on 2008-04-04
nice little app... i've been having some issues with it though. it seems to get disconnected with no error message and the buddy list never updates. i can't seem to link it to anything in particular. i'm a developer but never tried python so i have no clue how to debug it... but i'm willing to try if you point me in the right direction.

---

### Post by twisted_steel on 2008-04-06
Version 0.3 is out.  I have Launchpad hosting the files now, but will continue to save a copy on my site.

Link: [https://launchpad.net/xblstatus](https://launchpad.net/xblstatus)

New features:
[LIST]
[*]Notification support using Libnotify and DBus
[*]Offline friends will now show how long they have been offline
[*]Preferences are now saved in ~/.xblstatus/xblstatus.config - there is no more need to edit the script file before running
[*]I put a new icon together so it is easier to see in the taskbar[/LIST]To get [Mumbles]("http://www.mumbles-project.org") support, download the plugin from Lauchpad and copy it into ~/.mumbles/plugins/.  Select 'DBus' as the notification type in the XBL Status preferences.

---

### Post by twisted_steel on 2008-04-06
> **MadMax08 said:**
> great little app you have here. the only thing i noticed is that if a user is playing an orginal xbox game on their 360, it shows them as 'offline'. i'm not sure if there's anything that can be done about that, i also dont know if it shows up as 'online playing xxxxx' in Live messenger or on your 360 dashboard under the same conditions...

maybe a "minimize to tray" option?

just a thought

keep up the good work.

:)

I'm not sure about the original Xbox games.  It might be dependent on the game itself, but I have seen a friend show up as 'Playing Xbox Dashboard' or something similar to that.  Let me know if it does show up on the actual live site or in your Dashboard, but doesn't in the program.

I'll see if I can get a 'minimize to tray' option in a later version.

---

### Post by twisted_steel on 2008-04-07
> **smurphster said:**
> nice little app... i've been having some issues with it though. it seems to get disconnected with no error message and the buddy list never updates. i can't seem to link it to anything in particular. i'm a developer but never tried python so i have no clue how to debug it... but i'm willing to try if you point me in the right direction.

Does the friends list ever show up for you?  If it does, but then stops, does the Xbox Live page still work in a browser?  I am making a few assumptions about the connection at this point.  Before I started writing this, the Live site would be down or in maintenence all the time, but now it has been cooperating every time I've run or tested it.  I also have a new version out (see the above post).  Does the problem still happen with that version?  I didn't change any authentication/refreshing code, but it could just be a problem with the list in the GUI.

Here is a quick overview on how it works.  This is all done in LiveConnect.py.  The initial connection is created to the friends page, which is then redirected to a login page.  The form is filled out and then submitted.  Upon logging in, a cookie is saved and a page in the middle has a form that is submitted to finally get to the friends page.  In my testing, it has been fine with just refreshing the page every minute because I believe it keeps the session alive.  I haven't done any testing with disconnecting my computer to see what happens.  I have some TODOs sprinkled in with the authentication, but I never anything break.

---

### Post by smurphster on 2008-04-07
every time i notice it is not up to date, i've been logging into the web site to check. this is usually after a few hours of running. i just close the running instance, start a new one, and it runs just fine. my connection is very stable for the most part. a few times it happened, i had been restarting my router (trying to fix my voip issues... totally unrelated). it sounds like your script does not keep a connection open all the time so the only time i'd expect to see something wrong was if it was refreshing while the connection was down (even then i would expect it to work after another minute). i will download the updated version tonight and let it run a few days. maybe i'll dig into the code this weekend if i have time. are there any good python resources on the web?

---

### Post by smurphster on 2008-04-07
i like the new preferences and notifications :)

---

### Post by twisted_steel on 2008-04-07
> **smurphster said:**
> every time i notice it is not up to date, i've been logging into the web site to check. this is usually after a few hours of running. i just close the running instance, start a new one, and it runs just fine. my connection is very stable for the most part. a few times it happened, i had been restarting my router (trying to fix my voip issues... totally unrelated). it sounds like your script does not keep a connection open all the time so the only time i'd expect to see something wrong was if it was refreshing while the connection was down (even then i would expect it to work after another minute). i will download the updated version tonight and let it run a few days. maybe i'll dig into the code this weekend if i have time. are there any good python resources on the web?

Maybe the cookie/session expires after a few hours.  That could explain why closing and reopening the program fixes it.  I'll also take a look on my end and see if I notice anything like that.

As far as resources, I am using [ClientForm ]("http://wwwsearch.sourceforge.net/ClientForm/")to interact with the page forms and [Beautiful Soup]("http://www.crummy.com/software/BeautifulSoup/documentation.html") for help with parsing the friends page.  There is a [general Python tutorial]("http://docs.python.org/tut/") and a more specific page for the [library used to access URLs]("http://docs.python.org/lib/module-urllib2.html").

---

### Post by twisted_steel on 2008-04-07
> **smurphster said:**
> i like the new preferences and notifications :)

Thanks.  It's slowly getting there :)

---

### Post by MadMax08 on 2008-04-08
> **MadMax08 said:**
> great little app you have here. the only thing i noticed is that if a user is playing an orginal xbox game on their 360, it shows them as 'offline'. i'm not sure if there's anything that can be done about that, i also dont know if it shows up as 'online playing xxxxx' in Live messenger or on your 360 dashboard under the same conditions...


i looked into this while online both with xblstatus and xbox.com open, and when a user goes from the dashboard (Which shows up as "Playing Xbox360 dashboard") to playing an original xbox game, it shows them as "offline" both on xblstatus and on xbox.com. however, the game i tested it with (indiana jones) isn't an xbox live game; i dont have any original xbox games that are live-compatible with me. i can try it with one that is live-compatible sometime this evening.

the new preferences and notifications are great, btw!

---

### Post by smurphster on 2008-04-10
> **MadMax08 said:**
> i looked into this while online both with xblstatus and xbox.com open, and when a user goes from the dashboard (Which shows up as "Playing Xbox360 dashboard") to playing an original xbox game, it shows them as "offline" both on xblstatus and on xbox.com. however, the game i tested it with (indiana jones) isn't an xbox live game; i dont have any original xbox games that are live-compatible with me. i can try it with one that is live-compatible sometime this evening.

the new preferences and notifications are great, btw!

xbox 360 doesn't stay connected to xbox live while playing originals. its up to the game to sign in. so if the game doesn't sign you in (or is not live-enabled at all), you'll appear offline. i tried w/ halo 2 and it seems to work fine.

---

### Post by smurphster on 2008-04-18
i still haven't gotten around to debugging this but i noticed something today that might interest you. someone signed on and i got a notification (ok); every minute his status did not change yet i still got a notification. hopefully that might give you an idea of what loop its stuck in or what variables are stuck.

---

### Post by smurphster on 2008-04-18
i've spotted a loop that need some error checking (actually, probably before the loop). its in the function parseFriendsPage. if there is something wrong with the page or we got something we didn't expect, the for loop that loops through allGamertags will not do anything since allGamertags will be empty. thus the current list will stay in tact (including each friend's previous status which is why i kept getting that notification). that doesn't explain why we're getting a faulty page to begin with but its a solid starting point. i've inserted a bunch of print commands to see what the page looks like when the error occurs. hasn't happened yet so we'll see.

and no, i do not have too much free time :P

---

### Post by smurphster on 2008-04-19
here's the response i get every minute while the buddy list does not update:

[HTML]
<html>
<head>
	<noscript>JavaScript required to sign in
		<meta http-equiv="Refresh" content="0; URL=https://login.live.com/jsDisabled.srf?lc=1033"/>
	</noscript>
	<title>Continue</title>
	<script type="text/javascript">
		function OnBack(){}
		function DoSubmit()
		{
			var subt=false;
			if(!subt)
			{
				subt=true;
				document.fmHF.submit();
			}
		}
	</script>
</head>
<body onload="javascript:DoSubmit();">
	<form name="fmHF" id="fmHF" action="https://live.xbox.com/xweb/live/passport/setCookies.ashx?rru=httpZ3AZ2FZ2FliveZ2ExboxZ2EcomZ2FenZ2DUSZ2FprofileZ2FFriendsZ2Easpx&wa=wsignin1.0" method="post" target="_self">
		<input type="hidden" name="NAPExp" id="NAPExp" value="Mon, 28-Jul-2008 18:21:51 GMT">
		<input type="hidden" name="NAP" id="NAP" value="V%3D1.6%26E%3D67c%26C%3DB09sT_W8q64-vumM5uQcrXYMl4knO0CQ850wdI3zPwrNJaxgOQ5pmg%26W%3D1">
		<input type="hidden" name="ANON" id="ANON" value="A%3DBF1232C2BA848AD041A9B996FFFFFFFF%26E%3D6d6%26W%3D1">
		<input type="hidden" name="ANONExp" id="ANONExp" value="Wed, 05-Nov-2008 19:21:51 GMT">
		<input type="hidden" name="t" id="t" value="EgAFAQMAAAAEgAAACYAAGHBO/lfMJ5HWJdhFXPyNKZqVgkVFm4SNdU8a5lyHYDEkwD+id/T+ynsfbTZWwZml37pECYJ0YEYpjf9ve7wqh4daN2tPaqiAPq0m9rn/pXDaJbNs7kaehpkaAAQ+sx/4QAQhyVwXs8JkpM71h5WBTr2uB+Rse6hCXzjA32iFyAJ0AFIAdACAbgEA5bnv/Eu0CUjHQwlI1gIBAAAAAAAAAAAkAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAS68rpSyti0YAAM/VCUjHuBtIAAAAAAAAAAAAAAAADQA2Ny40OC4yMzcuMTkA">
	</form>
</body>
</html>
[/HTML]

i'm not sure how many times i got this, i counted 38 that fit in the terminal buffer. then i got this error that stopped the refreshing entirely:

```

Error connecting to the Live friends page.
Reason: (111, 'Connection refused')
Traceback (most recent call last):
  File "./xblstatus.py", line 456, in timerUpdate
    self.refreshFriends()
  File "./xblstatus.py", line 271, in refreshFriends
    self.xbLive.refresh()
  File "/home/smurph/xblstatus/LiveConnect.py", line 143, in refresh
    self.refreshFriends(request)
  File "/home/smurph/xblstatus/LiveConnect.py", line 162, in refreshFriends
    self.friendsPage = response.read()
UnboundLocalError: local variable 'response' referenced before assignment

```

i'm not sure if we should even worry about the error. i'm guessing what's happening is our "client" is not cooperating with the refresh page so xbox.com eventually refuses our connection after X number of tries. so i guess the question is, can this other page be handled? it looks like the form just needs to be submitted.

does anyone know why this page pops up to begin with? i've noticed it when using a browser too. i want to say its  the session expiring (not the cookie) but its a bit odd to force your browser to hit another page to refresh your session. of course we're talking about M$ so i guess its not that surprising.

---

### Post by twisted_steel on 2008-04-19
Thanks for taking a look at this.  Does the page that comes up look like the login page that you get when you first try to go to the live site?  If so, I think I've seen that before when refreshing in my browser, but not when using the program.  If that's the case, I probably just need to add in another check to look for the page and submit the form again.

---

### Post by smurphster on 2008-04-19
i haven't taken a real close look at it but i believe its the same page that comes up when you log in before it takes you back to where you were. i noticed there's a spot in the code that submits a "hidden" form, i think this is the same thing. i took a stab at a fix myself and i'm waiting to see if it works. basically i have it check to see if the title of the page is "Continue", if so, retrieve the form, submit it, retrieve the response (which should be the friends page), and continue...

python is quite the interesting language. its like OO on the fly. there's a lot of potential for innexperienced programmers to make some real ugly programs :)

---

### Post by smurphster on 2008-04-20
this is annoying...

the object returned from urllib2.urlopen() is described as a "file-like object..." but really it only has read(), readline(), readlines(), fileno() and close(). without seek(), how are you supposed to do more than one pass through the object? how useless!

the problem is we have to do a read() to see what the title of the page is. if its "Continue", we want to grab the form objects using ClientForm.ParseResponse(). problem is, after the read, the pointer is at EOF and ClientForm doesn't parse anything.

i figured out i can read about 200 characters to get the title and then have ClientForm handle the rest. another option would be to get the response a second time for ClientForm. both are pretty ugly. you're the experienced python programmer, what do you think?

---

### Post by twisted_steel on 2008-04-20
Sorry for the delay.  I was outside for most of the day since the sun was actually out 8)

It seems strange that this 'hidden' page comes up in the middle of your requests.

From the [urllib2]("http://www.python.org/doc/lib/module-urllib2.html") page, it looks like that while the *response* variable has the file-like methods, it should also have a *geturl()* method.  If I remember correctly, redirects are transparent in urllib2, so in the *refreshFriends* method, it would open the friends page and in your case, it would then be redirected to the hidden/login page after a certain amount of time.  Just before the page is read, it might be possible to read the current URL of the *response* variable.  If the URL is the friends page (listed in *self.friendsURL*), it should be fine to continue with reading the page and parsing out the friends.  If it doesn't match, then there are two options that I can think of off the top of my head.

The first would be to just call *self.connect()* again.  That method takes care of handling the login page and redirects.  It will then refresh the friends again, but it would then (hopefully) match the correct URL and continue on its merry way.

The other is to just submit that Continue page.  The URLs for the login and Continue page are different.  You could check to see if it matches the Continue page, and if so, submit the form, if it doesn't match the friends page or the Continue page, then fall back to the *self.connect()* method.  The URL for the Continue page is *[https://login.live.com/ppsecure/post.srf?](https://login.live.com/ppsecure/post.srf?)...* (the rest I left out, but you could just do a match on the beginning of the URL).  The URL for the Login page is *[https://login.live.com/login.srf?](https://login.live.com/login.srf?)...* (the rest was also left out).  If it matches that continue page, I think you can add in the hidden form submit code to send the form to the friends page.  Then continue as usual and read the resulting page.

Some quick pseudocode ...

```
try to open the page[LIST]
[*]if the URL matches the hidden page, submit the form and read the friends page
[*]if the URL matches the friends page, just read and parse the page like normal
[*]if the URL matches the login page, try to connect again
[*]if the URL is anything else, write a debug message to let the user know something has changed with the site[/LIST]
```The reading of the friends page and parsing can probably be consolidated into one area, with just the hidden form submit above, to consolidate code.

Hope this helps and thanks again for looking into the problem :)

---

### Post by smurphster on 2008-04-21
checking the url is a good idea. i'll give that a try

the only problem i see with calling self.connect() again, is that it has the potential of getting stuck in a very ugly loop. i'll keep playing with it and let you know what i find

has anyone else reported this issue? do you leave it running for several hours with no problems? seems odd that i'm the only one with this problem.

---

### Post by twisted_steel on 2008-04-21
Yeah, the loop would be something worth trying to avoid.  Nobody else has reported this problem and I haven't had any problem with running it for a few hours.  I only checked the current friends list compared to the one on the Live site for accuracy.

I added in some debug code to print out the page with a timestamp to see if this happens to me.  One thing that I noticed, which seems strange to me, is the page is never complete.  It is always cut off at the end for some reason.  It usually stops somewhere around the page footer code, but one time it was dangerously close to cutting off the friends information.  I'm running Hardy on my box, so I'm not sure if that's the reason, or if this has been happening all along.  It could be that it somehow thinks there is an end of file (EOF) character in the output.

---

### Post by twisted_steel on 2008-04-21
It's been refreshing properly for me (minus the strange read() issue) for the past 4 1/2 hours.  I only have 12 friends in my list - maybe that makes some sort of difference?

---

### Post by ace007 on 2008-04-21
I'm very interested in this project as well.  I wish I could be of some use, but python is next on my list to learn.  Too bad the world doesn't run on Fortran/Matlab.

Where is the best place to check on the status of the project?  Heck, I'd be a beta tester.

---

### Post by twisted_steel on 2008-04-21
> **ace007 said:**
> I'm very interested in this project as well.  I wish I could be of some use, but python is next on my list to learn.  Too bad the world doesn't run on Fortran/Matlab.

Where is the best place to check on the status of the project?  Heck, I'd be a beta tester.

I had a class where we exclusively used the 'Fortran 66' subset of the language, and it was interesting to say the least :p

I think the best place to check would be the Launchpad page: [https://launchpad.net/xblstatus](https://launchpad.net/xblstatus).  If I get some spare time, I'd like to sit down and add in some info to the blueprints page on there and also add in any known bugs to the bug reports, just to keep track of things.  It also might be worth keeping an eye on this thread, which seems to be where the bulk of the discussion takes place.  I'm on [FreeNode]("http://en.wikipedia.org/wiki/Freenode") from time to time as well.

---

### Post by twisted_steel on 2008-04-21
> **twisted_steel said:**
> I added in some debug code to print out the page with a timestamp to see if this happens to me.  One thing that I noticed, which seems strange to me, is the page is never complete.  It is always cut off at the end for some reason.  It usually stops somewhere around the page footer code, but one time it was dangerously close to cutting off the friends information.  I'm running Hardy on my box, so I'm not sure if that's the reason, or if this has been happening all along.  It could be that it somehow thinks there is an end of file (EOF) character in the output.

It turns out that I only saw the problem because of the way I was looking at my debug file.  I had it redirected to a file and was looking at it with tail -f, which was not displaying the end of the file. When I opened the debug file itself, everything was intact.  :confused:

I'm just glad that it wasn't a real problem.

---

### Post by ace007 on 2008-04-21
I'm an Aerospace Enginerd so I have had to learn to bend Fortran to my will in order to user older (read: all) code.  All I can say is, Matlab FTW.

I dabbled in Perl and Tcl; how much different is python?

---

### Post by twisted_steel on 2008-04-22
> **ace007 said:**
> I'm an Aerospace Enginerd so I have had to learn to bend Fortran to my will in order to user older (read: all) code.  All I can say is, Matlab FTW.

I dabbled in Perl and Tcl; how much different is python?

I haven't used Tcl, but I see Python as being relatively close to Perl.  One of the big differences is the use of whitespace.  Indentation is used to determine things like method/function bodies and if-else blocks.  It is one of those things that can really throw you off if you're not expecting it.

Two resources that you might want to check out are the [Python 'Getting Started' Guide]("http://www.python.org/about/gettingstarted/") and the online book [Dive Into Python]("http://www.diveintopython.org/").

Edit ... not sure how things show up on your computer, but those last two resources are links

---

### Post by twisted_steel on 2008-04-22
> **ace007 said:**
> I'm an Aerospace Enginerd so I have had to learn to bend Fortran to my will in order to user older (read: all) code.  All I can say is, Matlab FTW.

I dabbled in Perl and Tcl; how much different is python?

I haven't used Tcl, but I see Python as being relatively close to Perl.  One of the big differences is the use of whitespace.  Indentation is used to determine things like method/function bodies and if-else blocks.  It is one of those things that can really throw you off if you're not expecting it.

Two resources that you might want to check out are the [Python 'Getting Started' Guide]("http://www.python.org/about/gettingstarted/") and the online book [Dive Into Python]("http://www.diveintopython.org/").

---

### Post by smurphster on 2008-04-22
yeah the whitespace thing confused the hell out of me at first. once i understood the error, it was very simple from then on :)

i only have 16 friends on my list so that's not too different than your 12. i haven't really timed it to see how long it takes but i usually notice it after 6 hours or more.

---

### Post by twisted_steel on 2008-04-22
> **smurphster said:**
> i only have 16 friends on my list so that's not too different than your 12. i haven't really timed it to see how long it takes but i usually notice it after 6 hours or more.

Ah, I see.  That's probably why I never noticed it.  I think I finally had it running about 5.5 hours in total yesterday.

---

### Post by smurphster on 2008-04-23
got a different error this time:
```

Traceback (most recent call last):
  File "./xblstatus.py", line 456, in timerUpdate
    self.refreshFriends()
  File "./xblstatus.py", line 271, in refreshFriends
    self.xbLive.refresh()
  File "/home/smurph/xblstatus/LiveConnect.py", line 143, in refresh
    self.refreshFriends(request)
  File "/home/smurph/xblstatus/LiveConnect.py", line 159, in refreshFriends
    print "Error code:", e.reason
AttributeError: 'HTTPError' object has no attribute 'reason'

```
and no "Continue" page this time...

---

### Post by smurphster on 2008-04-23
my fix successfully re-submitted the continue form and continued to run. however, at some point one of my buddies got stuck and is no longer updating. everone else is updating just fine. not sure if that's related but i'm guessing not.

btw, i got the continue page after 480 refreshes so 480 / 60 = 8 hours. i'll see if that continues to be the case.

anyway, here's what i have for a refresh function:
```

    def refreshFriends(self, request):
        # Refresh the friends page using the given request since we should now
        # be logged in for the session
                
        try:
            response = urllib2.urlopen(request)
        except urllib2.URLError, e:
            if hasattr(e,'reason'):
                print "Error connecting to the Live friends page."
                print "Reason:", e.reason
            elif hasattr(e,'code'):
                print "Error with the request to the Live friends page."
                print "Error code:", e.reason

# 4/20/2008 -- Eric Murphy (smurphster) -- handle the "Continue" page properly
	page = response.read()
	response.close()
	soup = BeautifulSoup(''.join(page))
	title = soup.findAll("title")[0].contents[0]
#	print 'title: ' + title 
	if (title == "Continue"):
#		print "continue page"
		# since the type of response cannot seek, we have to request it again
		response=urllib2.urlopen(request)
#		print 'call ClientForm.ParseResponse'
		forms = ClientForm.ParseResponse(response, backwards_compat=False)
		response.close()
		form = forms[0]
#		print 'click the form'
		request2 = form.click()
		try:
#			print 'get response'
			response2 = urllib2.urlopen(request2)
		except urllib2.URLError, e:
			if hasattr(e,'reason'):
				print "Error connecting to the Live friends page."
				print "Reason:", e.reason
			elif hasattr(e,'code'):
				print "Error with the request to the Live friends page."
				print "Error code:", e.reason
		print 'read response'
		self.friendsPage = response2.read()
		response2.close()
	else:
		self.friendsPage = page
        
	# Save the HTML of the friends page
#        self.friendsPage = response.read()
#        response.close

#	print self.friendsPage
        
        # Parse all the friends and save them in the dictionary self.liveFriends
        self.parseFriendsPage(self.friendsPage)
        
        return

```

---

### Post by smurphster on 2008-04-23
looks like things just got a quite bit more difficult. if you have over 16 friends, it starts paging. i have a page 2 of my friends page... that's why that one friend got stuck, they're on the 2nd page when offline, 1st page when online. arg!

i'll take a closer look this weekend

---

### Post by twisted_steel on 2008-04-24
> **smurphster said:**
> looks like things just got a quite bit more difficult. if you have over 16 friends, it starts paging. i have a page 2 of my friends page... that's why that one friend got stuck, they're on the 2nd page when offline, 1st page when online. arg!

i'll take a closer look this weekend

Nice, a second page.  I wonder if it keeps going if you have, say, 33 friends.  I should add some more friends for testing purposes.

Thanks for the above fix.  I'll also try running it this weekend to see if it keeps it going for me.

---

### Post by smurphster on 2008-04-25
i'm assuming it will have another page every 16 friends. it gives you links to each page on the bottom so beautiful soup should be able to snag each of those urls and we'll just need a loop to parse each of them.

i should try w/ my wife's account. she has LOTS of friends. she gets the "OMG IT'S A GIRL" reaction every match :)

---

### Post by Joeb454 on 2008-04-25
Some people tend to be "OMG IT'S A GIRL" ... commence abuse

It's not good being a female and playing games like CoD4 etc. online, a lot of people deem it a men only world.

I should note that I'm not female either :)

---

### Post by smurphster on 2008-04-25
not that this has anything to do with this topic but... i think that mentality is absurd and is what gives gamers a bad rep. just more proof that sexism is alive and kicking. i can't believe how many racist and sexist people i run into on XBL.

anyway, i keep running into other errors at random. sometimes its an index out of range when fetching the form, other times its just an error fetching the page. i guess it just needs some fallback in case the page errors for whatever reason.

---

### Post by NickD-NLUG on 2008-05-25
> **ace007 said:**
> I'm very interested in this project as well.  I wish I could be of some use, but python is next on my list to learn.  Too bad the world doesn't run on Fortran/Matlab.

Where is the best place to check on the status of the project?  Heck, I'd be a beta tester.

I'm still up for helping, although pretty short of time too.

I've just got the program running, nice piece of work.  I think it definitely needs a status information on the screen, but yes, rather cool.  I'll help as I can.

---

### Post by smurphster on 2008-06-05
> **NickD-NLUG said:**
> I'm still up for helping, although pretty short of time too.

I've just got the program running, nice piece of work.  I think it definitely needs a status information on the screen, but yes, rather cool.  I'll help as I can.

i've been playing with this on and off but i'm not making any progress. i like python and all that but i think the screen scraping technique is not going to cut it. if anyone knows how to tap into xbox live through some other method, i'm all ears.

also, i've looked into writing plugins for pidgin (formerly gaim) and i think that may be a good route too (why re-create the wheel?). pidgin already has a feature-rich gui, buddy list management, why not use it?

twisted_steel, you still around?

---

### Post by twisted_steel on 2008-06-05
> **smurphster said:**
> i've been playing with this on and off but i'm not making any progress. i like python and all that but i think the screen scraping technique is not going to cut it. if anyone knows how to tap into xbox live through some other method, i'm all ears.

also, i've looked into writing plugins for pidgin (formerly gaim) and i think that may be a good route too (why re-create the wheel?). pidgin already has a feature-rich gui, buddy list management, why not use it?

twisted_steel, you still around?

Yeah, I'm still around.  I've been busy with work and grad school.  I need more hours in the day :-P

I tried emailing someone who has a site that somehow taps into Live through some sort of agreement, but I haven't heard anything back from them.  They also did not have anything with friend info on there.  I'll send the email to Major Nelson to see if maybe he can forward it to someone in the know.  MSN messenger has no problem doing this, but of course the protocol is undocumented, and it's their product.

I was also thinking a while back that it would be cool if this could hook into pidgin.  The only way that I'm aware of at the moment to get the data is through screen scraping.  So while your friends could potentially show up in pidgin, you would be stuck with the same limitations.  Perhaps there is some possibility of extending the MSN support, but again, accessing Live info is undocumented and unsupported.

---

### Post by Strawp on 2008-06-06
Yeah, this would be great in Pidgin. I'll bet actual messaging would be doable as well - there is a messaging web interface for live.xbox.com that could be hacked a bit. I have plenty experience of fooling web interfaces into thinking they're a legit web request so perhaps if you got the project so far I might be able to chip in and help out with the messaging part?

---

### Post by smurphster on 2008-06-06
> **Strawp said:**
> Yeah, this would be great in Pidgin. I'll bet actual messaging would be doable as well - there is a messaging web interface for live.xbox.com that could be hacked a bit. I have plenty experience of fooling web interfaces into thinking they're a legit web request so perhaps if you got the project so far I might be able to chip in and help out with the messaging part?

the clientform package we're currently using seems to have no problem with the login screen so i bet messages wouldn't be a problem either. problem is it would be very slow chatting (currently it refreshes every minute) and if we turn that faster, there'd be a lot of traffic. i'm going to look into the msn/xboxlive protocol a bit more before i start messing with that.

---

### Post by Strawp on 2008-06-06
I don't think speed is too much of an issue - the chatting through the Live blade in-game is incredibly slow anyway.

---

### Post by twisted_steel on 2008-06-09
I sent an email to the Xbox.com Community Developer group to see if they have some sort of API available.  In the meantime I'm going to document the current method of accessing the site as a fallback plan.  That way there is a base to help try to figure out handling specific cases, such as smurphster's large (well, larger than mine ;)) friends list.

I believe there is Pidgin protocol support for MySpace, but I'm not sure if that is done by scraping the page or if there are APIs available.  It might be something worth looking into if the Pidgin integration is used for Xbox Live.

---

### Post by twisted_steel on 2008-06-09
I installed Live Messenger in Windows, and from what I could tell, the only way to see my friends was to click on the Xbox icon on the left.  The friends list in the main window was empty because I don't use that account for MSN Messenger.  When I clicked on the Xbox icon, it loaded a page that didn't exist when I tried looking up the actual address in a web browser.  I used [ospy]("http://code.google.com/p/ospy/") and Live Messenger crashed after I injected the application and it started to load the page.  I looked up part of the domain on Google and found [this page]("http://live.xbox.com/en-us/profile/FriendsMessengerTab.aspx"), which looks exactly like the one that loaded when I was in Live Messenger.  From what I can tell, Live Messenger takes care of setting an authentication cookie before going to that page.  If you try going there on another computer without being logged into the Xbox Live site, it only shows the top section.  However, if you are previously logged in, it shows the friends list at the bottom of the page.  It looks like this one is a lot smaller in size.  Smurphster, can you check and see if it lists all of your friends?

Edit:
[This]("http://www.xbox.com/en-us/messengertab/xboxtab.htm?tab=xbox") is the first page I found, which redirects to the one I listed above.

---

### Post by TheSe7enthSin on 2008-06-09
I just wanted to pop into this topic and say that I'm enjoying the progress & findings you all have made so far. I don't post a reply here too often, since I can't really contribute...But I do track the topic for new posts.

And it's awesome that this topic is still kicking.
=]

---

### Post by twisted_steel on 2008-06-09
> **TheSe7enthSin said:**
> I just wanted to pop into this topic and say that I'm enjoying the progress & findings you all have made so far. I don't post a reply here too often, since I can't really contribute...But I do track the topic for new posts.

And it's awesome that this topic is still kicking.
=]

Yeah, it's really come a long way, even though it's now relegated to the Archive section.  Only a few more months and the thread hits the one year mark :mrgreen:

---

### Post by NTolerance on 2008-06-11
This program is great, thanks for your work on it.

Would it be possible to encrypt the password?  Even better, could we use GNOME keyring to store the login data?  Thanks!

---

### Post by twisted_steel on 2008-06-11
> **NTolerance said:**
> Would it be possible to encrypt the password?  Even better, could we use GNOME keyring to store the login data?  Thanks!

I've been thinking about adding this feature eventually and just opened up a bug to make note of the feature request.  Thanks.

---

### Post by vinnie on 2008-07-13
I just stumbled upon this thread accidentally and here is an app i've wanted for so long i can barely remember.

(bows to twisted_steel)

I'm not running Linux at the moment, i'm waiting for the next Kubuntu with KDE 4.1, so i was going to ask if someone can post a screenshot of the app

---

### Post by twisted_steel on 2008-07-13
> **vinnie said:**
> I'm not running Linux at the moment, i'm waiting for the next Kubuntu with KDE 4.1, so i was going to ask if someone can post a screenshot of the app

Here you go.

---

### Post by phyrewall on 2008-07-15
Great app, I've been looking for something like this for a while!
Thanks!

Would it be possible to take it out of the window list and place it in the notification area?

---

### Post by Strawp on 2008-07-15
How tricky would it be for this to be ported as a Pidgin plugin?

---

### Post by twisted_steel on 2008-07-15
> **Strawp said:**
> How tricky would it be for this to be ported as a Pidgin plugin?

I was actually looking into the other week.  I *think* it should be fairly straightforward.  By that I mean it looks like the pidgin protocol plugins have certain definitions that need to be followed, not that it will be done in a day ;) The hard part, at least for me, will be translating the scraping from Python to C, as it's been a few years since I've programmed in straight C.  This was one of the reasons I'd like to sit down and document the current way of polling the Xbox page for details along with any special cases.  I did find the source code for the Facebook protocol plugin on Google code: [http://code.google.com/p/pidgin-facebookchat/source/browse/trunk/libfacebook.c](http://code.google.com/p/pidgin-facebookchat/source/browse/trunk/libfacebook.c).  I think I saw a general plugin around somewhere, but I can't find it at the moment - maybe it's somewhere on [here]("http://developer.pidgin.im/wiki/CHowTo")?  One of the things that makes this a lot different than the current implementation of XBL Status is the author uses POST and GET to make the page requests.  There is also a MySpace IM plugin floating around, but I haven't had a chance to see if it interfaces with the web page directly or via some other set of calls.

I guess the bottom line at the moment is the Pidgin plugin would be excellent, as it removes some of the burden of trying to figure out why GTK spits out random errors about the TreeView event though it looks like everything is working as it should be.  I'd love to sit down and start working on it, but work, school, and the occasional vacation are really using up my time.  I will be class-free in mid-August if that helps ;)

---

### Post by twisted_steel on 2008-07-15
> **phyrewall said:**
> Great app, I've been looking for something like this for a while!
Thanks!

You're welcome :)

> **phyrewall said:**
> Would it be possible to take it out of the window list and place it in the notification area?

Are you thinking of something like having an icon that just sits in the notification area that you can click on to bring the window to the front and either clicking on it again or closing the window hides it to the tray by default?

---

### Post by Strawp on 2008-07-15
Great - I'll keep this thread on my notifications list :)

---

### Post by vinnie on 2008-07-18
> **twisted_steel said:**
> Are you thinking of something like having an icon that just sits in the notification area that you can click on to bring the window to the front and either clicking on it again or closing the window hides it to the tray by default?

I was thinking about that too. Is it doable?

---

### Post by Strawp on 2008-07-24
Couple of questions:

1. I had a link set up in my top panel to this but I think there is an issue with the current working dir getting lost and the script not running (because it believes it's installed in the panel, not in ~/xblstatus). Any tips on how to get that working?

2. I don't think this is tracking when people are logging off, or if it is then it's not removing them from the list. If I leave it running all evening then I get a very large list of all the people that had logged on, but many of them have gone offline. Their status still says "playing <whatever>". Any new releases scheduled?

---

