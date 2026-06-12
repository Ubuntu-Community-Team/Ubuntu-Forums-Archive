---
title: "Madwifi working on macbook"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by rogue_runner on 2007-05-12
Hello,

First of all apologies for the noob factor of my question that may present chortles..
 
That said I have put Ubuntu Feisty on my macbook and have encountered a number of problems which I have attempted to solve for quite a while now I'm admitting defeat.

*no previous knowledge of linux or linux shell shell..*

Following this [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) guide I should be able to work it out by myself...however I am stumped by how to "Open a shell terminal in the MadWifi source directory." - internet searches failed to provide me a conclusive answer....
Then I returned to the very useful wiki [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) and tried to copy paste the commands in. It installs I believe but then the lines
tar -zxvf madwifi<tab>
cd madwifi<tab>
make
sudo make install 
produce an error with new line (googling this I tried to remove the lines etc but to no avail)

I am well and truly stuck. Help would be very much appreciated!

(oh and before I forget I also seem to be unable to get the 915 resolution to work....any ideas on that?)

Thank you in advance :)

---

### Post by dustynus on 2008-03-29
Try doing a:

sudo apt-get install build-essential

Then try doing the:
sudo make
sudo make install
sudo modprobe ath_pci

:)

---

