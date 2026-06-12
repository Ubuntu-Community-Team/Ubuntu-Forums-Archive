---
title: "Klamav"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-27
hi, i just installed Klamav from [here](http://klamav.sourceforge.net/klamavwiki/index.php/Main_Page) i installed by double-clicking - 
DoubleClickOrExecuteMeToInstallKlamaAV-0.32
i was hoping for a GUI and real-time protection to help protect my XP partition. how am i supposed to know the commands? i don't understand how everyone else just seems to know them :confused:  there's nothing that tells you where the readme is. all i have found is running "clamscan" in terminal. when it runs it tells me that it's out of date, then scans 16 files :p  when i ran clamscan --help there's nothing there about any GUI or even how to update. 

i just want to understand how to run this then install a hosts file then i'll send afew days reading about Ubuntu. ATM it seems i'll be trying to work out how to use Klamav and trying to find out about Linux hosts files for the next year :( 

can you help me update Klamav and find the GUI, please? thanks :)

---

### Post by amohanty on 2005-11-27
Ok are you trying to protect your XP partition from Ubuntu? If so dont worry, by default XP partition (if it is NTFS) is mounted read-only so it cannot really be written to from Ubuntu. If its FAT32 even then I dont think you need to be concerned because a Windows virus cannot run/execute itself on linux :) (aint that beautiful) and so cannot screw up your win files.

HTH
AM

---

### Post by Danielle on 2005-11-27
hi, amohanty thanks, it's great. but, i still move afew things from partition to partition. and i send and receive emails to and from friends who use windows. i'd just like to know when i come into contact with malware. i don't understand why most people here don't seem to mind.

Ubuntu is still capaible of passing on viruses if they're not stopped with a scanner isn't it?

---

### Post by amohanty on 2005-11-27
The reason people are not concerned here has to do with the way viruses operate. For e.g. if you use Outlook (it has improved recently - but still) you just need to open an email to ectivate a virus/worm which then executes a script/itself to eat up all your files and/or if its a worm to send itself to everybody on your mailing lists. Now something that is executable on Windows for eg a .exe/.wsh/.vbs file is _not_ executable on Linux, which means that the virus/worm cannot even get to step one, ie execute something/itself let alone do the rest.

Please understand that this is a very simplistic explanation of the actual process, but you should be able to get the idea.

Finally you have to realize that security/safety starts with you. As long as you dont forward untrusted material (emails, files etc) to your outlook using friends, they will be fine.

HTH
AM

---

### Post by Danielle on 2005-11-27
[QUOTE=amohanty]The reason people are not concerned here has to do with the way viruses operate. For e.g. if you use Outlook (it has improved recently - but still) you just need to open an email to ectivate a virus/worm which then executes a script/itself to eat up all your files and/or if its a worm to send itself to everybody on your mailing lists. Now something that is executable on Windows for eg a .exe/.wsh/.vbs file is _not_ executable on Linux, which means that the virus/worm cannot even get to step one, ie execute something/itself let alone do the rest.

Please understand that this is a very simplistic explanation of the actual process, but you should be able to get the idea.

Finally you have to realize that security/safety starts with you. As long as you dont forward untrusted material (emails, files etc) to your outlook using friends, they will be fine.

HTH
AM[/QUOTE]
thanks, i know if you've read my posts here i sound like a complete moron, but i do understand windows security - api hooks, dll injection, buffer overflow etc. i know you have to run malware for it to be installed too. i know nothing about Unix though. anyway, i don't think anyone can change my mind. i really do want some kind of real-time protection.

---

### Post by amohanty on 2005-11-27
I am sorry if I offended you, that was not the intent. 
ok the link on the page points to a tar.gz file which will take quite a bit of real estate to explain how to install properly. Try the following:

Goto: System->Administration->Synaptic Package Manager
Click on Search
type in clamav
install it and you should be ready to go.

NOTE: you might have to enable the universe repos to install this. Look at the wiki to figure out how to do so.

HTH
AM

---

### Post by Danielle on 2005-11-27
also, i want to say i realise that Ubuntu runs as a limited user, but what would happen if you downloaded a trojan and ran it as sudo? i don't really understand how to install stuff yet with Ubuntu and it's likely i could download something from an unsafe place then run it as root. until i only use Synaptic Package Manager for installs and understand how safe installing things are, i should have real-time protection i think.

---

### Post by Danielle on 2005-11-27
[QUOTE=amohanty]I am sorry if I offended you, that was not the intent. 
ok the link on the page points to a tar.gz file which will take quite a bit of real estate to explain how to install properly. Try the following:

Goto: System->Administration->Synaptic Package Manager
Click on Search
type in clamav
install it and you should be ready to go.

NOTE: you might have to enable the universe repos to install this. Look at the wiki to figure out how to do so.

HTH
AM[/QUOTE]

no, i'm not offended, i'm sure you're right it seems most people here have the same view as you. i don't really understand Linux when i do i might change my mind. 

 i'm going to uninstall Clamav first. i know i installed Klamav but there's no sign of it. afew clamav commands work like:
clamscan and the switches for clamscan (-r /home, -r / etc) but freshclam doesn't work. i've only had a few hours sleep. i'm going to carry on abit later, i think i'll go mad if i try and install it now :|  thanks for your help  [img]http://ubuntuforums.org/images/icons/icon6.gif[/img]

---

### Post by amohanty on 2005-11-27
to completely remove any signs of klamav if it is not visible in synaptic do the following at the terminal:

sudo updatedb
locate -e klamav

if locate return all valid klamav files then you can do
rm -rf $(locate -e klamav)

or if locate returns other files as well individually delete all folders.

HTH
AM

---

### Post by mistergq on 2005-11-27
I too am trying to install klamav.  I got the GUI installer up, but then I get an error that it can't find the directory of my kernel.

Anyways, how does clamtk work?

---

### Post by amohanty on 2005-11-28
I think you ought to try and install clamav which is in the repos. the klamav installer from the klamav site woudl require you to build the app which may require you to tinker with the location of the kernel headers.

HTH
AM

---

### Post by arphe_el on 2005-11-28
please let me know the step on how you install the gui? thanks!

---

### Post by Danielle on 2005-11-28
[QUOTE=amohanty]to completely remove any signs of klamav if it is not visible in synaptic do the following at the terminal:

sudo updatedb
locate -e klamav

if locate return all valid klamav files then you can do
rm -rf $(locate -e klamav)

or if locate returns other files as well individually delete all folders.

HTH
AM[/QUOTE]
thanks for the help. the stupid thing never installed :(

arphe_el, there's something called clamtk in synaptic that's a frontend.

---

### Post by Danielle on 2005-11-28
i just installed it. i installed all the breezy files it would let me then marked clamtk too. it works perfectly. but, i don't think it runs in real-time.

---

### Post by rami on 2007-02-19
I just installed Klamav, and since there isn't much activity on the forum about this program, and a lot of questions are still unanswered, I decided my question here...

I successfully installed klamav using this guide [http://klamav.sourceforge.net/klamavwiki/index.php/FAQ#How_do_I_install_from_packages_on_Kubuntu_Edgy_Eft_.286.10.29.3F](http://klamav.sourceforge.net/klamavwiki/index.php/FAQ#How_do_I_install_from_packages_on_Kubuntu_Edgy_Eft_.286.10.29.3F)

Everything seems fine and its scanning and all, however whenever I enable autoscan, I get this message : "the auto-scan process died unexpectedly". I am really new to this program and I really don't know where the log files are to share with you guys....any help :)??

---

