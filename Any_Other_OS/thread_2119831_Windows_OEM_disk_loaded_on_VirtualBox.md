---
title: "Windows OEM disk loaded on VirtualBox"
date: 2013-02-24
forum: Any Other OS
---

### Post by Curbie on 2013-02-24
Has anyone been able to get XP to run on VirtualBox from a Windows OEM disk like a dell? 

I bought one from [http://www.softwareslashers.com/Windows-XP-Professional-W-SP3](http://www.softwareslashers.com/Windows-XP-Professional-W-SP3) and when it is time to boot it, it just reads the CD for a time, then just sits there, nothing ever comes to the screen.

I have an already licensed version of XP that installs fine in 30 day evaluation mode that I tested VirtualBox with, so I doubt it's VirtualBox and suspect the CD, but who knows?

---

### Post by cariboo on 2013-02-24
Moved to Other OS Talk, as this isn't an Ubuntu question

---

### Post by DuckHook on 2013-02-25
> **cariboo907 said:**
> ...this isn't an Ubuntu question

I suspect OP *was* asking an Ubuntu question: namely, how to install XP into an Ubuntu hosted VM.

@OP

According to MS, installing an OEM issued OS into a VM violates their licensing terms. A Dell OEM XP-SP3 disk will search the mobo for a Dell vendor code and if it does not find one, it's DRM will kick in and bork the install. SP1 and SP2 will install, but tell you that you are running an unlicensed copy of XP and refuse to activate. SP3 will not even install.

I happen to think that this is a completely idiotic policy, but then, that's why I run Linux in the first place. I am not permitted to tell you what workarounds exist, but it's no secret that Google will. You will have to decide on your own if any further attempts on your part violate MS's license.

---

### Post by PhilGil on 2013-02-25
My recollection is that Dell XP Pro disks are locked to the BIOS and  will only work on a hard disk install to a Dell machine. On my Dells,  I've always had to download a disk image (ISO) file to install XP in  VirtualBox. The good news is that the key should work if you torrent the  correct XP version.

In the interest of covering my posterior, using an OEM disk on a  computer it was not originally licensed to is a violation of the XP  EULA. Installing from a downloaded ISO instead of the original disk is  also a violation.

There is also some risk to using torrent downloads. However, I've used ISO torrents without incident in the past.
[I]
Mods, if I've violated forum rules please delete this post.[/I]

---

### Post by ACubed10 on 2013-02-25
I have windows xp installed in virtualbox.  I used my technet account (im a microsoft professional) to download the xp .iso.  Runs fine.

---

### Post by Curbie on 2013-02-25
P { margin-bottom: 0.08in; }   Hi Duckhook,
 

 I'm stilling trying to implement the single boot xUbuntu with XP running on VirtualBox suggestion that  many made on the thread about my XP to Ubuntu transition, if the site I bought that CD from was a scam selling pirated CD, I got scammed.
 

 I'm just trying to make transition to xUbuntu, I thought I was buying legal software because so many sites were selling the same thing (a Dell OEM XP-SP3 disk).
 

 Do you have a link for XP pro software that is't a scam and does work with VirtualBox or what I'd type into google for that work around?

---

### Post by ACubed10 on 2013-02-25
that's a tough one. Only place I'd suggest trying is straight from Microsoft.com  or maybe even newegg.com if they have any left

XP is very old.  Any reason you need XP?

---

### Post by DuckHook on 2013-02-25
I wouldn't go so far as to call it a scam. Likely, the SW is not pirated and would be perfectly legal if installed directly onto a Dell. However, if you take the same Dell, install Ubuntu on it, then VirtualBox, and then install XP inside Vbox, this violates the EULA. Some have argued that this is a "grey area". Bully on them. I admire and respect their spunk. Unfortunately, my own reading of MS's EULA is pretty clear: it's not allowed. Therefore, such an installation is technically in violation, although I would insist that it is a perfectly reasonable use of the software and is no violation in spirit. ...another topic for another day.

I can't give you detailed instructions even for a Google search that wouldn't potentially compromise me with our current, sad, DRM-police-state, but surely some obvious search terms come to mind? Try different combinations and permutations till you succeed!

---

### Post by DuckHook on 2013-02-25
> **ACubed10 said:**
> XP is very old.  Any reason you need XP?

I still run legal copies of XP in a VM for some ancient games and 10-year-old apps that don't need the latest. I'll be damned if I'm paying MS for anything more than I need to. And since I absolutely never surf, download, e-mail or interact with the outside world in any way, shape or form through XP means that its pending die-date is immaterial to me. I expect to be running it for the next 10 years. I suspect that the OP has a similar view and saw the chance to buy an OEM license as an honourable and upstanding way to do something beneficial to both parties. MS got a sale; he got a mostly obsolete OS that was all he needed but at a good price. This actually makes tons of business sense except in the topsy-turvy world of proprietary software.

---

### Post by Curbie on 2013-02-25
P { margin-bottom: 0.08in; }A:link {  }   [COLOR=#000000]ACubed10, [/COLOR]I just searched both MS's store and egghead and XP pro is not for sale at either, I don't need XP, I want XP, I have I band new (1 month old) win 8 system I just boxed up and put in the garage. I like the GUI on both xbuntu and XP, I value stability and function not flash.
 

 Duckhook, from the site I bought the disk from “**[COLOR=#000000][SIZE=2]DELL DISC BUT CAN BE INSTALLED ON ANY BRAND COMPUTER!”, a quote which can be verified from the link I posted in my first post of this thread, If that quote is not factual, it's a scam![/SIZE][/COLOR]**
 

 I've been trying to stay legal, but this transition is going to get done, somehow. Probably from from your patients and help in the other threads where I laid out my needs and reasoning for a new system configuration, but you assessment is right on track.

---

### Post by ACubed10 on 2013-02-25
> **Curbie said:**
> P { margin-bottom: 0.08in; }A:link {  }   [COLOR=#000000]ACubed10, [/COLOR]I just searched both MS's store and egghead and XP pro is not for sale at either, I don't need XP, I want XP, I have I band new (1 month old) win 8 system I just boxed up and put in the garage. I like the GUI on both xbuntu and XP, I value stability and function not flash.
 

 Duckhook, from the site I bought the disk from “**[COLOR=#000000][SIZE=2]DELL DISC BUT CAN BE INSTALLED ON ANY BRAND COMPUTER!”, a quote which can be verified from the link I posted in my first post of this thread, If that quote is not factual, it's a scam![/SIZE][/COLOR]**
 

 I've been trying to stay legal, but this transition is going to get done, somehow. Probably from from your patients and help in the other threads where I laid out my needs and reasoning for a new system configuration, but you assessment is right on track.
yeah I knew Microsoft stopped selling it.  Just didn't know if newegg had any copies left

---

### Post by Curbie on 2013-02-25
[COLOR=#000000]ACubed10, I still have the same problem of being stuck half way between function systems, 10 days now, any ideas?
[/COLOR]

---

### Post by DuckHook on 2013-02-26
Hi Curbie,

I'm noting that no one else has responded, so here is what you need to know:

1. The OEM copy that you purchased won't install in a VM because it is checking for (and will only install on) a Dell BIOS. Since your VM shows a VirtualBox BIOS to the OS, it is refusing to install.

2. However, the important thing here is your license key. That was properly purchased and is presumably still valid. Your problem is, you just need a CD that doesn't check for a Dell BIOS.

3. Such disk images are not illegal and the MS site itself allows you to download one. MS knows that without a legitimate key, you can't run the OS past 30 days anyway. It's the key that is critical, not the disk image.

4. You can download the ISO from the MS site [here]("http://www.microsoft.com/en-us/download/details.aspx?id=25129"). I found this site by simply Googling "windows xp iso download". You may wish to note my Google methodology. If you need to access further resources in the future, you simply phrase your query in a way appropriate to your needs (like I just did) and Google will return a ton of hits sorted in order of relevance. The MS site was at the top of my particular query.

5. You don't even need to burn this ISO to disk. VirtualBox can be configured to mount an ISO into its virtual CD drive so that it automatically boots. XP will then install as if it were installing on an actual computer.

6. Set up your VM properly before you run it the first time. If you mess up a setting, reinstall if need be without burning your key. It is important to get it right because XP chokes on changes to the VM after it has been installed. Knowing your needs somewhat, here are the settings I recommend (assuming your system has the resources to spare):
a. Give it two processors. Your heavy usage will make use of the 2 processors, but XP will not recognize more than 2 either.
b. Give it 4GB of ram. XP recognizes no more than 4GB, so max it out but don't waste any more on it either. You must turn on PAE before XP will recognize 4GB.
c. Give it half of your HDD space.
d. Give it 64 MB of video. You will find games rather slow, so do recreational stuff on Xubuntu instead.
e. Be sure to set a shared folder. I use my /home/duckhook/Public directory. Any files in this directory are now shared between your XP client and your Xubuntu host.

7. Run the VM and it should install. My XP installs take hours. Yours may take less time. The two processors will help, but be prepared for a long haul. This is another area where Xubuntu shines. My Xuubntu installs take 20 minutes.

8. Your biggest challenge will come when you must input the key. Because you purchased an OEM key, I don't know whether the XP install will allow activation. OEM keys work by recognizing the BIOS and automatically activating. However, if input manually into a mismatched system, you may have to phone up MS activation centre and activate manually. They may tell you that activation is permitted only on full licenses and OEM (read: discounted) versions don't qualify.

9. If so, you will either have to pay them for a full license key, or you will have to decide if you want to make use of the many workarounds on the net. The propriety of such action is up to you. I've already given you a good example of how to phrase Google requests. It is against forum policy to give help on something like this, so you are on your own here.

If you encounter difficulties setting up your VM or have further virtualization questions, I suggest starting a new thread in the virtualizing subforum. That's where all the VM gurus reside. Again, they will not be able to help you with "unofficial" XP activation. You are still on you own on that one.

Good luck!

---

### Post by coldraven on 2013-02-26
As mentioned above the Dell disc wil be checking the BIOS for some strings.
See here:
[https://www.virtualbox.org/manual/ch09.html#changedmi](https://www.virtualbox.org/manual/ch09.html#changedmi)
I have posted here on this before with a script that you run before trying to install XP.
I found it on the VirtualBox forum
Googling dmidecode and my name might help.

Now it is working I rarely use it, maybe I just wanted a challenge :p
As for legality, I paid for XP and I do not think that the EULA would stand in a European courtroom.
It came with this laptop and is running on it, what difference does it make if it is in a VM?

---

### Post by DuckHook on 2013-02-26
+1 coldraven

Wonderful tip. Thank you. Didn't know you could do that, but it makes sense that you would be able to.

Took up your suggestion and Googled "coldraven dmidecode ubuntu". Your thread was the second hit. For those interested, it is post #6 on the following thread:

[http://ubuntuforums.org/showthread.php?t=2070347](http://ubuntuforums.org/showthread.php?t=2070347)

> **coldraven said:**
> As for legality, I paid for XP and I do not think that the EULA would stand in a European courtroom.
It came with this laptop and is running on it, what difference does it make if it is in a VM?

+1 again. My thoughts exactly. Unfortunately, here in the DRM-police-state, sound logic isn't worth much.

How are things in Hyperborea? We are starting to thaw out here in Cimmeria.

---

### Post by Curbie on 2013-02-26
TD P { margin-bottom: 0in; }P { margin-bottom: 0.08in; }TT.cjk { font-family: "WenQuanYi Micro Hei",monospace; }TT.ctl { font-family: "Lohit Hindi",monospace; }   DuckHook & coldraven,
 

 Real helpful posts, I spent yesterday going though both notions, I downloaded the ISO from MS, pointed VM's “First Run Wizard's” “Media Source” to the ISO, booted, and got a “FATAL: No bootable medium found! System halted.” error, but I will search for other ISOs when I get time, today I have to setup racks for experiments (their closing in on me), and process the results of some time sensitive biological experiments.
 

 I spend time yesterday reading about about and playing with dmidecode I grabbed a dell dmidecode script to change the VM's Bios to emulate a dell:
 #! /bin/bash 
 VM_NAME="XP" # Name of your Virtual Machine 
 VSETED="VBoxManage setextradata $VM_NAME" 
 CFG_PATH="VBoxInternal/Devices/pcbios/0/Config" 
 $VSETED $CFG_PATH/DmiBIOSVendor       "Dell Computer Corporation" 
 $VSETED $CFG_PATH/DmiBIOSVersion      "A12" 
 $VSETED $CFG_PATH/DmiBIOSReleaseDate  "08/26/2004" 
 $VSETED $CFG_PATH/DmiBIOSReleaseMajor  2 
 $VSETED $CFG_PATH/DmiBIOSReleaseMinor  3 
 $VSETED $CFG_PATH/DmiBIOSFirmwareMajor 2 
 $VSETED $CFG_PATH/DmiBIOSFirmwareMinor 3 
 $VSETED $CFG_PATH/DmiSystemVendor     "Dell Computer Corporation" 
 $VSETED $CFG_PATH/DmiSystemProduct    "Dimension 4600i" 
 $VSETED $CFG_PATH/DmiSystemVersion    "<EMPTY>" 
 $VSETED $CFG_PATH/DmiSystemSerial     "JTGL999" 
 $VSETED $CFG_PATH/DmiSystemUuid       "99999C9C-9999-9999-999C-CAC99F999999" 
 $VSETED $CFG_PATH/DmiSystemFamily     "X86-based PC"
 

 I'm not trying to get it to register, just load, after I execute the dell Bios dmidecode script, and reboot, I get this error:
 

 Failed to open a session for the virtual machine **XP**.
 Invalid configuration for device pcbios device (VERR_PDM_DEVINS_UNKNOWN_CFG_VALUES).
 


  	 	 	 		 			Result Code:  			
 		 		 			NS_ERROR_FAILURE (0x80004005)
 		 	 	 		 			Component:  			
 		 		 			Console
 		 	 	 		 			Interface:  			
 		 		 			IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
 		 	  
I start a new virtual machine for every new try. Any ideas?

---

### Post by DuckHook on 2013-02-26
> **Curbie said:**
> ...I downloaded the ISO from MS, pointed VM's “First Run Wizard's” “Media Source” to the ISO, booted, and got a “FATAL: No bootable medium found! System halted.” error

On previous attempts, I recall that you had some issues with burning a CD (correct) vs copying the ISO file directly to the CD (incorrect). Please make sure that you burn the CD using brasero and try again. I know the ISO image can be directly attached to the VM using the settings in the graphical manager, but I don't set up my new VMs using the wizard, so can't tell you if the ISO is mounted before running (Linux must loop-mount the ISO to see the files inside, else same problem you had in the past). This whole unknown can be bypassed by burning a proper CD (which you probably want for safekeeping anyway) and installing it as you would to a real machine.

Can't help you with the script. I've never used it before, nor changed BIOS settings, so it remains only an interesting concept to me.

---

### Post by Curbie on 2013-02-26
P { margin-bottom: 0.08in; }   DuckHook,


Ok, loaded brasero with “Software Center”, rebooted, opened brasero, clicked the “Burn Image” button, pointed to MS's ISO for the “Select image to write”, loaded a blank cd, selected the cd for “Select a disc to write to”, and clicked the “Burn” button.
 

 Brasero goes through its burning image to cd, says success, starts creating image checksum, then says “Please eject the disc from “ATAPI DVD A  DH20A6L" manually.  
 The disc could not be ejected though it needs to be removed for the current operation to continue.”
 

 I click the only button “Cancel”, I guess canceling the checksum, then  brasero says “Image successfully burned to cd, and I hit the “Close” button.
 

 All discs have many files and directories on them, not just the .ISO file as before, I test two discs booting with both VirtuakBox and re-setup my system with a XP bootable hard drive, and no go for either.

---

### Post by DuckHook on 2013-02-27
You deserve a medal for the most tenacious cussed Xubuntu convert award. I'm sorry you keep butting your head up against a wall. You have my admiration for your sheer determination.

It seems that your MS download did not create a bootable disk. Everything up to the Cancel/Close process was done properly. Brasero is often unable to eject a disk and it must be done manually, but the burn is finished by then and everything should be good to go. Either the download was corrupted or, irony of ironies, MS issues defective ISOs.

I can only think of two things that you can do at this point: Try an ISO from "another" site, or work out the VM BIOS change needed to fool your Dell OEM disk into thinking it is installing onto a Dell. Someone else will have to step you through that. Hopefully, @coldraven is still following this thread.

---

### Post by Dr. C on 2013-02-27
> **DuckHook said:**
> I suspect OP *was* asking an Ubuntu question: namely, how to install XP into an Ubuntu hosted VM.

@OP

According to MS, installing an OEM issued OS into a VM violates their licensing terms. A Dell OEM XP-SP3 disk will search the mobo for a Dell vendor code and if it does not find one, it's DRM will kick in and bork the install. SP1 and SP2 will install, but tell you that you are running an unlicensed copy of XP and refuse to activate. SP3 will not even install.

I happen to think that this is a completely idiotic policy, but then, that's why I run Linux in the first place. I am not permitted to tell you what workarounds exist, but it's no secret that Google will. You will have to decide on your own if any further attempts on your part violate MS's license.

IANAL The Windows XP license terms are silent on the subject of running an OEM version of XP in a virtual machine on the **same** computer, instead of running it directly on the hardwre. The Windows Vista and Windows 7 terms explicitly allow it. The Windows 8 terms explicitly forbid it. [http://www.microsoft.com/en-us/legal/intellectualproperty/UseTerms/default.aspx]("http://www.microsoft.com/en-us/legal/intellectualproperty/UseTerms/default.aspx"). Software licenses are legal contracts, so the first step is to actually read the license rather than blindly clicking &#8220;I agree&#8221;. The next step is to actually read the relevant copyright legislation in your jurisdiction since it may give you rights not in the license. Asking Microsoft will likely only give one their position on the contract in a non binding fashion.  If one needs legal advice then one needs to talk to a lawyer.

Now for the technical part. I have done this with Windows 7 Pro with an HP OEM disk. It installed correctly but entered into a 3 day failed activation state. One has to manually change the key to the key provided on the sticker on the computer and reactivate and then it activates fine. This is because large OEM Windows XP/Vista/7 disks come with a pre-activated key that is tied to the OEM bios. This key is not the key provided to the end user on the computer. I have not tried this with XP but I suspect the behaviour will be the same. It will install but require reactivation with the key on the computer.  

One final note with running Windows XP/Vista/7 in a virtual machine under VirtualBox. Do not activate until after the guest additions are installed and one has finalized the parameters of the virtual machine, since changing the virtual machine or installing the guest additions is a hardware change as far as Windows is concerned and may trigger reactivation.

---

### Post by Curbie on 2013-02-27
P { margin-bottom: 0.08in; }   DuckHook,
 

 Thanks, I just don't think MS's ISO is bootable, it launches fine from  a running XP, but won't boot there either. But still, I may be able to boot VM using the XP sp1 (I need at least sp2) I've been using to test VirtualBox, then use that XP to to launch MS's ISO, but I couldn't determine if it was XP pro when I downloaded it.  
 

 This has to get done, I can't abandon 25 years of work I did using MS apps, I also refused to be abused by them anymore, I will get this figured out, one way or the other.
 

 I may ask the VM BIOS question on the VM sub-forum.

---

### Post by coldraven on 2013-02-27
Two tips:

After creating a virtual HDD run the bios script.
If you  to do it after installing, XP will not activate

AFAIR you can point to an .iso file from within VirtualBox, it saves burning a disc
The little icon to the right of the disc select thingy.  (sorry, no VBox on this machine)

---

### Post by coldraven on 2013-02-27
> **Curbie said:**
> P { margin-bottom: 0.08in; }   DuckHook,
 

 Thanks, I just don't think MS's ISO is bootable, it launches fine from  a running XP, but won't boot there either. But still, I may be able to boot VM using the XP sp1 (I need at least sp2) I've been using to test VirtualBox, then use that XP to to launch MS's ISO, but I couldn't determine if it was XP pro when I downloaded it.  
 

 This has to get done, I can't abandon 25 years of work I did using MS apps, I also refused to be abused by them anymore, I will get this figured out, one way or the other.
 

 I may ask the VM BIOS question on the VM sub-forum.


The only disc that came with this laptop is a multi language HP Restore disc. It has no serial numbers on it and the sticker on the laptop is for Vista Business edition. I bought it especially because it was a "downgrade"from Vista. (the serial does not work for XP)

AFAIR I used nlite to slipstream SP3 into the disc and just keep the iso on an external drive.

I spent days getting it to work and mostly use Windows for Sketchup.

I impressed the hell out of a windows nerdy friend when I span the compiz cube with XP running fullscreen on one face and movies etc. on the other three.
It was worth the time and effort just to see his face :)

---

### Post by Curbie on 2013-02-27
DuckHook,

Last night I setup a VM just to test that MS ISO, it's just sp3 no XP and it require sp1 to load, I'll look for sp1 today.

coldraven,

When I setup a new VM and try the to load dell cd I bought with the First Boot Wizard, the dell cd reads for a while then just stops with no errors, I'm guessing that the install program sees that the hardware bios is not dell and stops.

Then I setup a new VM, run the the dell bios script
#! /bin/bash
VM_NAME="XP" # Name of your Virtual Machine
VSETED="VBoxManage setextradata $VM_NAME"
CFG_PATH="VBoxInternal/Devices/pcbios/0/Config"
$VSETED $CFG_PATH/DmiBIOSVendor       "Dell Computer Corporation"
$VSETED $CFG_PATH/DmiBIOSVersion      "A12"
$VSETED $CFG_PATH/DmiBIOSReleaseDate  "08/26/2004"
$VSETED $CFG_PATH/DmiBIOSReleaseMajor  2
$VSETED $CFG_PATH/DmiBIOSReleaseMinor  3
$VSETED $CFG_PATH/DmiBIOSFirmwareMajor 2
$VSETED $CFG_PATH/DmiBIOSFirmwareMinor 3
$VSETED $CFG_PATH/DmiSystemVendor     "Dell Computer Corporation"
$VSETED $CFG_PATH/DmiSystemProduct    "Dimension 4600i"
$VSETED $CFG_PATH/DmiSystemVersion    "<EMPTY>"
$VSETED $CFG_PATH/DmiSystemSerial     "JTGL999"
$VSETED $CFG_PATH/DmiSystemUuid       "99999C9C-9999-9999-999C-CAC99F999999"
$VSETED $CFG_PATH/DmiSystemFamily     "X86-based PC"

… before running the First Boot Wizard, and then when I run the First Boot Wizard the cd reads for a second and stops immediately with the error:
Failed to open a session for the virtual machine XP.
Invalid configuration for device pcbios device. (VERR_PDM_DEVINS_UNKNOWN_CFG_VALUES).

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb} 

It seems like the script is hammering a value in the VM bios because I'm getting the error from VirtualBox not Windows or dell on boot, I got the script by searching for “VirtualBox dell dmidecode”, and if the script was correct or I was doing things correctly, it seems the dell cd would read for a while like it does when I don't run the script.

To my eye that would mean that that something is wrong with the script or the way I'm executing it, I've only been using xUbuntu for 17 days, and it's been ~25 years since I monkeyed with unix (Brerkley 6 or 7), so who knows what I'm doing wrong.

I too use Sketchup, it's one of the three programs I need XP for.

---

### Post by DuckHook on 2013-02-27
I think I might see your problem: did you download just the service pack and not XP itself? If so, then it would account for why you can't boot with it... there is no XP operating system. Just a guess on my part, but you should check it out.

Also, I didn't know till now that you had XP-sp1! Why not just use that to install? After it installs successfully, it will just go online and update itself--first to sp2, then to sp3, along with what seems like a thousand security updates since sp1 was released. You can use your newly purchased OEM license key to activate when you judge that you've got everything set up to your complete satisfaction.

Or am I missing something here?

<edit>
I just re-checked the MS link, and indeed, it is only the service pack--no operating system. Apologies for sending you on a wild goose chase.

Still curious as to why you can't just use your old XP disk and use the new key though.
</edit>

---

### Post by Curbie on 2013-02-27
DuckHook,

I ask the simple question “Can this be done” in some of my biological experiments, and the yes or no answer can take months to get, and most of time the answer is no, that didn't even come close my definition of a “wild goose chase”, no problem.

This xUbuntu and VirtualBox stuff is all new to me, all I can do is try the suggestions and see what I can learn from them, like I said, this transition HAS to get done, and I will get there somehow.

The bootable XP I've been testing with is old, and I misspoke when I said it was sp1, it's not even sp1 and Sketchup requires at least sp2 to load, it survived to purge of what I would take when I moved because it wasn't filed with the spool of OSs I threw out before the move. At one time I had 13 licensed XP machines running in what was my dining room, with Norton anti virus.

In December last, I got a virus, and after spending two days to get through Symantec support maze, I was informed the protection I had been paying for these years only “helped” you to prevent viruses, but now that had one it's my problem that they would remove it for a fee.

Bye bye Symantec, I spent time removing the virus and bought Avast which found another virus that found it's way to two drives that norton didn't even report, I wasn't happy.

That repaired configuration ran for about two week before the HP machine died (probably the on board video controller), so I bought the machine I'm now running on as a fix for that.

When I boot up with the hard drive that was in my HP, XP refused to boot with a HP factory loaded “Code Purple” bomb, and when I fixed that MS piled on and reported that the OS wasn't valid for the machine, so I threw it into 30 day eval mode.

I bought a band new Win8 for communication while I was recovering by original XP setup and 25 years of work, I hated Win8 so much that the new machine is in the garage now collecting dust where it belongs.

As I said before, everybody had a sob story, I just fix problems, and move on, but in pondering that chain of events, MS is the probem, not for protecting their OS, but for knowing about serious security flaws in the OS for 20 years, and profiting from them at the expense of their customer base, instead of fixing them.

Those security flaws can be fixed, Ubuntu doesn't have them, all those companies seem to conduct their business practices just within the law, despite the serious consequences that those business practices can have on their customers, and I can no longer support it.

---

### Post by DuckHook on 2013-02-28
[Here]("https://www.virtualbox.org/manual/ch09.html#changedmi") is the VirtualBox manual page with instructions on how to change the DMI. Perhaps you can change each variable manually rather than running a script. That way, you will be able to see which step chokes your procedure.

I also encourage you to post in the VirtualBox forums where they specialize in addressing VMs.

---

### Post by Curbie on 2013-02-28
Ok, just an update, after reading all I can on the **dmidecode scripts to set Virtualbox bios to emulate a Dell, I was able to download three, and tested VM with each line manually by line with the terminal verifying that each line was properly set in the VM's bios with “VBoxManage getextradata”, but XP fails to boot with all three scripts.**
 

 **So figuring that Virtualbox is operating properly because is boots with my test XP, I pulled the xUbuntu drives out of my machine, put the XP drive running in 30 day eval back in, and tried to boot the cd from hardware, and when trying to boot from hardware, the boot sequence displays a “General Protection Fault”, bad cd.**
 

 **So I went back out to web site which is now down for repairs, then called their customer support line which said their experiencing difficulties and to leave a message, so now I wait for a callback.**

---

### Post by DuckHook on 2013-02-28
*sigh*

Lordie, Lordie. You have my sympathies.

You've been wrestling with a bad CD all this time.

Let us know how it goes.

---

### Post by coldraven on 2013-03-02
Just in case any of this info is of use.
As I said above, this laptop had XP pre-installed and for a while I dual booted with Ubuntu.
Before I removed XP I used some Windows program which trawled through the registry and recovered two different serial numbers.
So with the Vista sticker on the base I now had three completely different numbers.
My restore CD would boot and install into VBox but when I ran the XP VM it would get to the windows desktop and start asking to be activated.
None of the serials that I had would make it work.
That is when I realised that I had to create a fake BIOS **before** installing XP, then it just activated itself, no need for any of the serial numbers.

Tip of the day!
When you get this to work and XP has done it's zillion updates do a VBox>Export VM to an external drive.
The Export function always says at the beginning that it will take two hours but actually takes about 10mins. :)
Then if or when XP becomes borked you can just delete it and re-import your shiny new XP installation.
You can also take "snapshots" in VBox but I like to have the option of a complete backup.

Good luck, I hope it all works sooner rather than later.

---

### Post by Curbie on 2013-03-02
Coldraven,
 

 If you keep knocking down the problems one by one, no matter how many, eventually there will none left standing in the way. A big problem got knocked down today. I got through to the place I bought my cd from, and the guy there went out of his way to burn and send me an ISO file to replace my bad cd, and solved my VM boot problems.
 

 I'm back to testing Virtualbox's setup with XP before I activate XP because it seems some of the Virtualbox's stuff doesn't like to be change after you install XP, and I what to make sure everything is correct before I activate XP.

 

 I'll write up, post my solution, and close out this thread when I this fully set up.
 

 Thanks for your help.

---

### Post by Curbie on 2013-03-03
[SIZE=3]I have xUbuntu 12.04 LTS amd64, running on a 3 core AMD with 8gb of ram, and 1tb of disk; here is the setup I used to configure Virtualbox running XP. The version of Virtualbox I downloaded with the Software Center was 4.1.12, and the latest version on the Oricle site[/SIZE]
 

 [SIZE=4][SIZE=3]1[SIZE=3])[/SIZE] I downloaded and installed and Virtualbox and [/SIZE]**[SIZE=3]Extension Pack [/SIZE]**[SIZE=3]version 4.2.## [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) [/SIZE][/SIZE] 

 

 [SIZE=4][SIZE=3]2[SIZE=3])[/SIZE] I bought a Dell OEM cd from [http://www.softwareslashers.com/Windows-XP-Professional-W-SP3](http://www.softwareslashers.com/Windows-XP-Professional-W-SP3) (I had bad mouthed this company in previous posts, for which I apologize for, the disk turned out to be bad, and they went out of their way to burn and send me a replacement ISO)[/SIZE][/SIZE]

 

 [SIZE=3]3[SIZE=3])[/SIZE] I started a new virtual machine in Virtualbox using DuckHook's recommendations.[/SIZE]

 [SIZE=3]a. Give it two processors. Your heavy usage will make use of the 2 processors, but XP will not recognize more than 2 either. (I also had to check “Enable IO to APIC” to keep Virtualbox from popping a warning.)
b. Give it 4GB of ram. XP recognizes no more than 4GB, so max it out but don't waste any more on it either. You must turn on PAE before XP will recognize 4GB.
c. Give it half of your HDD space. (I make the disk 50gb to make sure I don't get lazy on the fullest transition to xUbuntu as possible)
d. Give it 64 MB of video. You will find games rather slow, so do recreational stuff on Xubuntu instead.
e. Be sure to set a shared folder. I use my /home/duckhook/Public directory. Any files in this directory are now shared between your XP client and your Xubuntu host.
[/SIZE]

 [SIZE=3]4[SIZE=3])[/SIZE] Ran this script:[/SIZE]

 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" "Dell Inc." [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" "1.0.3" [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseDate" "06/20/2008" [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseMajor" 2 [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseMinor" 1 [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSFirmwareMajor" 2 [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSFirmwareMinor" 1 [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" "Dell Inc." [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct" "Vostro 410" [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemVersion" "<EMPTY>" [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemSerial" "DJX9DH1" [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemUuid" "44454C4C-4A00-1058-8039-C4C04F444831" [/SIZE] 
 [SIZE=3]VBoxManage setextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemFamily" "" [/SIZE] 
 

 … [SIZE=3]and you can check the variables with:[/SIZE]
 [SIZE=3]VBoxManage getextradata "XP" "VBoxInternal/Devices/pcbios/0/Config/VARIABLENAME [/SIZE] 
 [SIZE=3]5[SIZE=3])[/SIZE] Started the new virtual machine with Dell OEM cd[/SIZE]

 

 [SIZE=3]6[SIZE=3])[/SIZE] Whenthe XP install[SIZE=3] [/SIZE]i[SIZE=3]s[/SIZE] done and registered, with the Virtualbox window running XP still open, install Virtualbox “Guest Additions” from Virtualbox's “Devices” dropdown[/SIZE]

 

 [SIZE=3]I spent time today loading all my data that I accumulated over 30 years and thinking about a way to better organize it to suit this new configuration, this is a big task and and I will do most of it over time. Now on to system maintenance.[/SIZE]
 

 [SIZE=3]Thanks to all that helped, this was a very important piece of of my configuration puzzle.[/SIZE]

---

### Post by sudodus on 2013-03-03
Congratulations :KS

This thread was way out of my territory, I'd rather go wild goose hunting ;-)

[COLOR=#696969](Some years ago, when it was still possible to buy Windows XP, I installed it without problems into VirtualBox in Ubuntu 8.04 LTS. This *VBoxWinXP* has survived upgrading to 10.04 LTS and 12.04 LTS.)[/COLOR]

---

### Post by coldraven on 2013-03-04
> [SIZE=3]I spent time today loading all my data that I accumulated  over 30 years and thinking about a way to better organize it to suit  this new configuration, this is a big task and and I will do most of it  over time. Now on to system maintenance.[/SIZE]

Congratulations! Hopefully that is the last MS product you will ever need to buy :)

---

### Post by Curbie on 2013-03-05
> **coldraven said:**
> Congratulations! Hopefully that is the last MS product you will ever need to buy :smile:
After weeks of struggling to get MS's OS hooks out of me and save 25 years of MS application produced data, it's certainly the last MS machine I'll ever buy, who knows what applications MS will buy and monopolize in the future, but as long as it runs on XP and doesn't require Internet access, I'll do what it takes to get the job done until something comes along to replace it.
 

 MS insisted that I make this transition to xUbuntu and who am I to argue with MS, they've known about security flaws in their OS the decades, but instead of fixing them (Ubuntu doesn't have them, so they can be fixed), they profit from the misfortune of their customers.
 

 When you setup Windows so it can't can't call MS, the OS hounds you daily (“your system is at risk”), but MS doesn't hound you daily or even once to make a recovery disk, MS profits if you have to buy a replacement OS, and viruses certainly can cause OS reloads, I no longer can (or have to) support MS's business practices.  
 
Thanks for your time and help.

---

### Post by Curbie on 2013-03-05
Now that my new configuration has been up and running for a few days, I like to publicly thank Duckhook and sudodos for all their time, recommendations, and help with configuring and system, it is operating very transparently.
 

 I always felt, that if I put one foot in front of the other, eventualy, I'd get to where I'm going, and now that I'm there, I'm starting to forget the work it took to get here. I'm already starting to focus on alterative engery experiments again, so I wanted to say this before I'm engrossed it that.

---

### Post by DuffPaddy on 2013-03-12
What an extremely useful thread this has been; thanks to all who've contributed. Excellent, clear advice and an OP who just wouldn't quit. ;)

I'm looking to do a similar thing myself, but with the following differences. I wonder if anyone could advise if this might present problems.

The main PC I used to use for work in my home office, an old Fujitsu-Siemens Esprimo, recently had its motherboard fried. So I've taken the hard disk out and grabbed the essential files I need and I'm back working on my new machine. However, for various reasons I'd like to have a go at making a virtual machine from my old system (which ran XP).

Of course, the problem is that the machine won't even boot as far as the BIOS, which makes it impossible to run dmidecode, even from a live disc. Fortunately, a colleague has exactly the same PC model and is going to send me a copy of the output from running dmidecode (Windows version) on his machine. So I'm hoping that I can use coldraven's trick to change the VirtualBox BOIS settings as required to mimic an Esprimo. I'll then either use the Esprimo's recovery disc or (better still, if it works) a CloneZilla copy I made of the Esprimo's hard disk to hopefully recreate my old PC in a VirtualBox guest machine as best I can.

The only thing that worries me is the DmiSystemSerial and DmiSystemUuid settings, as these won't be the same as on my PC. So my question is essentially, will this matter? Are these fields typically checked by an OEM installation, and if so, will it invalidate the EULA to be running my new VM at the same time as my colleague's PC is online?

(Apologies that my first post here is in the "Other OS/Distro" forum, but this was by far the best and most recent thread I could find on the subject. Oh and my main job is as a Linux sysadmin, so I'll be sticking around here.)

---

### Post by Curbie on 2013-03-12
I'm certainly not an expert, but MS may look at the DmiSystemSerial and DmiSystemUuid for authentication, I really don't know, but if they do, your fears may be justifiable. I'd just buy a Dell OEM cd, I've seen them as low as $17.00 on Google Shopping.
 

 I don't let XP communicate with the Internet at all, Internet communications only can happen with xUbuntu, the one and only time I let XP communicate with the Internet was to register, and now that reregistration is done, XP is only lives off-line.
 

 XP cries twice when it boots up that it can't call MS, once that my “System may be at risk” then to “To keep my computer up to date”, but XP is pretty stable after 10 years and I'm not ever planning to let MS “update” it.
 

 Good luck, I'm happy with my xUbuntu/Virtialbox XP configuation.

---

### Post by DuffPaddy on 2013-03-13
Thanks, Curbie. I'll hopefully be giving this a try later today.

Now that I've slept on it, though, I think maybe what I can do is to use the values of [COLOR=#000000]DmiSystemSerial and DmiSystemUuid from my own host PC, and all the other settings from my colleague's Esprimo. But I'll play around with the settings, see what works and report back.[/COLOR]

---

### Post by coldraven on 2013-03-13
@DuffPaddy
This is from memory so it will be a bit vague.
If you dig into the folders on the OEM disc you will find one called Fujitsu.
In the folder are some strings.
My guess is that it makes a hash of the makers string and some of the BIOS strings and uses that for activation.
I tried once to use my Restore disc in a different brand computer and it immediately knew that it was from a another manufacturer so it must check those strings first.

One thing is certain. Before XP is unsupported in 2014 I will let it do a full update and then lock the VM in a lead lined box under my bed and never let it near the internet again ;)

Good luck!

---

### Post by Curbie on 2013-03-13
DuffPaddy, if you have your old Esprimo [COLOR=#000000]DmiSystemSerial and DmiSystemUuid, I'd try that with your original [/COLOR]Esprimo [COLOR=#000000]recovery disk first, that should already be authenticated with MS[/COLOR], and I would think of could test the recovery disk to see if it thinks the virtual Esprimo is it's factory configuration off-line. I'll have to read just what MS is claiming to fix in their last release, since I have backups of my Virtualbox files, I might consider a final update, but XP already does everything I need it to.

I'll certainly be interested to heard how it goes.

---

### Post by DuckHook on 2013-03-13
If I understand you correctly, you are trying to port an existing XP OS originally installed on a specific hardware box by hitching up the old HDD to a new box and just asking VirtualBox to use the old installed OS as its Virtual Machine image? If this is not what you are trying to do, then please ignore what follows.

This is possible, but very tricky, very risky and involves magic wands and fairy dust. The problem is that, in your case, it isn't just a matter of changing a few serial numbers and User ID settings. Your original system was installed with XP OS settings based on actual hardware, whereas your intended VM creates very different "hardware". Linux is hardware agnostic, but XP is not. In fact, XP is very hardware specific, in large part, to prevent exactly the easy portability from one system to the next the you desire (I suspect this is part of MS's antipiracy paranoia). VirtualBox can be set up to run its virtual machine from an actual HDD using the RAW disk setting, but XP will detect that your mobo has changed, your HDD is a different, your CPU count may have changed and consequently refuse to run.

You can work around these things, but the procedure is not for the faint of heart and instructions are on the VirtualBox site [here]("https://www.virtualbox.org/wiki/Migrate_Windows").

Be warned going in: many have hosed their Windows install by unsuccessfully trying to do this port. If you consider your Win install a lost one already, then I suppose that there is nothing to be lost by trying.

I highly recommend that you extract your Licence activation key from Windows before you start. This will allow you to install a fresh XP OS should your porting attempt not succeed. I don't remember the precise process for doing this, but it can easily be found by Googling for it.

Good luck!

---

### Post by DuckHook on 2013-03-13
> **Curbie said:**
> I might consider a final update, but XP already does everything I need it to.

Hi Curbie:

Good to see everything worked out for you. Without question, you've been the most tenacious and determined new user I've ever helped out on these forums and you deserve the success. Just a brief suggestion: I intend to keep updating XP up to its very last die-date (April 8, 2014) after which I will disable the virtual NIC in the VM and thoroughly isolate it from the big bad world out there. Until then, I will continue to take advantage of the MS support I've already paid for. You may wish to do the same because many of the updates are not just security but bug fixes that may allow apps to run better. ...just my further two pennies.

---

### Post by DuffPaddy on 2013-03-13
@Curbie: Sadly I don't have the original UUID from the box, as it won't boot at all now. I do have the serial number though, from the label on the box, and I've added that to the VBox BIOS settings, along with all my colleague's, which I now have. Regarding my colleague's settings, I notice that my serial number is only a few higher than his. Now this is probably laughably naive, but could I calculate my original UUID by adding that same difference (in hex) to the end of his UUID? I would assume that manufacturers do this sort of thing in bulk, but I don't know whether it's as simple as everything being sequential like that. Failing that, I suppose it must be recorded on my old hard disk somewhere.

For an initial test though, I've changed the VM's BIOS settings as best I can, with the UUID set to all Fs for now. It's certainly installed from the OEM disc OK, and seems to be working, but I've not attempted to register or perform any updates yet.

@Duckhook: Hmm, it looks like my next attempt, attempting to load up a VM from a clone of my hard disk, might be trickier than I thought. I knew there'd be hardware issues to overcome, but I thought I might somehow be able to go into safe mode and replace the appropriate drivers. I'll try it and if it's too tricky I'll leave it alone and stick to the base XP installation. I'm not working on the original hard disk though, only a clone of it, so I can't scupper that.

As an aside, how on Earth do those people who buy an OEM disc from eBay and try to install it on real hardware get on? I would imagine it would be a lot trickier to have to change real BIOS settings, most of which are surely not modifiable from the menu.

---

### Post by Curbie on 2013-03-13
Duckhook,

I always felt, that if I put one foot in front of the other, eventually, I'd get to where I'm going, and now that I'm there, I'm starting to forget the work it took to get here. It's the “here” that's important, what it took to get here is not.

I'm reorganizing where and how I store my data between the stuff that works transparently on xUbuntu and the stuff that must live on XP, this will take a while, but at least I can get done what I need to get done in XP while I test and learn how to get my data into a suitable xUbuntu application. Thanks for all your time and help, your configuration suggestion is working as advertised and was worth the effort.

PuffDaddy – I hear you with wishing I had my dead HP's bios settings, if you have the time and interest to play, you can try to see if you could calculate your original UUID, but I would think that would only work if the hex representation of your colleague's DmiSystemSerial matches his ascii S/N, I never played with the bios settings of a factory loaded machine so I really don't know where or how those numbers are used, or you could just try a few in that known range of S/N hunting for one that's already authenticated, but the machine is no longer in use.

---

### Post by coldraven on 2013-03-13
there is an other way
hang out at a recycling centre, fairly soon someone will dump a PC with a valid XP sticker on it.
Bingo!

---

### Post by DuckHook on 2013-03-13
> **coldraven said:**
> there is an other way
hang out at a recycling centre, fairly soon someone will dump a PC with a valid XP sticker on it.
Bingo!

:lolflag:

---

### Post by DuffPaddy on 2013-03-14
Well, one OEM install, 2 Service Packs and 125 updates later, here I am with a working Windows XP virtual system! I even ran Windows Genuine Advantage and it passed all the tests without problem. So either it's not checking that UUID or it doesn't care about it. And after reading the article DuckHook linked to, I'm not even going to attempt restoring my cloned system. I'll build it up step by step from this base instead.

For future reference, here's the batch file I used to the get the ball rolling. It's a variation on the bash scripts posted earlier.

```
set VM_NAME=Esprimo
set VSETED="C:\Program Files\Oracle\VirtualBox\VBoxManage" setextradata %VM_NAME%
set CFG_PATH=VBoxInternal/Devices/pcbios/0/Config
%VSETED% %CFG_PATH%/DmiBIOSVendor       "FUJITSU SIEMENS // Phoenix Technologies Ltd."
%VSETED% %CFG_PATH%/DmiBIOSVersion      "5.00 R1.20.2334"
%VSETED% %CFG_PATH%/DmiBIOSReleaseDate  "12/20/2005"
%VSETED% %CFG_PATH%/DmiBIOSReleaseMajor  ""
%VSETED% %CFG_PATH%/DmiBIOSReleaseMinor  ""
%VSETED% %CFG_PATH%/DmiBIOSFirmwareMajor ""
%VSETED% %CFG_PATH%/DmiBIOSFirmwareMinor ""
%VSETED% %CFG_PATH%/DmiSystemVendor     "FUJITSU SIEMENS"
%VSETED% %CFG_PATH%/DmiSystemProduct    "ESPRIMO E"
%VSETED% %CFG_PATH%/DmiSystemVersion    ""
%VSETED% %CFG_PATH%/DmiSystemSerial     "(my old system's serial number)"
%VSETED% %CFG_PATH%/DmiSystemUuid       "FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF"
%VSETED% %CFG_PATH%/DmiSystemFamily     "103C_5336AN"

```

Ideally though, I guess you'd want to fill in that UUID if you could find it. Also, I'm not sure whether I should have split that BIOS version up into major and minor releases.

As regards the valid XP sticker, I already have one of those! I've lifted of off the old case. Unfortunately, over time the last couple of characters have been scratched off, but I'm hanging on to it for proof that I have a genuine licence anyway.

Many thanks for all your help on this one, folks!

---

### Post by Curbie on 2013-03-14
Great job!

---

### Post by gtippitt on 2013-03-28
I just got a new laptop I found on sale.  It came Win8, with I would replace with XP if it weren't such a pain to find the drivers I would need for newer hardware.  I hate Win8 with a passion.  I used WinNT, Win2K, and WinXP, which were bad enough, but the new one is lots worse. It perfectly sensible to want to continue using XP if you bought it and it does what you need Windows for such as games or in my case DRM ebook from the library.

An answer to your question about the OEM disk.  If you install XP in a small partition for dual  boot , you can then point VirtualBox to run off that copy of WinXP.   Sometimes you can still have problems with the OEM disks not recognizes hardware that it wasn't originally sold for.  I've don't some reading about booting a virtualBox from an installed dual boot partition.  It appears to work with older versions of Windoze, but I'm having problems getting it to work with the copy of Win8 that my laptop came pre-infected with.  Its not working the same because Win8 uses a new partitioning system and boot manager called UEFI.

If you google for "dual boot and virtual box windows and ubuntu" you will find lots of discussion of doing what you will need to do.  Some of the results will be people are using Virtual Box under Windoze to run a Ubuntu guest - skip those.  With WInXP, you should boot Ubuntu and then start the WinXP as a virtual guest as you are trying to do.


Good luck
greg

---

