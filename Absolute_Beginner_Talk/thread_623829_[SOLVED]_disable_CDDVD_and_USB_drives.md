---
title: "[SOLVED] disable CD/DVD and USB drives"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by getut on 2007-11-26
I am trying to use Gutsy in a very tightly controlled environment and I need to somehow disallow access to all removeable drives.

I've tried a couple of ways that I have found via searches both here and Google but they all involve simply stopping automount. The devices are still accessible through nautilus.

I need to disable their access completely except for the root user.

---

### Post by Dr Small on 2007-11-26
For CDROM Drives, you could chmod /usr/bin/eject to 0 for others, but it still doesn't restrict physical access from opening and closing the drive..

---

### Post by CatKiller on 2007-11-26
I thought that this was part of the options in System -> Administration -> Users and Groups?

Otherwise, you could give ownership of those devices to a group that doesn't contain those users as members.

---

### Post by getut on 2007-11-26
No, those options seem to only stop the automounting in gnome. It still shows up in nautilus and then mounts with a desktop icon if you click on it.

I've also tried changing permissions or groups or ownership on /dev/cdrom and all the /dev/usb(x) but the system changes it back and allows access.

I found out about the hidden group called cdrom and I thought wow.. I bet I just remove the user from that group.. but no user except a HAL user is in that group as it is. And that still wouldn't have helped the USB issue.

So changing permissions on the /dev/xxx entry for the device seems the best bet, but it keeps getting over-ridden somehow by the system.

---

### Post by monte48lowes on 2007-11-26
Much as the group cdrom is used for controlling access to the CD-Rom the group plugdev is used to control access to usb storage.

Mike

---

### Post by LowSky on 2007-11-26
You could always disable the CDROM and USB at the BIOS level and password the BIOS. not the best fix but it works.

---

### Post by getut on 2007-11-26
> **monte48lowes said:**
> Much as the group cdrom is used for controlling access to the CD-Rom the group plugdev is used to control access to usb storage.

Mike

Well.. either there is a bug with the system or those groups don't work as I/you think they should.

If you look at those 2 group memberships, there is only one user in the group and it is a user called Hardware Abstraction Layer. Ever removing that user from the groups doesn't fix the issue. It just keeps right on mounting the drives.

These machines are going to auto sign on and be open to everyone, so we need to have a very limited exposure and very tight controls about what can run on the boxes and what can enter and leave the boxes.

---

### Post by Dr Small on 2007-11-26
Are they going to be at a library or something ?

---

### Post by monte48lowes on 2007-11-26
Have you looked into pessulus?

Mike

---

### Post by getut on 2007-11-26
> **monte48lowes said:**
> Have you looked into pessulus?

Mike

No.. but tried it just now and I found no settings having to do with drives or mounting at all other than the ability to restrict access to the drive mounting applet. Which really is not a solution because the drives are AUTO mounting and could be mounted from command line even if they weren't.

To answer Dr. Smalls question... this application is much worse than a library. They are going on a plant floor in a secluded area with 3rd shift employees. In other words... bored people with nothing to do but probe for anything they can mess up on the computers.

We basically want 3 applications to run on these and nothing else and to make it impossible for any data to enter or leave the company through these terminals.

---

### Post by CatKiller on 2007-11-26
Out of interest - my understanding was that it worked as you imagined that it should - have you logged out and logged back in since making the changes to the user groups? I understand that that is when group membership is checked.

---

### Post by Dr Small on 2007-11-26
Oooh. Ok. Well, have you tried going into the user account under System > Administration >  Users & Groups, select Properties > User Priviledges and unchecking "Access External storage devices automatically" ?

---

### Post by getut on 2007-11-26
Catkiller..  yes.. always doing a complete reboot between changes and not getting the effect I was looking for (no drive access).

Dr. Small.. yes.. tried that option also. Basically the effect that setting had was that it stopped auto creating the icon on the desktop when the drive was attached or a CD was put in. The drive still showed up in nautilus and simply clicking the nautilus link caused it to be fully mounted.. still allowing access.

I think I may have a fix,I will post more later after some testing and playing. I found some info about HAL policies. I have foundnothing exactly what I am looking for but I think its enough that I can play and find the exact effect I am looking for.... no removable drive access at all.

---

### Post by poudin on 2007-11-26
could u not signon as root on the systems and check the kernel modules

lsmod

then, could u not remove the modules that allow for usb and cdrom..

rmmod modulename

.maybe a Ubuntu Forum monitor could comment for sure.

as an alterndate...u can run linux on thin client workstations as well...which could restrict what the users can use for devices as well

---

### Post by getut on 2007-11-28
Poudin... I tried that but something in Gutsy immediately reloads the modules. They seem to be forced somehow. Blacklisting modules did not work either.

I finally found the fix to disable the removable drives for a kiosk or locked down corporate environment. The method I found also has the beneficial side effect that they can still be mounted by root/sudo commands, but do not mount for the normal user.

What I found is HAL policies and I did tons of searching and could find no examples of people using the policies to block all removable drive access, but I did find snippets here and there all over the place good enough to put me on the right track.

Disclaimer, the way I will describe below does not seem to be the "recommended" way to use policies. The default policies in Ubuntu Gutsy have a 10osvendor folder and a 20thirdparty folder located in /usr/share/hal/fdi/policies. The 10osvendor folder contains policy files (.fdi) that control how devices are handled by the system... not just drives and media.. but pretty much all hardware such as keyboards and mice, scanners, etc. ObFrom the reading that I did, the 10osvendor polices are not really supposed to be changed, but instead there should be a 30user folder created and cutom policies by the user should be put there. *** I could never get any policy in the 30user folder to take effect. *** I finally ended up editing 20-storage-methods.fdi policy file in the 10osvendor folder and the systems would honor the changes.

Basically I just added the following 6 lines anywhere ABOVE the <!-- udf --> section. Just in case the exact location is critical, I actually added the lines after the <!-- EFI firmware partitions --> section. Here are the 6 lines:
```
      <match key="@block.storage_device:storage.removable" bool="true">
        <merge key="volume.ignore" type="bool">true</merge>
      </match>

      <match key="storage.drive_type" string="cdrom">
        <merge key="volume.ignore" type="bool">true</merge>
      </match>
```

Obviously, the first 3 lines take care of USB drives, the second 3 takes care of optical devices. There is very likely a cleaner way to do this. If anyone knows please provide input to the thread, but otherwise, this worked for me and hopefully can help someone else.

---

### Post by monte48lowes on 2007-11-30
Glad you got it working the way you wanted. :guitar:

Mike

---

