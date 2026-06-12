---
title: "How can I access my 2nd HD in my virtual machine?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by nash1 on 2007-10-21
Ok, so I just installed Gutsy today, as well as VMWare Server 1.04.  The virtual OS (XP Pro) is running fine except even after adding the USB controller my virtual machine will not recognize my USB hard drive (Gutsy picks it up without a problem).  I did some digging and it looks like that's out of the question because you can only use USB 1.1 with VMWare Server (if I'm wrong, please tell me how to fix it) and so I took the drive out of the enclosure and hooked it to the ide 0 channel.  I rebooted the virtual machine, but it still doesn't see the HD.  So I turned off the VM and tried to add the HD like I had to add the USB and sound controller.  Everything went well until I tried to add the new physical disk and I get this message:
"Use of this feature is for advanced users only and may cause loss of data or inability to boot, particularly when this raw disk partition is used as the boot device. Only limited support is available for this feature.
For the most current documentation, please see [http://www.vmware.com/info?id=201](http://www.vmware.com/info?id=201) and click the link "Installing an Operating System onto a Physical Partition from a Virtual Machine."" 
I chose to use the entire disk after continuing, and then afterwards I get the message stating "Disk file:  This disk file will store partition access configuration for the selected physical disk as specified for this virtual machine"
After I click next I get a warning stating that I don't have permission to access the file.  All I want to do is get some files off this disk (they're NTFS format) onto my virtual machine.  Can anyone help me?

---

