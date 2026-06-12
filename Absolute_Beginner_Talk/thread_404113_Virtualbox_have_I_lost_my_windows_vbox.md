---
title: "Virtualbox: have I lost my windows vbox?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by kevmartin on 2007-04-08
Hi,

First off let me say I wasn't sure where to post this - general help, or what - so I went for Absolute Beginner as thats really what I am - and HOPEfully thats the reason for my issue and someone will be able to advise easily.

OK, I have Ubuntu Edgy running on a dualboot system, and have been trying to switch to virtualbox for my windows needs.  I just started it up and get an error - my windows box is inaccessible, and this:
```

Hard disk '/home/kev/.VirtualBox/VDI/NewHardDisk1.vdi' with UUID {c53d93ba-4042-4e38-9bb1-17d7fb051948} is already attached to a machine with UUID {f99595ba-fce3-4b87-9d05-b7af4bb2269c} (see '/home/kev/.VirtualBox/Machines/Windows/Windows.xml').

Result Code: 0x80004005
Component: Machine
Interface: IMachine {fd443ec1-0009-4f5b-9282-d72760a66916}

```

I have no idea what this means - or how to fix it. Restarting vbox did not help. Attaching a screenshot that might provide a clue to those in the know.

Thanks in advance
[IMG]http://cashcrusader.info/Screenshot.jpg[/IMG]

---

### Post by ajmorris on 2007-04-08
> **kevmartin said:**
> Hi,

First off let me say I wasn't sure where to post this - general help, or what - so I went for Absolute Beginner as thats really what I am - and HOPEfully thats the reason for my issue and someone will be able to advise easily.

OK, I have Ubuntu Edgy running on a dualboot system, and have been trying to switch to virtualbox for my windows needs.  I just started it up and get an error - my windows box is inaccessible, and this:
```

Hard disk '/home/kev/.VirtualBox/VDI/NewHardDisk1.vdi' with UUID {c53d93ba-4042-4e38-9bb1-17d7fb051948} is already attached to a machine with UUID {f99595ba-fce3-4b87-9d05-b7af4bb2269c} (see '/home/kev/.VirtualBox/Machines/Windows/Windows.xml').

Result Code: 0x80004005
Component: Machine
Interface: IMachine {fd443ec1-0009-4f5b-9282-d72760a66916}

```

I have no idea what this means - or how to fix it. Restarting vbox did not help. Attaching a screenshot that might provide a clue to those in the know.

Thanks in advance
[IMG]http://cashcrusader.info/Screenshot.jpg[/IMG]


How much RAM in the settings for this windows VM is set. Which version of windows is it? and can you post you windows.xml file that is reported in the error? Also have you tried VMware? it is very good, if you have enough RAM

---

### Post by kevmartin on 2007-04-08
> **ajmorris said:**
> How much RAM in the settings for this windows VM is set. Which version of windows is it? and can you post you windows.xml file that is reported in the error? Also have you tried VMware? it is very good, if you have enough RAM

Thanks for responding :-)

RAM setting for it is 512Mb, version is XP SP2.  The only recent change to the system I can think of that might be related is a change to the fstab for the real windows partition to allow for ntfs-3g. (That's not to say it is related - just the only change I can think of that has been made and even vaguely seems possibly related to me).

The XML file is very long due to all the snapshots, so I'll prune those out as they don't seem relevant (hope thats right).

I haven't tried vmware no - I have 3Gb RAM, but do think the whole point of having Windows accessible through a virtual machine is so both it and linux can run simultaneously, with me switching from one to the other using the apps I can only run in windows in that and everything else in ubuntu.  I had to phone MS and get them to activate over the phone for vbox - hopefully if I try vmware it wouldn't mean having to do that again - it was a pain lol.  But I am willing to try it if is friendly and useful enough (opinions highly welcome).  I have also seen references to qemu but know nothign about it.  

Here's the xml (and thanks again):

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<!-- InnoTek VirtualBox Machine Configuration -->
<VirtualBox xmlns="http://www.innotek.de/VirtualBox-settings" version="1.2-linux">

  <Machine OSType="winxp" currentSnapshot="{1e9f288b-a0d5-4ef8-bbe9-f6b2262a1c9d}" lastStateChange="2007-03-31T03:23:19Z" name="Windows" uuid="{f99595ba-fce3-4b87-9d05-b7af4bb2269c}">
    <ExtraData>
      <ExtraDataItem name="GUI/LastCloseAction" value="save"/>
      <ExtraDataItem name="GUI/LastWindowPostion" value="63,40,1156,917"/>
      <ExtraDataItem name="GUI/Fullscreen" value="off"/>
      <ExtraDataItem name="GUI/AutoresizeGuest" value="off"/>
    </ExtraData>
 
[ 9 snapshots deleted here to keep it short ]

   <Hardware>
      <CPU>
        <HardwareVirtEx enabled="false"/>
      </CPU>
      <Memory RAMSize="512"/>
      <Boot>
        <Order device="Floppy" position="1"/>
        <Order device="DVD" position="2"/>
        <Order device="HardDisk" position="3"/>
      </Boot>
      <Display VRAMSize="32"/>
      <RemoteDisplay authTimeout="5000" authType="null" enabled="false"/>
      <BIOS>
        <ACPI enabled="true"/>
        <IOAPIC enabled="false"/>
        <Logo displayTime="0" fadeIn="true" fadeOut="true"/>
        <BootMenu mode="messageandmenu"/>
      </BIOS>
      <DVDDrive passthrough="false">
        <HostDrive src="/dev/hdb"/>
      </DVDDrive>
      <FloppyDrive enabled="true"/>
      <USBController enabled="false"/>
      <Network>
        <Adapter MACAddress="080027C7BE66" cable="true" enabled="true" slot="0" type="Am79C973">
          <NAT/>
        </Adapter>
        <Adapter MACAddress="080027A0D807" cable="true" enabled="false" slot="1" type="Am79C973"/>
        <Adapter MACAddress="080027B23BDB" cable="true" enabled="false" slot="2" type="Am79C973"/>
        <Adapter MACAddress="0800271C1025" cable="true" enabled="false" slot="3" type="Am79C973"/>
      </Network>
      <AudioAdapter driver="oss" enabled="false"/>
      <SharedFolders>
        <SharedFolder hostPath="/media/sda5" name="DATA"/>
        <SharedFolder hostPath="/media/sda2" name="WINPARTITION"/>
        <SharedFolder hostPath="/media/sdc1" name="IOMEGA"/>
        <SharedFolder hostPath="/media/IOMEGA_HDD" name="IOMEGA2"/>
      </SharedFolders>
      <Clipboard mode="Disabled"/>
    </Hardware>
    <HardDiskAttachments>
      <HardDiskAttachment bus="ide0" device="master" hardDisk="{95fcc974-bb2b-4e3d-873e-49c56a47e056}"/>
    </HardDiskAttachments>
  </Machine>

</VirtualBox>

```

Edit to add:  Alongside the Machines folder in the .Vitualbox folder, I see a folder named VDI  In that is: NewHardDisk1.vdi (1.1 Gb in size).  Seems not quite right to me - so I thought I'd mention it.

---

### Post by kevmartin on 2007-04-08
On the issue of VMware - I found this article on [**setting it up to boot an existing windows installation**]("http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition")

It sounds a bit scary in terms of various warnings of don't do this or that or you'll lose all the data, but other than that, I'd be interested in opinions on this approach - it sounds ideal.

---

### Post by kevmartin on 2007-04-21
Still no luck here with virtualbox - I upgraded to Feisty hoping it would magically fix the issue, but of course it did not. Things still seem the same.

Any ideas anyone?  Thanks.

---

### Post by kevmartin on 2007-04-23
Well so much for that.  I tried deleting the entry - it gave me a warning it would not be able to be restored "by GUI".n but now it is gone, though the sub-entries still exist under the Virtual Disk Manager.  But if I try clickign Add for any of those I get an error that they are not a main entry or somethign.

I guess this is adding up to a dealbreaker for virtualbox for me.  Major shame as for a little while it seemed like a real solution for me.  So I'm probably stuck on dual-booting  :-( as I'm really not game to try the vmware conversion instructions I mentioned earlier when they are full of "be careful or you'll destroy everything" warnings.

---

### Post by GSF1200S on 2007-04-23
> **kevmartin said:**
> Well so much for that.  I tried deleting the entry - it gave me a warning it would not be able to be restored "by GUI".n but now it is gone, though the sub-entries still exist under the Virtual Disk Manager.  But if I try clickign Add for any of those I get an error that they are not a main entry or somethign.

I guess this is adding up to a dealbreaker for virtualbox for me.  Major shame as for a little while it seemed like a real solution for me.  So I'm probably stuck on dual-booting  :-( as I'm really not game to try the vmware conversion instructions I mentioned earlier when they are full of "be careful or you'll destroy everything" warnings.

hmm.. I installed virtualbox yesterday and Ive had no problems with it running. I cant share between the vbox and linux yet.. but im getting there.

Where in the process do you get the error? I would suggest deleting ALL of your .vdi except the one containing your actual windows install..

---

### Post by GSF1200S on 2007-04-23
> **kevmartin said:**
> Still no luck here with virtualbox - I upgraded to Feisty hoping it would magically fix the issue, but of course it did not. Things still seem the same.

Any ideas anyone?  Thanks.


If you upgraded to feisty, and your kernel was upgraded in the process, virtualbox wouldnt work. Try moving the vdi file and reinstalling virtualbox. 

We can get this... It worked fine for me on feisty. BTW, how did you install it? I used a debian package...

---

### Post by GSF1200S on 2007-04-23
> **kevmartin said:**
> Hi,

First off let me say I wasn't sure where to post this - general help, or what - so I went for Absolute Beginner as thats really what I am - and HOPEfully thats the reason for my issue and someone will be able to advise easily.

OK, I have Ubuntu Edgy running on a dualboot system, and have been trying to switch to virtualbox for my windows needs.  I just started it up and get an error - my windows box is inaccessible, and this:
```

Hard disk '/home/kev/.VirtualBox/VDI/NewHardDisk1.vdi' with UUID {c53d93ba-4042-4e38-9bb1-17d7fb051948} is already attached to a machine with UUID {f99595ba-fce3-4b87-9d05-b7af4bb2269c} (see '/home/kev/.VirtualBox/Machines/Windows/Windows.xml').

Result Code: 0x80004005
Component: Machine
Interface: IMachine {fd443ec1-0009-4f5b-9282-d72760a66916}

```

I have no idea what this means - or how to fix it. Restarting vbox did not help. Attaching a screenshot that might provide a clue to those in the know.

Thanks in advance
[IMG]http://cashcrusader.info/Screenshot.jpg[/IMG]

Take a look at the difference in our virtual disk manager... its way different. When you created a virtual machine, did you use fixed size or dynamically expanding? It looks to me like you should reinstall virtualbox with the debian package, recreate a virtual machine, and reinstall windows. I cant see any reason for you to have so many .vdi files, especially when I have only one.

Im no expert here, but Ive found this forum doesnt deal with virtual machines that often, so im going to give it a shot...

---

### Post by GSF1200S on 2007-04-23
dangit, forgot the screenshot..

---

### Post by kevmartin on 2007-04-23
> **GSF1200S said:**
> Take a look at the difference in our virtual disk manager... its way different. When you created a virtual machine, did you use fixed size or dynamically expanding? It looks to me like you should reinstall virtualbox with the debian package, recreate a virtual machine, and reinstall windows. I cant see any reason for you to have so many .vdi files, especially when I have only one.

Im no expert here, but Ive found this forum doesnt deal with virtual machines that often, so im going to give it a shot...

Thanks for the input.  I think all the entries in the disk manager came from snapshots I was taking when I started out. I had big problems with screen resolutions so as I built my virtual machine I was being ultra cautious taking snapshots I could revert to at each step along the way.  I did use the deb package and had it set for dynamic sizing. I'm leaning towards being brave and trying vmware before I try virtualbox again - to get an idea which one I prefer. Opinions seem to be really divided between the fans of each of the two. Either way I think a reinstall is on the cards - if I have to phone Microsoft for activation again I'll scream lol (thats one of the big appeals of the vmware option - being able to use an existing partition for the virtual machine).

---

### Post by GSF1200S on 2007-04-23
> **kevmartin said:**
> Thanks for the input.  I think all the entries in the disk manager came from snapshots I was taking when I started out. I had big problems with screen resolutions so as I built my virtual machine I was being ultra cautious taking snapshots I could revert to at each step along the way.  I did use the deb package and had it set for dynamic sizing. I'm leaning towards being brave and trying vmware before I try virtualbox again - to get an idea which one I prefer. Opinions seem to be really divided between the fans of each of the two. Either way I think a reinstall is on the cards - if I have to phone Microsoft for activation again I'll scream lol (thats one of the big appeals of the vmware option - being able to use an existing partition for the virtual machine).

Ok, let me fill you in on a few things before you start.

1) VMplayer is free, but youll need to create a virtual machine with QEMO (something like that) in order to use vmplayer. All other versions of Vmware cost...

2) Supposedly, virtualbox takes far less resources.

3) If you install vmplayer and run your existing windows install, you wiill have to input a cd key every time you boot into actual windows. Keep this in mind if windows is used for some games. After like 30 times, youll have to call microsoft and activate it again. I dont know how many times theyll do this...

4) You have to turn off certain processes in windows in order to run it. Driver profiles will also need to be changed.

Also, whats involved with that activation? I have 29 days before I need to activate windows. Did you tell them it was on a virtual machine on your computer or what? I need to be careful here..

Good Luck

---

### Post by kevmartin on 2007-04-23
Wow, that sounds interesting about having to use the CD Key when booting back to Windows proper.  Probably wouldn't be likely to be a problem for me as long as the virtual windows performs well enough.  I don't us games at all, but my biggest reason for keeping windows is for very 3D design work, which is very memory intensive indeed. If thats going to cause me to go back to windows proper regualrly anyway, then I may be better with vbox.

Regarding the activation I struck, I have my original copy of XP on CD for which the computer no longer exists, so I used that for my virtual machine, while my windows proper has the copy of Media Center XP I got with the computer last year.  What I told them when I rang was kind of the truth but without mentioning the virtual thing or linux.  I just said I had completely rebuilt my computer so the XP was being used on a effectively a whole new machine, and the original machine no longer exists.

---

### Post by GSF1200S on 2007-04-23
> **kevmartin said:**
> Wow, that sounds interesting about having to use the CD Key when booting back to Windows proper.  Probably wouldn't be likely to be a problem for me as long as the virtual windows performs well enough.  I don't us games at all, but my biggest reason for keeping windows is for very 3D design work, which is very memory intensive indeed. If thats going to cause me to go back to windows proper regualrly anyway, then I may be better with vbox.

Regarding the activation I struck, I have my original copy of XP on CD for which the computer no longer exists, so I used that for my virtual machine, while my windows proper has the copy of Media Center XP I got with the computer last year.  What I told them when I rang was kind of the truth but without mentioning the virtual thing or linux.  I just said I had completely rebuilt my computer so the XP was being used on a effectively a whole new machine, and the original machine no longer exists.

Well. I wish I could figure out how to share files between linux and my VM.. im starting to get angry. I used your other thread:
[http://ubuntuforums.org/showthread.php?t=378725&page=2&highlight=virtualbox+sharing](http://ubuntuforums.org/showthread.php?t=378725&page=2&highlight=virtualbox+sharing)

and of course it did nothing for me.


You will have a hard time using virtualbox or any virtual machine to run something 3D. The only method I know of is a VMware program you must pay for, and directx support is in BETA on that pogram. People have complained of it being very slow and buggy, but working nonetheless. You might want to stick to dual booting until they work the bugs out...

---

### Post by kevmartin on 2007-04-23
> **GSF1200S said:**
> Well. I wish I could figure out how to share files between linux and my VM.. im starting to get angry. I used your other thread:
[http://ubuntuforums.org/showthread.php?t=378725&page=2&highlight=virtualbox+sharing](http://ubuntuforums.org/showthread.php?t=378725&page=2&highlight=virtualbox+sharing)

and of course it did nothing for me.


You will have a hard time using virtualbox or any virtual machine to run something 3D. The only method I know of is a VMware program you must pay for, and directx support is in BETA on that pogram. People have complained of it being very slow and buggy, but working nonetheless. You might want to stick to dual booting until they work the bugs out...

Yeah I'm pretty much resigned to being stuck on dual booting just for the 3D stuff like Poser and Bryce. Even booting to windows normally chews up massive amounts of RAM for these apps. I upgraded from 1Gb to 3Gb RAM a few months ago - improvement, but still never enough lol

---

### Post by GSF1200S on 2007-04-23
I got it man.. I know exactly what you need to do.

I noticed another post where you asked about transferring files from the guest OS to the Host OS, and vice versa. Well, I tried the advice suggested by one of the members, and bam, as soon as I rebooted, **windows was inaccesable as it was for you**. I deleted the .vdi, created a new one, reinstalled windows (aghh.. i know) and rebooted VirtualBox. The I started googling, and I found an awesome post on a Mepis Linux forum. Following carlops' advice, I was able to create a shared folder in Linux, and mapped a network drive to it in Windows. Now, I can move files to and from my guest OS as much as I want. As a trial, I downloaded AVG Free for windows on linux. Placed it in the folder, went into the network drive on Windows and INSTALLED AVG Free on my guest OS. It works, and heres the link

[http://www.mepislovers.org/forums/showthread.php?t=5152]("http://www.mepislovers.org/forums/showthread.php?t=5152")

Make sure to read ahead a few times... he makes a few code mistakes at first, but he gets it right and it works.

Good Luck!

---

### Post by kevmartin on 2007-04-24
Welllll ... this is my news: I tried installing Qemu according to a how to on here - seemed fine until I got an error I couldn't work out :)  Then I installed Vmware when I noticed it was in the application manager.  But I couldn't work out how to create images for it, so I went back to plan A - virtualbox.  I uninstalled it completely, reinstalled it, then when I went to create my virtual machine, clicked on existing instead of new - all those images (well 1 image and all the others were snapshots/sub-entries) were still there.  So I selected that one, and started it up - guess what, no need to reinstall windows - it was already there installed from before :-)

I did have to phone Microsoft and activate again, but they didn't ask any questions this time, just gave me my codes.  So I'm back in business.  Will try the networking stuff later tonight.  I did lose my installed applications too - but thats no biggy.

---

### Post by jackmc on 2007-06-23
arg. I have this error... looks like there was no real solution :(

---

### Post by hotplainrice on 2007-07-04
Same issue.
Exactly the same.

Tried re-creating the machine by building a new one with an existing vdi.     Windows is there, but all the snapshots aren't incorporated.

---

### Post by AxL456 on 2008-02-16
hi everyone..

well i guest the poster of this thread does not have the problem anymore, but i'll find some solution that work for me in this link:
[http://forums.virtualbox.org/viewtopic.php?t=2845]("http://forums.virtualbox.org/viewtopic.php?t=2845")

vbox seems to have some problems when you delete a share folder from the host.

---

