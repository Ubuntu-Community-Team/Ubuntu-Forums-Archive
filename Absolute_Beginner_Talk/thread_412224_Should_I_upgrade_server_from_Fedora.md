---
title: "Should I upgrade server from Fedora?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Calash on 2007-04-17
With the upcoming release for Ubuntu I have been wondering if it is time to move another one of my systems to it.

The system in question is a 2ghz AMD system that acts as a file server, MP3 server, test web server, and PVR using MythTV.  Right now it is running Fedora Core 6.

My main problem is that every time I update the system via yum, all the drivers break and I have to spend a few hours reinstalling the updated versions.  On my desktop that is running Ubuntu I have done several updated (2 kernel updates that I can think of) with very few problems.

I guess I have a few questions.

Will I see similar issues to what I see in Fedora if I reload with Ubuntu?  I have a lot more running on that system than my desktop, so it may not be a function of the OS, but of the hardware.

Would Ubuntu Server be better for this type of application?  It is a headless system with auto-login.  I manage it via VNC and SSH.  It does have a wireless keyboard, but trying to use the console on a 20inch tv is not fun :)

Any feedback would be very helpful.

Thanks :)

---

### Post by crispy_420 on 2007-04-18
You may just have the issues in Ubuntu and kernel updates. This is just how linux is no matter the form.

For example, everytime I update a kernel, no gui till I redo my ATI(fglrx) drivers as they are kernel modules. You may have the same issue with your TV tuners and a kernel update.

---

### Post by Calash on 2007-04-19
I did the upgrade of my desktop from Edgy to Feisty last night with no issues at all.....I am very impressed.

Based on that I think I will change my PVR to an Ubuntu build.  From what I have read the Server distro would not be a good choice so I will stick with Desktop.

Thanks for the feedback :)


One other question.  In searching I have read mixed reviews about LinuxMCE.  If I am reading it correctly it installs MythTV as part of it's build...is that correct?  Also, does anybody have any experience with this product?  My concern is that I use this system for other things than just the PVR and I would not want to lose that function.

Worst case I can reload, try it...and if I don't like it reload again :).

---

### Post by igknighted on 2007-04-19
> **Calash said:**
> I did the upgrade of my desktop from Edgy to Feisty last night with no issues at all.....I am very impressed.

Based on that I think I will change my PVR to an Ubuntu build.  From what I have read the Server distro would not be a good choice so I will stick with Desktop.

Thanks for the feedback :)


One other question.  In searching I have read mixed reviews about LinuxMCE.  If I am reading it correctly it installs MythTV as part of it's build...is that correct?  Also, does anybody have any experience with this product?  My concern is that I use this system for other things than just the PVR and I would not want to lose that function.

Worst case I can reload, try it...and if I don't like it reload again :).

You will probably have less trouble with Fedora., because it is already set up.  MythTV is  a PITA with Ubuntu as well.  In Fedora it is also easier to lock the kernel version to your current one, so you won't run into this issue.  Then again, Ubuntu updates the kernel less frequently, so its pick and choose.  Honestly, if you have a setup that works, don't ever upgrade it unless there is a specific feature you need... it causes less issues that way.

All of this said, it is easier to only have to remember one set of commands, so if yuo use Ubuntu for your desktop you might want to follow suit.  I wouldn't just jump ship though, carefully consider your options first.

---

### Post by Calash on 2007-04-20
Well, I could not resist tweaking....so I dug up a hard drive and reimaged that to Feisty.

The base install of MythTV was very painless.  The pvr-150 was supported by the default install, and the front-end apt-get package does all the work for you.

I did have issues with lirc, but I finally found a good tutorial to get me past that :)

I am rebuilding my Samba shares and moving the data back from my backups.

I think I may leave it this way....I really like Ubuntu better than Fedora...just seems to work easier.

Escept for VNC....still having issues with that, but I can use SSH and my wireless keyboard until I get it worked out :)

---

