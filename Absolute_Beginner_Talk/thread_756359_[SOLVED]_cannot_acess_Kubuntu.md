---
title: "[SOLVED] cannot acess Kubuntu"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-04-15
I installed regular Ubuntu a few weeks back on it's own hard drive.  I decided I would like to give Kubuntu a whirl.  Before asking for help there were a few suggested threads before typing in your request.  One of the threads seemed to have my answer.  So I followed the instructions and unpacked the KDE package and installed it.  I went and logged out and went back to the login screen.  went to the options menu.  The choices were:

last session
run Xclient script
run Gnome 
run Gnome in secure mode
and secure terminal.

I chose the Xclient hoping to get to a KDE desktop.  Instead I get Gnome.  I think I missed something or made a boo-boo somewhere.  It seemed straight forward.  Any help making the necessary changes to get to the KDE desktop would be appreciated.

Mark Shuman

---

### Post by Inxsible on 2008-04-15
did you install kubuntu-desktop ? using that thread you were talking about ?

to get to a kde desktop, you will need to install that package

---

### Post by jbrown96 on 2008-04-15
Which KDE package did you install? kdebase should install the minimal desktop and create an option under "Select Session" on the login screen. An alternative way to start KDE is to press Crtl+Alt+F1 at the login screen, which will take you to a console login. After loging in, type ```
sudo /etc/init.d/kdm start
``` to start KDE. If that doesn't work then either the wrong package was installed or there was a problem during installation.

---

### Post by phread59 on 2008-04-15
I ran the following:

sudo apt-get install kubuntu-desktop.

It seemed to download ok.  Gave me a box that said it would use about 700 or so mb.  It seemed to download the desktop and a pile of the K specific programs and plug ins.  I just cannot seem to acess it.  I cannot find it to remove it and start over again.  I must have made an error somewhere in the install.  I don't know enough of the syntax to run a check for it or remove it from the CLI.  I cannot seem to be able to find it on my harddrive.  I don't know where to go to get a list of all the programs that are on my hard drive.  Any suggestions on how to look to see if it indeed made the download and install.  Maybe I need to start it up some how before I can use it.

I did run

sudo/ect.init.d/kdm start

Couldn't locate the file.  I guess I goofed up somehow.  I just want to have the ability to choose which desktop I want to run.  I do not really want to mix them I just want to try it out and see if I like it more than GNOME.  GNOME is working Ok.  I don't like a few things in the way it works.  Just want to try the KDE interface .

Mark Shuman

---

### Post by Inxsible on 2008-04-15
If you downloaded everything and it installed fine, then at the login screen, there should be an option where you can select kdm or gdm. If you select kdm, you should log into KDE. It might be under sessions - i think

---

### Post by phread59 on 2008-04-16
Bump for the afternoon crowd.

Mark Shuman

---

### Post by phread59 on 2008-04-16
Not sure why the sudo install failed but fail it did.  I used synaptic and installed the KDE desktop.  It shows up in options and I can access it.  All is well.  I think however I like Gnome better so far.  It just seems more logical to me.  But I now have KDE to ply with and learn.  Thank you all for your help.

Mark Shuman

---

