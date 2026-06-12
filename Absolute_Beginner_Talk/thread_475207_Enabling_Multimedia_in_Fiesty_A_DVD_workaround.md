---
title: "Enabling Multimedia in Fiesty: A DVD workaround"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by timberdc on 2007-06-15
Hi everyone! I tried playing my first dvd last night, and found it didn't work. So I looked in the sticky section, and there is a wonderful thread called "Enabling Multimedia In Fiesty"

[http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

I tried following the directions given in the "DVD" section, but when I tried to edit my sources.list file, it would only open as read only.  :(
 

So if this happens to you, here is a quick and painless workaround that worked for me:
 

First, open Terminal.

Copy and paste (or type, if you prefer) the following code:

 

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

 

Terminal will ask for YOUR password, if applicable. Go ahead and enter it.

 
Now, go to Synaptic Package Manager. (System &#8594; Administration &#8594; Synaptic Package Manager)

Click the "Settings" button in the top tool bar.  Choose "Repositories" from the pull down menu.

Now click "Third-Party Software" in the top menu bar.

Click the "Add" button.

You should get a dialog box that asks you to " Enter the complete APT line of the repository that you want to add as source". 

Paste (or type, your preference) this location in the field provided:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

Click the "Add Source" button.

Click "Close".

You may receive a dialog stating "Repositories changed".  Click "Close" if you do. 

Now click the "Reload" button to refresh your repositories.

Close Synaptic, and go back to Terminal.

Copy (or, again, type) the following code:


sudo apt-get install libdvdcss2 w32codecs


Close Terminal. 

This worked for me with a default install. I hope this helps if you are having problems editing your sources.lists file.

Cheers!

Dougie C.

---

### Post by pete83 on 2007-06-15
I think you only had trouble because you forgot to put the "gksudo" or "sudo" at the start of the command in that walkthrough.

Edit: but your way is just as good, and more user-friendly.

---

### Post by timberdc on 2007-06-15
> **pete83 said:**
> I think you only had trouble because you forgot to put the "gksudo" or "sudo" at the start of the command in that walkthrough.

Edit: but your way is just as good, and more user-friendly.

Well there you go! I just copied and pasted the commands as shown. Thanks for the tip!

---

### Post by pete83 on 2007-06-15
Oh... if you copied the entire command, then the problem was that you copied the "$" sign at the start... the $ sign is already there at the command line, so don't copy that part....

---

### Post by timberdc on 2007-06-15
> **pete83 said:**
> Oh... if you copied the entire command, then the problem was that you copied the "$" sign at the start... the $ sign is already there at the command line, so don't copy that part....

lol! I'm a n00b :D

---

