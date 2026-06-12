---
title: "How may I remove a Rootkit reported for a Windows 7 please"
date: 2013-04-12
forum: Any Other OS
---

### Post by welshmike on 2013-04-12
A friend of mine runs W7 on his PC. A month ago it started to run slugishly and this morning after the daily AVAST anti-virus update AVAST reported that his sytem was infected with a Rootkit and wanted to schedule a boot time scan. He did a boot time scan and AVAST reported four occurrences of the same file and he then had AVAST move these to its virus chest. He rebooted his PC but there was no change in its slow perfomanace. 

I read this way of removing a rootkit: [http://www.ehow.com/how_6506657_fix-windows-root-kit-ubuntu.html](http://www.ehow.com/how_6506657_fix-windows-root-kit-ubuntu.html) but it could be a scam. 

Advice welcomed please.

---

### Post by maglinu on 2013-04-12
Why not just recommend your friend to ask for help on the avast forum? They have some excellent malware removal experts there, who can suggest the correct tools (including linux live cd's if needed) for that rootkit.

---

### Post by mike acker on 2013-04-12
i would backup all his data, reformat his disk, and re-install windows. the rootkit may be in the MasterBootRecord: Use a low-level format on the disk.

---

### Post by welshmike on 2013-04-12
maglinu,

Thank you.

Having not used Windows for a while that did not occur to me. Durr!!!

---

### Post by welshmike on 2013-04-12
mike aker,

That would be my approach and have done it for other people's screwed Windows systems in the past.
I really did not want to impose on my friend all the Windows hassle of OS reinstall and reinstall of all the applications.

Pardon my ignorance about Low Level Formatting but having used Mr Google I found [this]("http://www.dedoimedo.com/computers/low-level-formatting.html") and am now "educated" ;) .

[I]P.S.
(It is really so friendly that Ubuntu makes things so much easier and in particular going from one release to another.
 I have dual boot of a previous 10.04 and current 12.04 LTS releases of Ubuntu that share the same /home.
 It is super that Ubuntu Software Centre contains most of the applications I need.)[/I]

---

### Post by jeffce on 2013-04-15
Might be too late but did you catch what type Rootkit that Avast detected?  Most...if not all...can be removed but the problem is the amount of damage done to the system prior to finding the rootkit...especially if dealing with Sirefef infection.  The use of aswMBR or TDSSKiller would probably be the best approach.  Hope that helps.

---

### Post by welshmike on 2013-04-15
My friend did tell me. It was a file containing a program that he never runs and was copied from his Documents folder on his old PC.
So it was a false positive but nevertheless he got AVAST to put it in its quarantine chest.

However his PC still runs slowly and it is time he got around to running Malwarebytes.

---

### Post by mike acker on 2013-04-15
> **welshmike said:**
> My friend did tell me. It was a file containing a program that he never runs and was copied from his Documents folder on his old PC.
So it was a false positive but nevertheless he got AVAST to put it in its quarantine chest.

However his PC still runs slowly and it is time he got around to running Malwarebytes.

windows PCs slow down over time. for one thing they tend to accumulate LOTS of junk files -- in the \temp area partcularly . I normally use PC Tools Reg Mechanic to perform the clean-up and this corrects registry errors as well

another thing-- the disk on a windows pc gets fragmented because windws tries to keep all data at the outter edge of the disk rather tha choosing to write into contiguous sectors when possible . so in addition to the junk clean up you need a defrag run .

the real question is : what is preventing this person from switching to Linux/Ubuntu ?  The new LibreOffice 4 is a significant improvement .

---

### Post by welshmike on 2013-04-16
Oh I do so agree about Windows slowdown in general. I've had so many calls from friends and associates needing help to fix such.
IMO it was a bad design decision to have a registry and the opportunity for applications to mismanage DLLs. Frag of NTFS is well known. Not so with ext4.

The above plus the origin of Windows being DOS and written as a stand alone opsys with later additions of code to handle networking produced a bodge job of an OS.
That's why I run a Linux distro; a networking system from its Unix roots :D
Currently Ubuntu 12.04 after years starting at 8.04 and holding onto 10.04 until now is coming along nicely for me.

Despite repeated entreaties my friend is averse to change and going to Ubuntu. Going from XP on his old PC to W7 on a new fast one was enough of a change for him. :(

P.S. I'm looking into running Malwarebytes and/or GMER and/or TDSSkiller to see what may be ailing my friend's W7.

---

### Post by mike acker on 2013-04-16
> **welshmike said:**
> Oh I do so agree about Windows slowdown in general. I've had so many calls from friends and associates needing help to fix such.
IMO it was a bad design decision to have a registry and the opportunity for applications to mismanage DLLs. Frag of NTFS is well known. Not so with ext4.

The above plus the origin of Windows being DOS and written as a stand alone opsys with later additions of code to handle networking produced a bodge job of an OS.
That's why I run a Linux distro; a networking system from its Unix roots :D
Currently Ubuntu 12.04 after years starting at 8.04 and holding onto 10.04 until now is coming along nicely for me.

Despite repeated entreaties my friend is averse to change and going to Ubuntu. Going from XP on his old PC to W7 on a new fast one was enough of a change for him. :(

P.S. I'm looking into running Malwarebytes and/or GMER and/or TDSSkiller to see what may be ailing my friend's W7.

I've had good results with Malware bytes .  Please though, ask client whay he cannot move th Ubuntu/ 12.04 LTS

I some cases, if they are running CAD or Photoshop or some kind of corporate policy then they may not have a choice. But for the basics Ubuntu covers it pretty good,--
[LIST]
[*]Browser: Firefox or Chrome 
[*]e/Mail Thunderbird ( can synch with an IMAP mail server ) 
[*]Office: LibreOffice 4 ( better compatibility w/ msft office now; still needs work ) 
[*]GEdit (text) 
[*]Images:
[LIST]
[*]Gwenview 
[*]RawTherapie 
[*]GIMP 
[*]KolorPaint 
[*]GScan2PDF 
[*]pdf shuffle reorganize pages in pdf(s) 
[*]openshot video edit 
[/LIST]
  
[*]Music
[LIST]
[*]Audacity 
[*]Audacious 
[*]Brasereo disk burn 
[*]VLC DVD player 
[/LIST]
  
[*]misc
[LIST]
[*]searchmonkey 
[*]ubuntu drop box 
[*]kazam screencaster 
[*]krename multiple file rename 
[*]clipit cut and paste saving program 
[*]krusader 2 pane file navigator 
[/LIST]
  
[/LIST]

local file sharing ( sambda) gets a huge black mark with a score of -50 for Ease of Use . it needs a gui editor to make it configurable and reliable

---

### Post by jeffce on 2013-04-16
Hi,

If your friend was getting a report from Avast about a rootkit I would run TDSSKiller to be on the safe side.  That is an actual rootkit removal tool.  GMER will give you notification of the rootkit and is very good at it but removal with TDSSKiller is easier.  

Malwarebytes (which is NOT a rootkit scan unless you download the MBAR Rootkit tool) could be your next option if there is no rootkit/bootkit detected followed by an online scan using ESET online scanner.

Here are some links if you like:

[IMG]http://i1224.photobucket.com/albums/ee380/jeffce74/TDSK.jpg[/IMG] Please download [TDSSKiller]("http://support.kaspersky.com/downloads/utils/tdsskiller.exe")

[LIST]
[*]Double click **TDSSKiller.exe**
[*]Press **Start Scan** but do nothing else as we are just looking for what is there.
[*]If Malicious objects are found, select **Skip** by changing the *Cure dropdown* in the upper right.
[*]Google search any entries found to be sure that they are actually infections...once complete, run TDSSKiller again and select Cure for the entries found to be malicious.
[LIST]
[*]*A copy of the log will be saved automatically to the root of the drive (typically C:\)*
[/LIST]
[/LIST]


-----------------------------

[IMG]http://i1224.photobucket.com/albums/ee380/jeffce74/mbam-3.jpg[/IMG] Please download [[COLOR=blue]**Malwarebytes Anti-Malware**[/COLOR]]("http://www.malwarebytes.org/mbam-download.php") to your desktop.



[LIST]
[*]Right-click and Run as Administrator **mbam-setup.exe** and follow the prompts to install the program.
[*]At the end, be sure a checkmark is placed next to **Update Malwarebytes Anti-Malware** and **Launch Malwarebytes Anti-Malware**, then click **Finish**.
[*]If an update is found, it will download and install the latest version.
[*]Once the program has loaded, select **Perform quick scan**, then click **Scan** as shown below.


      [IMG]http://i1224.photobucket.com/albums/ee380/jeffce74/MBAM-2.jpg[/IMG]
[*]When the scan is complete, click **OK**, then **Show Results** to view the results.
[*]Be sure that everything is checked, and click **Remove Selected**.
[*]When completed, a log will open in Notepad. Please save it to a convenient location if you would like the results reviewed.
[/LIST]





The log can also be found here:


**Windows 2000 & Windows XP**:
C:\Documents and Settings\<USERNAME>\Application Data\Malwarebytes\Malwarebytes' Anti-Malware\Logs


**Windows Vista & Win7**:
C:\Users\<USERNAME>\AppData\Roaming\Malwarebytes\Malwarebytes' Anti-Malware\Logs
----------

**[COLOR=blue]ESET Online Scanner[/COLOR]**


Go [[COLOR=red]**_here_**[/COLOR]]("http://go.eset.com/us/online-scanner") to run an online scannner from ESET.

Hope this helps.  :)

---

### Post by welshmike on 2013-04-16
mike acker,

With respect I don't need convincing how excellent Ubuntu is.
Some people and that includes my friend just will not listen to well balanced arguments.
So I think the solution is to leave his sytem alone in its W7 sad state and say I can do nothing with W7 but will install Ubuntu should he agree.

---

### Post by Elfy on 2013-04-18
*Thread moved to **Other OS/Distro Support**.*

---

### Post by 3rdalbum on 2013-04-19
Viruses and malware  don't typically make computers run slowly. It is much more likely to be something else on the system, or the usual Windows slowdown.

Only an idiotic malware writer would slow down the computers of their victims. It just alerts the victim that something is wrong, and they immediately reach for the anti-virus.

---

