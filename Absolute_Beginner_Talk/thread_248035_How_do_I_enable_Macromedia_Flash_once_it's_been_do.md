---
title: "How do I enable Macromedia Flash once it's been downloaded"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2006-08-31
I came upon a website that needed me to have Adobe's Macromedia Flash plugin on my Firefox Browser - otherwise I'm going nowhere with this website.

So I look in Synaptic and find something that looks appropriate, hey, I find something called flashplugin-nonfree but installing this gets me no further. I'm still unable to play the content of this website.

So I've downloaded the latest Adobe flash player onto my desktop and then extracted the file onto my desktop. It looks like that I need to use the terminal to install this software that's on my desktop.


How do I install the flash player software that's sitting on my desktop?

---

### Post by rosiet on 2006-08-31
Ooh, good question.  I am trying to do the same thing.  Whenever something that needs Flash comes up in Firefox I click on the "use Plug-in Finder" box to download it but it always says "failed" and offers manual install.  

I'm just trying the manual install now, but I've got this memory in the back of my mind of needing a .deb file last time I did this, without really remembering what one of those is...

Help appreciated.

---

### Post by rosiet on 2006-08-31
OK, just managed it and it's easy.

If you've saved the .tar.gz file to your desktop just open a terminal and type:

gunzip install_flash_player_7_linux.tar.gz

then:

tar -xvf install_flash_player_7_linux.tar

then:

cd install_flash_player_7_linux

then:

./flashplayer-installer

and follow the instructions.

It asked me to "ask your administrator to remove the xpti.dat from the
components directory of the Mozilla or Netscape browser."

I don't know if you actually need to do that, but on my computer I found that file in this directory:

~/.mozilla/firefox/snrn77of.default

and deleted it.  Hope this helps!

Rosie :-)

---

### Post by Architeuthis on 2006-08-31
Download the tar.gz file from the official page of adobe. [http://www.adobe.com/shockwave/download/alternates/#fp](http://www.adobe.com/shockwave/download/alternates/#fp)

Extract it and run the flashplayer installer file with the terminal (just double click and select view with terminal.

---

### Post by Handssolow on 2006-08-31
I've experimented with the above suggestions. I'd previously downloaded install_flash_player_7_linux.tar.gz  onto my desktop and also also extracted it onto the desktop.

As suggested above, I copied and pasted the following lines into my terminal as 
gunzip install_flash_player_7_linux.tar.gz

but I was met with the reply in the terminal: No such file or directory

Or inputting
tar -xvf install_flash_player_7_linux.tar

this gave the reply: No such file or directory
tar: Error is not recoverable: exiting now

Using a different approach.
Left double clicking on the previously downloaded and extracted file on desktop, then the flashplayer-installer, I accepted the option to run it in a terminal. This gave the following message.

You are are running Macromedia Flash Player installer as a non-root user. Macromedia Flash Player will be installed in your home directory.

Installation seemed to follow and I think I'm able to play flash media properly though one site needed Flash 8. I can find no evidence that I've installed the Macromedia Flash player anywhere in Firefox.

Any comments?
Shouldn't I see some evidence of my installation in Firefox?
Should I have installed Flash Player as root-user?
Any suggested websites where I might test my Flash Player installation?
Are there any security issues with Flash Player?

---

### Post by Toxicity999 on 2006-08-31
The previous post wasn't right or wrong. To install it globally you need to run it in a sudo environment. Otherwise you only get a local install unless this is a single user machine then by all means proceed.

---

