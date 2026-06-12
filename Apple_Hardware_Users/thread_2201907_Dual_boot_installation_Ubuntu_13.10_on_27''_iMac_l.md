---
title: "Dual boot installation: Ubuntu 13.10 on 27'' iMac late 2009 with Mavericks"
date: 2014-01-26
forum: Apple Hardware Users
---

### Post by Balamku on 2014-01-26
I have no knowledge of Ubuntu, but I wanted to install it on my 27’’ iMac. 
I spend weeks reading through lots of information, that was more confusing than helpful in the end…  
So this post is divided into two sections:   
One is trying to be(come) an installation guide - trying to be helpful so don’t kill me if things turn nasty! 
  - with the open issues below…    

IMPORTANT: You will need an USB mouse that plugs in and works straight away! (Simple Logitech one did the trick, - after trying 4 mice…)  
If you have a USB keyboard sitting in the basement it will make things a lot easier, I have used the aluminium one that came with the Mac, you just have to be patient to pair it….    

1. Create space to install Ubuntu 13.10 

   In OS X Maverick (10.9.x), the Disk Utility is able to add a partition to the current disk without completely repartitioning the hard drive. To use this method, start Disk Utility, (Applications > Utilities) select the Hard drive to partition, move to Partition in the submenu, and click the '+' button below the current layout graphic to add a partition. You can then resize the partition to suit the amount of space you would like to use for Ubuntu. Don't worry about the partition format, we will be deleting it later. With Maverick you can resize your partition: Resize the new partition (make it a lot smaller!) so that enough space remains for Ubuntu. 
(In theory it should be enough to resize the existing partition, but I do not know if that will trigger Boot Camp?)  
Boot Camp will be available under Utilities once you have created a 2nd partition. Start it but do not start the Windows installation - press cancel. (I did this because many posts say it is necessary for Dual Boot to work, but it makes your system hybrid - see open issues) 

   2. Download and install rEFInd  
Unpack Refind-bin-0.7.7 and find the install.sh file. Open a terminal window. Drag and drop “install.sh” into terminal window. Type in admin password if requested. Read message (warning and successful installation) 
(I did not use rEFIt since I read a lot about problems with 13.10 because it is outdated.)    

3. Download and burn Ubuntu13.10  
Sounds easier than it is - it took me a lot of time to figure it out…  If you want to install 13.10 on an Intel Core 2 Duo make sure you find the right image. It is named:   
ubuntu-13.10-desktop-i386.iso 
  - I had to look around quite a bit, but this is the only Intel image, all others are AMD-based, so make sure you download the correct one. 
I haven’t figured out wether this one installed the 32-bit or the 64-bit version, but it works….  
DON'T burn the .iso directly! You need a .cdr version to be able to boot it.  
Again open Disk Utility and drag and drop the .iso onto the left below your hard drives. Click on it and in the top part open the drop down to convert it to “DVD/CD master” without encryption.  
Once its saved you have got two versions on the left: the iso and the cdr version. Make sure you burn the right one with slow speed. To do so click "Burn" while the cdr is activated and change the speed in the drop down menu and click to verify it.  
Don’t worry if you can’t read it. Eject the CD. 
   
4. Restart MAC  
Test the rEFInd - you should be able to start hitting the apple, shut down and reboot (yellow symbol).    

5. Try Ubuntu  
Insert the Ubuntu disc - power down and restart pressing the “C” key. (If the boot menu starts, click the yellow reboot and hold the “C” immediately.) 
 NOW turn off your magic mouse!! (backside of the mouse the little knob green is on grey is off) you can turn it off earlier but it has to be off in order to connect it.  
Ubuntu will let you choose between trying and installing.  Choose “Try Ubuntu” - it will take some time, but will start with your USB mouse but no keyboard.    

6. Connect your keyboard 
 Click on the Bluetooth symbol in the upper right corner (same position as on the MAC).  Search for new devices and do change the setting in the menu: Device type to “Input devices” (and if it doesn’t work try to set the PIN to 0000).  
NOW switch on the magic mouse. If you see the keyboard coming on and off - ignore it.  
You should be able to connect the magic mouse once it has found its proper name, it might not work (as in my case), but will trigger the keyboard (why? no clue!), on which you now press the power button for several seconds until the green light stops and then press power again with the green light coming on for a few seconds.  
Now you should be able to see the keyboard, first with numbers, than with the name its gotten under your MAC installation. Wait for the MAC name and than connect it. 
You will have to insert a PIN that you see on the screen. Afterwards the keyboard should be paired. You might have to try again, - keyboard and mouse are known issues…    

7. Connect to the internet  
The wireless should work immediately, just put in your path-phrase. I used “show password” to make sure the keyboard settings are OK.    

8. Test Ubuntu  
Sound, display … all worked fine for me - so I started Step 9….    

9. Install Ubuntu 
  Click on the Install Ubuntu13.10 icon on the desktop or the second from the top on the left side. I did choose to install third party software and updates…   
Ignore the choices and select “Something else” at the very end of the menu.   
Now you see all your hard drives and more “free space” at the end of the list. 
Create a new logical partition “at the beginning of the space” with “Ext4 Journaling file system” and “/“ as mount point. Don’t use all the space!   
Create another partition minimum twice your memory as logical partition, “beginning of space” with Swap in the selection menu as your swap area.    
Many guides tell you, the boot loader should point to your Ext4 (/sda5 in my case) partition, this didn’t work for me and left the linux boot frozen in a black window. 
I just re-tried the installation.  Instead point to your main drive that gives you the name and size of your whole drive (1TB and /sda in my case) (this is also different to the EFI partition! EFI is /sda1 in my case)    
Now Ubuntu installs ( you have to choose your location and later username, pw… but that is all self-explaining…    
Choose “log in automatically” to make sure you don’t have to type in your password without a keyboard!    
Afterwards you have to play around with mouse and keyboard again - and you have to! - in order to use the boot loader…    

10. Reboot  
You will see the Apple and it is your default, starting if you do not interact. Try to boot Ubuntu - the right Penguin, but don't worry if Apple starts up. Unfortunately the mouse and keyboard issues are the same on the MAC… but the settings allow you to let the keyboard pair automatically.    

11. Check boot loader
  Make sure you have your keyboard connected before you exit either Mac or Ubuntu, as you will need it. 
 You should see two Penguins sitting next to the Apple, the right one with start GRUB and GRUB will start Ubuntu.    

12. Delete Macintosh HD2
 Start your MAC partition enter Disk Utility, delete the 2nd disk and allocate the space to the other disk(s).    

Hope this is all you have to do!    

If not, my hint would be to press F2 twice in the rEFInd Boot and in the command line type: ro root=/dev/sda5 (your ext4 partition) - did not have to do that, but found it on the web. 
Lots of other help: [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)     

Now my two remaining issues:  

1. My system is hybrid (found a command line to check that), but there is no need, since I will not install Windows. 
I have two boot loaders, with no added value. (Plus the spare Penguin in the middle??? - I can live without the Ubuntu icon )  
—> Out of curiosity: is there a way to clean this up? - Better installation??? 

   2. Mouse and keyboard: I found a guide for 12.04 to insert the PIN of mouse and keyboard under dev/lib/bluetooth/your device but in 13.10 they are all in one directory - under "names" they are all shown, but I did not find a file to insert the PINs.  
I tried the command line sudo apt-get install blueman, but it didn’t change a thing…. 
I have searched around the forum but most entries are for 12.04 or older and do not seem to work!  
The magic mouse is connected but not paired in Ubuntu and the on/off button doesn’t stay in the on position….. (I found a post for this one, but the solution didn’t work)  
Keyboard needs to be re-connected every single time (Mac and Ubuntu)….  I read many posts but nothing worked....  
Any ideas?

---

