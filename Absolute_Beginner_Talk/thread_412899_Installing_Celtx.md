---
title: "Installing Celtx"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Demented on 2007-04-18
Hi, I'm new to Xubuntu and am ignorant when it comes to knowing how to successfully installing anything that isn't int he Add/Remove console.

How would I go about installing the software that is found here:
[http://www.celtx.com/download.html]("http://www.celtx.com/download.html")

Plus, is there any software like Celtx that is available on Linux and better?

---

### Post by Demented on 2007-04-18
Do I have to utilize the command line?

---

### Post by Drillbit on 2007-04-18
> **Demented said:**
> Hi, I'm new to Xubuntu and am ignorant when it comes to knowing how to successfully installing anything that isn't int he Add/Remove console.

How would I go about installing the software that is found here:
[http://www.celtx.com/download.html]("http://www.celtx.com/download.html")

Plus, is there any software like Celtx that is available on Linux and better?

I'm a newbie too - this my first time "helping" someone - but I have used this software and love it.

First download the file and extract it to you desktop. The go to your home file and drag it in there. Rename it to ".Celtx"

Then go back to desktop and 'right click' to 'create a launcher.' 

In there you hit browse and it should take you back to your home folder (hit ctlr + h to see hidden folders) click into '.Celtx' and find a file that simply reads 'celtx.'

From there you can launch it. Hope this made sense. Enjoy. Great tool.

---

### Post by Demented on 2007-04-18
Thanks. That works. Is there anyway to just put it into my Applications menu?

---

### Post by Demented on 2007-04-19
Sorry to bump this, but I'm still wondering. Do all installed applications like that have to stay on the desktop or can you somehow put the launcher in the application menu?

---

### Post by muhkayoh on 2007-04-21
At last, a chance to help somebody!  :D

Right click on Applications, then click Edit Menus.  From the Menu Layout dialog, select the subgroup in the Menus list (on the left) that you'd like to add Celtx to (I picked Office since that's where all the wordprocessor stuff is by default).  That'll give you the current list of applications in that group on the right.  You'll see a New Item button; click it.  The rest of the steps are probably self evident.  Give it a name (Celtx, most ikely) and then click the Browse button.  Browse to the folder with the launch script and open that in the space that's labeled Command.  You can also wrangle an icon if you want.  Just click on the No Icon button and surf to the icon folder within the Celtx folder.

I just did this and it works fine in Edgy.

Matt

---

### Post by burning_man13 on 2007-10-09
I've got a question for all of you... when I do all of that I get this error:
Details: Failed to execute child process "/home/tony/.celtx" (Permission denied)

What can I do to correct that?? why is it failing to execute "child process"

---

### Post by TKR101010 on 2007-11-13
> **Drillbit said:**
> First download the file and extract it to you desktop. The go to your home file and drag it in there. Rename it to ".Celtx"

Then go back to desktop and 'right click' to 'create a launcher.' 

In there you hit browse and it should take you back to your home folder (hit ctlr + h to see hidden folders) click into '.Celtx' and find a file that simply reads 'celtx.'

From there you can launch it. Hope this made sense. Enjoy. Great tool.

Thank you so much. I was trying to launch it from the command line and not getting anywhere. You advice worked great :)

---

### Post by Gavla on 2007-11-15
I'm a new user and trying to understand this a bit better, celtx is the first thing I've come across that isn't in synaptic. I'd love a little bit of explanation.
I sudo mv'd it to /usr/celtx so that all my users could use it, is this a sound thing?
What are the implications of the fact that this isn't constructed as a debian package? I notice that there's still a .celtx created in the user's home directories, so i guess celtx's internal settings will still be remembered for the different users? There's no automatic adding to the menu and the default save directory is the home director, which is little worry. Obviously, there's no automatic update or removal, but there was the latter  when I first tried by aliening it into a .deb (but i removed it 'cause it put it in the home directory and could only be used by that user). Will anything else be sort of 'missing' 'cause it's been done this way?

---

