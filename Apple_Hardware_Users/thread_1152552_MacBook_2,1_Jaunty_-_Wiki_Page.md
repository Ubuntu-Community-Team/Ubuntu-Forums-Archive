---
title: "MacBook 2,1 Jaunty - Wiki Page"
date: 2009-05-07
forum: Apple Hardware Users
---

### Post by tiagobt on 2009-05-07
I noticed there was no wiki page for the MacBook 2,1 in Jaunty, so I decided to create the page myself: **[MacBook 2,1 Jaunty]("https://help.ubuntu.com/community/MacBook2-1/Jaunty")**.

Although I tried to make the instructions as general as possible, my tests were made in Kubuntu. For this reason, it would be nice if someone using Ubuntu could test the instructions and maybe add the missing parts.

Also, there are a few points I'm not very sure about. It would be nice if you guys could help me clarify them:

[LIST=1]
[*]**[Suspend & Hibernate](https://help.ubuntu.com/community/MacBook2-1/Jaunty#Suspend%20&%20Hibernate)**
I placed the script to restart Bluetooth inside /etc/acpi (suspend) and the script to restart appletouch inside /etc/pm (hibernate). The procedure seems to work, but I read somewhere that the scripts inside /etc/acpi are no longer called. Does anyone know if this information is true? Where should I place the scripts?

[*]**[Desktop Effects (Compiz)](https://help.ubuntu.com/community/MacBook2-1/Jaunty#Desktop%20Effects%20(Compiz))**
I listed three options to get 3D acceleration working because I read reports about people using them. However, only the first option (reverting the driver) works for me. Did anyone get the acceleration working properly with the other options in the final release? Should I delete options two and three?

[*]**[External Monitor](https://help.ubuntu.com/community/MacBook2-1/Jaunty#External%20Monitor)**
As I mentioned, I couldn't get the external monitor working while the MacBook screen is off. Am I doing something wrong? Does this mode work at all?

[*]**[iSight](https://help.ubuntu.com/community/MacBook2-1/Jaunty#iSight)**
I couldn't fix the "green capture issue" in Skype, MSN and Cheese. Is this a known bug?

[*]**[Reducing Drive Load/Unload Cycles](https://help.ubuntu.com/community/MacBook2-1/Jaunty#Reducing%20Drive%20Load/Unload%20Cycles)**
Same question I had in "Suspend & Hibernate". Is the script placement correct? I ended up putting the script in four different places, just to make sure. Is that too much?
[/LIST]

Comments and suggestions are also appreciated! :cool:

Thanks,
Tiago

---

### Post by cyberdork33 on 2009-05-08
> **tiagobt said:**
> I couldn't fix the "green capture issue" in Skype, MSN and Cheese. Is this a known bug?

yea pretty much. I think it is an issue with gstreamer. There is a bug report on it.
[https://bugs.edge.launchpad.net/mactel-support/+bug/349255](https://bugs.edge.launchpad.net/mactel-support/+bug/349255)

Also, for iSight, you should add info to the general iSight wiki (since it is the same for pretty much all macs)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)

---

### Post by tiagobt on 2009-05-08
Thanks. I have included links to the iSight wiki page and to the bug report you mentioned.

---

### Post by tiagobt on 2009-05-09
The openSUSE documentation explains how to use **pm-utils**:
[http://en.opensuse.org/Pm-utils](http://en.opensuse.org/Pm-utils)

I think that the scripts in **/etc/acpi** and **/etc/pm** are all executed, but the customized scripts should be placed in **/etc/pm/sleep.d**.

To fix the Bluetooth and appletouch issues, I created the following script:

```
#!/bin/bash
case $1 in
    hibernate)
        echo "Begin HIBERNATE"
        /etc/init.d/bluetooth stop
        modprobe -r appletouch
        echo "End HIBERNATE"
        ;;
    suspend)
        echo "Begin SUSPEND"
        /etc/init.d/bluetooth stop
        modprobe -r appletouch
        echo "End SUSPEND"
        ;;
    thaw)
        echo "Begin THAW"
        modprobe appletouch
        /etc/init.d/bluetooth start
        echo "End THAW"
        ;;
    resume)
        echo "Begin RESUME"
        modprobe appletouch
        /etc/init.d/bluetooth start
        echo "End RESUME"
        ;;
    *)  echo "WRONG!!!"
        ;;
esac
```

I don't think I need any other customized scripts.

Also, I noticed that Ubuntu already comes with a script to fix the drive load/unload cycles. The script is placed in **/etc/acpi/resume.d**, **/etc/acpi/suspend.d** and **/etc/acpi/start.d**.

Do you think this is the correct workaround?

More information about **pm-utils**:
[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html)

---

### Post by tiagobt on 2009-05-13
I think I've figured out some of the issues:
[LIST]
[*] The scripts to reload the drivers after suspend/hibernate should be placed in **/etc/pm/sleep.d**. The idea is that pm-utils will be the default tool to handle these types of configuration in the future. The scripts inside **/etc/acpi** are just there to maintain compatibility. I've updated the Wiki to comply with this information.
[*] Using UXA acceleration mode sometimes works, but, in my experience, the X server freezes frequently, specially in KDE. Actually, the screen freezes almost every time I log into KDE (during the splash screen animation). Reverting the driver seems to be the best option right now.
[*] I found scripts to control the drive load/unload cycles in several locations, making me believe this issue is handled by default in Ubuntu. For this reason, I removed the instructions related to that from the Wiki.
[/LIST]

Tiago

---

### Post by Richardcavell on 2009-05-24
Tiago,

I just installed Ubuntu as a dual-boot system.  I think it would be worthwhile adding some comments about:

- Mapping the keyboard as an Apple keyboard and making the command/enter keys do something useful
- Adding Refit (and making it look snazzy!  I use the icons from this: [http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/](http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/))
- Partitioning and creating a separate swap partition
- Many other things.

Would you mind if I gave it some additions?

Richard

---

### Post by cyberdork33 on 2009-05-26
> **Richardcavell said:**
>  - Mapping the keyboard as an Apple keyboard and making the command/enter keys do something useful
Keyboard mapping stuff should go in the AppleKeyboard wiki:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)
You can reference this wiki in the Macbook wiki page. Also, Command is mapped to SUPER by default. this is the same thing that the WIN key is mapped to on other PC keyboards. Compiz has many shortcuts defined using the command key.

> **Richardcavell said:**
> - Adding Refit (and making it look snazzy!  I use the icons from this: [http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/](http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/))
- Partitioning and creating a separate swap partition
I don't really know if customizing rEFIt belongs in the documentation (as it is not Ubuntu), but you can link to some stuff if you like. Also, installation and partition stuff should go in the installation wiki:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by tiagobt on 2009-05-28
Richardcavell,

Please make all the additions you find necessary. Just remember to put the information in the appropriate wiki page, like cyberdork33 mentioned.

Thanks,
Tiago

---

### Post by cyberdork33 on 2009-05-30
> **tiagobt said:**
> Richardcavell,

Please make all the additions you find necessary. Just remember to put the information in the appropriate wiki page, like cyberdork33 mentioned.

Thanks,
Tiago
yes, thanks for any and all help!

---

