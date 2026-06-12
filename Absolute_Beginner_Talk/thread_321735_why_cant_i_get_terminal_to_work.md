---
title: "why cant i get terminal to work"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by markpoole@ntlbusiness.com on 2006-12-19
Hi what is the command line and where is it?

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
what is the command line and where is it?

---

### Post by Ben Sprinkle on 2006-12-19
Start -> Accessories -> Terminal.

You use it for certain commands, you can do almost anything in it. It is also located in /usr/bin/bash or /usr/bin/sh
:)

---

### Post by jem7v on 2006-12-19
This is also known as the Terminal. If you're running Ubuntu, it should be under Applications -> Accessories.

If you've ever used DOS before, it's a bit like that. It's a way to do stuff by typing instead of clicking.

---

### Post by MarkTX on 2006-12-19
The command line (terminal) for linux is what the MS Dos prompt was for Windows.

You can find it by clicking on Applications / Accessories / Terminal

If you want to have a full screen command line press CTRL+ALT+F1, and CTRL+ALT+F7 gets you back to the graphical user interface.

The command EXIT will take you out of command line mode.


Hope that helps

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
When in terminal it does not comply with install flash player command why?

---

### Post by jingo811 on 2006-12-19
Don't know answer to your specific CLI problem.  But get Automatix and most plugin stuff for Realplayer, Quicktime, Flash etc. will get handled with some click and point.

---

### Post by MarkTX on 2006-12-19
What exactly are you typing to install flash?

---

### Post by kazuya on 2006-12-19
Are you using or trying to install flashplayer 9 for linux? This is the best way.
And there are howtos for installing flashplayer 9 for linux.
You may follow this tip here:


Before following this tip: It may help to go to synaptic and search for flash. If it is already there, you may have to uninstall it to prevent conflict with the new flash 9 you would be getting from here.
  #3       1 Week Ago  
FreedomIsntFree  
First Cup of Ubuntu
   Join Date: Dec 2006
Beans: 3 

 
Re: adobe flash 


I used the automatix method for getting flash on my system.

--------------------------------------------------------------------------------

Flash 9 is now availible to *nix users. It's about damn time right? Anyways, go get it at [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

Here are instructions on installing it:

Download the file and save it wherever.
Navigate to the folder that it is in.
Type: gzip -dc FP9_plugin_beta_112006.tar.gz | tar x
Navigate into to folder it extracts.
Copy the file to your /home/USERNAME/.mozilla/plugins folder by typing:
cp libflashplayer.so /home/USERNAME/.mozilla/plugins
If you do not already have a plugins folder, type:
mkdir /home/USERNAME/.mozilla/plugins
Shutdown whatever browser you are using and restart it. 

If you are using Konqueror (like me) it should still pick up the plugin because it looks for them in there by default.

Hope that helps!

---

### Post by thomasaaron on 2006-12-19
There are a ton of good online resources for learning to use the command line.

I'd suggest starting by googling (Advanced BASH-Scripting Guide).

It starts off fairly basic and is a nice reference to have handy.

Be careful, though...you might end up liking it.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
I just want to install a flash player and its a real balls ake. The direction from adobe asks me to go to a command line and 
Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).
nowt happens?

---

### Post by BarfBag on 2006-12-19
Like others have said, the best path for you would be [Automatix]("http://www.getautomatix.com/").  You can install the flash player with a few clicks.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
mark@mark:~$ gzip -dc FP9_plugin_beta_112006.tar.gz | tar x
gzip: FP9_plugin_beta_112006.tar.gz: No such file or directory
mark@mark:~$ 

thats what i get out of terminal

---

### Post by Perfect Storm on 2006-12-19
make sure you apply the command in the same place as the downloaded file. Also check if the name of the file has changed.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
how do i do that?

---

### Post by Perfect Storm on 2006-12-19
cd /to/the/place

eg. if you downloaded it to your Desktop
```
cd Desktop
```

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
mark@mark:~$ cd Desktop
mark@mark:~/Desktop$ 

thats the come back?

---

### Post by Perfect Storm on 2006-12-19
If you have the file on your Desktop you can now go on with the other commands :)

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
what commands and where do I put them, sorry; please.

---

### Post by linear on 2006-12-19
The command line (a/k/a shell prompt, command prompt) is the place you enter text commands. It's often a faster and more powerful way of getting things done. For many people, it's harder to use than the graphical UI.

One way to get to a command line is via a Terminal window (Applications > Accessories > Terminal).

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
why cant i get terminal to work? I go!
mark@mark:~$ cd Desktop
mark@mark:~/Desktop$

thats the come back?

---

### Post by riven0 on 2006-12-19
> **markpoole@ntlbusiness.com said:**
> why cant i get terminal to work? I go!
mark@mark:~$ cd Desktop
mark@mark:~/Desktop$

thats the come back?

That sounds correct to me. You just changed your directory. To list your files, do > ls -a

But what exactly are you trying to do with the terminal?

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
mark@mark:~$ is -a
bash: is: command not found
mark@mark:~$ 

Thats what i get back?

---

### Post by Perfect Storm on 2006-12-19
the one that kazuya explained.

---

### Post by rowanparker on 2006-12-19
It's a lowercase *L* not an *i*.

Please can you not post more than one thread about this issue.

---

### Post by bruenig on 2006-12-19
use ls -a not is -a

That is "l" as in log not "i" as in in.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
mark@mark:~$ ls -a
.              .esd_auth        .gstreamer-0.10            .Trash
..             .evolution       .gtkrc-1.2-gnome2          .update-manager
.bash_history  Examples         .ICEauthority              .update-notifier
.bash_logout   .gconf           .metacity                  .wapi
.bash_profile  .gconfd          .mozilla                   .Xauthority
.bashrc        .gksu.lock       .nautilus                  .xsession-errors
.config        .gnome           .recently-used.xbel
Desktop        .gnome2          .sudo_as_admin_successful
.dmrc          .gnome2_private  .thumbnails
mark@mark:~$ 

thank you can you tell how to install a flash player that is the desktop, please!
Mark

---

### Post by raul_ on 2006-12-19
Could you just do a little searching please? :mrgreen: those questions have been answered hundred of times, so it would even be faster for you to search instead of waiting for someone to reply

[http://linux.org.mt/article/terminal]("http://linux.org.mt/article/terminal")

---

### Post by rowanparker on 2006-12-19
You have already started a thread about that.

And you ignored most people's responses.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
non of them worked!

---

### Post by rowanparker on 2006-12-19
Use [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation").

So that doesn't mean you should create a new thread about it.

---

### Post by Kobalt on 2006-12-19
How to install flash : [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html")

---

### Post by Beggar Su on 2006-12-19
If you don't want to use terminal, do this:

Download flash player 9 from the adobe lab website ([http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)) 

If you want to install the plugin for firefox, download from the '**installer for linux**' link to i.e your desktop. Go to the desktop, right click, extract. Open the folder(s) and find the **libflashplayer.so** file.

Go to your home folder (by clicking 'places' from the top bar > 'Home Folder'). Press **ctrl**+**H** (to show hidden files or click 'view' then 'show hidden files'). Find **.mozilla** folder and open it. Go to **Plugins** folder and copy and paste the **libflashplayer.so**

Restart firefox by closing and opening it if you had it opened.

If you wanted the other file from adobe's website - the standalone player for linux - , just download the file, extract it, and double click **gflashplayer** file.

---

### Post by handylinux on 2006-12-19
[email]markpoole@ntlbusiness.com[/email]:

I note you also posted this query in the Apple-PPC forum. Are you using Ubuntu on an Apple PPC computer? If so, please note that Adobe does not supply a Flash implementation for that platform, which may be why you're not getting results, because trying to install the i86 version won't work on a PPC computer.

There are a couple of third-party Flash solutions for Linux/PPC, though neither of them is complete yet. See the "[Got Gnash Going! Woot!]("http://www.ubuntuforums.org/showthread.php?t=320221")" thread at the Apple-PPC forum.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
this is silly i can play the intro 2 jonny be good by The late great and most majestic J.H yet i open a single file on a the desktop no way. this is my first day and this is what i do I drag the file of desk top into terminal and hit return then it opens the next file I do the same now im looking at the installer ect
What do I do next?
Mark

---

### Post by BarfBag on 2006-12-19
I don't understand your question.  If you want to get answers around here, use a clear subject and type in a way we can understand.

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
thank you for replying! I just want to open a flash player file. I want to use terminal. all attempts so far have failed! can you help?
Mark

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
I never intended to place the post up again that was a mistake for any one reading with crossed horns, I'm sorry!
Mark

---

### Post by tmatt95 on 2006-12-19
> **markpoole@ntlbusiness.com said:**
> I never intended to place the post up again that was a mistake for any one reading with crossed horns, I'm sorry!
Mark

Hmm strange. If you right click and select it to open with Firefox, does it play then?
Regards,
Matt
P.S This is just a shot in the dark. We will get it playing in the end :D

---

### Post by markpoole@ntlbusiness.com on 2006-12-19
hi and thank you for your help did not know i could do that but when i did it just places another file on the desktop please will you tell me what to do next?
Mark

---

### Post by bulldog on 2006-12-19
Hi Mark.
It's much appreciated if you should do some searching before you ask your questions.
We all want to help you to use ubuntu,but we can't teach you all the basic things you need to know to use your distro.

So before asking anything,do a search if your question isn't answered before [I think so in most cases]
Read some tutorials to get confident with Linux,and if you have a problem you really can't fix,were glad to help you. 

To help you starting with exploring,some useful links,

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

[http://www.linux.org/lessons/beginner/l4/lesson4e.html](http://www.linux.org/lessons/beginner/l4/lesson4e.html)

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

