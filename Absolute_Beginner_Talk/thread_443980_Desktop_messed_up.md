---
title: "Desktop messed up"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Jubal on 2007-05-14
After booting up my desktop looked normal except for the display switcher in the corner not being there.  When I open a program it overlaps the top taskbar and I am unable to minimize it.  I can open a new program over that but have to close programs to see the top taskbar.  The opened programs also do not display on the bottom taskbar.  Any ideas what happened?  Everything has been fine since upgrading to 7.04 till today.

---

### Post by e6626550w on 2007-05-15
After booting up my desktop looked normal except for the display switcher in the corner not being there. When I open a program it overlaps the top taskbar and I am unable to minimize it. I can open a new program over that but have to close programs to see the top taskbar. The opened programs also do not display on the bottom taskbar. Any ideas what happened? Everything has been fine since upgrading to 7.04 till today.
Reply With Quote



Yeah, I had something similar happen the other night too. There is something wrong with Feisty in this regard. 

How to fix this is to right click on a panel and then cick the "add to panel". Look in the desktop and windows section of selections and you'll see your missing workspacer icon, tell it to 'add'. You need probably to add the 'window selector' or 'window list' icon too... I forget which it was. 

Just play around with this and you'll get you desktop back the way it should be.  It is frustrating I know but it is easy to fix if you know how. Everything is easy once you know how, right? 

eileen...

---

### Post by Jubal on 2007-05-15
Well I did get the windows selector back up but it is not working properly, and my programs are still covering up the top panel.

---

### Post by carloslosgrande on 2007-05-15
I too have had this problem, several times. Usually its when I try to use 'desktop effects'. I've also had caused by 'restricted device manager'
I've tried deleting panels and setting up new ones but in the end every time I've had to reinstall from disk. I currently have 'restricted device manager' working ok and the system is fine. I've given up on the desktop effects, it doesn't like my box.
I found this on the forums a while ago, thanks to arsgeek, very useful;

Ubuntu Tricks - how to generate a list of installed packages and use it to reinstall packages

This tutorial will work for any Debian based system, but is written specifically for Ubuntu.
I&#8217;ve recently had the occasion to make a complete list of software installed on one of my Ubuntu boxes, and then reinstall it from scratch. Here&#8217;s a quick and easy way to generate a list of installed .deb packages, and then use that list to quickly reinstall them.

digg_url = 'http://digg.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc';

First, let&#8217;s make the list. You&#8217;ll be doing all of this in a Terminal Session:

> dpkg --get-selections | grep -v deinstall > ubuntu-files

NOTE: Wordpress interprets two dashes (- -) as one dash (&#8211;). When you&#8217;re putting this into your CLI, make sure it&#8217;s dropping two dashes &#8216;- -&#8217; without the space between them.
Now you&#8217;ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a seperate partition or on a disk somewhere. Heck, it&#8217;s not that big, email it to your gmail account.

So now you&#8217;ve got this list and all is well, until you&#8217;re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.
Once you&#8217;ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
> sudo apt-get update
(this next is only to get the latest upgrade and you can leave it out sudo apt-get dist-upgrade)
> sudo dpkg --set-selections < ubuntu-files

NOTE: Wordpress interprets two dashes (- -) as one dash (&#8211;). When you&#8217;re putting this into your CLI, make sure it&#8217;s dropping two dashes &#8216;- -&#8217; without the space between them.

Now you&#8217;ve told your system what it needs to install, so let&#8217;s install it all.
> sudo dselect

This will open up a dselect session. Type>  &#8216;I&#8216; and allow dselect to install of the the packages listed in your ubuntu-files document. When it&#8217;s finished, type &#8216;Q&#8216; and hit the ENTER key to exit dselect.

Now you&#8217;re a lot closer to where you were before.

good luck

---

### Post by Jubal on 2007-05-15
I haven't ever tried to use desktop effects, and I have checked it is off.  Hopefully I won't have to reinstall.  :confused:

---

### Post by carloslosgrande on 2007-05-15
Ok, sorry if I've made it seem worse than it is. I haven't had any luck at fixing this problem other than reinstall, however, I'm far from being knowledgeable in this, or that, for that matter. I've become quite used to reinstalling and I'm quite setup for it now so it often seems the simplest answer for me. I have a predeliction for impulsive actions and often break things - I even broke Synaptic once!

That said its always useful to have the backup previously mentioned. ie do it while you can and then you won't have so much to worry about.
I think I'm making this all sound quite bad when it isn't.

I'm sure there's someone here can give you a lead in the right direction for this.

---

### Post by e6626550w on 2007-05-15
> **Jubal said:**
> Well I did get the windows selector back up but it is not working properly, and my programs are still covering up the top panel.

Delete the whole top panel and build it back from scratch. That was what I had to do. The problem is fixable without any elaborate geek tricks. No need for a complete reinstall either. I just fiddled around and by luck stumbled into how to fix it. I was ready to throw the computer out the window, though I must admit before finding the solution. A couple of posters were kind enough to tell me what the problem was but by then I had already fixed it.

eileen...

---

### Post by Jubal on 2007-05-15
Well after re-doing the top panel and reinstalling I still was having the problem.  I decided that my windows manager was messed up somehow so I installed blackbox and now everything is fine.  Not sure what happened.  Thank you everybody for your help.

---

