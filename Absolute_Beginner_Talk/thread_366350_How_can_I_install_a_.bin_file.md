---
title: "How can I install a .bin file"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by foxwiz on 2007-02-20
I have a file on my ubuntu desktop.  It is called jre-1_5_0_11-linux-i586-rpm.bin

How can I install this file?


I am new to linux so please be "verbose" with your answer.  I have only been on for a few days now.

Thanks in advance

Gary

---

### Post by yabbadabbadont on 2007-02-20
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

It would probably be a good idea to read and follow the instructions there.  Much less likely to get yourself in trouble that way.  :D

---

### Post by Zuuswa on 2007-02-20
Have you tried searching the repositories for the program you are trying to install?  Using synaptic to install programs is a breeze!  I hardly ever download and install programs manually.  Just go to System>Administration>Synaptic Package Manager and use the search function.

Here is a useful link for you to try:
[https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by Tomosaur on 2007-02-20
Right click the file, go to properties, then the permissions tab, and click the box at the bottom which allows you to execute the file. Click ok, then double click on the file. A menu should pop up, and you should click 'Run in terminal'.

This should work. Alternatively, you can do all this in the command line a bit quicker, but you mentioned you're new to linux, so you may like to stick with the GUI for now.

---

### Post by Velotix on 2007-02-20
.bin files are usually problematic - they're files written in direct machine code which means they'll run so long as you make them executable.

But in your case, that looks like an RPM-based file, and Ubuntu doesn't have an RPM-based installer. Ubuntu uses .deb files for installing packages, so even if you run the file it probably won't work. I personally wouldn't risk it without finding out more.

That looks like the Java installer file to me, and I know for a fact that it's in the Ubuntu repositories, so perhaps it would be easier to install it manually from the repos?

Anyway, to answer your question, the command to make a file executable is:

```
sudo chmod +x [filename]
```

Then you can just enter the filename into a command line interface (Terminal, Konsole, etc.) and it'll run.

---

### Post by foxwiz on 2007-02-20
I looked at the instructions and I don't what to do.  I am not sure what I have and how to install.  Can I get some instructions on how to install?

It talks about Sun Java, it talks about Blackdown Java, it talks about different versions, I have a bin file on the desktop that I would like to install.

Is there a way to install the file?  

Thanks

---

### Post by Tomosaur on 2007-02-20
> **foxwiz said:**
> I looked at the instructions and I don't what to do.  I am not sure what I have and how to install.  Can I get some instructions on how to install?

It talks about Sun Java, it talks about Blackdown Java, it talks about different versions, I have a bin file on the desktop that I would like to install.

Is there a way to install the file?  

Thanks

Chances are you've downloaded the wrong file altogether. Just open up a command line and type:
```

sudo aptitude install sun-java5-bin

```

This is the same program as the one you are currently trying to install, except you don't need to mess about. Just delete the file from your desktop.

---

### Post by foxwiz on 2007-02-20
Thanks for all the replies.  I posted the reply above before I read all the replies that everyone posted.

The reason I downloaded this .bin file was because I wanted to play some tunes.  I went to [www.twistedtunes.com](www.twistedtunes.com) and tried to play a tune from the audio vault.  The message that I got was: Totem could not play 'mms://media.twistedtunes.com/twistedserver/twistedtunes/TT_351_4.wma'.  No URL handler implemented for "mms"

The goal is to be able to play tunes from this site.  What do I need to do?

Thanks for any help,

Gary

---

### Post by foxwiz on 2007-02-20
I just tried to install the Java using the following command:

sudo aptitude install sun-java5-bin

and I received an error saying "Couldn't find any package whose name or description matched "sun-java-bin"

---

### Post by Tomosaur on 2007-02-20
You must have missed the 5, the command ins:
```

sudo aptitude install sun-java5-bin

```

---

### Post by Sentinel83 on 2007-02-20
Hi foxwiz,

Tomosaur makes a good point, and you should probably use the java file in the Ubuntu repositories.  However if you want to try to install the file on your desktop, you will need to make sure it is executable first, then run the file.
To do this you will need to type two commands in the terminal once you are in the directory where the file lives.

Step 1 - Open the Terminal and cd to your desktop, so type 'cd \home\foxwiz\desktop'
(w/o quotes)

Step 2 - Once you are in the Desktop directory, type -   chmod +x filename

Step 3 - run the file, so type -   ./filename 

Then follow the install...

Hope that helps...

---

### Post by foxwiz on 2007-02-20
I typed in the terminal window

sudo aptitude install sun-java5-bin

I received the following error message "Couldn't find any package whose name or description matched "sun-java5-bin"

I double checked the spelling to make sure I didn't screw it up!!

(One thing though, is this file the same as the one I wrote about earlier? because someone suggested that I delete it from the desktop)

I did delete it from the desktop.

---

### Post by Maestro23 on 2007-02-20
> **foxwiz said:**
> I typed in the terminal window

sudo aptitude install sun-java5-bin

I received the following error message "Couldn't find any package whose name or description matched "sun-java5-bin"

I double checked the spelling to make sure I didn't screw it up!!

(One thing though, is this file the same as the one I wrote about earlier? because someone suggested that I delete it from the desktop)

I did delete it from the desktop.

You don't run a .bin file like that.  Follow the directions posted by Sentinel83.

---

### Post by foxwiz on 2007-02-20
How can I install Java from the repositories?  I loaded Synaptic Package Manager (is this correct?)

I scrolled down and see javacc 3.2+
and some other stuff.  Is this what you are talking about?

---

### Post by foxwiz on 2007-02-20
I deleted the bin file from the desktop.

---

### Post by Maestro23 on 2007-02-20
> **foxwiz said:**
> How can I install Java from the repositories?  I loaded Synaptic Package Manager (is this correct?)

I scrolled down and see javacc 3.2+
and some other stuff.  Is this what you are talking about?

Open up Synaptic.

Search for Java6

Mark for Installation

Apply

---

### Post by Tomosaur on 2007-02-20
Ah yes, silly me. You need to activate some repositories. In synaptic package manager, click:
Settings > Repositories.

The first tab in the pop up menu will have several check boxes. Click them all, then click close.
On the main toolbar, click 'Reload'. This will scan the repositories and allow you to find extra software. Click 'search', then type 'sun-java' and click the search button. All of the sun-java software packages will appear in the panel on the right hand side. The ones you need to download are:
sun-java5-bin
sun-java5-plugin

To do this, just click the little box next to the package name, and select 'Mark for installation'. If the sun-java6 versions are there, you may aswell download those instead. Once you've marked all of the packages you want to download, click 'Apply'. Synaptic will then download and install these packages :)

---

### Post by PartickThistle on 2007-02-20
You don't need to install Java to play an MMS stream.  

```
sudo apt-get install mozilla-mplayer
```

To execute a .bin file;

```
cd /path/to/your/downloaded/file
chmod a+x downloadedFile.bin
./downloadedFile.bin
```

---

### Post by foxwiz on 2007-02-20
sudo apt-get install mozilla-mplayer

I put this into the terminal window and it said it couldn't find mozilla-mplayer.

---

### Post by Maestro23 on 2007-02-20
> **foxwiz said:**
> sudo apt-get install mozilla-mplayer

I put this into the terminal window and it said it couldn't find mozilla-mplayer.

It is there.  Did you enable extra repositories like the person above said?

---

### Post by foxwiz on 2007-02-20
I did a search in the Synaptic Package Manager and found mozilla-mplayer.  I installed it but I still can't play the wma file.   I get an error message saying "No URI handler implemented for "mma"

---

### Post by foxwiz on 2007-02-20
Maestro23,

Yes I did enabled the repositories like the other poster said.  Then I typed what you said to type (I can't see the other message because I'm replying now), and it couldn't find it.

I did locate mozilla-mplayer in Synaptic Package Manager and loaded it, then I still got the No URI handler implemented for "mms"

Thanks for helping, I am so "wet behind the ears" with Linux.  Eventually, I'll get this stuff and be a Wizard!!!

---

