---
title: "can WinApps under Wine call Gnome utilities?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by BertP on 2007-09-28
I just installed  the Agent newsreader under  Wine  and I would like to call Gnome apps from Agent.    For instance , In Agent  I can setup a sound app to associate with any mp3s I may download  and a pic viewer  for  jpgs that I download.    Could I call   "Eye of Gnome" from  Agent or must I install a Windows jpg viewer  and mp3 player  into Wine to handle the files Agent downloads?

---

### Post by kyphi on 2007-09-28
Your jpg files will open with whatever application you have set your preference to, the same goes for mp3.

To set preferences, right click on the file icon (mp3 for example) and scroll down to Properties.  Then select 'Open with' and if the application is not there, press 'Add' and select it from the menu.  After that, all mp3 files will be opened by the programme you have chosen.  The same goes for jpg files.

---

### Post by BertP on 2007-09-28
Thanks for the help!

I just tried unsuccessfully to associate "Eye of Gnome" with  jpg images in Agent.   Here is what I did:

I downloaded a message containing a jpg.  (I saved it and verified that it is indeed viewable ) 
next I right click on he jpg in the message body.
Agent shows an error message telling  me that I don't have a viewer associated for Jpeg images
next I click the message box's  "Select Application" button and navigate to eog and select it
Agent returns the following error message:

"Unable to execute command  z:\usr\bin\eog  C:\Program Files\Agent\DATA\sample.jpg."

perhaps Agent expects the executable file,  eog, to have an .exe extension?
if so is there a way to create a link file with an exe extension that would point to eog?

Thanks again,  I am now in my second week of Linux and Ubuntu  and I love it!

---

### Post by kyphi on 2007-09-29
I had a look at Agent - never heard of it before.  So, it is a programme designed for Windows.

I have a Windows installation on one of my hard drives and can access any image (jpg, jpeg, gif, png) stored there from Ubuntu using Image Viewer (Eye of Gnome).

Make your file associations while in Ubuntu rather than in Agent.  Once they are set, they should always open in your chosen programme.

You may like to investigate virtualisation whereby you can run Windows (with Agent) on Ubuntu.
I use Innotek VirtualBox but there are others.

---

### Post by BertP on 2007-09-29
I can save the image then browse to its directory to view the image just fine..  and it is only a slight inconvenience to do this first..    However, I would prefer to be able to view the image (or mp3 or doc etc)  from the message itself.   That way I would not t need  to go to a directory where probably many  message attachments have been previously saved and then find the particular attachment associated with the usenet message that I am currently reading.

My intuition tells me that since Agent is running under  Wine's  Windows compatibility layer,  any process that Agent spawns will run in the same layer as well.  That's why I thought it was probably necessary to install native  windows apps for each attachment type if I want to  be able to retain Agent's ability to view an attachment directly from the  body of the current  usenet message

After trying Pan,  I suspect that there must be plenty of  Linux  users running  one of the feature-rich Windows Newsreaders.   So perhaps someone can give me a definitive answer
to my question. :)

BTW, I do still have the install file for Agent 200-652 if anyone needs it,  (though I will not share my registration key.)

---

### Post by BertP on 2007-09-29
A point of clarification about my install file:  

  Agent version 2 is 4 or 5 years old &  Forte no longer supports it, Therefore it's unlikely that a version 2 install can be found on any common downloading site.  However some reports from Wine users mention that Agent 2 is the last version that will save attachments correctly under Wine.  Therefore I will happily supply my install file to other Agent users that are able to locate their version 2 keys.    Agent version 2 runs under Wine's Windows 98 compatibility mode.

---

