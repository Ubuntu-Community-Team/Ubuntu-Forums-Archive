---
title: "Newbie question Edit"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-01-10
Hi. I'm trying to edit my grub menu.1st file to alter the boot sequence.  I've worked out how to do this but I get a warning when saving that I do not have permission to save the edited file?  Sorry should have said I have just installed Edgy Eft 6.10 from linux-magazine free distro this month.  Any help/advice gratefully received as I really like this version compared with my last attempt to understand linux a couple of years ago - suse I think.:D

---

### Post by meng on 2007-01-10
You need superuser privileges to edit that file.
sudo nano -B /boot/grub/menu.lst

---

### Post by bugster on 2007-01-10
Thanks Meng for the quick reply.  Forgive the dumb question but do I type that into the editor and save it as a file/

---

### Post by G Morgan on 2007-01-10
That command will load it into the editor when it starts. It will save when you exit with Ctrl+x. It will also backup the file.

---

### Post by meng on 2007-01-10
Yes, you need to invoke the text editor (there are many different choices of text editor in Linux!) with superuser privileges. Otherwise you can't save any changes. Nano is fairly intuitive as text editors go.

---

### Post by G Morgan on 2007-01-10
I see what he means now, you enter that at the bash prompt/terminal rather than in the editor. The sudo prefix gives you temporary root privileges, its a word you'll see a lot in Ubuntu.

---

### Post by steve.horsley on 2007-01-10
You use the sudo command to tell the computer you want to run another command (an editor in this case) as root, which means it runs with full privilege. If using text-based editors like vi or nano, you can open a terminal command-prompt (Accessories->Terminal) and enter one of these two commands:
**sudo nano /boot/grub/menu.lst**
or
**sudo vi /boot/grub/menu.lst**
but when launching a graphical program like gedit, you should use gksudo insead of sudo, like this:
**gksudo gedit /boot/grub/menu.lst**

P.S.
sudo will  likeky ask for your login password, just to make sure it's you and not someone walking by while you've gone to get a coffee that's asking for extra rights.

---

### Post by bugster on 2007-01-10
Thanks both for the quick help - now I'm going to sound even dumber.  Should I reload Ubuntu in text mode to find the Bash area?  At present I'm in the very pretty start up screen ..?

---

### Post by meng on 2007-01-10
Open a Terminal
Applications > Accessories > Terminal

---

### Post by bugster on 2007-01-10
Thanks again everyone.  I'll try it now.  Isn't this a great place to get help?!

---

### Post by tonyr1988 on 2007-01-10
Don't be confused by "Bash". It's what they call a shell - there's a lot of different ones to choose from (sh, bash, csh, tcsh, etc :P), but don't worry about the differences. Bash is the default one.

All you need to really worry about, unless you *need* advanced features, is:

Bash = Terminal = Console = Shell = Applications > Accessories > Terminal

P.S. If you're not sure where to type a command that someone is telling you, try the Terminal.

---

### Post by bugster on 2007-01-11
Thanks everyone - with your help  I just edited and saved my first file in ubuntu.  And in just 24 hours from installation.  Last distro I tried was suse I think and I never got this far in 2 months.  I'm very happy. :D :D :D

---

