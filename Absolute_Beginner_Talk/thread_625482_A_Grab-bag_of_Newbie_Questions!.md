---
title: "A Grab-bag of Newbie Questions!"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by the_Ben on 2007-11-28
Howdy forum!  I'm a brand new user to Ubuntu (started this week with 7.10), and am doing my best to get my feet wet on my own.  I've been able to install several programs without problems, and the OS recognizes most of my hardware automatically, but I have a few questions that I'm having trouble getting answered.  I've searched far and wide through these very forums, and with trusty google, but so far I can't figure out...

1) How to get my Lexmark 510 series printer to be recognized.

2) How to install software not listed in "add/remove applications".  (Programs like Comical, Google Desktop, Google Earth, etc.)

3) How to get the hang of the terminal.  I saw another thread that linked to explanations of all the commands, but now I can't find that thread.

4) I'm also having an issue with the thunderbird webmail addon.  I try to go about installing it the usual way, but it tells me "Not a valid install package -207".

There's other stuff as well, but it's late and I figure I can post the issues as they arise, if I can't find the answers elsewhere.  Thanks in advance!

---

### Post by oeolycus on 2007-11-28
2) [Guide to Google Earth]("http://ubuntuforums.org/showthread.php?t=195382") (maybe out-of-date) 
Nice guide to the differences between [apt-get and aptitude]("http://www.psychocats.net/ubuntu/aptitude")
[Synaptic]("https://help.ubuntu.com/community/SynapticHowto"), the graphical interface for installing packages (more detailed than add/remove)

3)Various [terminal ]("http://linux.org.mt/article/terminal")[command]("http://ubuntuforums.org/showthread.php?p=990636") guides

I found most of these with Google, which is very helpful if the Ubuntu search doesn't immediately bring up what you need. I also regularly consult this [guide ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")and this [webpage]("http://www.psychocats.net/ubuntu/").

---

### Post by jfinkels on 2007-11-28
> **the_Ben said:**
> 
2) How to install software not listed in "add/remove applications".  (Programs like Comical, Google Desktop, Google Earth, etc.)


See first link in my signature.

---

### Post by candtalan on 2007-11-28
Welcome!
> **the_Ben said:**
>  1) How to get my Lexmark 510 series printer to be recognized. There might not be much good news about this. Lexmark are known for not cooperating with linux. As models with no linux support may in future find lower sales figures, then it is possible things may improve with time.
>  2) How to install software not listed in "add/remove applications".  (Programs like Comical, Google Desktop, Google Earth, etc.)
 If you need software from outside the Repositories, there are at least two ways - either get the source code, compile it, and install manually (putting correct files in appropriate places) or get a binary file, which you have decided is trustworthy, and ensure it is given executable rights, and run it from an appropriate place. ./binaryfile  (dot and slash) will run 'binaryfile'. Note there is a 'package manager' also - synaptic, say, which has many possibilities. 
>  3) How to get the hang of the terminal.  I saw another thread that linked to explanations of all the commands, but now I can't find that thread.
  you are using the forums search? Also there are lots of such sites on the internet. google for something like linux commands tutor maybe?
>  4) I'm also having an issue with the thunderbird webmail addon.  I try to go about installing it the usual way, but it tells me "Not a valid install package -207".  Sorry, I dont know. It would be useful to have more details about what your usual way is, and exactly which file etc.

---

### Post by smacattack on 2007-11-28
for the printer...

try..
- going into System>Administration>Printing
-look for the driver section and click 'change'
-pick lexmark on the link and see if any of the listed printers matches your own.

that's all i can think of right now cause that's what i did for mine but someone may have something else to tell you.

goodluck.

---

### Post by Grey Box on 2007-11-28
[http://linuxprinting.org]("http://linuxprinting.org") has reasonably up to date information on printing driver availability. Drivers are not always GPL or freely available. Sometimes you have to go to the website of the manufacturer to get your drivers.

---

### Post by jpkotta on 2007-11-28
1)
[http://openprinting.org/show_printer.cgi?recnum=Lexmark-C510](http://openprinting.org/show_printer.cgi?recnum=Lexmark-C510)
Looks like it will work, but I didn't see it in the CUPS web interface.  I also don't see the ppd file on my system, so it's clearly in some special package, if it's in any at all. Note that the openprinting entry says something about poor Debian support, this means poor Ubuntu support.  Not that you can't get it running, but it may be more difficult than usual.

2)
GoogleEarth is in the [Medibuntu]("http://www.medibuntu.org/") repo.  GoogleDesktop is available as a .deb.  Comical needs to be built from source, it appears.  Have a look in the [wiki]("https://help.ubuntu.com/community/UserDocumentation") and you should get 90% there.

3)
[http://linux-newbie.sunsite.dk/index.html](http://linux-newbie.sunsite.dk/index.html)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
These will get you started with the command line.  It's not really something you sit down and learn, at least for me.  I just got the basics down, and learned a bit at a time from there.

---

### Post by hyper_ch on 2007-11-28
Google Earth is in the Medibuntu repos. Have a search on google for it and there's also a howto on how you add medibuntu to your existing repositories.

---

### Post by RomeReactor on 2007-11-28
Hi. For a cbz/cbr viewer like CDisplay, I suggest you wait until you get comfortable with the terminal, since you'll need to use it to compile Comical; meanwhile, try [Comix]("http://comix.sourceforge.net/") or [QComicBook]("http://linux.bydg.org/~yogin/"). Both are available through Add/Remove (search for **comic**) or in Synaptic.

[Linux Command]("http://www.linuxcommand.org/") is a good place to get acquainted with the command line.

Hope this helps.

---

### Post by the_Ben on 2007-11-28
Wow guys, thanks for the quick, informative responses!  :D  I'll have to check most of these out when I get back to my linux laptop at home.  Just out of curiosity, how long did it take you seasoned veterans to get comfy with the terminal?  Ya know, back when you first started using it?

> [QUOTE]4) I'm also having an issue with the thunderbird webmail addon. I try to go about installing it the usual way, but it tells me "Not a valid install package -207".
Sorry, I dont know. It would be useful to have more details about what your usual way is, and exactly which file etc.[/QUOTE]

Sorry, that was kinda vague.  Here's the dealio: I go to the appropriate web page ([http://webmail.mozdev.org/]("http://webmail.mozdev.org/")), download the webmail extension to Desktop (I'm not sure if I need to put it anywhere else), then open up thunderbird and the "addons" menu.  I click "install addon", point to the file on my desktop, and click okay.  It starts to load it, but then stops and gives me the error message listed above.  I'm not having any problems with firefox addons, FYI.  Any ideas?

---

### Post by Dedoimedo on 2007-11-28
Hello,

1. I use a Lexmark printer - and use HP drivers for it. Just find the equivalent HP printer and use its drivers for it. In other words, define your printer as HP in Ubuntu, rather than Lexmark.

Example: I have Lex E232. I use LaserJet 6L drivers for it. Works fabulously.

2-4. In general, you might find this useful (on me site)
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

Cheers,
Dedoimedo

---

### Post by jpkotta on 2007-11-28
> **the_Ben said:**
> Wow guys, thanks for the quick, informative responses!  :D  I'll have to check most of these out when I get back to my linux laptop at home.  Just out of curiosity, how long did it take you seasoned veterans to get comfy with the terminal?  Ya know, back when you first started using it?


When I first started using it, I had to use it.  I was an intern and I got this old AIX workstation.  There was a GUI, but it wasn't anything like KDE or Gnome.  It was MWM; later I figured out how to use IceWM.  Anyway, you had to do everything from the terminal: run programs, manipulate files, do various administrative tasks, etc.  I learned the basics in a day or two.  I was pretty good in a couple weeks.  I still use the command line a lot, because I work with several systems that don't have a graphical display.

---

### Post by the_Ben on 2007-11-28
> I use a Lexmark printer - and use HP drivers for it. Just find the equivalent HP printer and use its drivers for it. In other words, define your printer as HP in Ubuntu, rather than Lexmark.

Example: I have Lex E232. I use LaserJet 6L drivers for it. Works fabulously.

I actually still have the CD that came with the printer, I'm just not sure how to extract the appropriate files to ubuntu.  I'd be up for trying this HP driver option, but how do I determine what the compatible HP printer for a Lexmark 510 series is?

Oh, and is everybody clueless as I am about my thunderbird issue?  I'll do my dogonedest to search google for info in the mean time, but I'd really appreciate some help.  Thanks again guys!  Gotta love the ubuntu forums!

---

### Post by mmcmonster on 2007-11-29
As for [comical]("http://comical.sourceforge.net/"), unfortunately it is not easy to compile.  It does not have the standard ./configure file that most opensource packages have. :-(

Fortunately, someone already created a .deb package that is available [here]("http://tghc.org/packages.html").  Download it and double click on it, and it will download any accessory packages necessary for your system.  I'm using it on Gutsy right now. :-)

I would like to compile comical myself, but can't seem to get the right dependencies. :-(

---

### Post by candtalan on 2007-11-29
> **the_Ben said:**
> Wow guys, thanks for the quick, informative responses!  :D  I'll have to check most of these out when I get back to my linux laptop at home.  Just out of curiosity, how long did it take you seasoned veterans to get comfy with the terminal?  Ya know, back when you first started using it?

I guess I have always tried to avoid it mostly because I am not very accurate with typing. I got too used to gui clicking! I use it more now, and I am more careful with my typos.
I use rdiff-backup regularly as a cl command though.

---

### Post by nickdngr on 2007-11-30
I'm not at home so I can't check, but for comics I use Comix as opposed to Comical. I just checked under add programs for "comics" and ran across it. It works great for me.

---

### Post by Dedoimedo on 2007-11-30
> **the_Ben said:**
> I actually still have the CD that came with the printer, I'm just not sure how to extract the appropriate files to ubuntu.  I'd be up for trying this HP driver option, but how do I determine what the compatible HP printer for a Lexmark 510 series is?

Oh, and is everybody clueless as I am about my thunderbird issue?  I'll do my dogonedest to search google for info in the mean time, but I'd really appreciate some help.  Thanks again guys!  Gotta love the ubuntu forums!

Hello,
On the printer issue, try Google. That's what I did. Something along the line: "Lexmark 510 HP equivalent printer driver."
Good luck.
Dedoimedo

---

### Post by ubername on 2007-11-30
> **the_Ben said:**
> Wow guys, thanks for the quick, informative responses!  :D  I'll have to check most of these out when I get back to my linux laptop at home.  Just out of curiosity, how long did it take you seasoned veterans to get comfy with the terminal?  Ya know, back when you first started using it?



Sorry, that was kinda vague.  Here's the dealio: I go to the appropriate web page ([http://webmail.mozdev.org/]("http://webmail.mozdev.org/")), download the webmail extension to Desktop (I'm not sure if I need to put it anywhere else), then open up thunderbird and the "addons" menu.  I click "install addon", point to the file on my desktop, and click okay.  It starts to load it, but then stops and gives me the error message listed above.  I'm not having any problems with firefox addons, FYI.  Any ideas?

Sorry, I wrote this before I saw the above. It's for real newbies and doesn't address your particular problem but it might help:

Webmail:

In your browser (I use firefox so this is where the instructions are from) go to 

[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

right click on the webmail extension

[http://downloads.mozdev.org/webmail/web-mail-1-3-0.xpi](http://downloads.mozdev.org/webmail/web-mail-1-3-0.xpi)

or you could just right click on the link above.

Save it somewhere.

Open Thunderbird if it is not already open.

Go to Tools>Add-ons

In the bottom left of the panel there is (on my version of TB, 2.0.0.6) an 'install' button.

Click on this and navigate to your download (mine is webmail-1-3.0.xpi)

Click on the 'open' button.
A dialogue window should come up called 'Software Installation' showing web-mail-1-3-0
Wait a few seconds for the Install button to activate
Click on Install now,

Another window should open asking you to restat TB. Click on 'Restart Thunderbird'

Go and open Tools>Add-ons again. You should see Webmail there, however:
Here I had some problems. It took me three goes to restart TB to see Webmail. Post again if a few restarts don't work.

I use webmail for hotmail access so the next bit is about that. I can't speak for any other extensions.

Revisit [http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

Right click the hotmail extension or right click here:
[http://download.mozdev.org/webmail/hotmail-1-2-11.xpi](http://download.mozdev.org/webmail/hotmail-1-2-11.xpi)

Repeat the process above to install the extension and restart TB.
Go and open Tools>Add-ons again. In the Addons window click on webmail and click on the preferences button.
A window should appear showing three webmail servers
I set 
POP port to 1025
SMTP port to 2500
IMAP port to 1026
(i,e, in the dialogue box next to port for each server type in the number)
click 'close'

Next click the 'Webmail-Hotmail' extension. 
Click the preferences button
(I am assuming you have already added your hotmail account(s) in TB)
You should see a window with your hotmail account shown at the top. (if you have more than one account there is a drop-down which allows you to select an account.)
In the 'mode' panel first try 'Hotmail live (new website)
Click close.
close your add-ons window if it is still open.

From TB main window go to Edit>Account settings
Select your hotmail account(s) and click on 'server settings'
Change server name to 'localhost' and port to 1025
repeat for all Hotmail accounts.

Go to outgoing server (SMTP) in the TB Account settings window.
Set (or add) a SMTP server with server name 'localhost' and port 2500.

---

### Post by ubername on 2007-11-30
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
helped me.

---

### Post by the_Ben on 2007-11-30
Just to update you guys on my situation, I've got my printer working!  For any other owners of the Lexmark 510 series out there, I found all my answers on [this ubuntu forum]("http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer").  Still trying to work out the kinks with the Thunderbird webmail extension, but I gotta tell ya, getting that printer to work has given me new hope.  haha

As far as a comic reading program, what I have under "add/remove" is the GNOME comics organizer, and something called the Buoh online comics reader.  I'll try another web search to install Comix.

Next on the agenda (aside from the Thunderbird dealie) is getting my webcam to work.  Anybody have experience with the [Logitech QuickCam Deluxe for Notebooks]("http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/2988&cl=us,en")?  Thanks for all the help thus far, you guys are great!

---

### Post by the_Ben on 2007-12-12
Figured I'd just post again here rather than opening a new thread.  My latest issue is that after my crowning achievement of getting my Lexmark 510 series printer to work on Ubuntu (using someone else's work of course), my printer STOPPED WORKING!  Now, it was low on ink before it stopped working, and I dunno if there's some crazy default in Ubuntu that causes the printer to stop functioning when ink is low, but you'd think it would still print with crappy quality.

I've redone the process that made it work initially, but it's not doing the trick this time around.  Any idea how to repair this?  FYI, I used the method mentioned in the post above.

---

