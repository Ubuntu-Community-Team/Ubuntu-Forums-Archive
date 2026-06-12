---
title: "My Tasklist - various questions"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by dglp on 2006-04-30
I am working my way through various beginner's-type issues, and managing to answer some of them on my own, but would appreciate pointers from anyone. I have been compiling a list, and have copied it here. If you want to browse through it and answer any of the individual bits, I'd be glad for the assistance!

This list is categorised by broader topic, with the category in curly brackets. I've added answers to three of the questions. 

{Application Setup}
Installing applications from tarballs. Occasionally I find applications in places other than the repositories, such as some applications at [http://extragear.kde.org]("http://extragear.kde.org"). For example, a desktop manager called KConfigEditor links to kconfigeditor-0.9.6.tar.bz2 and kconfigeditor-0.9.6.tar.gz. I am trying to find out what to do with these files. Do I download them to my hard drive and point the repository manager at them? Do I need to extract the contents first? Should I add something to the Repository Manager that points to [http://extragear.kde.org?]("http://extragear.kde.org?") Is there a Kubuntu documentation page that explains this?


{Application Setup}
Why is it that I can hear CD recordings just fine, and can hear audio (.wav, .mp3, .ogg) using Beep Media player, but when I try to play **anything** using Amarok, I get a message that says 'not playable'? 


{Application Setup}
How to remove applications &#8211; specifically Amarok? **Answer:** Use Adept. Search on Amarok, Right-click on the entry, select Remove, then commit changes.


{Application Setup}
What do I have to do to record from microphone? I have set up Audacity, and can fiddle with the recording level settings, and with Kmix, but I do not get a satisfactory level. Most often I either get silence or an overdriven signal. The number of control settings is confusing, and I'm not sure which ones are producing the excessive gain. 


{Application Setup}
Open Office: how do I search on carriage/paragraph returns? In Microsoft the search string is ^p. What is it in Open Office?


{O/S Basics}
Special Keystroke Patterns: Ctrl+Esc, Ctrl+Alt+Backspace, etc. Is there a list of special keystrokes somewhere?


{Desktop Configuration}
Multiple taskbars: is there a way of distributing taskbars around the desktop? My taskbar is getting too crowded, so I want to split it and move the bits around the perimeter of the screen.


{Desktop Configuration}
Konqueror: Is there a cascading folder view option? The SideBar module has an expanding tree style of folder views, but I'm looking for something that works within the Konqueror window. Is there a setting I can change, or an extension to install?


{Desktop Configuration}
Konqueror: Why do my folder views always revert to the default even after I set them to Detailed?


{Desktop Configuration}
Dialogue Boxes: why do I have to mouse over a dialogue box for it to recognise my keystrokes? I would rather avoid using the mouse to select a given dialogue box. Is there a keystroke (~Ctrl+Tab) that will select successive boxes? Alternatively, can I disable the automated function?


{Desktop Configuration}
Oversized Dialogues: Some dialogue boxes extend off the bottom or sides of the display. For example, the Network Settings dialogue extends below the lower edge of the display, which means I cannot access the 'Administrator Mode' button. The box does **not** allow me to resize it, nor to move it upwards. There are other examples of windows /dialogues that extend beyond the edges of my display, and which I cannot adjust and gain access to. Why are these boxes doing this, and how do I get them to stop?  


{Networking}
How to connect to Internet via router. **Answer:** go to System Settings | Network Settings. Enable Administrator Mode, and if it recognises the LAN/WAN hardware, select a device and enable it.


{Networking}
Networking with TCP/IP: I have a network with manually-configured network addresses. How do I get Kubuntu to play? **Answer:** go to System Settings | Network Settings. Enable Administrator Mode, then using 'Configure Interface', 'Routes', and 'Domain Name System', set up the relevant DHCP/bootp, DNS, TCP/IP and other settings.


{Networking}
Access to printer on Windows machine: what do I have to do for my Kubuntu machine to see the shared printer?


{Networking}
Web server: how do I set up a machine as a web server?


{Networking}
Local area networking with Windows (2K Pro) machines. What are the necessary steps to ensure that the Kubuntu laptop and the Windows machines have access to files on each other's drives?

---

### Post by chriscando on 2006-04-30
[QUOTE=dglp]
{Networking}
Web server: how do I set up a machine as a web server?
[/QUOTE]

Use Synaptic to install apache or type 'sudo apt-get install apache2' in a terminal.  Then goto [http://localhost](http://localhost)  <- thats you!
Then you can also make a directory in your home folder called 'public_html' and can access the webpages there by going to [http://localhost/~your_username](http://localhost/~your_username)

---

### Post by dmacdonald111 on 2006-05-03
[QUOTE=dglp]
{Application Setup}
Installing applications from tarballs. Occasionally I find applications in places other than the repositories, such as some applications at [http://extragear.kde.org]("http://extragear.kde.org"). For example, a desktop manager called KConfigEditor links to kconfigeditor-0.9.6.tar.bz2 and kconfigeditor-0.9.6.tar.gz. I am trying to find out what to do with these files. Do I download them to my hard drive and point the repository manager at them? Do I need to extract the contents first? Should I add something to the Repository Manager that points to [http://extragear.kde.org?]("http://extragear.kde.org?") Is there a Kubuntu documentation page that explains this?
[/QUOTE]

For me, the easiest way is to download them to a dir called tar, change to that dir, uncompress so you have the dir, go into that dir and then ./configre. Once done, I delete the dir that was created and put the tar onto a DVDRW so I always have them :D

---

### Post by nanotube on 2006-05-03
for an excellent tutorial on how to install software, check out the second link in my signature.
there is a section on how to install from source tar.gz files, that you will find most helpful, i think. :)

---

### Post by dglp on 2006-05-05
Thanks to chriscando, dmacdonald and nanotube for the above. I haven't had time to follow through on these suggestions, but have browsed each and am looking forward to making progress on each!

I have been distracted by other issues, including problems with the re-installation of both Kubuntu and XP. Inevitably there are now more items for my Task List. So I'm adding them below for future reference/comments.

---

### Post by Rinzwind on 2006-05-05
q: {Networking}
Access to printer on Windows machine: what do I have to do for my Kubuntu machine to see the shared printer?

a: 
1. Choose &#8220;Network Printer&#8221; and &#8220;Windows Printer (SMB)&#8221;
2. put your Workgroup in the Host field
3. Put &#8220;guest@<host>/<printer>&#8221; in the Printer field (replacing <host> and <printer> with your host & printer names)


q: {Networking}
Web server: how do I set up a machine as a web server?

Read this for some install suggestions (also includes MYSQL):
[http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)

q: {Networking}
Local area networking with Windows (2K Pro) machines. What are the necessary steps to ensure that the Kubuntu laptop and the Windows machines have access to files on each other's drives?

a: "samba": install instructions are here: [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

---

### Post by dglp on 2006-05-05
**{System Maintenance}**
I have had misadventures in discovering how to sequence the reinstallation of XP and Kubuntu, and would like to develop an efficient method for backing up and restoring both, *including* backup and restore of the GRUB bootloader. 

At present I use the XP CD to reformat the drive, then reinstall XP, then use the Kubuntu CD to reinstall Kubuntu and the bootloader. However, I have noted that the bootloader is corrupted/wiped out whenever I do an XP repair, so I'd like to have  way of restoring that independently of doing the Kubuntu installation. 

Having read the ["HOWTO: Restore GRUB (if your MBR is messed up)"]("http://www.ubuntuforums.org/showthread.php?p=116936#poststop") thread and a few others, I am still looking for a way to back-up the bootloader. I am still working out the conceptual differences between and MBR bootloader and a root directory bootloader, and guess that a root bootloader would be easier to backup and restore. But I think my current installation uses an MBR option. So there's *that *to deal with in addition...

Suggestions?

** {System Maintenance}**
During one of my attempts to read the windows partition via kubuntu, I created a mount point that doesn't do anything, but which I cannot delete. I suspect that I created it via the Disk and Filesystems utility when I failed to replace <mount point> with something else in one of the options fields. 
[IMG]http://nunovo.zoto.com/img/45/10c7b31158e85adc8ac400d0435d9e5c-.jpg[/IMG]

Now it shows up every time I visit the home directory. How do I ret rid of it?
[IMG]http://nunovo.zoto.com/img/45/9cebae203897eeb5fd64c3a262694440-.jpg[/IMG]
* Note: there is an additional question about setting permissions so that I can make changes to files on the Windows partition. But I haven't gotten to that yet...

** {Ubuntu Forums}**
Is there a way of searching for an exact phrase? "phrase strings" and phrase+strings don't do anything other than return results of the individual words. So when I want to search on "backup GRUB" it returns all results for 'backup' and 'GRUB', which makes the trawling task much longer.

---

