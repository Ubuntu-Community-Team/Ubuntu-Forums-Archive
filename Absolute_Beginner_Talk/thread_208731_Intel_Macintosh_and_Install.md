---
title: "Intel Macintosh and Install"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by chasisaac on 2006-07-04
I just finished installing and have revamped some instructions
These are posted at:
[http://www.planetisaac.com/articles/ubuntuinstall.html](http://www.planetisaac.com/articles/ubuntuinstall.html)
I will get them into a better place shortly



After installing Ubuntu on my MacBook I have decided to edit/write these instructions that are originally from, [http://bin-false.org/?p=17](http://bin-false.org/?p=17). 

I want to clean up these instructions so that Macintosh users who want to use an Open Source solution for your computer and operating system. 

1. Back up your hard drive. I would suggest that you use Carbon Copy Cloner [http://www.bombich.com/software/files/cccloner.dmg](http://www.bombich.com/software/files/cccloner.dmg)

If you do not have an extra hard drive at least back up your personal data. Carbon Copy will take a snapshot of your drive and you can always go back to it. 

2. Deauthorize your computer from iTunes, just in case anything goes really wrong. Remember because of the DRM from Apple you may only authorize five computers in your life. Then your iTunes music goes bye-bye.

3. When you download rEFIt, make sure you follow the instructions in the read me file. Remember double-click on the Hard Drive icon and place the folder there. 

4. Download Apple's Boot Camp [http://www.apple.com/macosx/bootcamp/](http://www.apple.com/macosx/bootcamp/) 
When running Boot Camp go to the section of changing the partition sizes. 
You may quit Boot Camp when Apple wants the Windows disk.
I recommend about 11GB of disk space at the least. 
My first time I used 16GB and I have since reinstalled into a larger partition. 

5. Boot from the Dapper LiveCD by holding down the C key to boot from the hard drive. Have your ethernet plugged in for ease of ethernet.

6. When Ubuntu comes up click on the install icon. 

7. When you come to the partitioning section you will need to follow a few small steps.
a. Delete the newly made partition of 10GB. 
b. Click on the free space and add a new partition. 
c. the first one should be about 9.0 - 9.5 GB in size. Formatted as primary with ext3 format.
d. the second one will be what is left and that is your SWAP drive. Format with primary and linux-swap format. 

8. At this next step you will have to choose how you want things set up. Create the "/" on the 9.5GB size of hard drive and click the format (note the partition number SDA3 is what mine is. Set the swap drive up at the small partition. Make sure you choose the correct one. 

In the mount point setup, don’t mount the /mount/EFI System Partition. Even if you do the formatting will fail. 

The install will fail at the end when it tries to install GRUB. That’s OK.

# Step 9. Open a Terminal (Applications . . . extras . . . terminal) 
# Entering of 6 commands in terminal.
# (the # is a comment similar to REM )
# Till further notice comments will have the # notation. Hence you can see what you need to type in yourself. 

sudo mkdir /mnt/ubuntu

sudo mount /dev/sda3 /mnt/ubuntu/

sudo mount -t proc none /mnt/ubuntu/proc

sudo mount -o bind /dev /mnt/ubuntu/dev

sudo chroot /mnt/ubuntu /bin/bash

# This is a long single command,
# for this command you need to have internet access.

apt-get install lilo lilo-doc linux-686-smp linux-restricted-modules-2.6.15-23-686 linux-kernel-headers

# end long command.
# This is a tough section.
# from the prompt enter in 

liloconfig

# this will run the linux loader for you. 
# you will now edit the preference file for LILO called lilo.config
# there are several ways to do this. I will give you what worked for me. 
# the vi command is a Linux/Unix editor, this will take some patience to use. 
# [http://www.computerhope.com/unix/uvi.htm](http://www.computerhope.com/unix/uvi.htm) this has instructions for vi

vi /etc/lilo.conf

# we will use the 3dd command to delete three lines

3dd

3dd

3dd

#  do the 3dd command till the file is clear. 
# 
# go to the website and copy the following information 
# into the clipboard or you can type the information

boot=/dev/sda3
default=Ubuntu
map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
label=Ubuntu
read-only

# Now you are ready to insert the corrected data
# the 'i' command will allow you now actually edit the data. 

i

# paste from the clipboard to the file
# I added some comments on the date of modification.
# next hit the escape key

ESC

# you are back to using commands in vi
# the 'ZZ' command will exit saving changes

ZZ

# Open a new terminal window. This is NOT the chrooted window. 
# we will not run part and set up the booting

sudo parted

print

# Now you have to choose the partition with Ubuntu Linux. SDA3? 
# during the set command you will choose the number of your partition


set  3  # note: the three may be a different number

boot

on

quit

# hang on we are almost done. 
# close your terminal window

# Switch back to the chrooted terminal
# Run the command

lilo -b /dev/sda

# Exit out of your chrooted environment, and umount all the partitions you 

exit 

# or you can just close the window
# now we will unmount the work we have done

umount /mnt/ubuntu/proc
umount /mnt/ubuntu/dev
umount /mnt/ubuntu

# see not that painless. 

Reboot

# If everything has gone well you will come right up to rEFIt. 




#  Step 10 

# You may be tempted to try to boot into Linux right away. 
# Please do no do it. 
# Down arrow in the rEFIt menu and choose the option of :

Partition Editor

# Have the MPR/GPT sync. The program does this on its own. 
# Choose restart from the rEFIt menu
# Choose the Linux boot device
# Let Linux run and start up
# enter in your name
# enter in your password

# By this time if all has gone well you are looking at the Ubuntu desktop
# we have one more single command to go through.

sudo dpkg-reconfigure debconf 

# choose DIALOG from the menu
# choose all the defaults
# Ubuntu Linux is now on your computer. 
# you may go to [http://bin-false.org/?p=17](http://bin-false.org/?p=17) and finish all the Macintosh related specific items. 

# end documentation

editing and expansion of data from [http://bin-false.org/?p=17](http://bin-false.org/?p=17) written by chasisaac (ubuntu forums), aka macike, [www.planetisaac.com](www.planetisaac.com), [http://www.planetisaac.com/articles/ubuntuinstall.html](http://www.planetisaac.com/articles/ubuntuinstall.html)
published under the GNU public license, June 2006

---

