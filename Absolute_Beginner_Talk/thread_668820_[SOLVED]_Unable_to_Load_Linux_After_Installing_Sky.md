---
title: "[SOLVED] Unable to Load Linux After Installing Skype"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by chrissy833 on 2008-01-15
Today tried installing Skype from the website ([http://www.skype.com/download/skype/linux/choose/]("http://www.skype.com/download/skype/linux/choose/")) because it wasn't in my repos.  I chose the Feisty Faun 7.04 download and double clicked it to install it.  I ran Skype, and it seemed to work fine, although I did not actually make any calls.  This is the only major change that I've made reciently, aside from installing flash a day ago.  I shut down my computer.  The next time I started up my computer I got a long series of text after the splash screen.  Here is a very abbreviated version:

/dev/sda7 contains a file system with errors, check forced
unexpected inconsistence; run fsck manually

* manual fsck must be performed in maintenance mod with root mounted in read only mode

*root mounted in read only mode. maintenance shell started
[A series of Bash: command: command not found]
command line:

I (perhaps stupidly) tried removing skype at this point with sudo apt-get remove and it said:
"command "sudo" is available in '/usr/bin/sudo' The command could not be located because '/usr/bin' is not included in the PATH environment variable. 
bash: sudo: command not found"

I am running Ubuntu 7.10, and I have my computer set up to dual load with Windows.  When I restarted my computer, I was able to successfully boot and run in Windows.  I don't know my system specs off the top of my head, but if they would be helpful, I can look them up.

---

### Post by original_jamingrit on 2008-01-15
Have you tried running ```
fsck /dev/sda7
``` after the maintenance shell was started?  This should do a file system check on /dev/sda7 (I'm assuming that's your root partition).  The command "fsck" is similar to the defragging application in windows (but for command line, obviously).

---

### Post by chrissy833 on 2008-01-16
Thanks - I tried that and it came up with an error while reading a specific block.  It asked me if I wanted to ignore the block and force a rewrite.  Should I select "yes" on rewrite for that and all subsequent errors?

---

