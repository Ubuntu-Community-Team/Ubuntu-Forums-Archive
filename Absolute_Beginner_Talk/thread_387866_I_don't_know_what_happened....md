---
title: "I don't know what happened..."
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by drusepth on 2007-03-18
Alright, well recently I've been using two different user accounts on my Ubuntu 6.10.  I finally decided to merge to one, so I copied the needed files over to my other account and loaded up System > Administration > User Accounts.  I scrolled down, and clicked on the name of the account I didn't want anymore and click delete.  I closed it, and then restarted (I was doing the Inspiron 1501 Wifi fix and had to restart.)  When I restarted, I logged in to my main account, drusepth, and I started getting issues.  First, half of my System > Administration menu was gone, implying that I didn't have admin privledges anymore.  When I tried loading my network configuration (System > Administration > Networking) to enable my wireless connection, it told me I got an error with privledges and to contact my system administrator.  

I looked around, and nothing that requires admin privs would let me do anything.  I got the off-chance idea that I deleted something wrong in the user accounts menu, so I logged off and tried to log onto the account that I had supposedly deleted.  It let me in, but I wasn't privledged there either.

Anyways, I restarted again to see if for some reason something would come back to normal, and right after the initial Ubuntu loading screen, I get some error about not being able to kill a process.  (Sorry, I didn't write which one.)  And never got Ubuntu to go any farther.

So I restart again.  This time I get no errors, and it goes to the login screen.  I log in to drusepth, my account.

On an off note, when I try to change how loud my sound is, I get the error:
"The volume control did not find any elements and\or devices to control.  This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

I have no idea what would have happened.  Any ideas?

My brother said to set a root password and try to log in as root, so I type in the terminal "sudo passwd root" and it asks for my password, and nothing happens.  

I tried to give as much information as I could to help you help me.

---

### Post by drusepth on 2007-03-18
I figured I would just reinstall Ubuntu because I was going to set up a dual-boot anyways, but I can't mount my SD card to back up the few files that I want to back up.  I try 
sudo mount mmcdisk
sudo pmount mmcdisk.
Nothing happens.
I'll be back at my house tomorrow, so I'll have CDs to back stuff up to, but I found it odd that I could mount and unmount CDs, yet I can't mount my SD card.  It loads fine in my brother's laptop, so I know that nothing wrong happened to it.

When trying to mount the SD Card via the Disk Mounter in my toolbar, I get the error "Unable to mount the selected volume.  error: could not execute pmount".

---

### Post by zvacet on 2007-03-19
Why did you decide to delete one account?You did the right thing when you set two(one with admin privileges and one without it).It is a good thing to use account without admin privileges in everyday work.

---

### Post by drusepth on 2007-03-19
They both had admin privledges, I was just using one with less things on it so I could concentrate on something without being distracted by other programs while I worked.  I went to the terminal and typed in kuser and gor the user list, and drusepth and the account I supposedly deleted are on there, but under 'edit', they both have checkboxes checked saying they're disabled.  When I uncheck the disabled box, it gives me an error saying it can't open /etc/passwd.bak for writing.  I booted into recovery mode to work with that a little, and realized there is no passwd.bak in /etc/.  I don't know why it's trying to regerence to that file.

---

### Post by zvacet on 2007-03-19
I don´t know how to help you.I just want to say that having two accounts with admin privilrges is** redundant** if you are the only user.

---

### Post by drusepth on 2007-03-19
Alright, thanks man I'll keep that in mind.  When my brother used the computer sometimes, the other account would be the one he would use, but he stopped using it so I set it up for my needs.

Thanks though.

---

