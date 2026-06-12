---
title: "Mactel Support community created"
date: 2008-02-15
forum: Apple Intel Users
---

### Post by Seq on 2008-02-15
Hello,

After much discussion regarding "Mactel" support in ubuntu, two new teams and one project have been created in Launchpad:

[LIST]
[*][[SIZE=3]**Mactel Support Community**[/SIZE]]("https://launchpad.net/~mactel-support-community") - This is an open group for _all_ Mactel users to join, share ideas, find and report bugs, and help with support issues. This is a 'community' where any person with an Intel Mac can feel welcomed and find a friendly atmosphere with help, information, and encouragement. We encourage _anyone_ with a Mac to join this group.
[*][[SIZE=3]**Mactel Support** [/SIZE]]("https://launchpad.net/~mactel-support")- This team will consist of more technical members of the Mactel community that actively fix bugs, develop specialized packages and keep them updated, and create software for Mactel users. A mactel-specific kernel is in work for this archive right now. This team is moderated, meaning that one of the team administrators have to approve your membership. This membership will grant access to contribute to the mactel-support package archive that will hold the specialized software and applications mentioned above._ If you are interested in development activities, creating patches, writing support scripts, documentation, or debugging, then this is the group for you._
[*][COLOR=Red]Note: You _do not_ have to become a member of either of these groups to use the software in the package archive.[/COLOR]
[*][[SIZE=3]**Mactel Support (Project)** [/SIZE]]("https://launchpad.net/mactel-support")- This is a regular project. When you submit bugs in Launchpad, you can indicate "mactel-support" as the affected project. If you come across an existing bug in launchpad that pertains to Linux on Intel based Apple Computers, you can add "mactel-support" to the list of affected projects. This project is owned by the mactel-support team, and members will be notified of new bugs. 
[/LIST]

[COLOR="Red"]Update[/COLOR]: The [mactel-support PPA]("https://launchpad.net/~mactel-support/+archive") is now Active.


Some of the issues I hope for us to solve are the "out of the box" scenarios that may exist in Ubuntu, despite the best efforts of Ubuntu users and developers (Hey, there are lots of types of hardware out there).

One of the issues encountered is that each "mactel" machine has it's own tips and tricks, when essentially each generation are extremely similar (macbook and macbook pro are mostly identical hardware). A Goal of this team is to have a common PPA to provide packages that assist with support for all mactel machines, not just a specific model (Keeping in mind the GPL requirements of the PPA, so we can only do so much regarding certain drivers, etc).

We still need a team plan on how community members will advance to the PPA team. There are probably plenty of other goals and ideas that need to be discussed, so I throw the thread open to you. Please comment and suggest.

---

### Post by cyberdork33 on 2008-02-15
looks good man!

---

### Post by georgezzz on 2008-02-15
Sweet!

---

### Post by unai_goiko on 2008-02-15
I just joined the mactel support comunity at launchpad... should I upgrade to Ubuntu 8.4? 

I know it's still unstable but I usually upgrade to the unstable version 2 months before it's released so it should be about time now :)

---

### Post by Seq on 2008-02-15
> **unai_goiko said:**
> I just joined the mactel support comunity at launchpad... should I upgrade to Ubuntu 8.4? 

I know it's still unstable but I usually upgrade to the unstable version 2 months before it's released so it should be about time now :)

I wouldn't recommend it now if you expect it to work. If you are willing to do a lot of testing/fixing, Suspend has issues, nautilus has issues...

---

### Post by unai_goiko on 2008-02-15
> **Seq said:**
> I wouldn't recommend it now if you expect it to work. If you are willing to do a lot of testing/fixing, Suspend has issues, nautilus has issues...

Sounds like fun! hehe I guess i'll wait a coupe of weeks before upgrading...

---

### Post by robzon on 2008-02-16
Ok, I see there is kernel source in the mactel ppa. Now how do I use it? I can't figure out how to download and build the package..

---

### Post by michelem09 on 2008-02-16
Hi,
thank you for approving my subscription to the community, I'm very interisting in it.

Did someone try to connect to an **Airport Extreme base station** from Ubuntu? I tried with WEP and WPA key but without any luck, NetworkManager always re-ask me the key.
With iwconfig it doesn't work  too.

May be is it a ndiswrapper issue with bcm4328 card?
Thank you again

---

### Post by Seq on 2008-02-16
> **robzon said:**
> Ok, I see there is kernel source in the mactel ppa. Now how do I use it? I can't figure out how to download and build the package..

I'm still working on setting up the packages (I Started with the hardy kernel as it has a binary-custom mactel that works. The build failed, though). I'll be uploading Gutsy packages soon as well.

---

### Post by dancolish on 2008-02-16
Is this a newer version of your patched kernel that will replace the current generic kernel. I updated my kernel after a fresh install yesterday, then tried the wiki article and obviously the kernel patches didn't work because of backdating. Aside from starting over and not updating my kernel, how else can I a new kernel for my mac. Do you recommend a custom local build and applying patches to that? I suspect it would be best to use the mactel kernel that is coming because the group will be supporting it. 

I have a macbook c2d santa rosa. Everything is working except the touchpad features and brightness, sound, etc. function keys. For wifi I'm using nsidwrapper. Graphics are good, Sound is there, have not tried isight or other video stuff.

---

### Post by cyberdork33 on 2008-02-16
> **unai_goiko said:**
> I just joined the mactel support comunity at launchpad... should I upgrade to Ubuntu 8.4? 

I know it's still unstable but I usually upgrade to the unstable version 2 months before it's released so it should be about time now :)
Wow, yea don't do it yet. I have some other hardware running 8.04 right now. I updated this morning and now nautilus won't even start.

> **dancolish said:**
> Is this a newer version of your patched kernel that will replace the current generic kernel. I updated my kernel after a fresh install yesterday, then tried the wiki article and obviously the kernel patches didn't work because of backdating. Aside from starting over and not updating my kernel, how else can I a new kernel for my mac. Do you recommend a custom local build and applying patches to that? I suspect it would be best to use the mactel kernel that is coming because the group will be supporting it.You can do a local compile. It is something that everyone should try anyway. As far as I can tell, the keyboard / touchpad patches have made it into the official mactel-linux patchset, so using that should give you a working touchpad.

Also, maybe you can get Seq to send you the deb, then you can install it, forcing a downgrade.

---

### Post by cyberdork33 on 2008-02-17
i wanted to post some further details about the different teams for clarification.[LIST]
[*][[SIZE=3]**Mactel Support Community**[/SIZE]]("https://launchpad.net/%7Emactel-support-community") - This is an open group for _all_ Mactel users to join, share ideas, find and report bugs, and help with support issues. This is a 'community' where any person with an Intel Mac can feel welcomed and find a friendly atmosphere with help, information, and encouragement. We encourage _anyone_ with a Mac to join this group.
[*][[SIZE=3]**Mactel Support** [/SIZE]]("https://launchpad.net/%7Emactel-support")- This team will consist of more technical members of the Mactel community that actively fix bugs, develop specialized packages and keep them updated, and create software for Mactel users. A mactel-specific kernel is in work for this archive right now. This team is moderated, meaning that one of the team administrators have to approve your membership. This membership will grant access to contribute to the mactel-support package archive that will hold the specialized software and applications mentioned above._ If you are interested in development activities, creating patches, writing support scripts, documentation, or debugging, then this is the group for you._
[*][COLOR=Red]Note: You _do not_ have to become a member of either of these groups to use the software in the package archive.[/COLOR][/LIST]Thanks everyone, I hope this better distinguishes the intention of each group, and outlines the path forward we would like to see. If you have any ideas or projects that you would like to work on, please feel free to share and/or ask for help within these communities and here in the forums.

---

### Post by Seq on 2008-02-17
> **cyberdork33 said:**
> Also, maybe you can get Seq to send you the deb, then you can install it, forcing a downgrade.

I'm having trouble that stumped two guys on #launchpad, and I'm thinking about putting in a bug for it.

I uploaded a 2.6.24 for Hardy to the mactel ppa. This was the same as the one on my ppa, but I made a slight change to i386 platform so it will actually build. Both i386 and amd64 build successfully, but it fails when attempting to transfer from the build system to the repository... No idea what is going on yet.

I wanted to start the PPA with a proper -mactel kernel for gutsy, but for some reason the build fails (both on PPA build system and locally) with no real description of the error ("make[2]: *** [_all] Error 2").

The versioning scheme will be UbuntuVersion~mactelX, where UbuntuVersion is Ubuntu's version (2.6.22-14.51) and X is our revision (added patches, bug fixes, whatever). The ~ actually seems to equate to "less than", so Ubuntu's version is seen as having a higher version than ours. This is great as only our -mactel kernel will be picked up, and any other kernel related packages will be taken from Ubuntu.

Unfortunately, since I haven't gotten the -mactel kernel to build yet for gutsy, I need to upload the one that overrides -generic. I've uploaded it to my personal PPA to ensure it builds and transfers, and will then upload it to the mactel ppa.

---

### Post by Seq on 2008-02-17
I've revised the first post to use cyberdork33's description of the teams. I've also created a project so we can now tag bugs as affecting 'macbook-support'.

The project is owned by the mactel-support team. I'm not sure what we'll utilize this project for, though bug grouping alone is extremely handy. We now have a repository for revision control if we wish to utilize it (I'm not familiar with bzr yet, though).

---

### Post by dancolish on 2008-02-17
> **cyberdork33 said:**
> 
You can do a local compile. It is something that everyone should try anyway. As far as I can tell, the keyboard / touchpad patches have made it into the official mactel-linux patchset, so using that should give you a working touchpad.

Also, maybe you can get Seq to send you the deb, then you can install it, forcing a downgrade.

I have the PPA repos listed in my sources, but the package for .51-mac is not showing. How do I backport my current install to allow this new package to upgrade?

---

### Post by Seq on 2008-02-17
> **dancolish said:**
> I have the PPA repos listed in my sources, but the package for .51-mac is not showing. How do I backport my current install to allow this new package to upgrade?

Due to problems I've been having with the PPAs ([bug 192713]("https://bugs.launchpad.net/bugs/192713")), I've compiled the amd64 kernel and thrown it in my home repository. All files (and the source) are available here:

[http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/](http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/)

---

### Post by dancolish on 2008-02-17
> **Seq said:**
> Due to problems I've been having with the PPAs ([bug 192713]("https://bugs.launchpad.net/bugs/192713")), I've compiled the amd64 kernel and thrown it in my home repository. All files (and the source) are available here:

[http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/](http://packages.cidesign.ca/ubuntu/pool/macbook/l/linux-source-2.6.22/)

Thanks for uploading the packages. I tried to patch the current GIT head kernel, but ran into some trouble with HID patches. They were much older I think.

I will go with these packages instead for the moment. I'm pretty new at kernel compiling so it's been pretty interesting.

---

### Post by dancolish on 2008-02-17
Just wanted to give an update. I tried the new kernel on Seq's personal site. The install went fine, but I ended up without wireless and sound. The wireless error was 
Fatal; module ndiswrapper not found. 
The sound error was a failure to detect the sound device. 
I then decided to uninstall and go back to the wiki kernel. That kernel installed with a consistent panic. Then I upgraded to try and stabilize the system and everything work. I noticed that your modules were installed along with the main generic kernel. I am pretty sure that has a lot to do with it. Is there any specific versioning info I can see that will tell me more about why this worked? I really hate it when things just work...

---

### Post by cyberdork33 on 2008-02-17
> **dancolish said:**
> Just wanted to give an update. I tried the new kernel on Seq's personal site. The install went fine, but I ended up without wireless and sound. The wireless error was 
Fatal; module ndiswrapper not found. 
The sound error was a failure to detect the sound device. 
I then decided to uninstall and go back to the wiki kernel. That kernel installed with a consistent panic. Then I upgraded to try and stabilize the system and everything work. I noticed that your modules were installed along with the main generic kernel. I am pretty sure that has a lot to do with it. Is there any specific versioning info I can see that will tell me more about why this worked? I really hate it when things just work...You will probably have to build ndiswrapper for that kernel unless it is included in his packages as it links against the kernel. The sound one is odd, did you try it with the modprobe option from the wiki?

---

### Post by Seq on 2008-02-18
> **dancolish said:**
> Just wanted to give an update. I tried the new kernel on Seq's personal site. The install went fine, but I ended up without wireless and sound. The wireless error was 
Fatal; module ndiswrapper not found. 
The sound error was a failure to detect the sound device. 
I then decided to uninstall and go back to the wiki kernel. That kernel installed with a consistent panic. Then I upgraded to try and stabilize the system and everything work. I noticed that your modules were installed along with the main generic kernel. I am pretty sure that has a lot to do with it. Is there any specific versioning info I can see that will tell me more about why this worked? I really hate it when things just work...

Which package did you install from there? If you installed the linux-image-2.6.22-14-generic_2.6.22-14.51.mactel0_amd64.deb, you should have sound and ndiswrapper (it replaces the generic kernel with a slightly modified generic kernel).

There will be an issue going forward with the -macbook kernels however. We will have to rebuild linux-restricted-modules and linux-ubuntu-modules to support them (properly). lrm contains non-GPL components and thus can not be put on the ppa. It is a simple update (I've done it for myself). Any ideas?

---

### Post by dancolish on 2008-02-18
> **Seq said:**
> Which package did you install from there? If you installed the linux-image-2.6.22-14-generic_2.6.22-14.51.mactel0_amd64.deb, you should have sound and ndiswrapper (it replaces the generic kernel with a slightly modified generic kernel).

There will be an issue going forward with the -macbook kernels however. We will have to rebuild linux-restricted-modules and linux-ubuntu-modules to support them (properly). lrm contains non-GPL components and thus can not be put on the ppa. It is a simple update (I've done it for myself). Any ideas?

Does that above image have any additional bindings to headers or modules. I only ran the image .deb. Would having a santa rosa chipset effect anything? 

Would it be good to ensure that these patches make it into the main kernel line? If the community reports enough issues and a few members can actually support those issues I would hope they can be merged. I know we loose some ubuntu users to issues like these.

---

### Post by dancolish on 2008-02-18
> **cyberdork33 said:**
> You will probably have to build ndiswrapper for that kernel unless it is included in his packages as it links against the kernel. The sound one is odd, did you try it with the modprobe option from the wiki?

Yes I set the modprobe option correctly and modinfo showed the sound was there. However the actual sound device did not register in Xserver. It could be an issue with Xserver, but when I replaced the kernel with the main line kernel and the mactel headers everything worked again. I am definitely left scratching my head.

---

### Post by Seq on 2008-02-18
> **dancolish said:**
> Does that above image have any additional bindings to headers or modules. I only ran the image .deb. Would having a santa rosa chipset effect anything? 

Until the ppa is fixed, you can add my repository into apt. Please note that this is NOT RECOMMENDED FOR REGULAR PEOPLE. My server could go down, I could have a house fire, etc etc. That is why we are using the PPA. Note that I only build for amd64.

(EDIT: Don't use my personal repository anymore. Please use mactel-support)

> **dancolish said:**
> Would it be good to ensure that these patches make it into the main kernel line? If the community reports enough issues and a few members can actually support those issues I would hope they can be merged. I know we loose some ubuntu users to issues like these.
That's the plan. the trackpad patches are already in hardy's 8.14 kernel.

---

### Post by cyberdork33 on 2008-02-20
I updated the logos and homepages of the launchpad teams. Any suggested changes are welcome.

> **Seq said:**
> We still need a team plan on how community members will advance to the PPA team. There are probably plenty of other goals and ideas that need to be discussed, so I throw the thread open to you. Please comment and suggest.Might I suggest an IRC community meeting or the sort? This might be difficult to arrange given the international cooperation though. Maybe an internet forum is a better platform, but this one is not really right as this would be community discussion, and not a support topic. It would be good to have a discussion of ideas, roadmaps, etc and maybe get some "projects" started. 
Thoughts?

---

### Post by Seq on 2008-02-21
> **cyberdork33 said:**
> I updated the logos and homepages of the launchpad teams. Any suggested changes are welcome.

Might I suggest an IRC community meeting or the sort? This might be difficult to arrange given the international cooperation though. Maybe an internet forum is a better platform, but this one is not really right as this would be community discussion, and not a support topic. It would be good to have a discussion of ideas, roadmaps, etc and maybe get some "projects" started. 
Thoughts?

IRC is a good idea as we can have a more real-time discussion than waiting four or five hours for a reply to a question. Though you hit the problem with the times. I work 0800-1630 in UTC-5, and am easily free for meetings during 1700-2230 UTC-5.

My [PPA bug]("https://bugs.edge.launchpad.net/soyuz/+bug/192713") has been triaged for soyuz 1.2.3, which is unfortunately [slated for March 24]("https://edge.launchpad.net/soyuz/+milestone/1.2.3"). This bug unfortunately freezes my PPA (and the new macbook-support) ppa in it's tracks. If somebody else has registered for a PPA, I would like to see if you can try building and uploading this package (to your ppa) and see if it builds. I would be very interested in the results.

Thanks

---

### Post by cyberdork33 on 2008-02-21
> **Seq said:**
> IRC is a good idea as we can have a more real-time discussion than waiting four or five hours for a reply to a question. Though you hit the problem with the times. I work 0800-1630 in UTC-5, and am easily free for meetings during 1700-2230 UTC-5. Ha I thought you were in the UK, not London, Canada! I am UTC-6 so I can pretty much meet the same times you can. I'd like to hear from others that might want to be in a n online meetup. I was thinking of getting a bot on #mactel-support on freenode.net anyway. 

> **Seq said:**
> My [PPA bug]("https://bugs.edge.launchpad.net/soyuz/+bug/192713") has been triaged for soyuz 1.2.3, which is unfortunately [slated for March 24]("https://edge.launchpad.net/soyuz/+milestone/1.2.3"). This bug unfortunately freezes my PPA (and the new macbook-support) ppa in it's tracks. If somebody else has registered for a PPA, I would like to see if you can try building and uploading this package (to your ppa) and see if it builds. I would be very interested in the resultsYea I  noticed there are quite a number of PPAs down. I do have a PPA registered, so I can try uploading a build, but I am not too sure of the process.

---

### Post by Seq on 2008-02-22
> **cyberdork33 said:**
> Yea I  noticed there are quite a number of PPAs down. I do have a PPA registered, so I can try uploading a build, but I am not too sure of the process.

The launchpad/soyuz guys have fixed the issue with the PPAs (A permanent fix will come later, but this gets us going again)

I've had the PPAs rebuild the kernels, and they are hosted properly. Unfortunately, these are not the most current versions, so I will upload those at about 1700 (UTC-5). Give an hour or two for building, and we should have a functioning PPA tonight.

---

### Post by dmitrijledkov on 2008-02-23
Don't know if this is appropriate but I'd love to see updated config files for 2.6.24 kernel on mactel website. Cause so far I can't find any that work and I don't now linux enough yet to generate my own. Is anybody willing to help me compiling 2.6.24.2 on 1st gen Macbook? =D

---

### Post by cyberdork33 on 2008-02-23
> **dmitrijledkov said:**
> Don't know if this is appropriate but I'd love to see updated config files for 2.6.24 kernel on mactel website. Cause so far I can't find any that work and I don't now linux enough yet to generate my own. Is anybody willing to help me compiling 2.6.24.2 on 1st gen Macbook? =D
all you have to do is get an older kernel and run old config on it to "update" the config. Then you can use it / make adjustments / whatever.

There is a link in the FAQ about building kernels, and it shows you how to do this.

---

### Post by Seq on 2008-02-25
> **dmitrijledkov said:**
> Don't know if this is appropriate but I'd love to see updated config files for 2.6.24 kernel on mactel website. Cause so far I can't find any that work and I don't now linux enough yet to generate my own. Is anybody willing to help me compiling 2.6.24.2 on 1st gen Macbook? =D

If you are modifying Ubuntu's kernel, you can use their .config after applying the mactel changes. There are no updates neccessary.

---

### Post by Seq on 2008-02-25
Good news on the PPA front: Launchpad has a workaround in place to allow us to build packages again.


So going forward, please use the mactel-support PPA:

[SIZE="2"]**Gutsy**[/SIZE]:
```
deb http://ppa.launchpad.net/mactel-support/ubuntu gutsy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu gutsy main
```

What is there:
- _linux-image-2.6.22-14.51.mactel1_: This kernel needs a -mactel variant added. If anybody has some free time and wants to tackle this, please take a shot. I'll be glad to answer questions (my email, jabber/gtalk and msn addresses are listed in my forum profile)
- Soon: the mactel-support packages that I'm testing in Hardy (see below)
- Soon: Backported pommed from hardy

[SIZE="2"]**Hardy**[/SIZE]:
```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

What is there:
- _linux-image-2.6.24-8.14~mactel1_: This kernel has a -mactel variant. It seems to take preference over a similarly-versioned -generic kernel. This has all mactel patches.
- mactel-support-fixes: This provides two packages to fix fnmode (overridden by pommed at the moment anyway) and sound on santa rosa macbooks.
- mactel-support-meta: This provides a "linux-image-mactel" that will always pull the latest -mactel kernel. Also a mactel-support-macbook-v3 package that has some useful depends (the above two -fixes packages, the linux-image-mactel package, and pommed).

---

### Post by cyberdork33 on 2008-02-25
Attempting to get mailing-lists created:
[https://answers.launchpad.net/mailing-list-beta-testers/+question/25599](https://answers.launchpad.net/mailing-list-beta-testers/+question/25599)

Also, mactel kernel is working great on my iMac (not that I expected any different since there are not really any changes that affect my hardware)

---

### Post by alinux on 2008-02-26
Hello All,

I've a problem with my Wifi and ndiswrapper.

Yesterday I've reinstalled Hardy Herron Alpha 5.
After fresh install, firs I've updated my system. Afterwards I've
installed Seq, mactel kernel:

linux-image-2.6.24-8-mactel
linux-headers-2.6.24-8-mactel
mactel-support-fnmode-fix
mactel-support-srosa-sound-fix

Everything is perfect, Fn key, sound!

So I'm trying to install my Wifi card:

```

alinux@MacBook:~/driver/DRIVER$ ls
bcm43xx64.cat  bcm43xx.cat  bcmwl564.sys  bcmwl5.inf  bcmwl5.sys

alinux@MacBook:~/driver/DRIVER$ sudo ndiswrapper -i bcmwl5.inf 
installing bcmwl5 ...

alinux@MacBook:~/driver/DRIVER$ sudo ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present

alinux@MacBook:~/driver/DRIVER$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

alinux@MacBook:~/driver/DRIVER$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

alinux@MacBook:~/driver/DRIVER$ 

```
alinux@MacBook:~/driver/DRIVER$ apt-cache showpkg ndiswrapper-utils-1.9
Package: ndiswrapper-utils-1.9
Versions: 
1.50-1ubuntu1 (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
                  MD5: 34d652c4e1513449cf52ea780b207a82


Reverse Depends: 
  ndisgtk,ndiswrapper-utils-1.9
Dependencies: 
1.50-1ubuntu1 - libc6 (2 2.6.1-1) ndiswrapper-common (0 (null)) perl (0 (null)) ndiswrapper-source (0 (null)) 
Provides: 
1.50-1ubuntu1 - 
Reverse Provides: 
alinux@MacBook:~/driver/DRIVER$ sudo apt-get install ndiswrapper-utils-1.9
[sudo] password for alinux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```


Here is my lspci



```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

[CODE]
I've attached also messages and dmesg log file.

Every help is appreciated ;) Thanks thanks thanks!

---

### Post by cyberdork33 on 2008-02-26
this might be an issue with using the non-generic kernel. Try compiling ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb)

---

### Post by mabovo on 2008-02-26
When it will be released linux-image-2.6.24-10-mactel ?

---

### Post by cyberdork33 on 2008-02-26
> **mabovo said:**
> When it will be released linux-image-2.6.24-10-mactel ?You are going to have to give it time. Seq has to apply patches to the new source, fix any issues (if there are any) and then upload it to the ppa and have it build, and all that around his personal schedule. Personally, I didn't even know that there was a new release yet.

---

### Post by alinux on 2008-02-26
> **cyberdork33 said:**
> this might be an issue with using the non-generic kernel. Try compiling ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb)

Yes, maybe you're right, I've solved that with new ndiswrapper-1.52 stable version.
Everything works... but sometimes NetworkManager crashes... (not very often).

so for the moment solved things on my pc are:

1. Fn - key, other function keys.
2. Sound
3. Wifi
4. Touchpad (almost perfect).

not solved yet:
1. web cam
2. maybe hibernation, and suspend
3. cd-burning (not tested yet).
somthing else ?


Special thanks to cyberdork33 and Seq

---

### Post by Seq on 2008-02-26
> **alinux said:**
> Yes, maybe you're right, I've solved that with new ndiswrapper-1.52 stable version.
Everything works... but sometimes NetworkManager crashes... (not very often).

It is a -generic and -mactel thing. This will be an issue for all restricted-modules, ubuntu-modules... pretty much any third party pre-built module.

I asked for input on how to solve this, but haven't gotten any feedback. Technically, the -mactel and -generic kernels are identical, so modules from -generic will work with -mactel. A possible solution is just making a link to the common -generic addon modules directories (can be a postinst thing) to rebuilding and providing the available packages. Though restricted-modules is ineligible to be on the ppa due to licensing.

Does anybody know how other kernels are handling this?

> **alinux said:**
> so for the moment solved things on my pc are:

1. Fn - key, other function keys.
2. Sound
3. Wifi
4. Touchpad (almost perfect).
Good. Did you use the macbook support package I uploaded that installed the sound fix, or did you do that manually?

> **alinux said:**
> 
not solved yet:
1. web cam
2. maybe hibernation, and suspend
3. cd-burning (not tested yet).
somthing else ?

I haven't messed around with the webcam in a while.

Suspend works (not sure about hibernate, but I would assume). Currently you need to switch to a VT and back to X.org to get the screen re-initialized:
[LIST=1]
[*]Wait a few moments after resume
[*]CTRL+ALT+F1
[*]Wait a few moments
[*]CTRL+ALT+F7 (usually 7. could be 8, 9, etc)
[/LIST]

This was something that you could set on Gutsy with acpi-support (doubleconsoleswitch), but with hardy's switch to pm-utils it looks like this feature was lost. I don't know how to fix the video re-init, and I haven't had enough time to add a VT switch to pm-utils (well I did, but it didn't work...)

> **cyberdork33 said:**
> You are going to have to give it time. Seq has to apply patches to the new source, fix any issues (if there are any) and then upload it to the ppa and have it build, and all that around his personal schedule. Personally, I didn't even know that there was a new release yet.

I didn't know there was either.

---

### Post by cyberdork33 on 2008-02-26
> **Seq said:**
> This was something that you could set on Gutsy with acpi-support (doubleconsoleswitch), but with hardy's switch to pm-utils it looks like this feature was lost. I don't know how to fix the video re-init, and I haven't had enough time to add a VT switch to pm-utils (well I did, but it didn't work...)
The option is still in the acpi-support file... Are you sure they disabled it?

---

### Post by Seq on 2008-02-27
> **cyberdork33 said:**
> The option is still in the acpi-support file... Are you sure they disabled it?

hardy does not actually seem to utilize acpi-support at all for PM anymore. pm-utils is technically superior (and multi-distro, so hopefully more robust as time goes on), but there were a lot of corner cases in acpi-support that are not yet handled.

---

### Post by alinux on 2008-02-27
Today I've installed a new Linux MacBook 2.6.24-10-mactel, and ndiswrapper is gone again :)

```

alinux@MacBook:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

---

### Post by cyberdork33 on 2008-02-27
> **Seq said:**
> hardy does not actually seem to utilize acpi-support at all for PM anymore. pm-utils is technically superior (and multi-distro, so hopefully more robust as time goes on), but there were a lot of corner cases in acpi-support that are not yet handled.Got it. They seemed to have changed a lot of things over to new packages in Hardy. modules-update doesn't work anymore either. and Xorg 7.3 is flaky as I suspected. It was bad enough with the partial upgrade in Gutsy. Screens and Graphics still tends to do more bad than good as well. We may have a long way to go on this release.

> **alinux said:**
> Today I've installed a new Linux MacBook 2.6.24-10-mactel, and ndiswrapper is gone again :)

```

alinux@MacBook:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```
That's normal. Anytime you compile your own kernel module, you will have to rebuild it after upgrading the kernel to link it to the new version. They are getting better support for making this automatic with dkms, but it is still not quite there.

---

### Post by mabovo on 2008-02-27
Madwifi doesn't work with nm-0.7 and I have this situation with Ndiswrapper:

[   38.533454] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   38.533460] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net5416'
[   38.533979] ndiswrapper (load_wrap_driver:112): couldn't load driver net5416; check system log for messages from 'loadndisdriver'
[   38.544390] usbcore: registered new interface driver ndiswrapper

I am stuck wired !

---

### Post by cyberdork33 on 2008-02-27
You have to use a 64bit windows driver in a 64bit linux kernel.

---

### Post by Rog-Mahal on 2008-02-28
Is hardy stable enough to upgrade for my daily-use computer? I'd love to take a crack at some of this new software, but I need to make sure I won't nuke my system.

---

### Post by cyberdork33 on 2008-02-28
> **Rog-Mahal said:**
> Is hardy stable enough to upgrade for my daily-use computer? I'd love to take a crack at some of this new software, but I need to make sure I won't nuke my system.No, it is pretty bad on my iMac and  the Compaq in my signature. I have an old Dell Inspiron 5100 that it runs great on though.

---

### Post by Rog-Mahal on 2008-02-28
blast, oh well. I look forward to the backports to hardy, then. Great job guys!

---

### Post by sidemo on 2008-03-05
Hi

I have a MBP (3rd gen i think. Sept. 07?) I'd like to compile a new kernel but first I have a question. Where can I find the sources? (specific link?) I already edited my sources.list:
```

deb http://ppa.launchpad.net/mactel-support/ubuntu gutsy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu gutsy main

``` 
but there are no sources. Are they not yet up? 
Ah and I have a probelm with pommed v1.15. i can't adjust the volume. Instead of changing my volume it is scrolling on the active page.

Is hardy still that unstable?

thanks

andi

---

### Post by cyberdork33 on 2008-03-05
Hardy is getting much better. I think the next release will be a good one.

---

### Post by Seq on 2008-03-07
> **cyberdork33 said:**
> Hardy is getting much better. I think the next release will be a good one.

On Hardy, you should be able to install "mactel-support-macbook-v3". This will install the fixes that are applicable to this machine (Which is the only one I have to test). So this will give you the current (got the upload working last night) -macbook kernel, a wrapper to utilize Ubuntu's addon packages such as fglrx and ndiswrapper (linux-ubuntu-modules, linux-restricted-modules), the parameter that fixes sound is added, etc. Each of these fixes is it's own package (and can be removed like a regular package) so ideally we could create a "mactel-support-imac-v1" that would automatically fix imac-specific quirks, for example.

Ideally, quirks should be handled automatically by the original programs (alsa should detect that we need the mbp3 option, etc), but short of this at least we will setting up Ubuntu on mactel machines relatively painless.

---

### Post by ReneB on 2008-03-07
> **Seq said:**
> On Hardy, you should be able to install "mactel-support-macbook-v3". This will install the fixes that are applicable to this machine ...

Could you please tell us where to do find this 'mactel-support' item you are referring to?  I'm in the midst of installing Hardy a6 on my MBP (santa rosa) and neither the alternate or reg 64 bit versions are working (yet).  

It's a non-production partition so it's no biggie, but I'm interested in seeing if this will work better for me than my previous setup of Gutsy 64bit install w/the patches and fixes suggested in the wikis, etc. here and elsewhere.  With that setup (and pommed), I had most of what I wanted (backlit, sound, video) working but not any reliable WiFi -- I've got the Atheron (sp?) card, however, and not the Broadcom.

thanks for all your efforts on this!

rene

---

### Post by cyberdork33 on 2008-03-07
[https://launchpad.net/~mactel-support/+archive](https://launchpad.net/~mactel-support/+archive)

You will still have to get things installed before you can use the repository though and that in itself has been difficult in the past on your Machine.

---

### Post by ReneB on 2008-03-07
Thanks Cyberdork!

I had gotten this sort of thing up and running on my prev. Gutsy installed -- thanks to the wiki and tutorials!  I just had to poke around a bit to find the different pieces of information to help me do it. I also ended up trying various permutations of installs and even compiling to make it work.  Whatever I tried, however, I wasn't able to get reliable WiFi.   There's probably a way, but it's beyond  my skills unless I can follow a recipe of sorts.

cheers,

Rene


EDIT:

ahh, now I see the bugs in the mactel support and understand what you mean ... some of the prev. fixes are now broken perhaps. is that what you were referring to Cyberdork?

---

### Post by cyberdork33 on 2008-03-07
> **ReneB said:**
> ahh, now I see the bugs in the mactel support and understand what you mean ... some of the prev. fixes are now broken perhaps. is that what you were referring to Cyberdork?
no, I was saying that getting Ubuntu install (i.e. boot up the live cd, copy files) has been difficult. As I do not have your hardware, I do not know what has and has not been fixed on newer live cds

---

### Post by ReneB on 2008-03-07
So far it's not been much harder then Gutsy. I did have problems booting up from the LiveCD i burned.  I tried the regular desktop installed - twice actually with different burns  -- and the install never got past the install configuration both times. 

Then it worked using the 64 bit alternate install.  I have not messed around with it since, so now all I've got workng is what worked with the alt install  followed by pkg. updates and the ppa addition.  I'm going to see about the brightness, trackpad, and wifi now.

---

### Post by cyberdork33 on 2008-03-09
Added isight-firmware-tools and pommed-1.16 (with support for MacBookAir1,1 MacBookPro4,1 and MacBook4,1) to the mactel-support repository for Hardy

---

### Post by ReneB on 2008-03-12
Hi all:

I had installed Hardy latest vs. when it was released recently. With the help of the guides and other info I gleaned, I was able to get my MacBook Pro Santa Rosa (but it's got an Atheron wireless) working -- except for wireless.  I was able to get the initial PPA Packages installed as well as follow the how tos for pommed, etc.  to get all this working.  Specifically, the graphics were fine, the updated NVIDIA drivers prompted me to install them when I first booted so I had good resolution, and the backlit keyboard and FN keys worked properly for brightness and sound.  

Now, however, something in the recent updates seems to have broken things.  The screen resolution has gone back to something like 800X600 or something ridiculus. It seems it's forgotten the NVIDIA driver, and when I try to manually set it back the available settings don't seem correct.  Also, I've lost the pommed functions I previously had.

 I am not sure what is up, but one clue is that after a recent update of the PPAs a day or so ago is when things broke.  I tried updating today to see if maybe that'd help but I get a message from the Update Manager can't install everything because something is missing.  Right now I'm not on my ubuntu system so I can't look at the exact message. Later I'll check it out and edit this post to add it. I just wanted to put this out there in case it'd be of some use

Thanks

Rene

---

### Post by michelem09 on 2008-03-18
Today I booted my Ubuntu Hardy Heron with the latest 2.6.24-12 Ubuntu kernel and everything seems to work fine without the kernel from the mactel-support.
Touchpad, fn key and sound work. Is it right?

---

### Post by cyberdork33 on 2008-03-18
> **michelem09 said:**
> Today I booted my Ubuntu Hardy Heron with the latest 2.6.24-12 Ubuntu kernel and everything seems to work fine without the kernel from the mactel-support.
Touchpad, fn key and sound work. Is it right?
Do advanced synaptics functions of the touchpad work? Two-finger scrolling, multi-finger tapping, etc?

---

### Post by michelem09 on 2008-03-18
> **cyberdork33 said:**
> Do advanced synaptics functions of the touchpad work? Two-finger scrolling, multi-finger tapping, etc?

Yes, I do. If you need some system informations feel free to ask.

---

### Post by Debilski on 2008-03-18
I can confirm this; touchpad is working the same as on the older mactel kernel.
But on 2.6.24-12 (64bit) wlan does not work for me. Everything was good on 2.6.24-10-mactel but now wlan0 disappeard. I tried reinstalling/recompiling ndiswrapper but it does not help.
iwconfig says just
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

Any ideas? I do not see any error messages either.

---

### Post by michelem09 on 2008-03-18
> **Debilski said:**
> I can confirm this; touchpad is working the same as on the older mactel kernel.
But on 2.6.24-12 (64bit) wlan does not work for me. Everything was good on 2.6.24-10-mactel but now wlan0 disappeard. I tried reinstalling/recompiling ndiswrapper but it does not help.
iwconfig says just
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

Any ideas? I do not see any error messages either.

There is a bug with ndiswrapper and ssb: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558)

You need to remove ndiswrapper and ohci_hcd module then reinsert ndiswrapper first:

sudo modprobe -r ndiswrapper
sudo modprobe -r ohci_chd
sudo modprobe ndiswrapper
sudo modprobe ohci_hcd

---

### Post by mabovo on 2008-03-18
> **cyberdork33 said:**
> Added isight-firmware-tools and pommed-1.16 (with support for MacBookAir1,1 MacBookPro4,1 and MacBook4,1) to the mactel-support repository for Hardy

Any news for MacBook 2,1 with Hardy A6 with 2.6.24-12.22-generic ?
Also the leds of Caps Lock and num lock don't light on. Can be a config problem ?

---

### Post by cyberdork33 on 2008-03-18
> **michelem09 said:**
> Yes, I do. If you need some system informations feel free to ask.
Good to hear... Glad to see that Hardy is coming along quite well.

---

### Post by stefan_dk on 2008-03-20
Hey All!

I have added the the

deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main

lines to /etc/apt/sources.list and updated and upgraded. However, this made no difference. Is there anything else I should do to get the patched kernel?

I'm on a 64 bit gutsy and the newest santa rosa macbook. 

Sorry if the question is too simple :-)

Regards

---

### Post by Seq on 2008-03-20
> **mabovo said:**
> Any news for MacBook 2,1 with Hardy A6 with 2.6.24-12.22-generic ?
Also the leds of Caps Lock and num lock don't light on. Can be a config problem ?

See if you have the mouseemu package installed, and try removing it. I remember this was an issue I had with my old macbook1,1

---

### Post by Seq on 2008-03-20
> **stefan_dk said:**
> Hey All!

I have added the the

deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) gutsy main

lines to /etc/apt/sources.list and updated and upgraded. However, this made no difference. Is there anything else I should do to get the patched kernel?

I'm on a 64 bit gutsy and the newest santa rosa macbook. 

Sorry if the question is too simple :-)

Regards

There is not a patched version of the current Gutsy kernel in the repository. I have not had the time in quite a while to maintain the Gutsy packages, or to test them properly. Unfortunately nobody else has stepped up to take over.

On the bright side, Hardy looks awesome. I'm actually running without the PPA at the moment just to see what is missing. Decent out-of-box experience.

---

### Post by stefan_dk on 2008-03-20
> **Seq said:**
> There is not a patched version of the current Gutsy kernel in the repository. I have not had the time in quite a while to maintain the Gutsy packages, or to test them properly. Unfortunately nobody else has stepped up to take over.

On the bright side, Hardy looks awesome. I'm actually running without the PPA at the moment just to see what is missing. Decent out-of-box experience.

Well, that sounds great, anyway it is about time i try out the bleeding edge new stuff! :-) Thanks for the quick reply!

I'll grab the CD, and try it out first thing tomorrow! Is there a wiki guide (like the gutsy one), or are there anything I should be aware of? Kind of hard(y) to keep track of what is fixed and what is not.. for a n00b anyways =p

Regards

---

### Post by cyberdork33 on 2008-03-20
no new wiki page, but as you find any new information, you can add to the current one.

---

### Post by mkgkg on 2008-03-21
hi, i've installed the alpha 6 with the mactel repo and everything works well, also the wireless using the solution of the bug above.
my sound doesn't work. i've installed from the mactel repo the Sound fix for Santa-Rosa apples and then i reboot but nothing. then i follow the guide for the gutsy installation and i added to :
/etc/modprobe.d/options the follow line:

options snd_hda_intel model=mbp3 
 then i rebooted but nothing.
i'm using macbook santarosa with the newer version of kernel, 12.
Thanks

---

### Post by stefan_dk on 2008-03-21
Ok, so I've installed Hardy and some things work fine and some don't. At the moment i'm having trouble getting ndiswrapper to work... 
ndiswrapper -l yields:

bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)

I compiled ndiswrapper myself, and had no trouble installing it and the bcm driver. However I cannot connect to anything, and I have no wireless interfaces.

Does anyone have any ideas?

Also, to right-click i need to tab with 3 fingers, not 2. How do I change this?

Regards

---

### Post by mkgkg on 2008-03-21
for the wireless: 
install ndiswrapper module from apt. then download the driver from the dell web'site. (look into [https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa))

and then follow this :
Copy from Bug #182716:
To resolve the problem i crate a boot script using this steps:

1) U must create a file in /etc/init.d/ndiswrapper:

sudo nano /etc/init.d/ndiswrapper

1.a) and paste in it this text:

#! /bin/sh
### BEGIN INIT INFO
# Provides: ndiswrapper
# Required-Start:
# Required-Stop:
# Default-Start: S
# Default-Stop:
# Short-Description: enable to load ndiswrapper
# Description: enable to load ndiswrapper
### END INIT INFO

rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe ohci_hcd

############# end file ############

2) then set file access permissions:

sudo chmod 755 /etc/init.d/ndiswrapper

3) check if permissions are ok. Type:

ls -l /etc/init.d/ndiswrapper

[... ]
-rwxr-xr-x 1 root root 4388 2008-02-03 14:57 /etc/init.d/ndiswrapper
[... ]

4) last, create a symbolic link call S99ndiswrapper in the folder /etc/rc2.d, from /etc/init.d/ndiswrapper:

sudo ln -s /etc/init.d/ndiswrapper /etc/rc2.d/S99ndiswrapper

END OF COPY from Bug #182716.

for the two fingers work looks always on the guide linked above

---

### Post by cyberdork33 on 2008-03-21
> **mkgkg said:**
> for the wireless: 
install ndiswrapper module from apt. then download the driver from the dell web'site. Note that the Dell drivers (or any other drivers that have been found) do not work with the latest apple hardware. You have to use the XP driver from the restore dvd.

---

### Post by stefan_dk on 2008-03-21
Thanks for the tip on ndiswrapper, it worked like a charm :-) brilliant!

I have already tried out the Device secition proposed for mouse setup, but it completely messes up the trackpad. Two finger tapping switches workspace, and it's impossible to control the mouse...

Cyberdork, I use the dell driver and I have the newest MacBook (only 2 days old), the Santa Rosa 2.4Ghz. And it seems to work alright! I'll look out for any trouble though...

---

### Post by cyberdork33 on 2008-03-21
> **stefan_dk said:**
> Cyberdork, I use the dell driver and I have the newest MacBook (only 2 days old), the Santa Rosa 2.4Ghz. And it seems to work alright! I'll look out for any trouble though...
That's the Macbook Pro and Macbook Air that are not working with the dell drivers... at least nobody has been able to get them working previously. can you check the output of lspci and see if it says you have rev5 of the broadcom card?

---

### Post by stefan_dk on 2008-03-22
> **cyberdork33 said:**
> That's the Macbook Pro and Macbook Air that are not working with the dell drivers... at least nobody has been able to get them working previously. can you check the output of lspci and see if it says you have rev5 of the broadcom card?

Sure thing:
```

lspci | grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

You wouldn't have a clue as to what my problem is with my trackpad. Using the configuration proposed in the wiki really messes up the behavior! 

Regards

---

### Post by cyberdork33 on 2008-03-23
> **stefan_dk said:**
> Sure thing:
```

lspci | grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```You wouldn't have a clue as to what my problem is with my trackpad. Using the configuration proposed in the wiki really messes up the behavior!
You have the older rev3 card, so the dell driver will work fine for you.

I do not know what your issue is with the touchpad. There was a problem that required a kernel patch with Macbooks, but I think that has all been integrated into Hardy. If the settings in the wiki don't work for you then don't use them! there are many many options, and you can just try the specific ones you want. typing 'man synaptics" in a terminal will give you a description of all available options.

---

### Post by stefan_dk on 2008-03-23
OK, thank you very much or your help :-)

---

### Post by m.musashi on 2008-03-25
I can confirm that the bug script above seems to solve the problem. I have the bcm4328 chip in an iMac g5 and wifi is now working. However, I notice that there is an error on logout (it doesn't last long enough to read clearly) that says something to the effect of
```
module ndiswrapper does not exist in /proc/modules
module ohci_hcd does not exist in /proc/modules
```
Is this important and how would I fix it?

I'm using hardy beta 64bit.

---

### Post by cyberdork33 on 2008-03-25
> **m.musashi said:**
> I can confirm that the bug script above seems to solve the problem. I have the bcm4328 chip in an iMac g5 and wifi is now working. However, I notice that there is an error on logout (it doesn't last long enough to read clearly) that says something to the effect of
```
module ndiswrapper does not exist in /proc/modules
module ohci_hcd does not exist in /proc/modules
```Is this important and how would I fix it?

I'm using hardy beta 64bit.I think you are getting that error message because the system is still trying to unload the modules that it loaded in the first place, but the script already unloaded it. I would ignore it. It should go away then the bug is actually fixed in Ubuntu.

---

### Post by m.musashi on 2008-03-28
> **cyberdork33 said:**
> I think you are getting that error message because the system is still trying to unload the modules that it loaded in the first place, but the script already unloaded it. I would ignore it. It should go away then the bug is actually fixed in Ubuntu.

Thanks.

---

### Post by cyberdork33 on 2008-03-29
The developer of iSight-Firmware-Tools uploaded his latest version of the software to the Mactel-Support PPA which fixes issues with the udev scripts not executing.

---

### Post by cyberdork33 on 2008-03-30
Someone in the Mactel-Linux mailing list is working on a driver for the multitouch touchpads. [http://sourceforge.net/mailarchive/forum.php?thread_name=47EF5BFB.9030503%40gmail.com&forum_name=mactel-linux-users](http://sourceforge.net/mailarchive/forum.php?thread_name=47EF5BFB.9030503%40gmail.com&forum_name=mactel-linux-users)

---

### Post by Romu on 2008-05-13
> **michelem09 said:**
> Hi,
thank you for approving my subscription to the community, I'm very interisting in it.

Did someone try to connect to an **Airport Extreme base station** from Ubuntu? I tried with WEP and WPA key but without any luck, NetworkManager always re-ask me the key.
With iwconfig it doesn't work  too.

May be is it a ndiswrapper issue with bcm4328 card?
Thank you again

Sorry if this post was already answered, but yes I connect with Ubuntu and a Dell PC and my Macbook Pro to an Airport Extreme without any problem.

---

