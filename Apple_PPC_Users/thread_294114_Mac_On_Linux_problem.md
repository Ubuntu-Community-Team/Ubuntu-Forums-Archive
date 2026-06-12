---
title: "Mac On Linux problem"
date: 2006-11-06
forum: Apple PPC Users
---

### Post by mph66 on 2006-11-06
Hi,

I've got Ubuntu running nicely.  I've got MoL running nicely.  But when I'm in MoL and I insert my USB drive, it mounts to the Ubuntu desktop.  I need access to this drive via MoL.  I can't seem to get this to happen except by ejecting the disk and reinserting repeatedly until by some miracle, it mounts to the MoL desktop.  Any way I can get the drive to mount to the MoL or Ubuntu desktops by using some command/key combo?

Thanks,

-Marc

---

### Post by cmorgan47 on 2006-11-06
haven't tried a usb drive, but for CDs you have to list the drive as a block device in, i believe, /etc/mol/molrc.osx

think that's where it's listed.

---

### Post by mph66 on 2006-11-07
Yes, I can open the config file and USB devices are enabled, but when I have the MoL window active and insert a USB drive, it mounts to the Linux desktop anyway.  I really, really need to have the drive mount to the Mac desktop (because the Mac OS allows you to print to .pdf AND designate a filename and destination).  I evaluate student work using a locally-stored (USB Drive) web page that I then save as .pdf (so the evaluation cannot be changed by the casual user) and then I can keep a copy locally, and email evaluations to students for feedback, and parents so that they can keep tabs on their kid's progress.  

I've tried other threads here to get Linux working to print to pdf, and that works fine, but it saves work to one destination (a folder named PDF in the HOME directory) but then subsequent evaluations overwrite each other.  I need to save files as student names and sort into directories by class periods.

So finding the answer to this question is like a quest for the Holy Grail.  Linux is a great operating system, but it's really difficult to find solutions to simple problems.  I thank you for your response, because it's the closest thing I've come to an answer in the two weeks I've been asking.

-Marc

---

### Post by cmorgan47 on 2006-11-07
without anything to fiddle with here, i can offer a last resort solution.  it ain't pretty.

let the usb mount to linux, copy the contents to a temp folder and share that folder through either samba or NFS to the MOL side.  it's handy to have one of these shares anyways.

i'd like to think there's a way to get OO to save the pdf files in the way you want, but it's something i never need so i can't offer much advice there.

---

### Post by seatea on 2006-11-07
You can print to pdf in ubuntu, or I  can anyway. There is a small box in  the print dialogue page in the upper right hand corner just below the "Properties" box. Check it and  then click "Print"  and it   will ask for a name and location  to save to.

---

