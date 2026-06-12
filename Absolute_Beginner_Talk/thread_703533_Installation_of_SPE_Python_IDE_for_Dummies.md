---
title: "Installation of SPE Python IDE for Dummies"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by CostaRica on 2008-02-21
Finally an installation of the latest version of SPE Python IDE FOR THE REST OF US!!!

Bring your terminal and type or copy paste the line that follows the #Comment
Type your root password when prompted and enjoy

This is my firt 2 cents, and I hope someone benefits from it.

# Install SVC 
sudo apt-get install subversion 

# Install SubVersion of SPE 
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe 

# Install Curl 
sudo apt-get install curl 

# Install wxWidgets key
curl [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) | sudo apt-key add - 

# Add the following lines to your /etc/apt/sources.list file. Replace the "DIST" text with whatever is appropriate for your system. (gutsy) 

# wxWidgets/wxPython repository at apt.wxwidgets.org 
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) DIST-wx main 
deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) DIST-wx main  

# Update repositories 
sudo apt-get update 

# Install wxWidgets 
sudo apt-get install python-wxgtk2.8 python-wxtools python-wxaddons wx2.8-i18n 

# Go to the directory _SPE
cd _spe

# Make SPE.py executable
chmod +x SPE.py

# Launch SPE
python SPE.py

---

### Post by gimfred on 2008-02-25
Mate, this would be better off in the Development and Programming forum.

---

### Post by CostaRica on 2008-02-25
Sorry.

---

### Post by stani on 2008-03-03
Hi,
There is no need to download from the wxwidgets repositories. python-wxgtk2.8 is fine in feisty and gutsy from the universe repositories.

Stani

---

### Post by kfir on 2008-03-03
# Install SubVersion of SPE 
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe 


this do nothing!!!
any help?

EDIT
o.k i got it it tooks awhile and start to download
thanx

---

### Post by enixon on 2008-03-13
This was a big help! I've had SPE  IDE installed for a while, Just couldn't figure out how to navigate to its folder to launch it. Thanks a bunch for covering it all.

---

### Post by CostaRica on 2008-03-14
I appreciate your comment.  I was starting to think that nobody found it useful.:)

---

### Post by enixon on 2008-03-14
Is there a way to create a short cut using these commands that launches the program it's self so repetitive typing isn't required?

---

