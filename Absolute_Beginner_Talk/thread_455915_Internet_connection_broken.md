---
title: "Internet connection broken"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by blue-gum on 2007-05-27
I have dual boot with XP - I have never needed to boot to XP until today, to access the internet   :(

The story is that I have been reading the forum and working on Firefox and Real Player for some weeks.  Now have Real Player installed and running as it should.   I just can't get Firefox to recognise  .ram files and associate with Real Player. I copy and paste URLs into Real Player.    I have worked through forum advice, installed the add on Media Connectivity, removed all totem plugins from /usr/lib/firefox/plugins etc.   In the Firefox Edit - Pref - File Types -Advanced selection, ram and rm files are not listed and so I am unable to point them to Real Player in the usual way.

Last night I decided to upgrade Firefox from 2.0.0.2 to 2.0.0.3 (from memory..) I did this from terminal.   I started with sudo apt-get update, followed by the Firefox install.  This appeared to be successful, however did not solve my initial problem of getting ram into the file types listing.    I did not know how to locate the .dat file (forget the file name) that was recommended should be deleted on upgrade.

I rebooted this morning and found that Firefox could not connect to the internet.   I then decided to check if the problem was just with Firefox or if other programs also fail to connect.   Found Real Player also could not connect, although the modem seemed to be okay.

Was horrified - and then acted to hastily!   Decided to use Synaptic to remove Firefox with a plan to reinstall.   Doh!   Of course the pkg cannot download can it!!   

Problem is that I don't know why the internet connection is broken.   Could be something in the upgrades? 
Removing Firefox makes the problem worse.   

What can I do to get out of this mess I'm in?  Feel that I am out of my depth now - can I do something with the dual boot - download Linux Firefox from XP and perhaps copy this to removable media?   I am running Firefox in XP too.

---

### Post by PetePete on 2007-05-27
first of all you might want to remove the plugins from /usr/lib/mozilla/plugins ,i had the same issue and found removing from there did the trick.

if you do $ifconfig does it show any IP address? 

first of all we need to find out if this is a system issue or a local issue with firefox..

try to ping something, eg. $ping google.com

im guessing it wont work if you said synapitc couldn't connect. 

please also post your /etc/network/interfaces  
maybe we just need to re-setup your network settings

---

### Post by blue-gum on 2007-05-27
PetePete  thank you for your help.     I am very grateful for the forum.

I booted back into Ubuntu and followed your checks, all good, addresses there, Google ping ok.  Then decided to try Synaptic again  Da Da - Firefox downloaded and installed as it should.    I don't know why it didn't work before - and I have been stressing out for hours over this.   

Old problem still exists.   Firefox Edit - Prefs - File Types - Manage still does not list ram file type.   I then removed plugins form /usr/lib/mozilla/plugins as you suggested.   Then rebooted.   I find even less file types are listed, and no ram file types.    Listed are SPL, WM and WVX.

---

