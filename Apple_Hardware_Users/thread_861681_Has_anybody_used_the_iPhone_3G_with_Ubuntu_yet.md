---
title: "Has anybody used the iPhone 3G with Ubuntu yet?"
date: 2008-07-16
forum: Apple Hardware Users
---

### Post by dlangeliers on 2008-07-16
I'm thinking of picking one up, but I'm curious to know if anybody here has had problems syncing the new 3G up with linux. Any info (success, horror stories) would be helpful.

Cheers,
-Dave

---

### Post by kosumi68 on 2008-07-17
It first needs to be jailbroken. If you have information about how to do that, please report :)

---

### Post by Sigudian on 2008-07-18
the tool to jailbreak the iPhone 3g is not released yet, though its almost finnished (only some few bug's left)

[http://blog.iphone-dev.org](http://blog.iphone-dev.org)

i hope for a release tomorrow

---

### Post by m4cks on 2008-07-19
why would a jailbreak be required to get simple file system / amarok access to the device? i've been unable to do anything with the device so far. will jailbreak when it comes out .. i'm standing by.

---

### Post by kosumi68 on 2008-07-19
Hi m4cks,

many many iphone/ipod users ask the same question. The usb communication between itunes and the device is encypted, and as of yet, nobody has been able to decrypt it. Amongst computerists, this silly policy is probably the main reason to jailbreak the phone.

We all follow the iphone-dev team closely at this point :-)

---

### Post by kosumi68 on 2008-07-20
Ok, I managed to use the excellent PwnageTool to jailbreak the iPhone 3G. Please refer to google on how to do that.

Once jailbreaked, the instructions on this wiki are a good start:

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

The iphone-mount/iphone-umount commands seem to work. Amarok will pick the device up, and happily transfer songs to the phone. However, the music does not turn up in the ipod application. It could be anything; new file structure on the phone, me doing something wrong...

Anyways, partial success so far. :)

---

### Post by trionic on 2008-07-21
Surely what we need is an iPhone 3G running mobile Ubuntu :D

---

### Post by Sigudian on 2008-07-21
i think amarok as to be updated,
anyhow, im trying like crasy to get this to work, and im tired of opening VMware to get songs over. But i realize that i might not personally be able to make amarok and 3G iPhone work anyway

(just doing some testing back and forth and so on)

---

### Post by kaptainkaffeine on 2008-07-21
How did you get it to come up in your VM? When I plug my iphone in, it gives a "You plugged in a camera!" dialog and there is no mounting happening and no device appears in the VM's Removable Devices menu. What am I missing?

edit: Oh, is your jailbroken? I'd really like to be able to at least put music on it without. :(

---

### Post by kosumi68 on 2008-07-21
> **trionic said:**
> Surely what we need is an iPhone 3G running mobile Ubuntu :D

Yes! Although there might be vastly different views on the subject, it should  be techniqually possible now. In theory :)

---

### Post by bdcheung on 2008-07-24
+1...  mine shows up as a digital camera in vmware.

---

### Post by nortcr on 2008-07-27
I have connected my 3g to Amarok using the previously mentioned directions. I could see music on my iPhone and transfer music, but the iPhone did not like this too much . I eventually had to reinstall the firmware to resume proper operation. There must be differences in the file systems of the old iPhones and the new iPhones.

---

### Post by nortcr on 2008-07-27
On a similar topic, does Virtal Box with XP installed work with the iPhone in iTunes?

---

### Post by cck197 on 2008-07-27
I've just tried VirtualBox 1.6.2 (not the OSE release) and VMware Workstation 6.0.4 build-93057 and neither were able to restore a firmware image to my 2G iPhone. VMware came much closer though. iTunes errors were usually 1603 & 1614.

I'm having the same problem with the iPod database being visible in amarok and gtkpod but not showing up on the device.

The Lifehacker winpwn 2.0 jailbreak instructions work well though.

[http://lifehacker.com/399198/jailbreak-iphone-20-on-windows-with-winpwn](http://lifehacker.com/399198/jailbreak-iphone-20-on-windows-with-winpwn)

---

### Post by jwater7 on 2008-07-29
I set up a VMware player image using qemu commands, then installed XP and iTunes.  After that, I got an iTunes error, and remember doing something to enable USB 2.0.  After that it worked, and I've been syncing music with my phone for a couple weeks now.

---

### Post by synthaxx on 2008-07-30
As stated above **do NOT use ipod-convenience with the 3g!**
I think this will also count for 2.0 upgraded iPhone and iPod Touch's.

I've been trying to work backwards through the mount-unmount script, deleting the things it added but i think i missed a couple of steps because iTunes still can't read the contents.

So far i've deleted the 2 links (./iTunes ./iPod_Control), the SysInfo and directory in ./iTunes_Control/Device . This hasn't helped.

I still think i'm missing something. The music is now in ./iTunes_Control/Music which i don't think is the correct one. 

Can someone with a non-corrupted iphone 3g check where it's writing the directories/music? If I'm correct we should only have to move it back to it's original spot (and avoid having to reinstall the whole firmware).

Thanks!

/Edit: I just remembered that i synchronized some music with Amarok which took a really long time, maybe that's where it started moving the directory?

---

### Post by Rhubarb on 2008-07-30
<IMHO>
Why buy an iphone if it has to be jail-broken (and hence possibly the warranty voided) if you can't get it to talk with Ubuntu?

The iphone has been designed (poorly) to only work with itunes and apple / windows OS.  As it stands at the moment, it's the opposite of freedom.
</IMHO>

---

### Post by dannyobrien on 2008-07-30
So you can currently get access to the internals of the iPhone 3G using pwnage 2.0, but Apple changed the checksum on the iTunes database, so gtkpod and amarok can't put new music onto the phone, and corrupts the database if they try. The same is true of iPod Touch running firmware 2.0...

---

### Post by CAsurfer on 2008-07-31
Like synthaxx, I also used ipod-convenience with my 3G, and now I have the following 2 problems:

1) Even though I am able to read and write music to the iPhone using a variety of Linux media apps (Amarok, Rhythmbox, gtkpod), I am unable to play any of the music on my iPhone using the "iPod" app.

2) iTunes on my Vista partition no longer recognizes my iPhone, and insists that I restore it to factory settings, which I think means reinstalling the firmware.

---

### Post by jrattner on 2008-07-31
Has anyone solved this problem?  Can I transfer my music to the iphone 3g with Ubuntu?

Furthermore,  has anyone been able to sync any of their calendars or contacts with ubuntu?

---

### Post by Mic_Droz on 2008-08-01
@ jwater7 - what commands did you use? I was under the impression that no one could get the iPhone 3gs to sync with itunes in a VM? the old ones worked, but the 3gs have had problems... I'm sick of dual booting...

Can you point me to a thread or link that you used?

---

### Post by leonardoxiao on 2008-08-01
> **synthaxx said:**
> As stated above **do NOT use ipod-convenience with the 3g!**
I think this will also count for 2.0 upgraded iPhone and iPod Touch's.

I've been trying to work backwards through the mount-unmount script, deleting the things it added but i think i missed a couple of steps because iTunes still can't read the contents.

So far i've deleted the 2 links (./iTunes ./iPod_Control), the SysInfo and directory in ./iTunes_Control/Device . This hasn't helped.

I still think i'm missing something. The music is now in ./iTunes_Control/Music which i don't think is the correct one. 

Can someone with a non-corrupted iphone 3g check where it's writing the directories/music? If I'm correct we should only have to move it back to it's original spot (and avoid having to reinstall the whole firmware).

Thanks!

/Edit: I just remembered that i synchronized some music with Amarok which took a really long time, maybe that's where it started moving the directory?

After messing up my iPhone 3G, I had to wipe out everything. Now with the clean machine, this is what I have:

```
iPhone:/ root# ls -l /var/mobile/Media/
total 0
drwxr-x--- 4 mobile mobile 136 Aug  1 09:59 DCIM/
drwxr-xr-x 2 mobile mobile 102 Aug  1 10:59 Downloads/
drwxr-xr-x 2 mobile mobile  68 Aug  1 10:46 MxTube/
drwxr-x--- 2 mobile mobile  68 Jun 15 21:54 Photos/
drwxr-xr-x 2 mobile mobile  68 Aug  1 10:17 Purchases/
-rw-r--r-- 1 mobile mobile   0 Aug  1 09:57 com.apple.itunes.lock_sync
drwxr-xr-x 5 mobile mobile 170 Aug  1 09:57 iTunes_Control/
iPhone:/ root# ls -l /var/mobile/Media/iTunes_Control
total 0
drwxr-xr-x 52 mobile mobile 1768 Aug  1 09:57 Music/
drwxr-xr-x  2 mobile mobile  170 Aug  1 10:15 Ringtones/
drwxr-xr-x  2 mobile mobile  408 Aug  1 10:42 iTunes/
iPhone:/ root# ls -l /var/mobile/Media/iTunes_Control/iTunes
total 56
-rw-r--r-- 1 root   mobile   612 Aug  1 10:59 IC-Info.sidb
-rw-r--r-- 1 mobile mobile  1140 Aug  1 09:58 IC-Info.sidv
-rw-r--r-- 1 mobile mobile  6808 Aug  1 09:58 PhotosFolderAlbums
-rw-r--r-- 1 mobile mobile    96 Aug  1 09:58 PhotosFolderPrefs
-rw-r--r-- 1 mobile mobile   245 Aug  1 10:42 Rentals.plist
-rw-r--r-- 1 mobile mobile  1222 Aug  1 10:42 Ringtones.plist
-rw-r--r-- 1 mobile mobile     8 Aug  1 09:58 ShowMarketing
-rw-r--r-- 1 mobile mobile     0 Aug  1 09:57 iTunesControl
-rw-r--r-- 1 mobile mobile 16620 Aug  1 10:42 iTunesDB
-rw-r--r-- 1 mobile mobile  1232 Aug  1 10:42 iTunesPrefs
iPhone:/ root#

```

It looks like music are stored in /var/mobile/Media/iTunes_Control/Music/ folder.

What's the next step?

---

### Post by synthaxx on 2008-08-01
> **leonardoxiao said:**
> After messing up my iPhone 3G, I had to wipe out everything. Now with the clean machine, this is what I have:...

Sorry, i was way off. The actual problem is that anything that writes to your iphone does so to the iTunes database, which in the case of the 3g (and other firmware 2.0 devices) fails some kind of hash check.

So if you want to try out if a new version of a program writes correctly to the iphone, back up your /var/mobile/Media/iTunes_Control/iTunes directory (make sure you ftp it back using the "mobile" user!).
If it fails, just restore this directory via sftp.

I didn't get around to solving the problem, instead i backed up my contacts 'n stuff (the SQLDB files in /var/mobile/Library) and just wiped the whole thing. A quick resync with iTunes (which i loathe btw...) and everything was well again.

So until we hear something, just keep the above in mind when expirimenting (and backup with sftp just in case..)

I'll keep experimenting, if i find anything i'll report back.

---

### Post by twosox on 2008-08-01
> **jrattner said:**
> Has anyone solved this problem?  Can I transfer my music to the iphone 3g with Ubuntu?

Furthermore,  has anyone been able to sync any of their calendars or contacts with ubuntu?

Contacts -- yes.  Using the Funambol app (from the App Store) which I pointed at Schedule World ([http://www.scheduleworld.com](http://www.scheduleworld.com)), all of my contacts from my Thunderbird Address Book are now happily synced to my iPhone 3G.

Calendar -- not so much.  I am looking at syncing via USB to an Outlook calendar at work, then wireless to the ScheduleWorld once a suitable iPhone SyncML client is available (the Funambol guys have said that they will release a jailbreak version to do Calendar, but the App Store said NO to them including it in there, since it would compete with MobileMe).

In the meantime, I might try out NuevaSync ([http://www.nuevasync.com](http://www.nuevasync.com)) which apparently does some sort of Exchange emulation and then syncs to Google Calendar, which is what I need in order to combine (or at least see) my work calendar with my family calendar.

I'm still stumbling with the music and gtkpod doesn't seem to work on the 3G iphone yet.  In the meantime, I was unable to make it work with VitrualBox, so I cranked up a VMWare machine which seems to work fine -- I can add music and photos to the device, but I'd really like to see this work under linux.

---

### Post by asphixmx on 2008-08-04
Same problem here. I have ipod touch. Back in firmware 1.1.4, I was happy syncing with gtkpod all my music & videos. Since I upgraded to firmware 2.0 and some job doing ipod-convenience work again, I can upload music via gtkpod. The problem is the ipodtouch can't play it. It says there's no music. An advise: if you have ipod touch, firmware 1.1.4, stay there until there is a solution for 2.0. I hate to run windows just to use the iTunes to sync my music. Besides, I had to restore my whole ipod, cause the iTunes libraries were corrupted by the gtkpod :(
I hope someone finds a solution... if I find one, I'll be back posting.

---

### Post by korban on 2008-08-05
In the meantime VMware Player 2.0.4 Build 93057 is working for me.
You have to add ```
ehci.present = "TRUE"
``` to your vmx file to activate usb 2.0.

---

### Post by dragonflyby on 2008-08-05
I also bought a 3g iphone, and would like to share my article on [how to handle the 3g iphone on ehow]("http://www.ehow.com/how_2377867_handle-g-iphone.html"), hope it helps for you.
Or you wanna Watch DVD on 3G iPhone, go straight to the [DVD to iPhone Converter.]("http://www.pqdvd.com/dvd-to-iphone-movie-video-converter.html")

---

### Post by njee on 2008-08-08
I also have it up and running on VMplayer using the above mentioned USB 2.0 file edit in order to get it to recognise the iphone.

backups will work but as far as I have read you can't to a recovery / update because of the iphone powercycling during the process and it not getting picked up again by itunes in vmware....something a furture version of the player will hopefully correct.

I just jailbroke my iphone today using winpwn so hopefully I will get it up and running through gtkpod or banshee....

---

### Post by asphixmx on 2008-08-09
Confirmed, using vmware (activating USB 2.0) with itunes installed, the ipod touch or iphone 3g can sync... but uploading music using gtkpod in linux, corrupts the whole music library.

---

### Post by njee on 2008-08-09
Right, after getting vmware syncing up and running I thought I would jailbreak my iphone and try ssh. Jailbreak works fine and I can ssh in and use gtkpod - which seems to be able to upload the files fine (rhythmbox could see them on the iphone as well)

The problem seems to be with the firewire guid - I suspect there is something different there for the 3g because I've run through the various guides and tried everything but I still can't get the files to actually show up on the iphone.

Also as was reported - messing around with gtkpod means you will have to do a restore in itunes in order to use it again with itunes - and apparently you can't do a restore or update through vmware.

Incidentally does anyone know whether or not updating the software on my iphone will ultimately make it harder for it to work on linux in the future? I stll hold out hope of USB syncing at some point but it seems update 2.01 have some baseline changes to the iphone and I know previous ipod updates have broken compatability...

---

### Post by bhandley on 2008-08-10
Awesome.  After days of frustration I was able to sync my iphone using vmware player.  Thanks guys.  

Note: neither flavor of virtualbox (OSE/reg) or vmware server will work.  

Also, for those of you having problems with your computer rapidly switching between charging and disconnecting your iphone, go to "Preferences" > "Removable Drives and Media" and delete any command you have under the "Digital Camera" import command.  I originally unchecked the box but that seemed to make the computer ignore the thing all together sometimes.  Now it asks me if I want to download and I just push ignore.  Worked for me anyway.

So happy I don't have to dual boot!!

UPDATE!!!:
I spoke too soon.  syncing works ok, but when I upgraded firmware, i received some horrible error.  Don't remember what it said because I was too busy slamming my head into my monitor.  It left the phone in recovery mode and system restore gave me the same awful error.  I had to find an old 10gb HD and install XP on it just to get the iphone up and running again.  Don't know if any of you have had the same issue.

---

### Post by evanevan on 2008-08-11
So is there any expectation of a new libgpod that works with 2.0 firmware?

[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html) says the last stable version was released on Nov 11th 2007.

I'd love to just use an open source firmware as well, but from what I hear this is not possible on the device.

---

### Post by maxpilax on 2008-08-13
Has anyone found a fix for iTunes after a sync with Amarok ? I'm using v.2.0.1

---

### Post by Lord C on 2008-08-14
I removed Rhythmbox and installed gtkpod. gtkpod downloaded all my songs/playlists.

The next time I loaded iPod on the iPhone I see 'No Content'
So I checked over STFP and all the music is still there, it must be the bloody iTunes file that's messed up or something.

Trying iphone-mount and gtkpod again. It still sees all my files.

How can I get the phone to recognise my files again?

---

### Post by ethoxyethaan on 2008-08-14
[http://www.iphonelinux.org/index.php/Main_Page](http://www.iphonelinux.org/index.php/Main_Page)

far from ready. i don't even see why you would pay for a handheld device to remove the nonefree software on it and damage the GNU project further.

---

### Post by njee on 2008-08-15
@Lord C

I think it's something to do with the firewireguid not writing a hash that the phone will accept. I have the same problem with mine. It will put the files on there but the iphone won't recognise them until it gets an appropriate key - unfortunately I think they changed something for version 2.0

@ethoxyethaan. Everyone here running an open-source phone raise their metaphorical hand. Anybody? I'll be the first to admit that the iphone isn't open - in fact its the complete opposite. There is more than one conception of freedom and in this case its positive freedom. The freedom to integrate an mp3 player, phone with a decent UI and ipod in one. The freedom to be able to store more than 200 text messages and until an open source phone comes along that does all that better I'll make do with an iphone.

---

### Post by cyberdork33 on 2008-08-15
> **njee said:**
> @ethoxyethaan. Everyone here running an open-source phone raise their metaphorical hand. Anybody?

You have to understand that this forum is really intended to be a support area for running Linux (Ubuntu in particular) ON Apple hardware. Since this _is_ Apple and Ubuntu related I haven't had this thread moved (also because there really isn't anything that is a better place for this either). 

Either way, if his post doesn't help any in this topic, just ignore.

---

### Post by Lord C on 2008-08-15
Tried a backup and restore, to no avail. I believe the music is actually erased from the harddrive now - will check when I get home.

I wanted to upgrade firmware and re-jailbreak anyway, for the installer.app.

Looks like I'll be installing VMWare when I get home then, for syncing the iPhone :/
Shame. Wonder why they had to change the damn hash - always with the DRM.

---

### Post by spacetree on 2008-08-15
I'm liking apple less and less every day. I'm even starting to think "This guys are even meaner than micro$oft" 

Perhaps we have to wait until someone figures out how the hashing is done.

---

### Post by tippyknit on 2008-08-15
I haven't used the iPhone with my Ubuntu computer yet, but I do have an iPod that I attempted to use it with; which was an entire disaster. I had read that with wine you could install iTunes, which told me to reinstall it (43 times in a row, to be exact) because it didn't have the correct sync file. I used GTKpod which didn't give me any options other than what to sync. iTunes is a much more briliant solution. I ended up going straight back to apple because it was impossible to move my media onto my iPod. I still use Ubuntu on my old computer, but having an old iMac to use with an iPod is a good solution.

---

### Post by kosumi68 on 2008-08-16
Scanning through the bug reports of amarok, it seems this problem is being worked on. Since this has been tried by far too many already; syncing the iphone 2.0 firmware with amarok 1.4.9.1 does not work, it corrupts the ipod files. When there is an update, I am sure we will hear about it in this thread.

---

### Post by oooioiii on 2008-08-16
> **kosumi68 said:**
> Scanning through the bug reports of amarok

hi, what bug are you referring to?
I cant find any when searching for "iphone" :(

---

### Post by kosumi68 on 2008-08-17
The keywords are libgpod, which is the library responsible for ipod/iphone support, and 3G. Apparently people are working on reverse-engineering the new hashing scheme for iTunesDB introduced in the 2.0 firmware.

---

### Post by UbuWu on 2008-08-18
I sync my calendar over the air using [Nuevasync]("http://www.nuevasync.com/") with google calendar and evolution uses this calendar too, so I got that part working :-) Now only the music...

---

### Post by gameguy43 on 2008-08-23
> **UbuWu said:**
> I sync my calendar over the air using [Nuevasync]("http://www.nuevasync.com/") with google calendar and evolution uses this calendar too, so I got that part working :-) Now only the music...

Thanks for the tip.  i just got this working on my phone.  so i have contacts syncing with funambol+scheduleworld and now calendar syncing with nuevasync+google.

i'm also using easytask manager, which is okay-not-great, but it syncs to their servers online.  i'm not controlling my data, but at least there's more than one copy of it.

---

### Post by roalt on 2008-08-23
> **kosumi68 said:**
> The keywords are libgpod, which is the library responsible for ipod/iphone support, and 3G. Apparently people are working on reverse-engineering the new hashing scheme for iTunesDB introduced in the 2.0 firmware.

Thanks for the tip. On previous occasions (v1.1.4 or so), some other hacking took place with information on the iTunesDB:

[http://ipodminusitunes.blogspot.com/](http://ipodminusitunes.blogspot.com/)

[This message]("http://sourceforge.net/mailarchive/message.php?msg_id=d45479530807220400n57f174daud7e08e6d28105442%40mail.gmail.com") indicates that they have not yet figured out how to hack the iTunesDB.

So, I think for now Rhythmbox in combination with iphone v2.0.x will not work.

---

### Post by Mic_Droz on 2008-08-29
Hey guys, just trying to confirm - has anyone that has used the vmware player used xp sp3? I read somewhere that sp3 doesn't play nice when you try and sync the iPhone 3g, and frankly, i've been on sp3 for ages... plus, i haven't been able to find the post that said that in the first place.

what do you guys think? can i do firmware updates through vmware? or does that make the ship sink to the bottom of the atlantic? also, can i boot up windows xp if i really need to after using vmware player?

(sorry, i meant that i would like to convert a current partition of xp to be able to load in linux as a vm, but also be able to boot to xp native if i have to...)

---

### Post by doubledouce on 2008-08-29
I'm trying to figure out the exact same thing as Mic_Droz. I've come to terms with (reluctantly) having to install Windows on VMVare, but I have to know if I'll be able to transfer music to my iphone doing this. Anyone...?

---

### Post by timmillwood on 2008-08-29
This is the only thing that is stopping me switch from Mac OS X to Ubuntu.

---

### Post by twosox on 2008-08-29
> **Mic_Droz said:**
> Hey guys, just trying to confirm - has anyone that has used the vmware player used xp sp3? I read somewhere that sp3 doesn't play nice when you try and sync the iPhone 3g, and frankly, i've been on sp3 for ages... plus, i haven't been able to find the post that said that in the first place.

what do you guys think? can i do firmware updates through vmware? or does that make the ship sink to the bottom of the atlantic? also, can i boot up windows xp if i really need to after using vmware player?

(sorry, i meant that i would like to convert a current partition of xp to be able to load in linux as a vm, but also be able to boot to xp native if i have to...)

I have been using the iPhone and a VMWare XP machine (with SP3) for a little while now, and the connection seems to work just fine for me.  I have not tried to update the firmware with this configuration, though, because I heard that it can be problematic.  I think the approach to have some native XP/Mac around to update the firmware is probably the way to go.

---

### Post by bjhom on 2008-08-29
I have been using sp3 on vmware to sync for a week now. I however was unable to jailbreak using vmware. I think I read somewhere that it has to do with the USB resetting. I'll see if I can find a ref. I have a 16 gb 3g running 2.0.3.

---

### Post by jhonekumar on 2008-08-29
I'm using a wonderful iphone theme in my Pocket PC, you can also get this one at [http://www.iphonethemeforpocketpc.com/](http://www.iphonethemeforpocketpc.com/).

Feels like now i'm having a new iphone

Itz really amazing....

---

### Post by njee on 2008-08-31
I used to proper windows box to jailbreak my iphone - everything I have read up until a few weeks ago suggests you can't update / restore your iphone because VMWare fails to 'catch' the iphone when it reboots. I cant be sure but I believe an updated VMware is slated to try and fix this...or rather, people are angry at vmware for this not working.....

---

### Post by emshains on 2008-09-27
> **spacetree said:**
> I'm liking apple less and less every day. I'm even starting to think "This guys are even meaner than micro$oft" 

Perhaps we have to wait until someone figures out how the hashing is done.

The thing is, Microsoft took over Apple, when it purchased most of its auctions, now the real guy behind mac is Bill, and that means, no linux support ever, and to make  the relation-ships better with his old friend IBM, he made macs go Intel, which is one of the most idiotic things to do, because now you can't give any rational reason for buying a mac, other than style and macos.

You see, Microsoft could win the monopoly with windows, just by making the price lower than macOS's, but you can't out-deal something which has no price at all (price as in money), so it wants to out-run linux just by making it user-unfriendly, and so far it has succeeded. Just look, once AA got popular (about release 2.5) it ended the support for linux. 

Enough IT company talk, its time for iPhone. 
I am really eager to get my iphone, but it would be stupid to buy something that doesn't work, so, could I sync music with linux ? I don't want to pay for vmware, so is it possible for openbox ? (for the copy of windows, Ill use my friends copy) 
If that doesn't work, Ill borrow my mothers laptop, and Ill sync my music through samba, but has anyone tried to add a folder in iTunes, thats shared over the network ?

---

### Post by wanye on 2008-10-01
a (working) workaround for the hashing algorithm is to install PWNPLAYER (out real soon now) and use it instead of the standard music player app. it plays filesystem tunes. i just uploaded a bunch of mp3s via ssh/scp (filezilla ftp client) directly to the ipod touch via my home wifi connection. its playing them perfectly!

[http://www.pwnplayer.com](http://www.pwnplayer.com) or keep checking cydia. i dont know when its out, but its due soon and definitely works!

---

### Post by kosumi68 on 2008-10-01
> **wanye said:**
> a (working) workaround for the hashing algorithm is to install PWNPLAYER (out real soon now) and use it instead of the standard music player app. it plays filesystem tunes. i just uploaded a bunch of mp3s via ssh/scp (filezilla ftp client) directly to the ipod touch via my home wifi connection. its playing them perfectly!

[http://www.pwnplayer.com](http://www.pwnplayer.com) or keep checking cydia. i dont know when its out, but its due soon and definitely works!

Brilliant. Absolutely brilliant. Do you know if pwnplayer also plays .ogg files? I could not tell from the link.

---

### Post by dirtygreek on 2008-10-01
[http://www.virtualbox.org/ticket/491#comment:47](http://www.virtualbox.org/ticket/491#comment:47)

Supposedly, the problem can be fixed this way.  

```
sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot

```

---

### Post by wanye on 2008-10-02
> **kosumi68 said:**
> Brilliant. Absolutely brilliant. Do you know if pwnplayer also plays .ogg files? I could not tell from the link.

i dont think it does.

but as i said, its in beta, so who knows what cool features will get added.

pwnplayer and mxtube are now the killer apps for my ipod touch. i cant live without them :)

---

### Post by jack frost on 2008-10-08
> **dlangeliers said:**
> I'm thinking of picking one up, but I'm curious to know if anybody here has had problems syncing the new 3G up with linux. Any info (success, horror stories) would be helpful.

Cheers,
-Dave
*I have virtualbox -xp vm and was able to sync with itunes using the below post I found in the forums.  mine is 2g unlocked/jailbroken and it worked.. the orig post was for 3g phone; but it appears to work for 2g too.*
* *
[I]I was able to get my iPhone to sync. My setup:

Ubuntu 8.04 (Hardy Heron)
[[COLOR=#444444]VirtualBox 2.0.2[/COLOR]]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")
iPhone 3G (Software version 2.1)

I followed the steps mentioned in the thread on the virtualbox website

[[COLOR=#444444]http://www.virtualbox.org/ticket/491#comment:52[/COLOR]]("http://www.virtualbox.org/ticket/491#comment:52")

In particular, I did this:

[FONT=Courier New]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT][/I]

---

### Post by loconet on 2008-10-09
> **kosumi68 said:**
> Brilliant. Absolutely brilliant. Do you know if pwnplayer also plays .ogg files? I could not tell from the link.

Yah but now that puts music playing under the same restrictions as other apps. Mainly, you can't run the player in the background while doing other tasks. 


Oh Apple, how I hate you. You make Microsoft look like an open source shop.

---

### Post by dirtygreek on 2008-10-10
An absolutely awesome add-on, if you're jailbroken (and you should be) is Backgrounder.  Go to Cydia and look it up.  It lets you run almost anything in the background.

As for this kernel module, does it work only in VirtualBox 2.0? It hasn't worked for me in earlier versions, but I haven't tried 2.0 yet.

---

### Post by sicofante on 2008-10-11
> **loconet said:**
> Yah but now that puts music playing under the same restrictions as other apps. Mainly, you can't run the player in the background while doing other tasks.
Actually pwnplayer does run in the background and you can play music while doing other tasks.

---

### Post by snivek on 2008-10-12
Is pwnplayer availble for the iPhone yet?  I do not see it listed on cydia.

---

### Post by Jonny0204 on 2008-10-17
its not released yet, i found this file on mediafire tho, not sure if its working yet, i need to now jailbreak.

al post back to tell u if it works, assuming u aren't back on this thread soon.

[http://www.mediafire.com/download.php?na4mmzntzyi](http://www.mediafire.com/download.php?na4mmzntzyi)

---

### Post by Jonny0204 on 2008-10-18
Yeah it works fine, shame about not being able to have tracks off the filesystem using cover flow, but hopefully it will by the time its properly released.
Since it works fine with ubuntu i'm not complaining at all, but i'm gonna have to create a script that will allow me to place the music str8 into the desired folder on my iphone, its annoying to do it by hand.

---

### Post by jack frost on 2008-10-20
I have found these post to work for me for syncing 2g iphone in virtual box via itunes.
2g phone, unlocked and jailbroken, running 2.1 firmware..   the first is the fix if you have usb issues in virtual box, the second is the usb fix for the iphone.. I have been syncing now for a month.. works fine.   running hardy 8.04, amd64 x2.

 Someone did reply it worked for 3g phone.


Lets Install the essential build utilities so the vbox kernel module builds.
sudo apt-get install build-essential linux-headers-`uname -r`
Install i386 VirtualBox without repository:
wget [http://www.virtualbox.org/download/1...hardy_i386.deb]("http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb") ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb
 Install amd64 Virtualbox without repository:
wget [http://www.virtualbox.org/download/1...ardy_amd64.deb]("http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb") ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb
  
Check Here for updated Virtualbox Packages since the repository isnt added yet
Alternate install with Gutsy repository as some people have suggested works fine, just copy/paste these exact commands into the terminal:
sudo sh -c 'echo "# VirtualBox repository for Ubuntu Gutsy
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free" \
> /etc/apt/sources.list.d/gutsy-virtualbox.list'
wget [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install virtualbox
Now you Must add your self to the vboxusers group:
sudo adduser $USER vboxusers
Adding user `ionstorm' to group `vboxusers' ...
Adding user ionstorm to group vboxusers
Done.
 
Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:
sudo gedit /etc/init.d/mountdevsubfs.sh
 
You'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Now uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
 
Ok now logoff, then log back in so the vbox driver see's you are logged in to the vboxusers group.
If the above doesnt work try rebooting, if that doesnt enable usb you can try this:
Grab the vboxusers group id:
grep vbox /etc/group
vboxusers:mad::124:ionstorm
Edit the fstab with the group id # in bold:
sudo gedit /etc/fstab
Append this to the fstab then save/exit:
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
Now lets edit the mountkernfs.sh file with the gid in bold:
sudo gedit /etc/init.d/mountkernfs.sh
Paste the 2 lines below above the line: "# Mount spufs, if Cell Broadband processor is detected"
## Mount the usbfs for use with Virtual Box
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=124,devmode=664
You may not need to reboot, try doing:
sudo /etc/init.d/mountkernfs.sh



IPHONE USB FIX

[I] followed the steps mentioned in the thread on the virtualbox website

[[COLOR=#444444]http://www.virtualbox.org/ticket/491#comment:52[/COLOR]]("http://www.virtualbox.org/ticket/491#comment:52")

In particular, I did this:

[FONT=Courier New]sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot[/FONT][/I]

---

### Post by Pilo on 2008-10-23
jack frost thank you a lot!  Your directions were complete and easy to follow.  They worked perfectly for me (amd64 iPhone 3g). I no longer need to dual boot I can sync just fine.

Thanks again.

---

### Post by wanye on 2008-10-24
> **Jonny0204 said:**
> Yeah it works fine, shame about not being able to have tracks off the filesystem using cover flow, but hopefully it will by the time its properly released.
Since it works fine with ubuntu i'm not complaining at all, but i'm gonna have to create a script that will allow me to place the music str8 into the desired folder on my iphone, its annoying to do it by hand.

bear in mind that beta2 version is old. beta4 is out now (to testers) and b5 is due any day now, which fixes quite a few issues.

it wont be on cydia until it is stable. but if you want a copy of the up to date betas, just donate to errick (see the pwnplayer website) and he will send you a copy. just dont be all whiny if something is broken still.

it wont play ogg files YET, but errick is currently looking at wma playback, so i would have thought it would be along at some point in the future, along with loads of other features.

since upgrading from beta1 to b4, the player has become infinitely more stable (b1 crashed occasionally). i now no longer have any tracks in my itunes library, they are all on the filesystem (use something like filezilla to transfer songs via SCP) - coverflow doesnt work on it (yet), but i'd rather have ease of track management over shiny coverflow features for now. it saves me having to copy songs to my mac mini, import them to itunes, then sync it all up with the touch. too much effort!

---

### Post by inferno1005 on 2008-10-26
pwnplayer is now in cydia, its still the beta 5 version but it works :)

---

### Post by jack frost on 2008-10-26
> **inferno1005 said:**
> pwnplayer is now in cydia, its still the beta 5 version but it works :)


i saw it last night.. it says it does not play video yet though.. eventually...will it sync contacts like itunes?

---

### Post by wanye on 2008-10-26
at the moment, pwnplayer is JUST used for playing back music.

mewseek (a slsk client) has also been released to cydia. they both work really well...

---

### Post by darkvad0r on 2009-03-06
No need to use PwnPlayer if you sync through gtkpod or amarok, just follow these instructions:
[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

---

### Post by dirtygreek on 2009-03-06
This has been working for me, but I'm not sure if this or something else caused the problem I'm having - my album art is all crazied out.  Different songs have different cover art by different bands.  Anyone else?

---

### Post by darkvad0r on 2009-03-10
Yes, I had the same problem (I even wrote about it in the troubleshooting and tips section of the ubuntu wiki page I linked to above)

I suppose that the reason is that the album art was first sync'd with iTunes, and the database format was version 4 (in the Checkpoint.xml file on your iPhone). Then you change it manually to 2 to be able to sync through libgpod, so that effectively screws up the album art.

As I wrote in the wiki, the only workaround I found is to sync all of your music with gtkpod or amarok (and to have the album art embedded in the mp3s). You'll then be able to sync with iTunes or amarok or gtkpod without worrying about messing up your album art.

I hope I was clear enough :)

---

### Post by orduek on 2009-03-10
I'm loading music files to /var/mobile/Media/music but i can't find them in my Ipod application.
I'm with Iphone 3G.

---

### Post by RealG187 on 2009-03-11
This is why I hate iPod, you are locked down to propritory iTunes. As a Linux uaer that makes me mad.

My phone can mount as a USB flash drive or FTP serger and I can use Nautilus or any file manager to copy songs in regardless of OS, even can scan right into it from my scanner or copy songs from myg Xbox (modded with USB support, plug in USB device to [NSLU2 ]("http://bestwikiever.wikidot.com/NSLU2")which plugs into ethernet) or PS3 if I get one.

---

### Post by darkvad0r on 2009-03-11
@Orduek

I guess the wiki isn't as specific as it should be. If you just scp your music to some folder in your iPhone, the iPod application won't see it because it relies on a database to know where the music is.
If you want to be able to see it, you have to sync through one of the applications that use libgpod to keep that database up to date. 

I have tried with amarok, gtkpod and rhythmbox (which all use libgpod to sync) and the only one that doesn't work is rhythmbox.

---

### Post by Gliitch on 2009-03-24
I have this really annoying issue with Ubuntu and Pwn Player.When i load music up to my iPhone, its seen but gets skipped. I thought it might be ID3 tags, but some songs dont even display artist or album name and yet still play. :S (only sometimes) But in windows they are all fine. I don't want to use the bloated iTunes software.

Thanks 

Ok, so i managed to get it to Sync with Amarok :D but i dont get any Album art.. :( .. apparently gtkpod does this? Also is there anyway to get it to sync with Exaile, as i think that is by far the best music player around. xD

---

### Post by darkvad0r on 2009-03-25
> Ok, so i managed to get it to Sync with Amarok  but i dont get any Album art.. 

It might be related to this issue: [https://help.ubuntu.com/community/PortableDevices/iPhone#No%20Cover%20Art%20with%20Amarok](https://help.ubuntu.com/community/PortableDevices/iPhone#No%20Cover%20Art%20with%20Amarok). Let us know if that helps.

> Also is there anyway to get it to sync with Exaile

I've never tried, but since it uses libgpod to sync, there's a fairly good chance it's possible, why don't you try it and let us know how that worked ? You could even write about it in the wiki ;)

---

### Post by Gliitch on 2009-03-25
> **darkvad0r said:**
> It might be related to this issue: [https://help.ubuntu.com/community/PortableDevices/iPhone#No%20Cover%20Art%20with%20Amarok](https://help.ubuntu.com/community/PortableDevices/iPhone#No%20Cover%20Art%20with%20Amarok). Let us know if that helps.



I've never tried, but since it uses libgpod to sync, there's a fairly good chance it's possible, why don't you try it and let us know how that worked ? You could even write about it in the wiki ;)

Well at the moment, im getting a Python error in Exaile, but it shouldn't be too hard to fix. ;) I shall try later on tonight,and see how it goes. Also, using Amarok is is pretty much flawless with 2.2.1 firmware.

:D I upgraded to 3.0 Beta, but thats screwed up(not a developer) but solved that issue(it upgrades the baseband)+ Videos work, they take a bit of time to transfer. A reboot or restarting the Springboard works,you can reboot or restart SB by: $ killall SpringBoard or just reboot.

Does anyone know how to start apps via command line? As doing /Applications/PwnPlayer.app/PwnPlayer(thats just an example) doesn't work anymore. 
 Oh, i solved the Album Art problem ^_^ in Amarok,There is an option in the top menu to mass add album art work. :D Fixed the keyring issue too [http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14).

Ive noticed that when putting songs on with Amarok, it comes up with a screwed up alphabet.For example, A would appear half way down the line B would be at the very top. Anyone got a solution?  

Thanks for your response, much appreciated :D

@asphixmx

I find Pwnplayer to crash too much, especially if there is a large music library. Also it doesnt always copy over properly, some times just skips tracks.

---

### Post by asphixmx on 2009-03-25
I like more using dTunes or Pwnplayer. It is easier to transfer your folders with music using filezilla or mounting via ipod-convenience. Those two players can access folders, dTunes downloads music directly from the internet, erase files directly on your ipod; pwnplayer can make playlists...I feel more powerful those players than the ipod's default player. And sync job is easier, too. Well, that's my opinion.

---

### Post by RealG187 on 2009-03-26
What's dTunes?

---

### Post by Gliitch on 2009-03-27
> **RealG187 said:**
> What's dTunes?

dTunes is an alternative music player to the Iphone's stock one. you can also download torrents, when set up properly. Also delete files too.Fixed the messed up database. Just sync through itunes :)

---

### Post by Gliitch on 2009-04-14
I have managed to upgrade to 3.0 Beta 3 and i have signal too(ligit o2 sim) (im not a dev ;))Bluetooth stereo finally :D. I've tried to sync with amarok,(1) I edited the file in the lockdown folder, not sure what its called. But anyway, when i copied the files, it doesnt show up on my iphone, BUT it does show up in itunes and when its all synced up it shows in my collection, although it doesnt play. :( I havnt found a solution as of yet..Anyone wanna help out?? :)

---

### Post by dirtygreek on 2009-04-24
VirtualBox was working fine with my touch until I upgraded to Jaunty.  Now I get problems when it tries to mount the ipod - XP mounts it as a camera, but iTunes complains that it can't sync with it anymore. Any ideas?

Jaunty may not be the issue, and I haven't tried just syncing it with a regular windows machine yet - will try that next.

---

### Post by jack frost on 2009-04-24
> **dirtygreek said:**
> VirtualBox was working fine with my touch until I upgraded to Jaunty. Now I get problems when it tries to mount the ipod - XP mounts it as a camera, but iTunes complains that it can't sync with it anymore. Any ideas?
 
Jaunty may not be the issue, and I haven't tried just syncing it with a regular windows machine yet - will try that next.
 
I had the same thing happen i had my iphone and was syncing in virtual box.. you  have to recompile virtualbox with this:
 
 /etc/init.d/vboxdrv setup
 
I actually found it on their website forum.. I think I also ran the usb fix again too.. if I find it I will add that to the post.

---

### Post by jack frost on 2009-04-24
> **dirtygreek said:**
> VirtualBox was working fine with my touch until I upgraded to Jaunty. Now I get problems when it tries to mount the ipod - XP mounts it as a camera, but iTunes complains that it can't sync with it anymore. Any ideas?
 
Jaunty may not be the issue, and I haven't tried just syncing it with a regular windows machine yet - will try that next.
 
 
here is the other info I used for the usb virtual box fix:
 
 
Lets Install the essential build utilities so the vbox kernel module builds.
sudo apt-get install build-essential linux-headers-`uname -r`
Install i386 VirtualBox without repository:
wget [http://www.virtualbox.org/download/1...hardy_i386.deb](http://www.virtualbox.org/download/1...hardy_i386.deb) ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb
Install amd64 Virtualbox without repository:
wget [http://www.virtualbox.org/download/1...ardy_amd64.deb](http://www.virtualbox.org/download/1...ardy_amd64.deb) ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb
Check Here for updated Virtualbox Packages since the repository isnt added yet
Alternate install with Gutsy repository as some people have suggested works fine, just copy/paste these exact commands into the terminal:
sudo sh -c 'echo "# VirtualBox repository for Ubuntu Gutsy
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free" \
> /etc/apt/sources.list.d/gutsy-virtualbox.list'
wget [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install virtualbox
Now you Must add your self to the vboxusers group:
sudo adduser $USER vboxusers
Adding user `ionstorm' to group `vboxusers' ...
Adding user ionstorm to group vboxusers
Done.
Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:
sudo gedit /etc/init.d/mountdevsubfs.sh
You'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Now uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
 
Lets Install the essential build utilities so the vbox kernel module builds.
sudo apt-get install build-essential linux-headers-`uname -r`
Install i386 VirtualBox without repository:
wget [http://www.virtualbox.org/download/1...hardy_i386.deb](http://www.virtualbox.org/download/1...hardy_i386.deb) ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb
Install amd64 Virtualbox without repository:
wget [http://www.virtualbox.org/download/1...ardy_amd64.deb](http://www.virtualbox.org/download/1...ardy_amd64.deb) ; sudo dpkg -i virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb
Check Here for updated Virtualbox Packages since the repository isnt added yet
Alternate install with Gutsy repository as some people have suggested works fine, just copy/paste these exact commands into the terminal:
sudo sh -c 'echo "# VirtualBox repository for Ubuntu Gutsy
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free" \
> /etc/apt/sources.list.d/gutsy-virtualbox.list'
wget [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install virtualbox
Now you Must add your self to the vboxusers group:
sudo adduser $USER vboxusers
Adding user `ionstorm' to group `vboxusers' ...
Adding user ionstorm to group vboxusers
Done.
Setup VirtualBox USB Support:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:
sudo gedit /etc/init.d/mountdevsubfs.sh
You'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Now uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
 
I followed the steps mentioned in the thread on the virtualbox website
[http://www.virtualbox.org/ticket/491#comment:52](http://www.virtualbox.org/ticket/491#comment:52)
In particular, I did this:
sudo apt-get build-dep linux-source-2.6.24
sudo apt-get install linux-source-2.6.24 build-essential
tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot

---

### Post by orduek on 2009-04-30
Does anyone tried MewSeek Pro?
I downloaded it and when I open it and I got an msg says "Your music library cannot be read. Downloaded music will not be able to be added to ipdod".
Does anyone got that?
thank you.

---

### Post by Gliitch on 2009-05-03
Mew Seek Pro has been shut down due to Copyright Infringment, thats the last i heard. But with your problem, you have to sync one song from your itunes library(can be done in VirtualBox, so can Jailbreaking) doing so it will create the necessary folders/files for you to use Mewseek Pro properly.

---

### Post by supermorph on 2009-08-18
so can i re-confirm.

use a virtual pc (that emulator u said with an os which supports itunes)
and sync a picture or song or app, and the nessisary apps on ubuntu now have access to the iphone's database? (e.g the music etc)

what does it create? (is it an ssh trust?)
:)

thanks in advance for any help
i updated to karmic and wandered if thats gonna cause problems.

---

### Post by drdom on 2009-09-02
Does Internet sharing via Bluetooth work in Ubuntu? Do you have to jailbreak for this?

thanks in advance!

---

### Post by williamjems on 2009-09-03
Hi Drdom.

I am using ubuntu 9.04 But I have never try for Internet sharing via Bluetooth in ubuntu.
So I can try for this and let you know what happen. Thank you.

---

### Post by drdom on 2009-09-03
> **williamjems said:**
> Hi Drdom.

I am using ubuntu 9.04 But I have never try for Internet sharing via Bluetooth in ubuntu.
So I can try for this and let you know what happen. Thank you.

Hello williamjems.

I hope you'll do it! That's my main concern, because I'm prepared to boot to Windows occassionally to sync my iPhone, but I really need to get mobile internet to my Ubuntu. Thanks in advance!

---

### Post by cyper on 2009-09-08
Im currently trying to start using iPhone 3GS in iTunes running in Virtualbox 3.0.4 on Jaunty. Up to now i've succeeded to connect iPhone to iTunes and it was recognised. Ive shared my media folder to vbox (guest is Windows 7). Now i showed iTunes the share as iTunes Music folder, so I hope it wont copy all my music to virtual drive (anyway it would lack space there). As soon as it finish indexing music i'd try to add some to iPhone.
Up to now it seems all right.

---

### Post by Devastator9 on 2009-09-10
I just install VirtualBox Ver 3.0.6 r52128 and Itunes 9 in VB with no problems.
I did 3GS firmware update and SYNC in VB no problems.

Not sure if anyone else has tried Itunes 9 yet.

---

### Post by forbzie22 on 2009-12-12
I see a few people saying the iphone needs to be jailbroken first.

You can use an application called SHAREPOD on windows which is an excellent program, this manages to sync with every ipod / iphone incl 3GS perfectly. 

So i take it, it has been jailbroken.

I still use windows for iphone but constantly searching for linux alternative.

---

### Post by thinktyler on 2009-12-13
Happy to report that the iphone does work under ubuntu 9.10 with no need to jailbreak your device. 

You need: 

libusb-1.0 
usbmuxd
libiphone
iFuse and gvfs-backend-afc
libgpod

more information can be found here: 

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)

Happy ubuntuing.

---

### Post by kyleabaker on 2010-01-17
> **thinktyler said:**
> Happy to report that the iphone does work under ubuntu 9.10 with no need to jailbreak your device. 

You need: 

libusb-1.0 
usbmuxd
libiphone
iFuse and gvfs-backend-afc
libgpod

more information can be found here: 

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)

Happy ubuntuing.
Any idea what the progress on this is? I'd really like to see an easier method to getting my iPod Touch 3G to sync with Ubuntu. I hope this support ready in time to be included in Ubuntu 10.04 by default!

---

### Post by mjneil.81 on 2010-01-19
1

---

