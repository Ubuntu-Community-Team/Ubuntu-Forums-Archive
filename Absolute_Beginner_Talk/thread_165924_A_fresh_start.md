---
title: "A fresh start"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-04-25
If this is covered somewhere else, I truly apologize.  I did not find what I was looking for in my research elsewhere.  I also know that this is going to be longer than some like, but I thought you should know where I'm coming from and where I want to go to better help you in your answer(s). 

I did a dual boot install of Ubuntu because I had read that Linux was a faster, more stable, more secure OS, and because it's FREE!  I simply chose Ubuntu because in my reading, Ubuntu kept showing up in the top 2-3 of every list of the best of the Linux programs.  Since installing Ubuntu, I have so far not had an easy time.  Getting online was a task in itself.  (I only have one computer, so switching back and forth between Windows and Linux to learn/apply something was a pain.)  I then almost went cross-eyed reading 'help' and 'guides', and I (probably) incorrectly installed so many things that I screwed up the operation of my computer altogether .  I am committed to learning Ubuntu and will not quit trying.  I've always believed that when all else fails, start at the beginning.  I have reformatted my HDD and (again) done a dual boot install of Windows XP and Ubuntu 5.10.

I really am not very experienced in this sort of thing, so I'll humble myself, pull into a gas station, and ask directions.   What I NEED (at least initially) is for my children to be able to get online and use the Internet for research, download any text/graphics data, write reports, and save them in Windows format on a floppy/CD for use on schools' Windows machines.  Thus far, in Ubuntu, I have succeeded in connecting to my server and getting my printer to work.  I have not figured out how to copy docs in Office.Writer to my floppy/CD .  

If someone asked me how to set up a computer on Windows, my advice would be to format the HDD, install Windows, get connected to the server, go to Windows Update and install all downloads, install Spy Sweeper and Norton Internet Securities, go to the manufacturer websites of all your hardware and update all their drivers/patches, then install all of the applications they wanted to use (Office, Adobe Suite, etc).  As I said before, I'm not very experienced in this sort of thing, and maybe this advice isn't the best, but at least I know that these steps would provide me a functional machine that would take care of my aforementioned NEEDS.  In all of my reading, I have been unable to find this kind of help/advice to be applied in Ubuntu.  All of the help/advice I am finding seems to be focusing on trees and not the forest, so to speak. 

I would greatly appreciate someone giving me a sequence of actions/installations that I should perform to accomplish my goal, beginning with 'Should I update my Ubuntu version now, or wait?'.   If, while doing this, you could keep in mind that I am computer dysfunctional.  Here is what I mean: When I tried to download and install things in Ubuntu the first time, I could not even understand how to do things like “download to the *desktop*, open it, and from the *command line* type '****'”  I somehow managed to get the program to show up on the desk top, but Ubuntu and I did a lot of head butting from there.  I never did get my floppy to show up in Office.Writer (I did make it stop working altogether until I reformatted).

I know I'm asking a lot, but from what I've read so far, there are a lot of people in here who truly want to help others to learn.  Again, I apologize for this being so long.  I only wanted to be thorough.

---

### Post by delta32 on 2006-04-25
> **Guns90]'Should I update my Ubuntu version now, or wait?'.[/QUOTE]
It's optional, but it's best to run with the latest updates. It's pretty simple with the Synaptic program (System > Administration > Synaptic Package Manager).

[QUOTE=Guns90]When I tried to download and install things in Ubuntu the first time, I could not even understand how to do things like &#8220 said:**
> 
I try not to use command line when extracting something (unless I'm following instructions). I find it much easier to right-click on the file and click "Extract here". It's in Ubuntu by default.

[QUOTE=Guns90]I never did get my floppy to show up in Office.Writer (I did make it stop working altogether until I reformatted).
Is the floppy formatted? Is the floppy drive mounted? I don't think the floppy mounts itself by default. Try using "mount /media/floppy0" (or Places > Computers > Right-click "Floppy Drive" > Mount Volume)  next time you need to use your floppy.

Hope this answers some of your questions. :)

---

### Post by ncappel1 on 2006-04-25
I have trouble with my essays and papers too. I use ubuntu and have no printer (it's a hassle at college) but the problem is that the computers in the labs here only run windows and OSx. loading the files on these non linux computers, the formatting gets corrupted and messed up, even when I save to .doc in abiword and open office. I've tried saving files in rich text format, and even just plain text, but it's always a big hassle because the rich text and regular text doesn't have the formatting and options I need, often times. 

I find that the best solution is just to save two copies, one in rich text (or regular text) and another as PDF. The pdf is universal, and if for some reason I need to edit it at school, I can do that with the text documents.  

I also talked to the manager of the tech labs here at school and had a nice conversation about open source software. I presented him with my problem, and (him being a linux user) was very receptive. I tried to be polite, and the way the conversation ended was that he said he would try to install abiword on the computers in the various labs for this upcoming semester. It doesn't cost the school any money, and also encourages open source! it's great.

The other option I have used is to bring around a flash drive with a copy of abiword on it. it's a fairly small program, so it's easy to just unload and install in a jiffy, should a computer at school not have it, or I am not finished and not saved to pdf. I am able to save a copy of it on my personal space provided by the school too, in this way I have the installers for mac and windows ready whereever I am!

---

### Post by Guns90 on 2006-04-26
delta32

I just tried your suggestions.  When I right-click on the floppy icon in Places > Computers > Right-click "Floppy Drive I get....
'Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount'

When I input at the command line 'mount media/floppy0',  it get the response 'mount: I could not determine the filesystem type, and none was specified'.

---

### Post by Guns90 on 2006-04-26
ncappel1,

I appreciate your response; however, you didn't instill a lot of optimism in me.  If I don't make this a user-friendly system for my kids, it simply won't be practical for me to continue using this distro (let alone the continual barrage of complaints I would have to endure).  If I can't show them that they can use OpenOffice to do their schoolwork AND be able to take it to school and use it on the school's Windows machines, I might as well try another distro to see if I can make it happen there.  I'll wait to see if anyone else responds with suggestions.

---

### Post by confused57 on 2006-04-26
I see your dilemma, I tried to copy an OpenOffice file to floppy(had never done so) and couldn't figure out any way possible.  Found a thread, which suggested that the command line was the only way to save to floppy in Ubuntu(not newbie user friendly):

[url]http://www.ubuntuforums.org/showthread.php?t=93139&highlight=save+flop
py[/url]

For installing programs:

[http://www.ubuntuforums.org/showthread.php?t=165320](http://www.ubuntuforums.org/showthread.php?t=165320)

---

### Post by confused57 on 2006-04-26
Ok, I have the book "Beginning Ubuntu Linux From Novice to Professional" and was able to use it to figure out how to copy files to floppy without using the command line.

1.)Format the floppy(use FAT if sharing with Windows) by Applications--System Tools--Floppy Formater

2.)Click on Places--Computer,  then double-click floppy icon,  this will mount the floppy drive and place an icon on the desktop.  Then just drag and drop the file you want copied onto the desktop icon.  I just did it with the OpenOffice file that I created earlier and it worked.

3.) When you're finished, right click on the desktop floppy icon, unmount(icon will disappear), eject floppy.

I believe this book will be pretty useful in using Ubuntu...

---

### Post by macdo on 2006-04-26
You should always run an up-to-date system. However, as you describe yourself as 'computer dysfunctional', I suggest that you don't upgrade to Dapper Beta, if that is what you were asking. Wait for the June release.
Ubuntu is different from Windows in that all the programs you're likely to need are stored on the web in the same place (called repositories). So all you have to do to make sure your system is up-to-date is run synaptic, (System>Administration>Synaptic Package Manager). You'll probably want to enable the "universe" and "multiverse" repositories, which contain more applications that are not included in the basic Ubuntu: chose "Settings>Repositories>Add". Tick Universe and Multiverse for all three options of the drop-down box. When you click on OK, the program will give you the option of reloading the package index. Say yes to that. (You can also update the index by clicking on the reload button, of course). Then click on "Mark All Available Upgrades". 
Synaptic allows you to install new programmes by searching for them: for example, if you wanted to install clipart for OpenOffice.org, you would choose search, and type either "OpenOffice.Org" or "clipart". A list of files comes up, and you just click on the appropriate one and select "install". 

In Ubuntu, you don't really need an anti-virus, as Linux is pretty virus-proof (because you need root access to install anything, virii can't install themselves). However, if you want an anti-virus, then Clamav is probably what you want. The firewall that I find easiest is called Firestarter, a good idea if you are directly connected to the net.

Ubuntu often has a lot of alternative applications to do the same thing - so if you don't like something, there's often a different way of doing things. For example, to read PDFs, I use evince, put I could also use Xpdf or gpdf. - and that's just in Gnome! (To make PDF files, of course, you either "export as PDF" in OOo, or choose "Print", "Create a PDF document": no need for Acrobat.)

There! I hope that addresses some of your concerns! Have fun with Ubuntu!
Don't hesitate to ask more questions, either.

---

### Post by Guns90 on 2006-04-26
Well Guys, this is starting to come together for me.  

Macdo, thank you for that insight.  Very informative.  I now feel like I'm a lot closer to where I want to be.  

Confused57, that did the trick!  I have been saving in various formats , copying to floppy, opening it windows, working with it, saving it, and opening up back in Ubuntu.  It works!  I also discovered that process works on the CD/DVD.  On my own searching and reading, I found Automatix and installed it.  That's a big help.  

Thanks again Guys

---

### Post by Guns90 on 2006-04-26
Another question if you don't mind...

I just went to WineHQ and downloaded the Ubuntu version.  When I went to install it using Synaptic as they instructed, I got a WARNING window telling me that "the package was NOT AUTHENTICATED and that installing it could allow a maliciuos person into my computer and hurt my computer".  I'd appreciate a little advice on this matter.  Thanks

---

### Post by delta32 on 2006-04-26
It's just a warning to make sure you know it's not coming from the official repositories. If you know and trust where you are getting the file from, it's ok to hit apply and get it program.

---

