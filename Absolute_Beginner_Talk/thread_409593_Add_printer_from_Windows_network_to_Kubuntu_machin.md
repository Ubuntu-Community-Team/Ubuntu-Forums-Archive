---
title: "Add printer from Windows network to Kubuntu machine"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by bwolper on 2007-04-14
I am trying to add a printer to my Kubuntu on my laptop from my Windows network.  My printer is shared from my Windows machine.  Can anyone talk me through specifically with Kubuntu.  I am having trouble following instructions mean for Ubuntu.

I go to System Settings>Printers and then enter administrator mode by 
typing my Kubuntu password.

I go to Add Printer.  I press "next" though the introducation page.
On Backend Selection I select "SMB shared printer (Windows)"

Under User Identification I select "normal account" and I keep "root" as my login and I put my Kubuntu password for password.

I select next and then come to "SMB Printer Settings."

I fill in nothing and press "Scan."

My Windows network name shows up.

When I click on that, I expect to see a list of shared printers.  I don't get that.  Instead nothing happens.

When should I do next?

Thanks to anyone who can help me.

---

### Post by reality_hunter on 2007-04-15
hi, I like to help because I had gone through the same problem few days back and finally got it managed to work.....but I have UBUNTU and don't know if there is a big difference between that and kubuntu!  anyways I will assume that they are similar:

first of all get the name of your windows computer (not the username) and name of the shared printer
computer name = WIDOW
printername = PRINter

also lets say your home network name is HOME, this is what you do
now if you say that you see the network name on the printer setup utility but do not see the printers that is a little weird.

but anyways, when you select network printer and then SMB, don't put any passwords.  The next thing you see is bunch of blank fields right (atleast thats what i see) there should be a field looking like :
smb://
type in "WIDOW/PRINter" next to that field and if any luck you should get that scan, again try this without anypasswords first..........after this you choose your make and model number of the printer from the list and again I assume they are there. you should see the final button that says apply.  after hitting apply, it will notify you that it make some sort of smb file and thats is it you are almost done.

the next thing to do is add this printer from the localhost as well, so do this:
go to this website its actually CUPS ..so its not a website as to speak               [http://localhost:631](http://localhost:631)
in there you will find printer ->go there----and add new printer----> go through the steps....you should know what to do there EXCEPT one thing you have to remember is that when you select add windows(SMB) printer...it will ask you for the device URL and your device URL according to this will be:
smb:///WIDOW/PRINter

try this and print a test page and see if this works..................post the outcome or any problems back to this thread.

---

### Post by Sef on 2007-04-15
What is the brand and model of your printer?  Some printers, like HP, Epson, and Brother can work very easily with GNU/Linux.  Others, like Lexmark and Canon do not.

---

