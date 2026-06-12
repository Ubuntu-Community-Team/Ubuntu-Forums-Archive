---
title: "Install folding at home withoug pulling out hair?"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Smoken Joe on 2006-02-28
Well I read the sticki but it just did not make sence without prior knowledge. 
> 
Installation

The following script will download the latest client from the Folding@Home website, and install it to opt/foldingathome, either in / or $HOME. It will ask you to set up the client (the defaults are usually sufficient), and copy that configuration for every CPU in your machine.

It is not possible to provide a .deb package for Folding@Home, because the client must be downloaded from Stanford's website. This is to ensure the integrity of the research.

To install, download the tarball and do

tar zxvf fah_install-version.tar.gz

This should extract the archive to a folder called folding/. Then

cd folding
less README

to read the documentation. Finally,

sudo ./folding_install.sh install

to install the client.

You can also install to your $HOME, in case you do not have root access to the computer. Clearly, you would not have to prefix the command with sudo in this case. If you install to your $HOME, a cron job will be created to start the client automatically.

fah_install-20060225.tar.gz


Can someone fill in the missing steps? Do > tar zxvf fah_install-version.tar.gz do how here etc? 


Sorry missing the background.

---

### Post by taurus on 2006-02-28
```

tar zxvf fah_install-version.tar.gz
cd fah_install-version
sudo ./folding_install.sh install

```

---

### Post by jpkotta on 2006-02-28
I am the author of the installer and the wiki page.  You just run these commands in a terminal.  There is a more step-by-step [HowTo]("http://ubuntuforums.org/showthread.php?t=101817") in these forums.  Please go there or ask me for more help.

---

### Post by Cousindaddy on 2006-02-28
Sorry to see that you've encountered problems installing Folding@Home. While my Linux expertise is limited, I have installed this program and so might be able to help.

First, you need to go to Standford's Folding@Home page:
[http://folding.stanford.edu/download.html]("http://folding.stanford.edu/download.html")

When you scroll down you'll see two versions available for Linux; 5.02 and 5.04 (BETA). Download one of these by clicking on Download under the Penguin.

Next, in Terminal, switch to the directory where the file was downloaded to. In my case all of my files are downloaded to the desktop.

*cd Desktop*

Now, depending on which file you downloaded, enter one of the following two commands:
*chmod +x FAH502-Linux.exe*   -or-
*chmod +x FAH504-Linux.exe*

Now, you're ready for installation.  Enter the appropriate command for the file you downloaded
*./FAH502-Linux.exe*    -or-
*./FAH504-Linux.exe*

The setup will ask you some questions (Username, Team Number *(45104), etc.*).  Unless you want to make changes to the default setup just opt for ENTER.

And I think this should do it.  If there's anything amiss with this post please let me know.

Thanks for participating.

---

### Post by WelterPelter on 2006-02-28
Choose any username you want to. If you want to fold alone (i.e. a one-person team) then set your team number to 0. If you want to be on the ubuntu team, then set it at 45104.

---

### Post by Smoken Joe on 2006-02-28
Well got it working.

 Thanks much I dont know what I was doing wrong the first time but now all is good. :) 

I will probibily get on team ubuntu once I get more of my machines on this OS. Dont get excited most of them are old machines.  Right now I am working with a Tbird 1200 with 250 of value ram and intigrated graphics but now that I replaced windows it is running like a dream.

---

### Post by OfficeLinebacker on 2006-03-12
i just followed jpkotta's directions.  good stuff.  \\:D/

---

### Post by Godofgrunts on 2008-07-01
Me and some guys over at overclock.net have been working on a GUI installer for people new to linux. You can go check it out if you'd like.

[http://www.overclock.net/overclock-net-folding-home-team/339776-gui-f-h-installer-linux.html](http://www.overclock.net/overclock-net-folding-home-team/339776-gui-f-h-installer-linux.html)

The only problem is you need WxGlade installed. You can do some from the Add/Remove programs tool under Applications.

---

