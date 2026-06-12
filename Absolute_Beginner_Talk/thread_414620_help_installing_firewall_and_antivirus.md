---
title: "help installing firewall and antivirus"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by googlebytes on 2007-04-20
Screaming NooB here.
Ok, I guess I have firestarter on my Edgy machine already, but I would like the GUI, so I downloaaded the tar.gz file, but I did not know where to extracvt it to. When I opened a terminal and tried to type an install command, I get back a message that a firestarter file cannot be found. 
What am I doing wrong? Where should I extract the files to?

I also downloaded clamAV and Avast. Again how do I install? Thanks for putting up with this NooB.

---

### Post by greybirds on 2007-04-20
The Firestarter gui and ClamAV are both available in the repositories, so it's best to install them from there (you get automatic updates that way, among a lot of other nice things).

They're not available from Applications > Add/Remove but you can install them with Synaptic. Select System > Administration > Synaptic Package Manager.

They're not part of the main repository; they're part of the universe repo, which might not be turned on. Select Settings > Repositories from Synaptic's menu and look for a checkbox next to "Community-maintained Open Source software (universe)". If it's not checked, do so, then click the Close button.

Click the Reload button in the tool bar (this will retrieve the list of software available to install, including that in the universe repository you just enabled).

Now you can find Firestarter and ClamAV in the upper-right pane. Click the checkbox next to them and select "Mark for Installation". When you have both marked, click the "Apply" button in the toolbar under the menu. It will grind away for a while and then tell you the installation was successful (unless, of course, something went wrong).

Hope this helps.

---

### Post by freebird54 on 2007-04-20
The main use of these items is for protection of Windows installs you might come in contact with.  Firestarter will only enable you to OPEN ports and reduce your security if you wish/have a need to do so.

Clam AV will scan stuff that might come in contact with a Win machine in the future.  Neither is required for normal Ubuntu use....

Hope that helps!

---

### Post by orb9220 on 2007-04-20
> **freebird54 said:**
> The main use of these items is for protection of Windows installs you might come in contact with.  Firestarter will only enable you to OPEN ports and reduce your security if you wish/have a need to do so.

Clam AV will scan stuff that might come in contact with a Win machine in the future.  Neither is required for normal Ubuntu use....

Hope that helps!

Just as freebird said : You do not need any of those apps unless you are running a file,mail server and come into contact with window files. And even if one leaked into your linux system it would sit there not knowing what to do.

Ubuntu comes with ip tables installed which is the actual firewall. Firestarter is just the gui for it and does not need to be running. AntiVi programs are also not needed except as stated above for a server setup.

---

### Post by JT673 on 2007-04-20
They need to put a link to that article I read a month back...

The truth about Linux and Ubuntu is that you DON'T need AV and Firewall (unless you have Windows installed too, but I just unplug my comp every time I shut down).  There are maybe a dozen Linux viruses, and most of them aren't good enought to deal with the permission system.  Just focus on getting good Windows AV and firewall (if necessary), and try to not log in as root.  The root terminal and the sudo command, which bends the permissions system in that console, is there if you need it.

And, of course, we're here to help.

---

### Post by freebird54 on 2007-04-20
Here is a discussion of attempted Linus viruses - and why they don't work very well.  [http://linuxmafia.com/~rick/faq/index.php?page=virus#virus](http://linuxmafia.com/~rick/faq/index.php?page=virus#virus)

It is a long read - but interesting.  Essentially, the user has to do quite a lot for a virus to even run (give it permission, make it executable etc) and even then it can't spread easily (no Outlook to send from).  Even if you DO give it permission and execute it, it might very well not work, because LInux systems are unpredictable as to what they will be running for doing a given task - making assuptions about an buggy prog to work from iffy at best.  What with the ports all closed by default, 'social engineering' is the only valid pathway in - so a little common sense goes a LONG way!

---

### Post by googlebytes on 2007-04-20
Hey, thanks so much guys. I followed greybird's suggestions, and got the following errors:

E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured
E: clamav-getfiles: dependency problems - leaving unconfigured

now what do I do?

looks like firestarter may have installed correctly - do I access the GUI from firefox?

---

### Post by huestis on 2007-04-25
@Googlebytes:

I also am having a bit of trouble with ClamAV, however, the firestarter gui is in System -> Administration -> Firestarter.  Also, if you want to have an icon for it available at all times go into the preferences when you open Firestarter and select "Close to tray".

Hope this helps,

JR

---

