---
title: "Lubuntu install issues..."
date: 2013-05-28
forum: Any Other OS
---

### Post by dtrot55 on 2013-05-28
I have a little Asus EEE PC with a 4gig hard drive that I pretty much inherited because my boss wasn't too impressed with it.  So I have been for awhile now trying to find a Linux Distro I can use that is lightweight and not so resource heavy that the thing won't be able to run.  I have tried some distros already like (Puppee Linux, Peppermint, Linux Mint, Ubuntu remix and nothing has really been a good fix with it.  I wanted to give Lubuntu a try, but I have ran into a snag.  

I tried the live cd, but I can't get past the 4.3gig requirement on the hard drive.  So I tried the Alternate cd and I get to the software selection portion of the the install and then it fails.  So I continue with the install to find that all it did was install bash.  I did ls -a to see if there was a profile structure and I didn't see anything really.  I tried to do a sudo apt-get install lubuntu-desktop but it asked for the disc and it never finds the cdrom.  

Does anyone have some suggestions on what I can do with this computer?  I would assume I would run into the same problem with Xubuntu also, so any help would be much appreciated.

Thanks!

---

### Post by sudodus on 2013-05-28
It should work to install Lubuntu with the alternate iso file. The installer is text only, but the final installed system will be standard Lubuntu with the graphical LXDE desktop environment, and it will occupy approximately 2 GB (half of the available 'disk' space).

The alternate installer uses less temporary space as well as less RAM, and will work where the system is too small to install with the desktop iso. You should use the whole internal drive as the root file system '/', at least if you have 1 GB RAM. And you should add the mount option [FONT=courier new]**noatime**[/FONT] in the file /etc/fstab to decrease the wear of the SSD.

---

### Post by sudodus on 2013-05-28
By the way, how did you install it? From a USB boot drive or from a CD attached via USB?

Which version of Lubuntu did you try (12.04, 12.10, 13.04)?

Anyway, I suggest that you use a USB boot drive and that you select ***no*** extra software (it can be installed later, if you want to).

---

### Post by dtrot55 on 2013-05-28
I used the 13.04 alternate iso.  I told it to use the whole disk.  It then takes me through the process, though it would not give my ethernet an IP address so I setup the wireless and it worked.  Then it starts going through the install process, it then starts to "Receive" 858 packages during the Software Install portion of the install.  It then gets to 858 and the a big red screen pops up saying it failed.  So I selected the next process for it to continue and it finished.  I rebooted and took the disc out and a comman prompt came up for my login.  I entered my login and then got another command prompt as if I as in terminal in a GUI.  So basically it is just a command prompt.  I tried some commands and it didn't really seem like the usual linux structure.  I will try to get more info for you when I get home here shortly.

Thank you for responding :)

---

### Post by sudodus on 2013-05-28
How much RAM is there? You might get problems if less than 512 MB.

1. But first, I suggest that you try to alternate installer again. This time answer "***No*** do not install any new packages and no extra multimedia things". Those things can be installed afterwards, if you need them. And maybe there will be space enough, so that you won't get that big red screen, and that the installation will succeed.

2. If this does not work, I think you can make a persistent live Lubuntu system on a USB pendrive. It is important that the partition(s) on the pendrive do not exceed the space of the SSD (it can be smaller, but not bigger). When you know that the persistent live system works, you can clone it to the SSD drive in the netbook. In order for it to work you need to boot from a second pendrive, and then you can use dd to clone the persistent live system from the pendrive to the SSD drive.

3. Or you can try Knoppix, that often works very well with old computers and small computers. It is designed to be a live or persistent live system, like Puppy (but I like Knoppix more). The persistent live system is called "poor man's install" in the Knoppix world.

---

### Post by dtrot55 on 2013-05-28
I have 1 gig of ram.  This is pretty much the pc I have...except the storage is 4gigs [http://www.asus.com/Eee_Family/Eee_PC_900A/#specifications](http://www.asus.com/Eee_Family/Eee_PC_900A/#specifications)

---

### Post by dtrot55 on 2013-05-28
Here are some screen shots through the process.  I did not see a place to say "Do not install software"

[https://docs.google.com/file/d/0B7y-NZihiXgTUTZLWl90VTdxUUk/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTUTZLWl90VTdxUUk/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTN184WUVoY3dQZ2M/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTN184WUVoY3dQZ2M/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTaFFiQVMzcF9DaGc/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTaFFiQVMzcF9DaGc/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTVnBmYmJ4TWtvMzA/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTVnBmYmJ4TWtvMzA/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTMUs2RktoZ21Ra0k/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTMUs2RktoZ21Ra0k/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTeTBiX2k5T3B5bFU/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTeTBiX2k5T3B5bFU/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTaFRCLU8wYURTejA/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTaFRCLU8wYURTejA/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTR1NiUFF5cnJLbXM/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTR1NiUFF5cnJLbXM/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTYUI4MF9mRjVITnM/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTYUI4MF9mRjVITnM/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTeDlfa2UzbWV2Q28/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTeDlfa2UzbWV2Q28/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTb0ppb2NqaXNuYjg/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTb0ppb2NqaXNuYjg/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTaXZVbDVUVHVvbk0/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTaXZVbDVUVHVvbk0/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTcXJSMWYyRzBSVXM/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTcXJSMWYyRzBSVXM/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTLWdHVjZ4Z1EwdjQ/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTLWdHVjZ4Z1EwdjQ/edit?usp=sharing)
[https://docs.google.com/file/d/0B7y-NZihiXgTN0hCWXY4MXBCd2M/edit?usp=sharing](https://docs.google.com/file/d/0B7y-NZihiXgTN0hCWXY4MXBCd2M/edit?usp=sharing)

---

### Post by Way310 on 2013-05-28
Delete Some Files From The current operating system Try Getting 5-8 Gbs

---

### Post by dtrot55 on 2013-05-28
So I figured I would try something different and went ahead and downloaded  the 12.04 alternate cd and it is now working.  So I am assuming something on the 13.04 alternate cd hated this computer.  I will see if I can update now that the OS is on here.  Thanks for taking the time and helping me.

---

