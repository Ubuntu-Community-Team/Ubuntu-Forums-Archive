---
title: "trying to get XP in VMWare"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2007-10-06
I'm trying to run this HowTo 

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

I've got VMWare Player installed and when I run the VMX I get this error message.

"Cannot open the disk '/home/mds/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file."

Is it simply a matter of changing the permissions for that file (I tried that and I still get the same message). I'm not completely comfortable with how permissions work, so any pointers would be gratefully accepted.

The VMX and VMDK files are in my /home/mds folder.

---

### Post by finer recliner on 2007-10-06
i remember following this tutorial not too long ago. there's a couple minor typos. so make sure you read everything really carefully.

as for the permissions issue:
```

sudo chmod 777 /home/mds/windows.vmdk

```

that will give everyone access to reading/writing/executing the file (probably excessive in this case)

---

### Post by mdsmedia on 2007-10-06
Thanks for that. Didn't seem to make a difference though.

---

### Post by finer recliner on 2007-10-07
in the windows.vmdk file, make sure that you're pointing at the correct drive that has windows installed on it. here's mine:

```

# Disk DescriptorFile
version=1
CID=f344ca40
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowxp.mbr" 0
RW 117210176 FLAT "/dev/sda" 63

# The Disk Data Base
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "scsi"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "7296"

```

in my case, windows is located on /dev/sda
notice i didnt give it a partition number.
also notice that i had to change the adapter type to "scsi" since my drive is a scusi.

also double check to make sure the MBR name matches the one you created (windowxp.mbr)

hope this helps

---

### Post by mdsmedia on 2007-10-07
Thanks, I'll give that a go later.

It really is a pain having to boot into Windows, when I don't want to be there in the first place. ;)

At least in a VM I can get back to productivity a lot quicker.

Seriously though, my email, my calendar, my productivity, are in Linux. I have to boot Windows for my tax software. If clients have sent me info by email and I need to refer to it in preparing their tax return I sometimes have to go backwards and forwards between the 2 or REALISE their info is in the email before I go to Windows.

Thanks again. I hope this works. I'm sure it will. maybe just a little fiddling.

---

### Post by finer recliner on 2007-10-08
just realized what the issue probably is. you need to run vmware player as sudo to open this profile. 

```

gksu vmplayer

```

still double check your .vmdk for the suggestions i posted above as well

---

### Post by homburg on 2007-10-10
I had this error message as well and got rid of it.

In my case I had moved the appliance from a machine to another.

Seems one of the disk associated with the appliance could not be reached, so I opened the appliance in the server management console gui and removed all disks (harddrives, cd-rom's and floppys) from it, except the primary boot partition ofcourse.

I suppose it was only necessary to remove one of the harddrives, but my main goal was just to get rid of the error message and be able to boot the appliance, which I was.

---

