---
title: "About to give up on Linux"
date: 2017-12-19
forum: Apple Hardware Users
---

### Post by johnny5isalive on 2017-12-19
Last week I bought a brand new HP laptop and an external Samsung SSD. My goal was to have an office platform on the windows laptop and a completely separate dual boot version of Ubuntu on the SSD for a separate business.  

 I ran into several issues even following multiple guides that I found online.   Separately I was also informed that HP laptops come preinstalled with keyloggers from the factory.    So I returned my HP laptop and bought a Macbook Pro in its place.  

 I looked up an in-depth guide on how to accomplish my dual boot goal using my Mac.   But it said that even though I was trying to install the Linux on the SSD via USB drive live Linux,  that part of the Lenix would be written on to the Mac hard drive. To fix this and have a true dual boot I would have to do some sort of coding and remove the portion from the Mac hard drive and copy it back onto the SSD. 

 This really just sounds like a lot more headaches and the end result probably won't work.  I'm leaning towards abandoning the Linux idea and just using a Mac for both of my businesses.  

 What do you think? My new MacBook Pro arrives tomorrow in the mail, is it possible to have a true dual boot SSD with Ubuntu  without anything getting copied onto the Mac hard drive? Or should I just stick with the Mac and forget about Linux?

---

### Post by QIII on 2017-12-19
Moved to Apple Hardware Users.

Hello!

That decision is entirely up to you.  It is not for us to decide for you.

Should you decide to install Linux, we're here to help.

---

### Post by johnny5isalive on 2017-12-19
I would like to accomplish my original idea of having a fully functional Linux on an SSD that I could ise to plug into any computer and boot straight to it.  

But I'm not familiar with computer language or coding so if it's a hassle Then maybe its not worth it.  

 Is it possible to copy you Ubuntu onto my external  SSD without copying any linux files onto my brand new Mac hard drive, therby creating another problem to fix?    From what I read that is just "how it goes" but wanted to check with yall and confirm.

---

### Post by QIII on 2017-12-19
I'm not at all familiar with Apple hardware (I toyed around with it a bit around 1983 or so), but the fact that we have this particular sub-forum should give you some indication that you can achieve what you desire.  :)

There is a persistent misconception that one has to be a "coder" to use Linux.  You will likely be asked to run commands (not "codes" as people often misunderstand) in the terminal simply because that is the most convenient and basic way to do things. The terminal obviates the need for detailed knowledge of every one of dozens of desktop environments.  But that is not "programming".  It is just telling the computer to do what a button click might do -- but with much finer control.

I'm sure someone will be by in time to help you out.

---

### Post by yancek on 2017-12-19
> Separately I was also informed that HP laptops come preinstalled with keyloggers from the factory

Gross exaggertion from whoever you got that info.  The link below explains that there was software on the various HP computers which could be used in that fashion if someone with "admin" or "root" privileges and password made the change.  Still, you would expect better from a company like HP.

[http://fortune.com/2017/12/12/hewlett-packard-keystroke-logging-laptop-synaptics/](http://fortune.com/2017/12/12/hewlett-packard-keystroke-logging-laptop-synaptics/)

The problem you will have with a Mac is that it used UEFI and the part of Ubuntu that would be written to the Mac drive would be the UBuntu efi files which are placed on a separate EFI partition on the first drive.  That would be in a separate folder on the EFI partition and would not overwrite any of the Mac efi files.   You may be able to create an EFI partition on the ssd and install Ubuntu there with it's EFI files.  That would mean that when you want to boot Ubuntu, you would have to enter the BIOS each time and make that selection from the boot menu.  You would certainly have to use the manual installation option when installing as that is not the default.

The link below is the official Ubuntu documentation on dual booting or installing UEFI.  Ignore the references to windows.  I don't know that there would be much difference on a Mac as opposed to a PC and the EFI options would be the same.  Doubt you would have to worry about Secure Boot.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

EFI partitions are very small, usually 500mb or less so only a small part of that would be your Ubuntu files on the MAc drive.  Mac home computer make up a very small portion of the total home computer users, probably no more than linux so you are not likely to find much in the way of tutorials online.  No real incentive for Linux developers.  Read the link I posted and maybe try an online search for dual booting Ubuntu UEFI on a MAC and see what you can find.

---

### Post by DuckHook on 2017-12-19
I think you've been misled by a lot of misinformation:

[LIST=1]
[*]Firstly, I highly doubt that HP makes laptops preinstalled with keyloggers. At worst, their products might be slightly easier for scoundrels to subvert, but if they came with keyloggers, they would be begging for a lawsuit that would bankrupt them.
[*]Many people install a complete Linux OS onto a removable drive without any bits resident on their fixed HDD/SSD.
[/LIST]
Both QII and yancek have given you good advice and technical solutions.

I'm more concerned about the more fundamental question behind your questions—as it were. At the risk of presumption: you seem to be very hesitant to work with Ubuntu/Linux in general. Yet, you are asking about a rather complex install onto external media on a new laptop that just might have (not necessarily has) incompatible components. You also imply that this will be a production laptop (you state that it's for business). Given the assumed critical nature of this system and your utter lack of familiarity with Linux, are you sure you want to tackle the learning curve under such circumstances?

I personally think that Ubuntu is more fun than flying monkeys and that Linux has been one of the best gifts to humanity. But it is unwise to assume that it has no learning curve, or that you won't be spending a lot of time getting comfortable with it. A better introduction to Ubuntu might be to do so in your spare time on an older machine that is not critical to anything and that you use for practice.

You might also want to read the link in my sig: Linux is Not Windows

---

### Post by johnny5isalive on 2017-12-19
I understand that Linix will have a learning curve and so will Mac because I have never used Mac. 
But I had a computer savvy friend attempt to do what I want using his mac. And it was unsuccessful after multiple attempts, not to mention he ended up in having to reinstall Mac OS on his computer.  Makes me shy away from my idea.  

I just wanted to see if there was someway to partition the SSD ahead of time so that nothing, not even the EFI got written on the Mac hard drive.

---

### Post by mastablasta on 2017-12-20
apple hardware is very locked down. not only software wise, but also hardware wise. they will want users to buy specially made mac things. one of the reasons i would not touch it. if i had to use one, would just use the OS that came  on it.

---

### Post by johnny5isalive on 2017-12-20
Ok thanks.  I think thats what im gonna do.  My buddy was apparently testing it out more last night and ran into corruption issues and he said I should just forget my idea and use mac os only

---

### Post by kevin160 on 2017-12-26
> **mastablasta said:**
> apple hardware is very locked down. not only software wise, but also hardware wise. they will want users to buy specially made mac things. one of the reasons i would not touch it. if i had to use one, would just use the OS that came  on it.

What?!  

Locked down?  Like how Ubuntu only boots in Secure UEFI on all modern PCs because Microsoft said it's okay and let them have a certificate?  Nope, Macs don't have that problem.  

Specially made Mac things?  Can you give one example?  

Yes, there have been some issues getting Ubuntu to run properly on some recent models, but I understand those have mostly been resolved except for sound and suspend/hibernation.  Apparently they even have the new touch bar working.  That kind of thing is true of most new hardware on PC laptops, too.  Linux drivers are almost always a year behind.  

Having said that, the OP is probably better off starting by running Linux inside VirtualBox.  But that's true of anybody new to Linux.

---

