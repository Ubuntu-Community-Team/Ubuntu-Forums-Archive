---
title: "Ubuntu 12.04 LTS PPC to G4 PowerBook: No alsamixer"
date: 2013-06-28
forum: Apple Hardware Users
---

### Post by AndyInMokum on 2013-06-28
Hi all from Amsterdam

I've just installed Ubuntu 12.04 LTS PPC to my aging 15" Mac PowerBook as a last ditch solution to its redundancy. I tried Lubuntu 13.04 as the preferred installation and very quickly came to the decision that it was so riddled with bugs that as an average user, it wasn't worth pursuing. So I ditched that as a waste of time and effort. I've managed to install Ubuntu 12.04 LTS PPS and it appears to be working a lot better and faster than it's Lubuntu sibling.  However, there is no sound.  Alsamixer is just not there. I've used the terminal to check and it tell me no file or directory. Any help would be appreciated as this is the last major hurdle to getting Ubuntu up and running on my geriatric Mac. Many thanks.

---

### Post by rkmugen on 2013-06-28
Just to be sure you haven't skipped any important steps, have you tried the advice shown here on the PowerPCFaq?
[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

---

### Post by AndyInMokum on 2013-06-28
> **rkmugen said:**
> Just to be sure you haven't skipped any important steps, have you tried the advice shown here on the PowerPCFaq?
[https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)


   	 	 	 	   Good evening rkmugen from Amsterdam.  

 

 Thanks for getting back to me. I´m still having trouble getting the sound to work on my old 15” G4 PowerBook. (2004) I have been systematically been going through the, “Why do I have no sound?” trouble shooter in the Wiki pages.  

 

 **Checking for alsamixer in terminal:**
 

 andyinmokum@andyinmokum-laptop:~$ sudo alsamixer 
 [sudo] password for andyinmokum:  
 cannot open mixer: No such file or directory 
 andyinmokum@andyinmokum-laptop:~$  
 

 **Checking lsmod:**
 

 **andyinmokum@andyinmokum-laptop:~$ lsmod **
 **Module                  Size  Used by **
 **radeon                804604  0  **
 **ttm                    69558  1 radeon **
 **drm_kms_helper         39474  1 radeon **
 **drm                   216156  3 radeon,ttm,drm_kms_helper **
 **dm_crypt               19155  1  **
 **btusb                  14060  2  **
 **arc4                    1357  2  **
 **b43                   368242  0  **
 **mac80211              473195  1 b43 **
 **rtc_generic             1363  0  **
 **mac_hid                 3789  0  **
 **cfg80211              192425  2 b43,mac80211 **
 **bnep                   12554  2  **
 **rfcomm                 42291  12  **
 **bluetooth             182084  23 btusb,bnep,rfcomm **
 **parport_pc             37386  0  **
 **ppdev                   7758  0  **
 **lp                      9123  0  **
 **parport                37912  3 parport_pc,ppdev,lp **
 **pcmcia                 41860  0  **
 **yenta_socket           25370  0  **
 **pcmcia_rsrc            10259  1 yenta_socket **
 **bcma                   26036  1 b43 **
 **pcmcia_core            16855  3 pcmcia,yenta_socket,pcmcia_rsrc **
 **apm_emu                 1424  0  **
 **apm_emulation           7231  2 apm_emu **
 **snd_powermac           66397  0  **
 **snd_pcm                88810  1 snd_powermac **
 **snd_seq_midi            5452  0  **
 **snd_rawmidi            23692  1 snd_seq_midi **
 **snd_seq_midi_event      7251  1 snd_seq_midi **
 **snd_seq                61181  2 snd_seq_midi,snd_seq_midi_event **
 **snd_timer              23955  2 snd_pcm,snd_seq **
 **snd_seq_device          6920  3 snd_seq_midi,snd_rawmidi,snd_seq **
 **snd                    71315  6 snd_powermac,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device **
 **soundcore               7871  1 snd **
 **snd_page_alloc          7388  1 snd_pcm **
 **usbhid                 42303  0  **
 **hid                    85152  1 usbhid **
 **firewire_ohci          36642  0  **
 **firewire_core          61172  1 firewire_ohci **
 **sungem                 32153  0  **
 **sungem_phy             12068  1 sungem **
 **crc_itu_t               1483  1 firewire_core **
 **ssb                   51915  1 b43 **
 **uninorth_agp            7650  1  **
 

 

 **Note:**  snd_powermac           66397  0  
 

 So snd_powermac is not being used.
 

 **Checked “automatic setup with modprobe:**
 

 **# /etc/modules: kernel modules to load at boot time. **
 **# **
 **# This file contains the names of kernel modules that should be loaded **
 **# at boot time, one per line. Lines beginning with "#" are ignored. **
  **snd_powermac **
 **apm_emu **
 **snd-powermac **
 **therm_adt746x **
 

 **Note**: **snd-powermac ** is already present in the list.
 

 

                                          **[ Read 9 lines ] **
 **^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos **
 **^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell **
 

 This leaves the inherited Debian bug.  
 This is also where I get lost.
 

   GNU nano 2.2.6     File: /etc/modprobe.d/blacklist.local.conf                  
  
 # Local module settings 
 # Created by the Debian installer 
  
 blacklist snd-aoa-codec-tas 
 blacklist snd-aoa-fabric-layout 
 blacklist snd-aoa-i2sbus 
 blacklist snd-aoa-soundbus
 blacklist snd-aoa 
  
  
  
  
  
  
  
  
  
  
 File Name to Write: /etc/modprobe.d/blacklist.local.conf                         
 ^G Get Help         M-D DOS Format      M-A Append          M-B Backup File 
 ^C Cancel           M-M Mac Format      M-P Prepend 
 

 GNU nano 2.2.6  has got me baffled. I know its a text editor but I do not understand its operating functions. Presumably, the above list needs to be saved. My next set of questions are. Where do I save it to? What so I save it as? What are to key strokes needed to perform these tasks.  I am really new to Linux and I´m the first to admit I know very little. Hopefully this will get the old Mac singing again. (I¨m not holding my breath for it though).  Your help is greatly appreciated.

---

### Post by rkmugen on 2013-06-28
When you use nano to open a file that already exists, you can usually just press CTRL+x (denoted as "^x") to exit the file, and before it completely exits, it'll give you the chance to save the file, either as-is or if you'd like to rename it, or to save it to a different file with a new name.  Other system-critical files that you open with nano will notify you that you don't have 'write permission' or something like that (essentially, only the root user can edit those).  So for those files, you need to 'sudo nano blah.txt' where 'blah.txt' is the name of the file you want to open/edit.

Alternatively, you could even use a graphical text editor while you're logged into the GUI if you prefer it.  I use 'gedit' when I absolutely demand the ability to use a mouse to quickly manipulate large portions of text in a file.  You can even launch 'gedit' as a root user to edit system-critical files.  For example, if you wanted to use gedit edit a system-critical file called critical.txt, all you'd need to do is open up a terminal and type in 'sudo gedit critical.txt'.

I'm sure there are more concise tutorials for nano out there, but these  are really the only bits of basic info I found useful even for myself when I  edit files.

Also, could you tell me what shows up if you type this into the terminal (exclude the quote marks)?:  'gnome-alsamixer'

I'm expecting that you'd either see a window show up with controls for volume and such.... or that it'll tell you that it isn't installed.  If it isn't installed you could install it by typing (without quote marks):  'sudo apt-get install gnome-alsamixer'

If it is already installed, then something else is messed-up.

---

### Post by AndyInMokum on 2013-06-29
> **rkmugen said:**
> When you use nano to open a file that already exists, you can usually just press CTRL+x (denoted as "^x") to exit the file, and before it completely exits, it'll give you the chance to save the file, either as-is or if you'd like to rename it, or to save it to a different file with a new name.  Other system-critical files that you open with nano will notify you that you don't have 'write permission' or something like that (essentially, only the root user can edit those).  So for those files, you need to 'sudo nano blah.txt' where 'blah.txt' is the name of the file you want to open/edit.

Alternatively, you could even use a graphical text editor while you're logged into the GUI if you prefer it.  I use 'gedit' when I absolutely demand the ability to use a mouse to quickly manipulate large portions of text in a file.  You can even launch 'gedit' as a root user to edit system-critical files.  For example, if you wanted to use gedit edit a system-critical file called critical.txt, all you'd need to do is open up a terminal and type in 'sudo gedit critical.txt'.

I'm sure there are more concise tutorials for nano out there, but these  are really the only bits of basic info I found useful even for myself when I  edit files.

Also, could you tell me what shows up if you type this into the terminal (exclude the quote marks)?:  'gnome-alsamixer'

I'm expecting that you'd either see a window show up with controls for volume and such.... or that it'll tell you that it isn't installed.  If it isn't installed you could install it by typing (without quote marks):  'sudo apt-get install gnome-alsamixer'

If it is already installed, then something else is messed-up.

 Hi again, thanks for the info it is very useful indeed .  It is safely filed away for future reference. I took your advice and managed to find what I was looking for after a lot of digging. Ctrl+o. Unfortunately, the excitement of this discovery soon wore off.  I saved the changes using ctrl+o. Exited and rebooted Ubuntu. I have downloaded and installed through the Synaptic Package Manager, alsamixer and gnome-alsamixer; just for good measure. The alsamixer now shows up and can be activated and appears to be working. The Gnome-Alsameter just appears as a blank white box. The sliders in Alsameter move up and down, they can be locked or not and the mute toggle works. Tested the sound output with Rhythmbox and it appeared to be playing. Still the output is showing, "play sound through Dummy output". Still no sound. As I said before, I´m really new to Linux and I´v run out of ideas. Other than the sound, the old Mac is running like a top; positively sprightly! My main computer is a Fujitsu Siemens Li 3710 laptop with Linux Mint Debian Edition. It was so easy to install and configure; a real joy to use and it is rock solid. Ubuntu 12.04 ppc is a different story. It will make a fantastic backup computer though once the sound is working. Again, your help is greatly appreciated.

---

### Post by danield on 2013-06-29
Try changing /etc/modprobe.d/blacklist.local.conf by commenting out all the lines like this:

# Local module settings
# Created by the Debian installer

#blacklist snd-aoa-codec-tas
#blacklist snd-aoa-fabric-layout
#blacklist snd-aoa-i2sbus
#blacklist snd-aoa-soundbus
#blacklist snd-aoa 

Then add the following to your /etc/modules file:

snd-aoa-codec-tas
snd-aoa-fabric-layout
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa

---

### Post by AndyInMokum on 2013-06-29
Hi danield

Thanks for getting back to me. I just want to get one thing straight before I get started. When you say commenting out the lines, is this deleting them and then saving? Sorry to have to ask but I'm really new to Linux and programming in general and much of the terminology is totally alien to me. I'm looking forward to getting the old Mac up and running as she should. I've spent days trying to solve this problem. Many thank again and I keep you updated with the progress.

---

### Post by rkmugen on 2013-06-29
When people say to 'comment' some things out, that means to simply put a hash mark/pound sign (#) at the very beginning of the lines they appear in.  This tells the system to ignore those particular set of commands.  This is safer than deleting the lines entirely because if you mess up, you can at least have a chance to revert back to how the file was before you made your alterations.... at which point you can comment-out your tried (and failed) alterations so you can keep better track of what works and what didn't, all in the same file.

---

### Post by AndyInMokum on 2013-06-29
Good evening rkmugen and danield
 
Guess what - we have lift off!!  Bob Marley is singing loud and clear "No Woman No Pain" out of all speakers. Changing the Blacklist config files did the trick. After I/we got the the beast working I unistalled Alsamixer in favour of the Gnome-Alsamixer because it has more controls. Hopefully this will help others in a similar situation. Many thanks for all of your patience and help. I have a fully working "Macbuntu Machine"; fantastic stuff!

---

### Post by rkmugen on 2013-06-29
Great news!  Have fun with your new setup!

---

