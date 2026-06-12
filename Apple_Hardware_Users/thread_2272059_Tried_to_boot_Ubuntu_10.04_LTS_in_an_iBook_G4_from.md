---
title: "Tried to boot Ubuntu 10.04 LTS in an iBook G4 from cd but didn't work..."
date: 2015-04-03
forum: Apple Hardware Users
---

### Post by benny74402 on 2015-04-03
...the cause might be that I've the wrong version. After reading for a few hours in the forums it appears that there's a different version for PPC's as opposed to the regulars.

This cd has been used before and it worked well on other machines.

How can I tell if I'm using the wrong version by using the tools available with OS X?

Thanks in advance for any info on this!

PS. In the long run I'm intending to dual boot on this machine but not necessarily with 10.04.

---

### Post by este.el.paz on 2015-04-03
> **benny74402 said:**
> ...the cause might be that I've the wrong version. After reading for a few hours in the forums it appears that there's a different version for PPC's as opposed to the regulars.

This cd has been used before and it worked well on other machines.

How can I tell if I'm using the wrong version by using the tools available with OS X?

Thanks in advance for any info on this!

PS. In the long run I'm intending to dual boot on this machine but not necessarily with 10.04.

The iso should say "powerpc" somewhere in the file name . . . you should easily be able to get Xubuntu 12.04 running on that machine . . . 14.04 narrows the field of choices for PPC iso's . . . and you might need to use some "radeon" boot params . . . but is do-able . . . prolly no sound in 14.04 w/o doing some tweaking . . . .

e...

---

### Post by benny74402 on 2015-04-03
I forgot to state that, for now, I just have 394 MB of RAM. In the next few days I'm hoping to receive a 1 GB card that, hopefully, is compatible with the hardware. That's the main reason I decided to try the Ubuntu 10.04 (thinking it wouldn't need that much memory).

BTW, when trying to boot the cd I did it from memory & used the OPTION key & it booted up in "Safe Mode" without sound. Didn't know of any of those options in this hardware.

Where can I download or read about all the options for booting the iBook? I would like to check as with a normal PC, the BIOS or equivalent in this machine just to see what's tweakable.

---

### Post by este.el.paz on 2015-04-03
You can probably still get Xubuntu or Lubuntu 12.04 to work with that amount of RAM . . . 14.04 might need more.  Find your way to the "PowerPCFAQ" . . . part of the Ubuntu wiki . . . should show up in a google search, or might be in the sticky at the top of the page "Where can I find stuff to download for my PPC computer?" . . . there's only two stickies, one for mactel, the other for PPC . . . .

e...

---

### Post by Bucky Ball on 2015-04-03
Forget 10.04 LTS. No longer supported and you won't get a lot of help with it. Try Xubuntu or Lubuntu 12.04 LTS or 14.04 LTS, but to be honest, with that little RAM you probably won't have a lot of luck. Perhaps [Puppy Linux ]("http://www.puppylinux.com/")may be more appropriate.

---

### Post by benny74402 on 2015-04-04
Thanks to both of you guys, este.el.paz & Bucky Ball, for replying!

I went to the ubuntu wiki and read extensively. Many good info & links there!

I asked at linuxquestions.org about the possibility of dual booting with Puppy Linux and they sent me to Lubuntu.

What's the difference between Lubuntu & Xubuntu?

Thanks for any info on the above issues!

---

### Post by Bucky Ball on 2015-04-04
> **benny74402 said:**
> 

What's the difference between Lubuntu & Xubuntu?

Desktop environment and default apps. Lubuntu uses lxde desktop environment which is slightly lighter than xfce4, used by Xubuntu. Lubuntu is your best chance. They are both based on the Ubuntu kernel and use the same official repositories. As I mentioned, you would be lucky to get either going satisfactorily with your amount of RAM. 

You could try the [minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD")which involves installing the Ubuntu kernel then anything else you want: a lightweight DE, a few apps. That would be a steep learning curve, though, but if you're up for it ... 

I have a laptop with an i3 and 4Gb of RAM but have gone the mini install route for a number of years. It flies. No bloat. ;)

PS: See [here]("https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29"). Download the Lubuntu ISO and give it a try (14.04 LTS).

---

### Post by benny74402 on 2015-04-04
Thank you Bucky Ball for replying!

I just checked my system and I don't have a burning device in this laptop. The cdrom drive just reads info. I might fetch for an external cdrom player/burner at night to see if it's still functioning and usable on this harware; for the moment my front yard is calling me...

I'm thinking I'm going for the 'minimal install method', it doesn't sound too hard and it brings the promise of being as light as I care to make it. For the moment, I most re-read the instructions and take some notes before hand. Also, I'm going to try Lubuntu 14.04 LTS; I don't have a very fast web conn. but I can wait. Around this last point, I know that there used to be a Firefox ext. to download large files in segments even if it would take weeks for finishing it; since I'm using Safari version 5.0.6 and I haven't had yet the opportunity to play with it long enough, I don't know if this browser can handle such a situation successfully if it takes some days to finish. Do you or somebody knows if it can handle chunks of info & putting them together at the end?

Time to rer-read and taking notes now. I'll be back as soon as I'm ready to start...

---

### Post by Bucky Ball on 2015-04-04
You could use a [torrent]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Torrent") to download the ISO. You can also create a bootable USB if you have no optical drive (or it is read-only).

---

### Post by benny74402 on 2015-04-06
I'm sorry to say that I received a 1 GB SODIMM stick this weekend but, even though it looked exactly as the one inside, it netover went fully in place. I'm planning to open the laptop tomorrow during the day again & have a closer look at it to try to figure out what is different. I searched the web with the part number on the new chipset but no conclusive evidence to any side, yet.

I also found an old iomega cd player/burner with its cable & power supply (yet to be plugged in to check that the computer can talk to it).

Will keep posting as I go further on this...

---

### Post by benny74402 on 2015-04-08
I tried to use Disk Utility to repartition the HD and giving Lubuntu 10+ GB (first time) & ~8 GB (2nd time) but in both o at the end ccasions the procedure failed with the same message: "Partition failed blah, blah blah, Resource temporarily unavailable".

I used a small stack of triangles at the lower-right corner, dragging it upward to diminish the available space for the Mac OS. I didn't include any other flag, format scheme, etc. before hitting the Apply button. After this, another small window emerged with the Partition button as a second button, which I clicked. The process, apparently, started but at the end an error message was shown.

What might be missing? I'm supposed to be logged as having administrative credentials...

Any help/hint will be appreciated!

---

### Post by Bucky Ball on 2015-04-08
A clarification of what the blah blah blah was in "Partition failed blah, blah blah, Resource temporarily unavailable" would be helpful ...

We can't help a lot unless we know exactly the error messages you are getting. ;)

---

### Post by benny74402 on 2015-04-08
The precise wording I was unable to remember at the moment of submitting the reply, but I assure you that what's left out is inconsequential (IOWs, it contained no code # or wording that could provide useful info to the user).

If I just could remember how to take a screenshot (or better yet a kind of 'tour of how to use'/'what can be done with' with OX 10 I would try to replicate my moves and upload the relevant screens to the forum. I'm not even sure if I ever took a screenshot or not with the iBook.

I'm thinking of going to an Apple forum & instruct myself there before retrying this.

Afterward, I'm posting any news here...

---

### Post by benny74402 on 2015-04-09
I decided that this's doable, so downloaded the mini iso, checked it's md5sum already and up to now averything seems ok.

I hope that I downloaded the correct version of the file. Also, previously, I had downloaded the rEFIt file. The partition process on the internal HD is stopped but I'm thinking of installing (at least first of all) using the USB method.

I'm uploading a screnshot in case someone sees something wrong before I keep going too deep in the process.

---

### Post by benny74402 on 2015-04-12
Well, Bucky Ball, I was trying to replicate what the other day I was trying to do when partitioning the HD but today I first noticed that button saying "Verify HD Permissions" & it took maybe ~10 mins to complete. I've a copy of the output if it's of some importance..., I myself don't understand much of the implications of this test but it might have a huge implication on what I'm trying to do.

In any case, after the above I moved the lower-right corner of this representation upward until I got lower segment of about 8 GB of space and selected the '+' sign on the bottom, which made it appear a self-made name under the 'Macintosh HD', and it's supposed to become a 'journaled' partition, which I was not able to change to anything else & don't know the implications, either.

On all this process I'm supposing that a re-partitioning command on most/all systems (this one included, specially) doesn't destroy data, it moves data away for making room for something else. As mentioned somewhere in the forum/wiki, I searched within my OS X and never found a defragment command as it was suggested to be used before anything else was done. There I have already 2 steps not taken, yet, because of too fragmented info all over the place. I found in two different pages also a reference to the Alt key when the writer was referring to Macs or iBooks; at least in the iBook there's no Alt key which always I assumed to be the 'Command' key, yes, that one that appears on both sides of the Space key with a unique icon on it.

I'm now ready to go ahead and click on apply on that disk utility window for partitioning the disk; but first, I would like to have some more inputs from any of you on the above issues.

---

### Post by benny74402 on 2015-04-12
I first tried to edit the previous post while my internet connection failed and lost all the edition...

Second, when the connection was reestablished, I re-login, tried to find that thing of "Auto safe..." within the forum to recuperate the edition but failed to find it; so I re-wrote it again but just to find that I was not logged in although judging from the page header I was, and the post was lost again...

I'm not posting back that edition to the last post until I receive some info on this, why this's happening? It's not the first time it has happened this exact thing at this site but it's the first time it has happened twice in a row...

Have some things to do & I'll be disconnected for a few hours, only this time by my own will!

---

### Post by benny74402 on 2015-04-20
Last night I installed Transmission & downloaded the iso file [FONT=Lucida Grande]lubuntu-14.04.1-desktop-powerpc.iso. I also checked the MD5SSUM & everything looks OK. Now, what needs to be taking care of is... *back to the reading room*.

As soon as I feel I'm able to continue and have done something I'll come back to state the state of things.

Again, thank you for all your support![/FONT]

---

### Post by benny74402 on 2015-05-01
Well, I took a longer than expected break from the installation of Lubuntu on the iBook but have been rereading all the info on the forum/wiki pages in relation to this that I could find. In relation to this, I suspect the next page refers to a "machine" that already has Ubuntu installed (this's not my case):

[https://help.ubuntu.com/community/UNetbootin](https://help.ubuntu.com/community/UNetbootin)

I'm posting this from a tablet (not the iBook), so I guess that I need to check what file system the internal HD of the iBook has been formatted for. The method for 'trying' Lubuntu on the iBook that I think might work (at least less cubersome) is to use the usb method. Apparently, for this to work, I'll need the Unetbootin program but how to use it from OS X is not clear nor explained there.

Have a 2 GB sdcard with a usb adapter that is recognized by the iBook for this purpose. Any ideas as to how to proceed from here? Thanks a lot!

---

### Post by Bucky Ball on 2015-05-02
See [here]("http://unetbootin.sourceforge.net/"). The Mac version of Unetbootin is available there, top right corner is the button ...

---

### Post by benny74402 on 2015-05-02
Thanks Bucky Ball for replying!

After looking into the link you provided I noticed something that I've read before but failed to interprete correctly:[h=2]"Requirements[/h]
[LIST]
[*]Microsoft Windows 2000/XP/Vista/7, or Linux, or Mac OS X 10.5+. Note that resulting USB drives are bootable only on PCs (not on Macs)." Which takes me out of the players for this game... Think I need to keep looking. I'll round up what alternatives I've found and which are off-limits for me, and why (as a flowchart maybe).
[/LIST]

---

### Post by Bucky Ball on 2015-05-02
Ah ha, well spotted. ;)

The beat goes on ...

---

### Post by benny74402 on 2015-05-03
As a round up for the chain of events that let me to the present situation: still can't boot nor dual boot OS X and Lubuntu...


The first thing I didn't like about this laptop was that it was not capable of reproducing acceptable youtube or other sources videos. Then, someone told me it might be better if it was running Ubuntu, instead. I started to search for information about how to do this in the web (first thing I imagined was running a very light but powerful enough OS like Puppy Linux) but the feedback I received around this isue was that my best chances were around Lubuntu.


Then, at and around Ubuntu forum and also checking on some Apple specific forums I confirmed my feedback and decided to try it first by dual booting this laptop and then, if it was capable of demonstrating its value, let Lubuntu be the only OS working here.


As I went on I found out that there were more than one method for acheiving this and also some problems that I might encounter (that's why there're more than one method). The methods are:
1- Selecting, downloading & burning a suitable iso file and then booting from the cd drive;
2- Selecting, downloading & specially copying, maybe with modifications, a reduced file (core?) into a pendrive or sdcard and then booting from there. Here we have two variants: an absolute minimal install that requires the use of the shell to augment owr system via the PPA and the other one that uses an iconified screen to help with the available packages;
3- Think there's something extra for doing this: the method for bringing in the OS via a LAN cable (net boot in?).


I already have chosen Lubuntu 14.04 and have it at the desktop (MD5Sum checked OK). While reading about this, learned about the minimal install via/with an sdcard/pendrive if one has no means for burning a cd/dvd, which happens to be my case. So I selected & downloaded the apropriate (according to my decision of trying out Lubuntu 14.04) minimal iso file, which is standing next to the Lubuntu iso file mentioned above (also, MD5Sum checked OK).


Something that the forum states is that one should re-partition the HD for making room for the new OS (and also, recommends that before repartitioning one should defragment the volumes but I haven't found a command/app for doing this at the iBook). I remember having read somewhere that by means of the dd command one can achieve the same results as if one is using the defragmenter app in a Windows machine, but this's an iBook; so I'm not feeling the same as with a regular PC around this. Some clarification would be apreciated.


After trying to find the defragmenter within the iBook, and failing to do so, I decided to go ahead with the repartitioning. Twice I tried it (in different forms) and the process never finished. Glad that it didn't brake anything, apparently, either. So, here I am, if I can't repartition the HD, what use there is in trying to dual boot anything with OS X? Then, I remember that many years ago I was frugally dual booting XP and Puppy Linux. The way this was accomplished was like this:
1- make a folder with some files extracted from an iso file in it (maybe at root);
2- modify the boot loader that comes with XP to include the path to the new OS's folder;
3- maybe put some other flags here and there.


So, when starting the Sony laptop I saw a menu giving me the chance to choose which OS to boot and it worked very good, always. Can it be done with this laptop?


The main point in relation to the last paragraph is the easyness of not having to repartitioning the HD, something that appears to be in my case less than easy. I still can search for information with respect to other partitioning apps like gParted for the iBook to see if it's more capable for doing it but think I've lost some impetus.


Note: The information within the forum/wiki is fragmented in such a way that makes me think is a good idea if someone that knows the processes targeted there could sum-up everything in a flowchart style. Certainly, that would mean a world of difference in the way people like me approach the issue of dual booting in an iBook.

---

### Post by rsavage on 2015-05-04
> **benny74402 said:**
> 


After trying to find the defragmenter within the iBook, and failing to do so, I decided to go ahead with the repartitioning. Twice I tried it (in different forms) and the process never finished. Glad that it didn't brake anything, apparently, either. So, here I am, if I can't repartition the HD, what use there is in trying to dual boot anything with OS X? Then, I remember that many years ago I was frugally dual booting XP and Puppy Linux. The way this was accomplished was like this:
1- make a folder with some files extracted from an iso file in it (maybe at root);
2- modify the boot loader that comes with XP to include the path to the new OS's folder;
3- maybe put some other flags here and there.


So, when starting the Sony laptop I saw a menu giving me the chance to choose which OS to boot and it worked very good, always. Can it be done with this laptop?



Yes, sort of (you can't do it easily with hfsplus, but it works well from a USB drive), but ultimately it will be futile because YouTube videos won't play any better under Linux.

---

### Post by rsavage on 2015-05-04
See [https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F](https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_to_a_virtual_disk_like_.27wubi.27.3F)

But I think you would be better starting off with [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

---

### Post by benny74402 on 2015-05-04
Thanks for the info rsavage!

I was following the instructions on [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) precisely now and received the following message: "Resource busy". I tried fdidk first after the dev was unmounted, it didn't work; after taking it out and putting it back I issued the command once more and then it gave me this message. I most say that the first time I mounted it I took one file from there and put it on the desktop; don't know if this has something to do with it???

What I was trying to do was to follow the instructions on the cited web page in order to try to put in there the mini iso file and try to boot from the usb device on this machine. If that proves possible, then I would keep going installing some packages as needed. Hey, this's an experiment after all; something I might learn from all this!

The primary and most close to the present issue I wanted to solve by putting and running a linux OS here was seeing Youtube (as well as other) videos with an acceptable quality but it was not the overall purpose. I'm used to use linux instead of any other OS now for about 10 years and happens to be the case that I don't see this NEW OS (OS X) is better than what I'm used to. So, why not make the change with this hardware too?

---

### Post by rsavage on 2015-05-04
That's not a good way to do the mini iso.  Your problem is you are looking at non PowerPC information.  Please look at the second link I gave you.

---

### Post by benny74402 on 2015-05-08
I was trying to follow the instructions given at:

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

but when executing step #8 saw at the Terminal the following:

"[COLOR=#0000ff]**users-ibook-g4-7:~ user$ diskutil list**[/COLOR][COLOR=#0000ff]**/dev/disk0**[/COLOR]
[COLOR=#0000ff]**   #:                       TYPE NAME                    SIZE       IDENTIFIER**[/COLOR]
[COLOR=#0000ff]**   0:     Apple_partition_scheme                        *27.9 Gi    disk0**[/COLOR]
[COLOR=#0000ff]**   1:        Apple_partition_map                         31.5 Ki    disk0s1**[/COLOR]
[COLOR=#0000ff]**   2:             Apple_Driver43                         28.0 Ki    disk0s2**[/COLOR]
[COLOR=#0000ff]**   3:             Apple_Driver43                         28.0 Ki    disk0s3**[/COLOR]
[COLOR=#0000ff]**   4:           Apple_Driver_ATA                         28.0 Ki    disk0s4**[/COLOR]
[COLOR=#0000ff]**   5:           Apple_Driver_ATA                         28.0 Ki    disk0s5**[/COLOR]
[COLOR=#0000ff]**   6:             Apple_FWDriver                         256.0 Ki   disk0s6**[/COLOR]
[COLOR=#0000ff]**   7:         Apple_Driver_IOKit                         256.0 Ki   disk0s7**[/COLOR]
[COLOR=#0000ff]**   8:              Apple_Patches                         256.0 Ki   disk0s8**[/COLOR]
[COLOR=#0000ff]**   9:                  Apple_HFS Macintosh HD            27.9 Gi    disk0s9**[/COLOR]
[COLOR=#0000ff]**/dev/disk1**[/COLOR]
[COLOR=#0000ff]**   #:                       TYPE NAME                    SIZE       IDENTIFIER**[/COLOR]
[COLOR=#0000ff]**   0:     FDisk_partition_scheme                        *120.1 Mi   disk1**[/COLOR]
[COLOR=#0000ff]**   1:                 DOS_FAT_16                         118.8 Mi   disk1s1**[/COLOR]
[COLOR=#0000ff]**users-ibook-g4-7:~ user$ diskutil unmountDisk /dev/disk1**[/COLOR]
[COLOR=#0000ff][/COLOR]
[COLOR=#0000ff]**Unmount of all volumes on disk1 was successful**[/COLOR]
[COLOR=#0000ff]**users-ibook-g4-7:~ user$ **[/COLOR]
[COLOR=#0000ff]**users-ibook-g4-7:~ user$**[/COLOR]"

I was expecting to see the usual prompt that you receive when a command is executed successfully but the pointer just moved to the next line and I waited a lot of minutes expecting something else but nothing happened. So, I really don't know what happened with the command execution; the icon for the usb device on the desktop disappeared, though.

The above circumstances means that I stopped right there, read a few more lines of the cited webpage but, not finding anything in relation to this I commenced this post.

Should I proceed with the next step or something must be settled before moving on?

Note: What about the file system of the usb device (DOS_FAT_16), shouldn't it be changed to DOS_FAT_32 first?

---

### Post by benny74402 on 2015-05-08
Since I received no input with the above issue and, while waiting kept reading around my purpose and decided to try the instructions at:

[http://ubuntuforums.org/showthread.php?t=2225846](http://ubuntuforums.org/showthread.php?t=2225846)

I fetched for the information on the iBook in relation to partitioning and formatting but, in relation to this last site's instructions, found no FAT32 format alternative, which was my format of choice (on this, I'm following a lead that I read at another webpage).

I never found any way of verifying what format the volumes on the HD have, so don't know where to put the minimal iso image file I already have at the desktop.

Waiting for some input at this crossroads to continue with this, thanks!

---

### Post by benny74402 on 2015-05-10
Finally, I've decided to try to fry (burn) a re-writable cd using the lubuntu-14.04.1-desktop-powerpc.iso using the DiskUtility app within OS X and received the message that there was not sufficient free space in the cd. I cancelled the operation until I solve the issue.

Is there something within the iso file that I can delete from it without affecting its' functionality (strange languages dictionaries, i. e., Japanese, Russian, etc.; certain apps that I know for sure I won't be using that might be there...), safely?

Edit: If I already have the main iso file within the Downloads folder and also have the miniiso file image on the desktop, can I burn instead the miniiso.img file to the cd and use the lubuntu iso file at the Download folder to install apps after I've booted up with the cd containing the miniiso.img file?

Should I consider instead downloading another, more capable, burning app before continuing?

Re-Edit: The size of the iso in question above is a little over 750 MB.

---

### Post by Bucky Ball on 2015-05-10
You can fit the mini.iso onto a CD, yes, so go with that. Once you've installed you can create whatever hybrid you wish, a Lubuntu install or just parts of one blended with stuff from other flavours or whatever. (I only use mini installs.) You actually get an option as to what sort of machine you want to install during the installation, Lubuntu might be an option there. I never use those options, preparing to play Frankenstein on my own terms, so unsure. Have a look when you get there. 

The mini install is a little more involved, but not a lot to it, really (and you can always ask for help here if you get stuck). Best to be online with an ethernet cable because that's how it does things. The iso is teeny, but during the install it drags everything down the line (there's very little on the actual install media). 

You don't have a blank DVD for a regular Ubuntu install? Silly question, I guess, cos you'd be burning it if you did. ;)

---

### Post by benny74402 on 2015-05-10
Thanks for replying so fast Bucky Ball!

Going point to point. According to some of the many pages I've read the first thing I should do is to update the Firmware, if there's any to have. Have checked that out and, apparently, mine needs no update. Good!

My OS is also updated. Good, too. My cd burner (usb connected --Iomega) isn't capable of burning dvds. While trying to burn lubuntu I saw what appeared to be certain options for the burner app but have no clue as to how to use them nor if any of them is compatible with an iso file which is meant to **boot. **If you need that I post specifics from the latter I can bring back the app and take a screenshot and post it later. Not that good, for now.

The most pressing thing now is how to safely re-partition the HD without destroying Mac OS. Can it "safely" be done on an iBook G4 from an lubuntu installation cd (minimal or otherwise)? Have read that before Leopard (10.5) it cannot be done without loosing everything on the partition at hand, but I have 10.5.2; can I do this here without an OS X installation cd? By way of gParted for example (Mac OS X 10.5.2 version, if it exists; or something else --linux based)?

Edit: The options I was referring to above are the following:

"[FONT=Lucida Grande]**IOMEGA CDRW23042EXT3-B:**[/FONT]

  Firmware Revision:    ZOP1
  Interconnect:    USB
  Burn Support:    Yes (Apple Supported Drive)
  Cache:    1984 KB
  Reads DVD:    No
  CD-Write:    -R, -RW
[COLOR=#ff0000]  Write Strategies:    CD-TAO, CD-SAO, CD-Raw[/COLOR]
  Media:
  Type:    CD-RW
  Blank:    Yes
  Erasable:    Yes
  Overwritable:    Yes
  Appendable:    Yes
  Write Speeds:    2x, 4x, 8x, 10x"

see line in RED.

Re-edit: Which file should I burn into the cd, the mini.iso or mini.img?

---

### Post by benny74402 on 2015-05-14
I was trying to post a few moments ago including an attachment and I was logged out for an unexplained reason and almost have to close Safari and reload. I was taken to another Tab for choosing the file to be attached because I don't know why I cannot insert an image here and was almost impossible to close the Tab. I was receiving this small window saying that I don't have sufficient permission to perform the action and I should login, but this little window appeared so fast after closing that it was almost impossible to do anything in the milliseconds that I had. No matter how many times I hit OK it reappeared. THIS MIGHT BE A SITE's BUG!

Correction, It has taken me out again!

While following one of the threads here I stumbled with the following info that I don't know how to interpret:...

The last ellipsis are there because I can't upload a screen capture nor attach a file from my Desktop, even though at the bottom of the page states that I can attach files if I try to Go Advance for the option to appear it immediately log me out.

The above means that I can't ask what I needed...; would like to know if there's a problem with the internet or your site about this date & time, if you know.

---

### Post by benny74402 on 2015-05-19
[COLOR=#222222][FONT=Times]I was following the instructions at:

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

and, since there's no word about the format of the partition I just used what Mac OS X had given me when I partitioned the sdcard HFS+/journal; moved the minilubuntu.img file there and reboot -- it didn't work. No way I could find a way to point to the desired dev/partition/file...

I reboot to OS X again, reformat as DOS FAT16 (never found a way to format as FAT32), moved again the mini file there and retried --same thing, didn't work...

There now a new situation. Apparently, for being a FAT fs the OS X system doesn't like it and after last reboot it offered me a little window with 3 options: (1) Ignore, (2) Eject & (3) Fix or simething alike: I choosed #1. After this, I don't see it on the Desktop, can't mount it no matter if I'm using the Terminal or the DiskUtility.

**All these events occur because of the fragmentation and incompleteness of the info offered at the sites I've been visiting for learning how to do this**.

I've been discouraged before with this experiment and now I'm feeling worst! Even though my last comment is firm, I'm not quitting, yet.

How many steps should be taken to accomplish this? As far as I have counted/remember:
1) select an appropriate/working usb device and look for the name and location OS X gives to it;
2) partition the device; if it's going to be a Full install include the SWAP partition (in my case I didn't because it was intended for waking up the minimal install iso file, only, for making sure this hardware can run a linux OS;
3) (re)format the partition(s) in a suitable/workable form; here the sites visited doesn't mention anything (lack of info);
4) move the iso file to the target; here it's mentioned that OS X tend to add the .dmg to the .iso file converted but doesn't state if one should revert the action or if it's inconsequential (I reverted it back to .iso) --is this important?;
5) reboot and use 'alt' key after hearing the chimes (Apple computers have no 'alt' keys) and choose... what: device or file? I tried every possible combination of both but..., it didn't work!

How can I revert whatever I've done for making the device reappear again for working with it? At least, if I can learn how to do this here..., something is something!

My Terminal now gives me just this:

[COLOR=#EE82EE]users-ibook-g4-7:~ user$ diskutil list[/COLOR]
[COLOR=#EE82EE]/dev/disk0[/COLOR]
[COLOR=#EE82EE]   #:                       TYPE NAME                    SIZE       IDENTIFIER[/COLOR]
[COLOR=#EE82EE]   0:     Apple_partition_scheme                        *27.9 Gi    disk0[/COLOR]
[COLOR=#EE82EE]   1:        Apple_partition_map                         31.5 Ki    disk0s1[/COLOR]
[COLOR=#EE82EE]   2:             Apple_Driver43                         28.0 Ki    disk0s2[/COLOR]
[COLOR=#EE82EE]   3:             Apple_Driver43                         28.0 Ki    disk0s3[/COLOR]
[COLOR=#EE82EE]   4:           Apple_Driver_ATA                         28.0 Ki    disk0s4[/COLOR]
[COLOR=#EE82EE]   5:           Apple_Driver_ATA                         28.0 Ki    disk0s5[/COLOR]
[COLOR=#EE82EE]   6:             Apple_FWDriver                         256.0 Ki   disk0s6[/COLOR]
[COLOR=#EE82EE]   7:         Apple_Driver_IOKit                         256.0 Ki   disk0s7[/COLOR]
[COLOR=#EE82EE]   8:              Apple_Patches                         256.0 Ki   disk0s8[/COLOR]
[COLOR=#EE82EE]   9:                  Apple_HFS Macintosh HD            27.9 Gi    disk0s9[/COLOR]
[COLOR=#EE82EE]users-ibook-g4-7:~ user$ [/COLOR]
[/FONT][/COLOR]

---

### Post by rsavage on 2015-05-20
> **benny74402 said:**
> [COLOR=#222222][FONT=Times]
5) reboot and use 'alt' key after hearing the chimes (Apple computers have no 'alt' keys) and choose... hwhat: device or file? I tried every possible combination of both but..., it didn't work!

[/FONT][/COLOR]
Not going to work on a g4 ibook.  You need to go through openfirmware as described in the FAQ.

The link you gave uses the command dd. This overwrites any existing filesystem so you don't need to worry about formatting the USB drive before using the command.

---

### Post by benny74402 on 2015-05-20
Thanks for replying, rsavage!

I forgot to mention that I also used the <Command+Option+o+f> combination; of course, it didn't work, either.

About the dd command: you say that it doesn't matter as if it take care of it by itself... But, how can I control the FS format before using the command and make sure it stays like I've selected? I understand that this is crucial for the sdcard (or an usb device) being bootable. If the command takes care of it, how can I tell what FS format it ended up being?

Restating what I've asked above, how can I regain control (or visibility) of the device?

---

### Post by sudodus on 2015-05-20
The dd command clones the data from the source (in this case the iso file) to the target device (in this case an SD card or USB pendrive). Every bit is simply copied in a low level process, so whatever is in the iso file is written exactly as it is to the pendrive.

dd is very powerful but also very risky. It does what you tell it to do without questions. A small mistake (even a typing error) can destroy your family pictures, if you happen to write to the wrong drive. So dd is nick-named 'disk destroyer'. If you double-check and triple-check that everything is correct, you can use it and it does the work for you.

Otherwise you can download the iso file into another computer, where you can use a safer tool to flash the iso file to the pendrive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by rsavage on 2015-05-20
> **benny74402 said:**
> 
Restating what I've asked above, how can I regain control (or visibility) of the device?
I've no idea about macs, perhaps somebody else will help you?  It is unclear to me what caused it - did you run the dd command?

> 
I understand that this is crucial for the sdcard (or an usb device) being bootable. 

There are quite a few ways to use a usb device and some require a certain filesystem.  This is where I think you are getting confused.

Stick to the powerpc wiki it has several ways to use a usb device without using dd.  For the mini iso you don't even need a usb drive, you could just place the extracted files on a hard drive partition.

---

### Post by benny74402 on 2015-05-21
Thanks for replying, sudodus & rsavage!

I was following the instructions given at a link offered at the link you provided, sudodus.

I effectively ran the dd command already to clone the image file inside the sdcard, rsavage. I also asked for the disappearance of the device at an Apple forum; waiting for someone to reply...

The problem with your suggested approach, rsavage, of putting the mini iso file in its' own partition is that I'm tied here (up to now) with the DiskUtility app, and this won't let me re-partitiion the internal disk. I already tried to do it and failed. Apparently, it is something tied to the specific app I've here which is, in turn, tied to the OS X 10.5.2 that I'm running under. Already fetched for info on gParted in the web, thinking it might be able to do the trick here, but it won't in the iBook running my OS.

It seems that after each and every turn I find the same kind of obstruction: can't pass beyond this wall or another. I've thought that Apple decided to make it specially difficult for linux users to change anything in their products (even beyond whatever Windows ever tried already).

Edit: Is there a way for me at the iBook to reduce the 750 MB of the lubuntu.iso file by "extracting" some apps and other files that I knnow that I'm not planning to use down to about 700 MB and still leaving an iso file that is bootable?

---

### Post by sudodus on 2015-05-21
Most ***Lubuntu*** iso files are within CD size (700 MB). With Lubuntu you can try a newer version (than with Ubuntu).

---

### Post by benny74402 on 2015-05-22
Today I re-plugged the device and I received the same window I received after copying the image there (today, I noticed that the remaining option appearing there was "Initialize", which I selected this time). DiskUtility opened and, Alas!, the image is there and most strikingly yet, the file system appears as FAT32. Apparently, the dd command even takes care of the file system..., am I wrong here?

This is what I have up to now --see attachments below.

I think I need to add something there for making the device bootable, isn't it? Syslinux maybe? Where? From where? I've searched within the image and there's no syslinux there. I found a configuration file, though. Need extra help here!

---

### Post by benny74402 on 2015-05-22
I was following the instructions at: [http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630) and at the link provided there [https://www.kernel.org/pub/linux/utils/boot/syslinux/](https://www.kernel.org/pub/linux/utils/boot/syslinux/) downloaded the one that's named <syslinux-6.03> not exactly sure that this one was the right one. I didn't download anything else even though I suspected that the one under it that ended with ".sign" was the checksum for it. So, it remains unchecked. Nonetheless, I unpacked it and browsed it slowly for not risking passing over what I was looking for: [mbr.bin?]. I really don't know if this's the one I need or not, but I'm not copying nothing to the sdcard before I check the md5sum or something else before, for making sure of the integrity of the file.

I'm attaching the appropriate info below:

What I'm supposed to do on the disk1s1 partition? Shouldn't the bootable partition be the first one?

Thanks in advance for any info on above issues!

---

### Post by benny74402 on 2015-05-22
Was reading this page: [http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337) and decided to try the approach depicted there. The problem with this is that there's a reference to some files that I'm thinking the writer believes I should find within the iso file and I'm working with a miniiso image and those files aren't there (except the ofboot.b file, which is there). The files I'm referring to are: **(grub.cfg, grub.img and ofboot.b)**.

Even though there's mention of a 2 partition vs. a single partition device, if I'm going this way I would re-partition the device as a single FAT32 partition because it looks simpler (overall).

In any case, I'll wait for some input from you as to what 's the best next action.

Check the next attachments... The last picture is the top folder, the second picture is the contents of the third folder and the first picture is the contents of the PPC folder.

---

### Post by rsavage on 2015-05-23
> **benny74402 said:**
> Was reading this page: [http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337) and decided to try the approach depicted there. The problem with this is that there's a reference to some files that I'm thinking the writer believes I should find within the iso file and I'm working with a miniiso image and those files aren't there (except the ofboot.b file, which is there). The files I'm referring to are: **(grub.cfg, grub.img and ofboot.b)**.

No, that is not what the author (me) believes.

> 
Even though there's mention of a 2 partition vs. a single partition device, if I'm going this way I would re-partition the device as a single FAT32 partition because it looks simpler (overall).

No, not for the mini ISO it isn't.

If you can burn a cd, and you want to run the mini ISO, then why don't you just burn the mini ISO to cd?

---

### Post by benny74402 on 2015-05-23
Thanks for replying, rsavage! I'm sorry for having misinterpreted your post.

I've the complete lubuntu iso file (14.04.1) for PPC and I'm wondering if the said files might be there; how/where can I grab those files? BTW, someone at another forum (I guess) cleared something for me: disk1s1 is NOT a partition, just info concerning how the system should look at the device. Still, I keep asking myself as to how to interpret those entries under disk0 when one issue the command <diskutil list>; I've read that s1,s2,...s9,... referred to Volumes and this is the name Apple systems give to Partitions... hum.

The problem with burning the cd is that I don't have a dvd burner nor any dvd around so cannot go beyond 700 MB. My imagination and ignorance tells me that if you can make a miniiso file grow you should be able to make a regular iso file to shrink (somehow) until it is burnable on a cd. I've asked about it but haven't had a reply, yet.

About the previous approach, the miniiso file that I already converted to an image file is reported to have been downloaded from (look at the next attachment).

PS. Hope that no one has been offended by any part of my posts, specially you, rsavage, because I've read your posts quite a few times and believe I'll need to go there again...!

---

### Post by benny74402 on 2015-05-23
I tried your scheme, rsavage, but it failed to 'Open the DIR device'. I also checked if on that list appears an entry for fat-files and it does. Tried all combinations that came to my mind with the dir command (even tried it with DIR, instead) but to no avail. Oh,...

I'm remembering now that what I've copied there was an image of the original iso file and NOT the downloaded iso file itself.

But, since the FS there makes it impossible for me to look inside, delete the image or even mounting it I might need to go to the first step with partitioning it, erasing and using the dd command again only this time with the right file and all the rest. Do you agree this's the way to go?

---

### Post by rsavage on 2015-05-23
That thread was from 3 years ago - I've learnt and improved things since then.  It was never intended for the mini iso, but can be used as I explain in the thread.  The 3 files are attached on the the first post of the thread.

It's been a long time since I've used openfirmware so I can't tell you about that error, but I would do:

(assuming you are plugged into the usb port closest to the front of the machine)

```

probe-usb

boot usb0/disk@1:2,\install\yaboot

```

---

### Post by rsavage on 2015-05-23
> **benny74402 said:**
> 
I'm remembering now that what I've copied there was an image of the original iso file and NOT the downloaded iso file itself.


You've lost me.

---

### Post by rsavage on 2015-05-23
Please choose what ISO you want to boot and stick to it.

Please choose a method and stick to it:  You can either extract the files from the iso file onto the usb device, or you can just place the whole iso file onto the usb device.  

For the latter you need to then obtain a bootloader, which can be either be grub2 or yaboot, but for a live iso the partition containing the iso file cannot be hfs/hfs+.  

For the former, you can either use dd (this preserves the special attributes of the boot files - although this has no advantage on a g4 ibook - and also automatically sorts out the filesystem for you) or you can just do it manually (EDIT: to m[COLOR=#000000]ount the iso in MAC OS X Panther I 'right click', select 'Open With >' and choose 'DiskImageMounter', then just copy the files across to a formatted partition[/COLOR]). You can use yaboot which comes on the iso, but the extracted partition scheme cannot be a MS-DOS scheme because yaboot can't cope with this (not entirely sure even if it can cope with a FAT partition).

Again, I'm not familiar how Mac OS X works, but from my experience I would suggest something has gone wrong on your dd'd drive because you shouldn't have a 120gb fat partition.  You should be able to get yaboot to load from openfirmare using the command I gave above, but if it fails from thereafter then it is because of the fat partition.

---

### Post by benny74402 on 2015-05-29
I've found that in Leopard I've a tool at the Terminal that's capable of re-partition the HD loss-less as well as shrinking some of them for making space for Lubuntu. For this I will need some explanations and guidance. Guess the tool is "diskutil".

The explanations I'll need comes from the fact that I still don't completely understand the nomenclature Apple uses for the HDs, have a look at my post #27' attachment. If I'm forced to give an interpretation to that attachment I would say that the HD contains 10 partitions, being #0 the Apple Partition Map and the last, #9, where the OS X resides. The rest of the partitions have needed parts for the OS operations (drivers, updates, etc.). Am I wrong at this?

If I'm right with the above interpretation, what's the best approach for making room for Lubuntu with this tool? Starting to shrink the previous partitions starting with the most distant one (#1) and moving the next resized one appended to the last and so on or I should leave all of them untouched and resize only #9?

One useful thing to learn now would be to learn how to look at the contents of all those partitions, in that way I might figure out how much extra space these have been allocated and have an idea as to what are the safe margins for them.

 Some idea of the quirkiness of naming a process '***blessing***'?

I was about to try another method of booting the mini at the sdcard but got stopped when found that I needed some grub files and didn't used the dd command to move them there because of fear of wiping out the other files already in there but I think that even though I cannot mount the disk I, by means of some command, can move extra files there safely, is this correct? In other words, if I use the dd command on a disk/partition/folder repeatedly, am I destroying the previously moved files there or the new ones are merely appended?

Thanks in advance for any ideas in relation to the above!

---

