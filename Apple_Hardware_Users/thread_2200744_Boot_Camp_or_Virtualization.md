---
title: "Boot Camp or Virtualization?"
date: 2014-01-20
forum: Apple Hardware Users
---

### Post by shearer4 on 2014-01-20
Here's my set up and resources:
1. 1 MacPro late 2006, Dual XEON 2.66; 
2. 3 Sata disk drives;  250, 500 and 1Terra, plus a couple external FW hard drives and one USB hard drive. 
3. 16 Gigs of Ram on board
4. NVIDIA GT 2300, 256 Mb Vid/Ram
5. OS X 10.7.5 -  Right or wrong, this machine will not run Mavericks or even Mountain Lion.  Architecture is supposedly to blame? 
6. I have Parallels 6 and Windows Vista on this machine for work/business related stuff. It works fine. I have the Windows VM on a separate volume.  I won't need this much longer and will archive all the files. It's really just an accounting issue. 
7.  I use this Mac OS for some important stuff, but it's all backed up on externals plus DropBox holds the really important stuff. Plus I have MacBookPro I can look back to running DevonThinkPro via Dropbox which is where all the REALLY important stuff is. 

So; Yes, I have a lot of resources.  Why am I installing Unix?  Because I'm recently retired, in good shape and have been interested in computers since DOS.  So, this is something new to learn to keep the brain active and working. Hey; it's free!  Lumosity costs $10/month!  

Question;  should I Dual Boot (BootCamp) into either Mac OS or Unix? i.e. Ubuntu.  Means; moving my main/home drive to another volume, I think?  I use CCC to clone my current Macintosh Disk to another volume. So, not at all difficult. I can and have booted from this drive. 

Should I continue to use Vbox?  It works. I have Ubuntu 12LTs on it and it works fine, if a little sluggish.  I also have Mint 16 on it, which is much quicker but, of course lighter with less functionality. 

I'm spoiled!  My MacPro although not capable of running the latest Mac OS, is stupendously faster than my 2010 Mac Book and my work provided Lenovo Thinkpad, by A LOT.  I am so used to sitting down at the Pro and getting just immediate reactions to inputs.  Maybe I need to slow down? 

Or, maybe I can install Unix directly on my Mac Pro with all those resources and have at it?  

What do you think?  All advice welcome.   I have googled until my eyes dried out. There's a lot of advice out there. 

What do you think, based on experiences if possible? 

AS

---

### Post by baabsaget on 2014-01-21
I would dual boot. (what you call boot camp)
On my macbook pro, the procedure basically went like:

1. Install rEFInd
2. Make space for the ubuntu install by partitioning 
3. make an ubuntu live USB with unetbootin
4. Install Ubuntu in EFI mode OR install ubuntu in legay mode
5. Install all necessary drivers

I can post detailed instructions if you'd like.

By the way, OS X is actually closer to UNIX than Ubuntu is.

---

### Post by shearer4 on 2014-01-21
[QUOTE][COLOR=#000000]By the way, OS X is actually closer to UNIX than Ubuntu is.[/COLOR]/QUOTE]

Yes and no.  I recognize the OSX is built on Unix, but there are differences. For me, the importance of my data on my OSX User Folders is beyond description (hackers take note).   So, I am trying to do everything I can to keep and other instances of Unix separate, and on different volumes. I just want to experiment and learn.  Learning Unix on OSX is like abide with training wheels. Running Ubuntu, Mint and possible others is a new experience. That's really all there is to this.  

So;  you recommend that I use Boot Camp, Apple's assistant program for setting up a dual boot system on a single volume.  Or IOW you have had good experience with dual booting into OSX and Ubuntu on a macbook?  

That's good to know.  I had a lot of trouble with burning either DVDs or a USB stick and ending up with a bootable Ubuntu .iso disk?  Not sure what has caused this, but I will look at unetbootin, if I have that right?   Thanks for your help.  Very good!

---

### Post by 1clue on 2014-01-21
I recommend VMs.  That way you get to use as many operating systems as you want or have room for all at the same time, and you can copy/paste between.

Using multiple boot, you have to save whatever you're doing (related to the current project or not), shut down, boot the other OS, open the file (hopefully file formats are compatible enough) and do whatever you were going to do with it, save it, shut down, boot back to the original OS, open the file again, try it out to see if it works, lather, rise, repeat if necessary.  Or, just copy/paste.

You have plenty of room for a couple VMs.  Parallels works nicely for Mac, you can also use VMware and maybe a few others.

Regarding Mac OS X being closer to UNIX than ubuntu:  Yes and yes.  Mac OS is a fully licensed UNIX.  Meaning it inherits at least some source code from the original.  Linux is supposedly completely rewritten, although some FreeBSD code is in there and there was a legal tussle over that a few years ago.

That said, Mac OS X runs a whole lot of Open Source software, and if you put XQuartz on you can use the GUI stuff too.

I understand and respect what you're saying about segregation of your OSX data, but let's try to be correct here.  Starting off calling Linux UNIX is going to become the main point of any thread you make that correlation in.  It's legally, technically and philosophically incorrect, where calling your Mac UNIX is completely correct.

You could say UN*X and people will get it.  That's common practice as a reference to UNIX-like operating systems and would be correct in your context too.

---

### Post by shearer4 on 2014-01-22
Thank you for all this background and the recommendations.  I am guilty of not fully understanding the difference between talking about UNIX and Linux. I knew there were differences in both licensing and code, but was not aware of how sharp a line that could be. Now I know. Thanks. What I was trying to say was, Apple had so successfully developed OSX GUI to the point where one could easily forget there is even a terminal. And, for most folks, that's the whole point.  In the little bit of experimenting I have done with Ubuntu I see that learning some commands and running certain things on the command line is more efficient. 

After reading your post and some experiences others have had and also going a lot of searching and tweaking, I've decided the best way to go is what I have set up now that is, using VirtualBox and running VMs.  I've been able to get Ubuntu 12.04.3 /64 running pretty nicely on my system in VBox. 

I have Parallels 6, but it doesn't seem to play well with Ubuntu, especially when it comes to installing Parallels tools. But, that's another thread for some other time. 

Thanks again. I've learned quite a bit from your response.

---

### Post by 1clue on 2014-01-22
Also, a whole lot of Open Source software runs on OS X.  You'll want to install XQuartz if you don't already have it, (the easiest X server install you'll ever do, pretty much zero configuration) and you might want to get homebrew for mac.  Which is a package manager of sorts, to get a lot of open source stuff on your system.  You'll want to read the web page so you understand what you're getting.

Most Mac users don't know about Terminal.  It doesn't show up in their app list, most of them don't look in the utilities folder, and they have no idea why anyone would want to type anything into a terminal when they can click.  That's fine.  But FWIW if Mac OS X wasn't UNIX underneath I wouldn't be running it.

---

### Post by shearer4 on 2014-01-22
I am looking at it right now. Not sure where to get Hombrew, but I will figure that out. I know I had it as part of playing with Ruby awhile back.   Should be able to do 

sudo -apt get homebrew         Right? 

Thanks. 

AS

---

### Post by 1clue on 2014-01-22
[https://github.com/Homebrew/homebrew](https://github.com/Homebrew/homebrew)

It's not on Linux, it's on Mac.  Read the docs to get it installed, once you do it's like apt-get for the mac.

It's also not so selective as apt-get, you sort of get a bunch of stuff by default.

---

### Post by shearer4 on 2014-01-22
Ok.  I got Quartz, Xtools and Homebrew by searching the web.  Things did not all go well, but no problems.  I get an error message or two, so kept working on those. Finally, I believe I got the latest version of XTools command line tools I can run. Remember I'm stuck in 10.7.5 due to my processor and bus. 

So; now I have Quartz, X11 Command line.  What to do now?  I've read as much as I can.  Need to go to sleep now, but will check back email in the morning for Ubuntu posts.   

This is cool.  Thanks again.

---

### Post by 1clue on 2014-01-22
OK so now you can:

[LIST=1]
[*]**ssh -X <your_linux_box>** and then run X apps like firefox or synaptic using your mac as a workstation.
[*]**gimp** on your Mac (assuming you installed it) and get gimp running on your mac.
[/LIST]

You also have a lot of Open Source linux commands, and you can install more.

So XQuartz is the xorg server for Mac OS.  For X, client and server are sort of backwards from what you would think.  The server is where you sit and type, and the client is the app you're running, which could be on your local computer or somewhere else.

XTools is X-related tools.

Homebrew is a bunch of tools that you would use if you were on Linux, and which you might find handy on your mac.

So what we did is expand your Mac's brain a little bit and allowed it to run some of the things you're running on Linux.  I've been using this stuff for years now, it doesn't hurt the rest of your OS.

---

### Post by shearer4 on 2014-01-23
Not sure I understand much of this, but I will start doing some reading.  I was just playing with X11 Terminal and got the manual open, but I need to focus and read, experiment etc. 

Thanks very much again.

---

### Post by 1clue on 2014-01-23
Do you understand what cygwin is for Windows?

homebrew is pretty much the same thing for Mac.

The things I recommended (and that you installed) accomplish 2 things:
[LIST=1]
[*]They facilitate connecting to Linux in a more Linux-friendly way.
[*]They let you put some of the tools you'll learn about from Linux onto your Mac.
[/LIST]

If you take away the GUI, Linux and Mac are pretty close to each other.  There are big chunks where Apple uses their own thing, but if you look at the terminal there's a LOT in common.  Homebrew brings them closer together still.  It doesn't change anything Mac-specific, it only adds tools you might become familiar with in Linux.  And it's easy to remove if you don't like it, you just throw the directory in the trash.

This is typical with Commercial UNIX.  It's pretty common for them to have their own windowing system, their own authentication, whatever.  And typically on UNIX the 'non-free' version of the app has fewer options and is less usable than the Open Source version.  Which is why you get homebrew.

---

### Post by shearer4 on 2014-01-23
I don't know Windows very well and don't know what cygwin is.  

I do think I am getting somewhere getting this installed. As you know, recent Mac's have locked the User out of a lot of things. So, it's hard to find hidden files or any file that is at the root level.  

Somehow, I ended up with folders:   Macintosh Disk/Applications/quartz-wm-1.3.1/quartz-wm-1.3.1/ < and in that second iteration are the files configure install-sh depcomp and so on.  

I read the install read me and followed those instructions; which said to run  ./configure _then_  make _then_ make install _finale_ make clean.   All of this ran very fast without any error messages that I saw anyway.   

So, now I think it may be a problem that these files are buried too  many layers in the file structure. But, maybe not?  Anyway;  not that I understand this, but if open a Terminal and type homebrew,  I get a -bash: command not found.  There is no homebrew file or directory that I can find with Spotlight.  I thought I installed it last night, but maybe not.  

So;  now I'm just trying to figure, what next? Sorry to monopolize your time. I really am just learning something I have never worked with before.

---

### Post by shearer4 on 2014-01-23
Oops.  I'm starting to see. I have Ruby on here. I did not know that.  Wouldn't Ruby be run to use homebrew?

---

### Post by 1clue on 2014-01-23
Ruby is a scripting language, the same way perl and bash are scripting languages.  It's probably used by homebrew (and almost certainly installed by homebrew), although I didn't pay that much attention to it.

---

### Post by shearer4 on 2014-01-23
Right, okay.  So, I need to read and experiment and see what I've got here now. I just hope I have sprayed files all over my drive without any useable result. But, we'll see?

---

### Post by 1clue on 2014-01-23
All over your hard drive?  No.

All the files go to /usr/local/Cellar, and then are symbolically linked to /usr/local directories.

Easy and clean uninstall if you don't like it.  Read the docs, the more you read the more you realize how unintrusive this is.

---

### Post by shearer4 on 2014-01-23
[QUOTE][COLOR=#000000]All over your hard drive? No.[/COLOR]

[COLOR=#000000]All the files go to /usr/local/Cellar, and then are symbolically linked to /usr/local directories.[/COLOR]

[COLOR=#000000]Easy and clean uninstall if you don't like it. Read the docs, the more you read the more you realize how unintrusive this is.[/COLOR]/QUOTE]

No what I meant was since the files went into this strange path once I extracted. i.e. Mac/Applications/quartz-wm/quartz-wm/pkg-config/*files   It's not an elegant installation on my part. I can't seem to find /usr/local/Cellar  probably hidden by Mac OS?  

I'll read up.

---

### Post by 1clue on 2014-01-23
That strange path is extremely Mac-like.  XQuartz was written by Apple Computer.  Every Mac app goes to a folder like that.

Try opening Terminal and:

```

cd /usr/local
ls -al
ls -al Cellar
ls -al bin

```

Type those one at a time, you'll see what sort of thing happens with homebrew.

With Finder you don't see half the stuff on your drive.  I use Path Finder which, in spite of a huge bug that crippled me for a month, is still well worth the money.  If you're feeling stingy for now you can do it with Terminal.

For the record, Terminal seems pretty tame at first but it's actually a really good terminal.  It has a lot of configuration options, lets you define window groups and all sorts of interesting stuff.  It also works well with command-line full screen apps like vim and screen.  Another Apple product, comes on your Mac.  I might be a bit old school, but the more I use Terminal the more I like my Mac.  There really is a UNIX under there, it just has really really REALLY good fonts.  Which traditionally speaking would make it not very UNIX-like.

---

### Post by shearer4 on 2014-01-23
Great minds? A few minutes ago, I remembered I could list hidden files with the right argument in terminal command. I saw user/local 

Here I was able to run brew commands as instructed in the reading , i.e. brew doctor  and another, which I can't remember now. I'm at another computer now on a consulting thing.  Waiting, always waiting for someone else.  

I got an error message as such:  Warning: unexpected .pc  file found in pkconfig.  File; fuse.pc may cause problems and might have to be deleted?  Not sure. I think that may be the Fuse preference pane, which i have never really taken time to understand and not sure where it came from MacFuse?  

Anyway; you must be some kind of expert in this area?  I am very intrigued by this experience.  Again, who knows what I will do with it if anything. Sent you a Friend request. I have no idea if that's cool or not on this forum. Some are, some are just part of the platform and nobody uses it.  Again, I hate to take up so much of your time, but I guess if you were bothered, you would just not respond.  

I don't think the Terminal is lame. I'm still at that stage where I'm a little frightened of it. Which is probably wise.  There really is, as you said a UNIX under there. For a while I used DOS on an old PC long ago. I remember things like Norton Commander, which in hindsight were REALLY ugly but worked. Went through a few phases on Windows and got more and more frustrated. I finally bought my first Mac when it was still running Classic.  Since I am the resident computer problem solver in our household, both of my grown kids, my wife, my son-in-law and brother-in-law all have Macs after too many crashes and freezes and such with Windows.  Anyway;  more later.  I have to answer this dumb email.

---

### Post by shearer4 on 2014-01-23
> 
[LIST=1]
[*]**ssh -X <your_linux_box>** and then run X apps like firefox or synaptic using your mac as a workstation.
[*]**gimp** on your Mac (assuming you installed it) and get gimp running on your mac.
[/LIST]


This did not work out for me?  I do have my Vbox installations on a separate volume.  This is what I got

Alan-Shearers-Mac-Pro-2:~ alanshearer1$ ssh -X /Volumes/Tera_Drive/VirtualBox\ VMs/Ubuntu/Ubuntu.vdi 
ssh: Could not resolve hostname /Volumes/Tera_Drive/VirtualBox VMs/Ubuntu/Ubuntu.vdi: nodename nor servname provided, or not known
Alan-Shearers-Mac-Pro-2:~ alanshearer1$ ssh -X/Volumes/Tera_Drive/VirtualBox\ VMs/Ubuntu/Ubuntu.vbox 
ssh: illegal option -- /
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]

---

### Post by 1clue on 2014-01-23
brew update and brew doctor.

brew update pulls in the latest changes.

brew doctor tells you of potential problems and generally how to fix them.  You may need to google your particular problem.  'homebrew mac <message>'.

UNDERSTAND WHAT YOU'RE DOING before you do it.  I know that sounds impossible when you don't know the commands, but you need to look things over and try to make sure it's not doing something malicious.

**It's extremely bad to copy and paste from some web page into a terminal**.  Copy and paste into a text editor, make sure the code looks the same and then (possibly) save the script and execute it.

I don't think of myself as an expert.  I'm a user of homebrew, mostly indirectly.  I'm a software developer and some of my tools either require or are augmented by the stuff in homebrew.

As well, when I started using Linux, things were a lot different.  Xfree86 was out there but not stable, so most Linux boxes didn't have it.  Linux was bought from a bookstore with a magazine and a bunch of floppies, and then you used your 2400 (or 9600 if you were lucky) baud modem to get updates, and hope nobody called you.  It was a weekend project.

I guess the point of that is that the Linux command line is the native environment for me, I use a GUI but I ALWAYS have a terminal or 5 open.

Macs also have a disabled root user.  So you use **sudo *<command>* **to execute privileged commands.  So it's the same as Ubuntu that way.

---

### Post by shearer4 on 2014-01-23
> [B]It's extremely bad to copy and paste from some web page into a terminal. Copy and paste into a text editor, make sure the code looks the same and then (possibly) save the script and execute it.
[/B]
Understood.  That's not it.  The commands showed up in the terminal output. In other words:  run;  brew doctor etc..  

If you're a software developer you must be an expert in this general area.  So, again thanks.  

I sure remember the dial up modem days and when there was a way you could make your phone busy instead of get knocked off the connection, that was like a miracle!  Hah. 

Made some more progress before dinner. So, I am working my way.   Thanks again very much.

---

### Post by 1clue on 2014-01-23
I missed a post.

ssh -X <your linux box> means the IP address of your linux box.

ssh -X 192.168.1.45

Your command line doesn't know that your Linux box is a virtual machine.  It's a network command like telnet.

---

### Post by shearer4 on 2014-01-23
Right.  I tried to use a path, which seemed to make sense but now that you point it out, no.  Thanks.

---

