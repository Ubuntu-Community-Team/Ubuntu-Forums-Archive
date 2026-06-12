---
title: "Running Agent email/newsreader under Wine"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-04-13
I am trying to run a Windows program under Linux using Wine. Nothing is available that will satisfy my wife for an email/newsreader program other than Agent, produced by Forte Inc. It is also light years ahead of most programs, though I would settle for less, like Thunderbird. But if I'm going to have a Linux installation that's convenient, getting Agent to run under Wine is a must. I don't want to spend money on a commercial Windows emulator. 

I have Wine installed, and once I saw the program open momentarily.

Agent works fine under Windows. Wine complains that it needs Agent.XRS, which it tells me should be int he same directory as Agent.EXE, the Windows executable. 

Guess what? It is there, in the same directory.

I was hoping to have this working and be asking how to set up something to open Agent automatically, without having to burrow down a few directories and right click on the executable, then tell it to open with Wine, which is what I've been doing. BUt I haven't got it running yet, so I need to tackle that first.

Any suggestions? 

Agent is not on the list of programs on the Wine web site "how to" section. It does run under Wine, according to the company that produces it, but they don't support it.

Donald

---

### Post by Patrick K on 2007-04-13
I couldn't tell from your post. Did you install Agent into wine or are you trying to run it from the windows install?

---

### Post by t2000kw on 2007-04-13
> **Patrick K said:**
> I couldn't tell from your post. Did you install Agent into wine or are you trying to run it from the windows install?

I didn't know you could install a Windows program "into" Wine. I installed it into Windows on a Windows partition. Getting to it is not a problem. I can see it and the file it says it needs to use with the Windows executable file, both in the same directory.

If it can be installed into Wine somehow on a Linux partition, that would possibly be acceptable. What I liked about running it on a Windows partition was that it could be accessed from WIndows and everything would be up to date, there wouldn't be two places where email is kept. 

Don

---

### Post by qpieus on 2007-04-13
It sounds like you are trying to directly run the windows-installed agent.exe file. As Patrick K implies, you need to actually install agent using wine. Open up a terminal and navigate to wherever your agent installation .exe file is located. Then type "wine agentenu410-1088.exe" (without quotes and substituting the install file's name). After you do that you should see the installation dialog display. The installation should then progress just like it does under windows. After installation you should be able to launch the program by typing wine agent.exe in whatever directory agent installed to. You may need to set up a menu item to launch from menu (I use kubuntu and whatever I install via wine automagically gets added to the menu - don't know if gnome does this too).

I'm not sure if wine can do the installation to a windows partition, but I don't see why it couldn't. I'm also not sure if once it's installed if both your windows boot and the linux boot could both run the same files. Doesn't hurt to try though!

Good luck and please report back your progress. I also run Agent (v4.1),  but I use crossover office 5 to run it (works perfectly by the way).

---

### Post by t2000kw on 2007-04-13
Well, I got it to install and run, sort of. I can't get mail to retrieve. 

Now I can't seem to find it to run it again after I closed it. 

I did try to run it as a command line argument:

 wine agent

But I don't think it works that way. It does look like it will work. 

I'll get the hang of this eventually, but I need to figure out where it installed it and how to get a shortcut to it.

The fonts are all tiny, even after changing them. I don't know if my wife will be able to use it. I'll keep playing with it, though, once I can find out where it went. 

I'd like to know more about crossover office, your personal thoughts, if it works with the Windows partition or things get installed again in Linux somewhere, etc. I've read a bit about it but advertising is always positive. I want to get Wine to work first. If it looks like we're headed to using Linux, I'll investigate that program/platform next. 

Some of the error(s) during installation in terminal:

err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
fixme:ras:RasEnumConnectionsA (0x1b67aa8,0x34dc60,0x34dc80),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!

---

### Post by t2000kw on 2007-04-13
Is there a "file finder" application somewhere in Linux?

BTW, I'm not running KDE or Gnome. I'm using that "light" version Xfce desktop environment. I prefer KDE, as it is more like what I use at work and am accustomed to at home (Windows 98 or XP). 

I honestly don't think that Linux will overtake Windows in the next year or two, but with IBM getting involved, it might not be much longer. And I'm tired of cleaning out my Windows directory, doing a fresh install every 6 to 12 months (sometimes it lasts a couple years!), then reinstalling all of my applications. 

I do want to give it a good try this time. I was on the first beta test group of Xandros and thought it was OK but things have gotten a lot better and installations are pretty easy. It's the customization that's more involved. But I want to pursue this and see what happens.

---

### Post by qpieus on 2007-04-13
The installed files, including the agent.exe file, are in a hidden directory (.wine) in your home directory. For example the path to my agent installation is

/home/username/.wine/drive_c/Program Files/Agent

So to launch agent I would type in a terminal (or make a launcher):

wine /home/randy/.wine/drive_c/Program Files/Agent/agent.exe

I tried it out after my last post and I had some trouble too. When I run the exe I get an error about a shared folder not being available, or something like that. If I launch the exe using crossover however, then I get no error and it loads properly and works well, including retrieving headers and messages. It may be that v4.1 is pretty recent and it won't work right with wine (yet - wine is rev'd often so it may work OK in the future).

What version of agent are you using?
I'm curious now, I'm gonna try out an older version of agent and see if wine can handle it.

---

### Post by qpieus on 2007-04-13
I installed v 3.3 via wine and it seems to work correctly - connects to server, retrieves messages, etc. All the fonts look fine by the way, I'm not sure why yours don't.

I was able to get v 4.1 running (I didn't do anything as far as I can tell!) and it will connect and download messages, but when I exit it, I get a memory violation error or something like that. So It looks like the newer versions don't play nice with wine yet. 
If v3.3 is acceptable to you, then this may work OK for you.

As far as crossover office goes, I recommend it. It's running agent v4.1 perfectly. I have not installed v4.2 though, so I cannot vouch for that. Crossover costs $40 US. I just looked at their website and it looks like you can download a trial and try it out free for a while.

---

### Post by t2000kw on 2007-04-13
The latest build that I am aware of. I was in the beta test of 4.x. 

I think it's build 1088

---

### Post by t2000kw on 2007-04-13
I'll have to check and see if 3.x has multiple accounts. That would be needed since we couldn't have multiple instances of Agent.

The program did seem to work and tried to download messages. I should have checked the network settings. It might have tried to do a dial-up.

---

### Post by t2000kw on 2007-04-13
> **qpieus said:**
> The installed files, including the agent.exe file, are in a hidden directory (.wine) in your home directory. For example the path to my agent installation is

/home/username/.wine/drive_c/Program Files/Agent

So to launch agent I would type in a terminal (or make a launcher):

wine /home/randy/.wine/drive_c/Program Files/Agent/agent.exe

I "unhid" directories and files and dug down to /home/donald/.wine/drive_c/Program Files and there is only a "common files" folder. It's empty.

---

### Post by t2000kw on 2007-04-13
> **t2000kw said:**
> I'll have to check and see if 3.x has multiple accounts. That would be needed since we couldn't have multiple instances of Agent.

The program did seem to work and tried to download messages. I should have checked the network settings. It might have tried to do a dial-up.

Except I can't check it until I can find it.  ;-)

---

### Post by Patrick K on 2007-04-13
Just a hint for when you get it working satisfactorily. You can select the directory where Agent stories it's data files. That means, you can set it to the same directory Agent uses in Windows. The same data will be available to both the Windows installed version and the Linux (wine) installed version.  In the early versions I have (1.5, 1.9, 2.0) this is done in the configuration file. It really quite easy and is well documented in the help files. Your version might be different.

Oops, I should mention this is with FAT32. This may be problematic with NTFS, I don't know how wine gets along with NTFS. I don't know much at all about NTFS, having never used it (and likely never will).


If you installed Agent with the default location, it should be in the ./wine/drive_c/Program Files folder. Perhaps you selected to install in a different location. In a term window type "locate agent.exe". Try it with a uppercase A, too (Linux is case sensitive)

---

### Post by t2000kw on 2007-04-13
> **Patrick K said:**
> If you installed Agent with the default location, it should be in the ./wine/drive_c/Program Files folder. Perhaps you selected to install in a different location. In a term window type "locate agent.exe". Try it with a uppercase A, too (Linux is case sensitive)

I installed it in the default location and didn't pay attention, except that it appeared to be putting it on C drive, but that was probably under Wine.

---

### Post by qpieus on 2007-04-14
That's right, when the installation says it's installing to drive c it's referring to the fake drive c agent folder which is at /.wine/drive_c/Program Files/Agent.

You could make multiple instances of agent by the way. Just run the installation a second time and select a different installation directory. The entire program will be installed again separately.

---

### Post by t2000kw on 2007-04-14
Is there a way to find where Agent went to and then make a shortcut (or whatever it's called in Linux) to it?

---

### Post by qpieus on 2007-04-14
> **Patrick K said:**
> In a term window type "locate agent.exe". Try it with a uppercase A, too (Linux is case sensitive)
Try Patrick K's suggestion (I'm not on my linux pc right now so I can't try that out). If no luck with that, just try another installation and make note of where it installs to. It should be in the .wine directory somewhere.....

---

### Post by t2000kw on 2007-04-14
Sorry, Patrick, I somehow missed your suggestion. I'm getting email on two different systems and somehow missed the link in an email to your "locate" suggestion. Maybe I thought it was one I already read and didn't send it to the other computer. One system deletes email on the server. This Linux one leaves email on the server so I can get a redundant copy on the other machine if I read it here first. I'll try to be more careful. 

The locate function worked. I had found a wine directory before, but there's another one under the root folder. 

Once I found out where the file is at, I tried to type Wine /root/.wine/drive_c/Program Files/Agent/agent.exe but that didn't work. Neither did clicking on the file in file manager and choosing "open with wine." I get an error, something about unable to open agent.ini or something similar. It did open the first time when I installed it, and it accepted the reg code, so that shouldn't be the real issue. It's probably the way I'm trying to open it. 

Next step is to figure out how to get it to run, then to make a shortcut. In fact, there is another program I would like a shortcut on the desktop, if possible, and that is the Thunderbird email program. But that may not be necessary if I can get Agent to run properly.

I'm not in a real hurry, but if I don't' get this fixed soon I will have to re-do my Windows directory and reinstall all of my Windows apps right away. I will have to do that eventually anyway, but once I start on that, I'll probably have to give up on this for a while.  

Thanks everyone for your help so far!!!

Donald

---

### Post by Patrick K on 2007-04-14
There shouldn't be a .wine folder in root's folder. At least, I don't have one. Only the one in my /home folder. 

You may need to run Agent as root since it is in Root's folder. This is not good. Particularly since it will have ports open and your system could be compromised. 

I'm not sure how to fix this situation. What I would do is uninstall Agent using the wine uninstaller (in a terminal "wine uninstaller"). I think I'd also uninstall wine (in Synaptic search for wine, right click, select complete removal) and start over. You really don't want to run wine or any of its apps as root. Somehow you installed wine incorrectly.

---

### Post by t2000kw on 2007-04-14
Well, I just accepted the default installation folders.

Now, if it's not supposed to be there, how do I uninstall it?  And how to install it "correctly" if the default folders don't work?

Too bad it's not as simple as dumping everything into one directory and running it fromt here. This is one of those programs that you can actually do that in Windows, without needing the registry entries.

---

### Post by Patrick K on 2007-04-14
It's been ages since I installed Agent. You might try moving the Agent install from the root wine folder to your /home/.wine folder. It might work, if there are no registry entries. Put it in "Program Files\agent" under the drive_c folder in your home folder. 

My wine install defaulted to ~/home not /root/.wine. I haven't any idea how it installed to root. But I don't really know that much about wine or Ubuntu. Still learning. 

I'd try moving it. Then type "wine "c:\\Program Files\\agent\\agent"" (note the quotes around the path) in a term window. Who knows, it might work.

---

### Post by qpieus on 2007-04-14
Were you logged in as root when you installed agent? That would explain why agent got installed to /root. Anyway, I say start over. Delete the  /root/.wine directory, you want agent installed for you, not root. Delete any /.wine directory in your home also (unless you have other stuff there you installed using wine).

Let's check what version of wine you are using. I don't know how to do this from the command line, but the package manager can tell you. Mine says I'm using 0.9.34, which I think is the latest (I added the wine repository to my sources.list file).

Make sure you are logged in as you, not root, then in a terminal navigate to wherever your agent install file is and type wine followed by the install file's name. Since you are logged in as you, wine should install to your home/.wine directory. Then you should be able to launch agent by typing in a terminal wine /home/username/.wine/drive_c/Program Files/Agent  (assuming the installation dialog put the files there. If not, substitute the path to wherever you installed the agent files to).

---

