---
title: "Instructions unclear"
date: 2015-08-31
forum: Apple Hardware Users
---

### Post by thomas62 on 2015-08-31
Hi guys

It says on [this page]("https://wiki.ubuntu.com/PowerPCDownloads") to tell you guys if I think the instructions are unclear. 

I am extremely grateful for the time and energy ppl dedicate to this type of thing, however I am having trouble following the guides.

Specifically, it is [this part]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F") I am having issues with.

It seems like the guide is telling me to firstly place the file on the USB stick and later format the USB to allow for the Mac's partition. See **Copying the installer files - the easy way or ** [B]Copying the installer files - the flexible way.
[/B]
^^ this is the part that is least clear. Also, why no mention of unetbootin? This guide would lead some to instantly  erase their main drives - I appreciate the warning, but still if a third  party can resolve we should have the option.[B]

Can I use unetbootin to load my ios and then alter the USB to be "Mac compliant"
[/B]
Also, it says under Copying the installer files - the flexible way.

" you should use the following method to put the files on your stick"What files?All the files, the OS? Or just the ones we need to make the stick a bootable drive?I am probably just dumb, I have some basic command line knowledge and have managed to get my PC dual booting.

Thanks in advance, I ordered a charger especially for to revive this little beast so I am really keen. I will keep researching and get back to you all.

(Perhaps I should just try install Ubuntu).

Thanks

---

### Post by rsavage on 2015-08-31
What ISO are you trying to put on USB?

---

### Post by thomas62 on 2015-08-31
Hi 

ty for reply. 

lubuntu-14.04-desktop-powerpc.iso

I understand thousands of pl have probably followed the instructions, perhaps I am just tired.

I did try making a CD (seems easier by a factor of 10,000) but the file was just a little larger than the disk couldfit.

Cheers.

---

### Post by rsavage on 2015-08-31
I'm not sure about thousands of people, you could be the only one!  Indeed, you're the only person to say 'hey you told me to say if these instructions are unclear and they are' - so well done for that!  I wrote those instructions and they're really just a reference thing, they're obviously not aimed at people newish to Linux.

Those particular instructions are for the text installers, not the desktop ISO's. 

Please have a re-read of the first USB section, especially have a look at the links about booting directly from an ISO file.  Booting from USB is really easy once you get your head around it.  One thing I would recommend is you run the command probe-usb when you first boot into openfirmware.  That just makes sure your USB devices are seen.

---

### Post by thomas62 on 2015-09-01
Hey

Thanks - I could not access this site from work so I have been burning to post the following questions / comments.

I took a look at the link you shared and I can see where I am confused.

I am not looking to to boot from a usb, however I would like to place an installer on a usb and have that install the system components. This is how I installed Ubuntu on my PC.

Questions

1) I am considering trying to use the mini ios with network access method, it seems straight forward enough! Infact I am burning the file this instant, even though it is late and I should sleep.

- update - I have successfully booted into the mino iso file! In process of network install. Will keep you posted

2) My old airport wifi - will it work with newer routers?

ty

---

### Post by thomas62 on 2015-09-01
Q - should I have selected Guided - use entire disk and set up LVM? I bet this is in the install guide huh?

I am at "installing base system" and assume it'll let me choose the flavour when I get the packages?

Need to sleep, hurry machine!

---

### Post by thomas62 on 2015-09-02
Update - I am in:)

Linux video=ofonly 

Got me past blank screen.

I loaded up the text editor and system froze tho.

Question - can I get the airport to work?

Q It says Continue to wait or press S to skip mounting or m for manual recovery - what is this thing mean? I never did make any partitions.

---

### Post by thomas62 on 2015-09-02
Update - when I load the abiword word processor that comes pre-packaged, the system freezes. I think this may not be [related to my install though]("https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007043.html")

---

### Post by thomas62 on 2015-09-02
Update 

Following these instructions - there is no content in my xorg.conf file?

[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

I am guessing I need to install this dependency? Perhasp I do not need to do it.

I wrote to my 
yaboot.conf

And tried to make the changes go to boot, however it did not stick.

Working on wifi now. Lots of fun, sore back.

Update 

I really struggle to make my setting stick. I tried to write the changes needed to make battery show up. I showed up when I made change, but on reboot, not there.

Also - just got off phone with ISP - they say I can set up a WPA password and make my laptop accept TKIP - is this true?

TY either way - I keep reading and will start looking in forums to see if I can respond to questions.

---

### Post by thomas62 on 2015-09-02
Another update -

When I try load FF, document viewer or AB word the system freezes. Also, I can't open CD tray anymore to put new disc in - I guess this [http://ccm.net/faq/6185-ubuntu-open-close-the-cd-rom-tray-in-command-line](http://ccm.net/faq/6185-ubuntu-open-close-the-cd-rom-tray-in-command-line)

---

### Post by rsavage on 2015-09-03
Let me guess you have a radeon card?

---

### Post by thomas62 on 2015-09-03
Yes mate.

A summary of most pressing issues for you

1) Changes I try write don't stick on reboot (example update the boot loader file with radeon specific parameters)
2) I am not 100% my install worked properly, after base install and an attempt to collect lubuntu - there was no actual acknowledgement of successful install - just a cursor at top of screen (could be GPU?)
3) both FF and the word processor crashed on load

Ty.

---

### Post by thomas62 on 2015-09-04
I might try a diffrent flavour - like xbuntu. I feel that the install did not work.

I'd love to know why my edits are not sticking, it's allow me to explore some of the radeon settings more deeply.

---

### Post by rsavage on 2015-09-04
You haven't said what your doing/trying - have you run ybin if you are playing with boot parameters?


Try 12.04 if you are going to switch.

---

### Post by thomas62 on 2015-09-04
Hi

Thanks so much for your help. 

Fair call, sorry if I am not being specific.

Note - not that it should matter but I am using UX term

Note - I have a Radeon card.

On this command

grep RADEON /boot/config-$(uname -r) I was returned CONFIG_FB_RADEON=y

1) In kbin, I must pass the parameter video=ofonly before I can get a display up (otherwise I receive blank screen of death)
2) If I try to string parameters in kbin, for example,  Linux video=ofonly radeon.modeset=0 I get blank screen
3) If I edit this file 
sudo nano /etc/yaboot.conf

And change the append line to remove splash and or add video=ofonly

(Note - after I press crt o - I can choose to cancel, get help, write to dos / mac format, append/prepend, backup file etc, which do I choose? I have been selecting Mac format. Next time I try load the file, it can freeze - update - I was able to just hit enter when in single user, so perhaps it's just the terminal I use).

Before writing to boot partition with 
sudo ybin -v

I still need to run the video=ofonly command on start up (this is what I mean that it wont stick)

(perhaps I need to sudo reboot? Idea / did not help)

I still need to run the command on start up (this is what I mean that it wont stick

4) What am I doing to help myself? 
I am reading this 
[https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards](https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards)

And this

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F)

5) Well why are you asking me?

I am not 100% if the OS installed correctly, I got no actual indication that it worked - only a cursor.

- I also have an odd msg about being unable to boot during loading

Note - I booted in single mode and have my xorg.conf file open, I will look around at guide and try make some adjustments.

Update - I already have an xorg.conf file. It;s not clear to me what I need to change in this file apart from removing the stuff in monitor where comment are.  I understand there are other parts of the document that ref this file

---

### Post by thomas62 on 2015-09-05
Note - this is my mac

[http://www.everymac.com/systems/apple/ibook/specs/ibook_800.html](http://www.everymac.com/systems/apple/ibook/specs/ibook_800.html)

(I am pretty sure, unsure what EMC it is ). Deft 800mhz)

I got her for $10:)

---

### Post by rsavage on 2015-09-05
It says what is going on here [https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr](https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr) and here [https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F)

---

### Post by thomas62 on 2015-09-05
> **rsavage said:**
> It says what is going on here [https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr](https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr) and here [https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F)

Hi

Thanks you for your reply.

I plain missed that part, and my freezing issues is now resolved! It's buried in the text a little, my bad.

I am now trying to make yaboot parameter "stick"

I open this file
sudo nano /etc/yaboot.conf

I edit the 'append' line as suggested I save the file and run

sudo ybin -v to copy the file across to the boot partition.

Reboot, and the settings have not been invoked.

However, when I open the  yaboot.conf file again, I can see the change are there.

---

