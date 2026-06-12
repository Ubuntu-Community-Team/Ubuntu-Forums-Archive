---
title: "Is your RAID 0 dead? Read..."
date: 2012-05-30
forum: Any Other OS
---

### Post by sputtle on 2012-05-30
This is a fix for Windows users who have had their RAID 0 setup destroyed by installing or using Ubuntu and using a Gigabyte motherboard. I have no knowledge of other RAID setups or other brand motherboards so I cannot say if this will work. I also doubt this will work if you have installed Ubuntu on your HDD. While other set ups may be different, there should be many things similar and I hope this guide can help you. If you use another brand motherboard, you will still need that driver disk and can usually find the RAID driver easily by reading the file names and folders and using a little common sense.
 
_It is possible.._ That this fix will work without a flash drive. I didn't try it, so I don't know. After step 4 you could probably insert the motherboard disk. But I didn't know if the Windows install program would throw a fit or not, so I just used a flash drive.
 
 
**Quick background:**
I have a RAID 0 set up with Windows 7 installed. I wanted to have a back up portable OS with Ubuntu, ready to go, on my flash drive. When I ran the OS to see if it was working, it killed the RAID set up I had before. This had happened to me before while trying a multiboot set up with these 2 operating systems, but it happened again despite never being installed on the HDDs. But with the help of users like "traditionalist" and "not found," I was able to fix this problem. If you're bored and want to read about a few guys taking a round about way to solve a problem, go here [http://ubuntuforums.org/showthread.php?t=1990594](http://ubuntuforums.org/showthread.php?t=1990594) Remember, you don't always have to pin point anything to help someone fix a problem. They listened to me vent, talked to me and kept my brain working. They helped quite a bit more than they know. 
 
 
**You will need:**
A flash drive
Driver disk that came with your motherboard
Windows installation disk
 
 
 
**The problem:**
You ran Ubuntu onto your PC as a stand alone OS only to find that your RAID set up is not how you left it. After POST and before Windows/Ubuntu loads, you see both (or all) HDDs have an "Offline" status. If one or more of your drives has a status of "Member Disk" then this fix will not work for you. After verifying the DMI pool data, you see "DISK BOOT FAILURE..."
If you installed Ubuntu improperly on your HDD, then there is an extremely high chance that your previous OS is a total loss. With RAID 0 if you lose any part of one drive, everything is gone. It's because of how "striping" works. 
 
 
 
**The fix:**
 
1. Insert the driver disk for your motherboard and your flash drive into a working PC. Browse the files of the CD and copy the "GSATA" folder to your flash drive.
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winlanguage.jpg[/IMG]
 
2. Insert the Windows disk into the non-working PC and boot from it. After the benchmark you will get to this screen, select your language and click next.
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winrepair.png[/IMG]
 
3. Click the "Repair your computer" link on the bottom left.
 
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winsearch.png[/IMG]
 
4. You will come to this screen. Windows will search for installed OSs. It may find your install, it may not. Mine did, despite not being able to boot to it. **Insert your flash drive now.**
 
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/windrivers-1.png[/IMG]
 
5. Click the "Load Drivers" button.
 
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winfolder.jpg[/IMG]
 
6. Navigate to your flash drive and open the "GSATA" folder.
 
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winbit.png[/IMG]
 
7. Open the "32Bit" or "64Bit" folder depending which install you had on your HDDs. I had a 64Bit version of Windows installed on my PC so I opened this folder.
 
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winxraid.png[/IMG]
 
8. Select the "xraid_f.inf" file and open it. This is the file that contains the drivers for your RAID. 
 
 
 
 
 
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winsearch.png[/IMG]
 
9. After it installs, Windows will again search for Windows installations. If Windows doesn't detect your install this time around, there is still a problem with your OS, but not necessarily with your RAID set up. It all depends if Ubuntu had written anything to the drives while it was running. In my case, it hadn't, so all the data was still safe.

---

### Post by sputtle on 2012-05-30
[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winclose.png[/IMG]

10. Once this is finished, close this window by clicking the "X"





[IMG]http://i1231.photobucket.com/albums/ee512/sputtle/winrestart.jpg[/IMG]

11. You will be brought to this screen. On the lower right, click the "Restart" button and **remove your flash drive.** Let your PC boot normally and as long as the files are intact, Windows will load normally as before. Enjoy!

---

