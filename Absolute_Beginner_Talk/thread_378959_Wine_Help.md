---
title: "Wine Help"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Letni Norelec on 2007-03-07
So I finally Installed Ubuntu and now I want to install Wine.  Walk me through this as though I were a complete idiot.

Thank You in advance.

---

### Post by Letni Norelec on 2007-03-08
I went to wine HQ, selected the one for Ubuntu, and tried to follow the steps but when I tried to paste in the code thing it would not work.  I probably am lacking some knowledge of something or other so if you could please help me I would be much obliged.

---

### Post by fdrake on 2007-03-08
open the terminal and type :
sudo apt-get install wine
ps you need to open your repositories.

---

### Post by Letni Norelec on 2007-03-08
Then do I paste that code?  Also repositories?

---

### Post by Letni Norelec on 2007-03-08
I have found the Repositories.  But how do I open them?

---

### Post by fdrake on 2007-03-08
Ok,  go to System>Administration>Synaptic Package Manager
write your password
select Settings>Repositories
select Add

and check all the 4 components for each one of the four channels. So you can access to the full archive.
reload and search for wine select it and install it
good luck

---

### Post by Letni Norelec on 2007-03-08
I don't see the add button....

---

### Post by Kuoi on 2007-03-08
I think that is just a little mistake of 'fdrake'.

Don't look for the "add" button.

In the "Ubuntu 6.10" tab , under 'internet' you must select all 4 first phrases.

Hope this helps , Kuoi

---

### Post by Letni Norelec on 2007-03-08
Thank you kuoi.

---

### Post by fdrake on 2007-03-08
hope the images help.

---

### Post by Letni Norelec on 2007-03-08
But how do I get to the Software preferences?

---

### Post by fdrake on 2007-03-08
i just find out why you cannot see it. I am using ubuntu dapper instead you are using edgy. I think there are different names. So the only thing I can suggest you is this guide. [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by Patrick K on 2007-03-08
Go to System>Administration>Software Sources
On the Ubuntu 6.10 page check the four sources available. Close
Go to System>Administration>Synaptic Package Manager
Click on search and type "Wine"
You should get 5 packages to select from. Right click the the one that just says "Wine" and select "Mark for installation"
Click on Apply and follow the instructions

In a few minutes Wine will be installed.

---

### Post by Letni Norelec on 2007-03-08
Now I've got it!  OK it is installed, now how do I use it?

---

### Post by Letni Norelec on 2007-03-08
Like if I wanted to install a game.

---

### Post by Kuoi on 2007-03-08
Maybe you can follow this guide [psychocats -wine]("http://www.psychocats.net/ubuntu/wine")

Kuoi

---

### Post by Letni Norelec on 2007-03-08
Well it says under the SPM that wine is installed but it is not on the open with list.  I don't know if this means anything or not though.

---

### Post by Kuoi on 2007-03-08
Normally if you click on the setup file of the program you want to install , wine should start .

Kuoi

---

### Post by Letni Norelec on 2007-03-08
Well it seems that I just needed to update it.  It works now.  Thank all of you for your help.

---

