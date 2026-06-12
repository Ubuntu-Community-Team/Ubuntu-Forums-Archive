---
title: "Ubuntu Server AND Workstation"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Burningrush on 2007-08-02
Is it wise to use a server machine as a workstation as well? I want to build a file/email/development server, but I also want to use it as my normal computer.

Do Apache, Samba, SSH, and all other services I will need use up alot of resources?

---

### Post by djchandler on 2007-08-03
> **Burningrush said:**
> Is it wise to use a server machine as a workstation as well? I want to build a file/email/development server, but I also want to use it as my normal computer.

Do Apache, Samba, SSH, and all other services I will need use up alot of resources?

I would think that greatly depends on how much network traffic you expect to handle simultaneously. Also, you didn't mention if this would be on an intranet, or would be accessible to the internet, and what the expected traffic load might be. As for if the resources can coexist on one host and still allow foreground applications to function at a a reasonable speed, the answer would be yes, provided you have one half to a gigabyte or more of memory, unless you are running cpu intensive tasks such as 3D rendering, video editing, and media streaming. On the whole, I do think you will find this easier to do in Linux as opposed to Windows, where one application can hog nearly all cpu time. I have had Samba and Apache both running on a PIII 550 with 512mb ram before, and still had room and cpu cycles to run a web browser, email client, or word processor in the foreground, and was using it to develop blogging skills. I surely did not intend to do any 3D graphics rendering or video work on that particular box. (It has since been re-assigned to hosting an aging collection of SCSI input and storage devices, tape and magneto-optical, that I still need to access occasionally and is running Windows NT 4.0 currently.) But it was on an intranet, and was set up that way for developmental and teaching purposes only, i.e. there is no WAN traffic at all, and the size of the LAN is only 4 computers, and we have a separate JetDirect HP LaserJet, so no computer needs to host a printer.

Please specify your hardware setup as well, so that others can intelligently discuss the issues you intend to deal with. If you are expecting lots of WAN (internet) traffic, I think the answer to your question can vary wildly. A whole rack of servers will only handle a finite number of clients simultaneously, and that is also very much dependent on the upstream speed of the internet connection you have available.

Simply put, your first question begs dozens of additional questions before any definite answer(s) can be given.

DJ

---

### Post by Burningrush on 2007-08-03
> **djchandler said:**
> I would think that greatly depends on how much network traffic you expect to handle simultaneously. Also, you didn't mention if this would be on an intranet, or would be accessible to the internet, and what the expected traffic load might be. As for if the resources can coexist on one host and still allow foreground applications to function at a a reasonable speed, the answer would be yes, provided you have one half to a gigabyte or more of memory, unless you are running cpu intensive tasks such as 3D rendering, video editing, and media streaming. On the whole, I do think you will find this easier to do in Linux as opposed to Windows, where one application can hog nearly all cpu time. I have had Samba and Apache both running on a PIII 550 with 512mb ram before, and still had room and cpu cycles to run a web browser, email client, or word processor in the foreground, and was using it to develop blogging skills. I surely did not intend to do any 3D graphics rendering or video work on that particular box. (It has since been re-assigned to hosting an aging collection of SCSI input and storage devices, tape and magneto-optical, that I still need to access occasionally and is running Windows NT 4.0 currently.) But it was on an intranet, and was set up that way for developmental and teaching purposes only, i.e. there is no WAN traffic at all, and the size of the LAN is only 4 computers, and we have a separate JetDirect HP LaserJet, so no computer needs to host a printer.

Please specify your hardware setup as well, so that others can intelligently discuss the issues you intend to deal with. If you are expecting lots of WAN (internet) traffic, I think the answer to your question can vary wildly. A whole rack of servers will only handle a finite number of clients simultaneously, and that is also very much dependent on the upstream speed of the internet connection you have available.

Simply put, your first question begs dozens of additional questions before any definite answer(s) can be given.

DJ

This is going to be a brand new system - It will (probably) have an AMD 64bit processor of at least 2.0Ghz, at least 1GB of Ram, a 500GB RAID 1 setup and a 256MB NVidia Video card. This machine is primarily meant to be file server, but I would also like to set up a few maiboxes (10 at the most), I won't be hosting any websites on this machine, but FTP would be nice.

This should also be a PHP development server (development only, no actual sites, no real traffic), so I would need Apache, MySQL and PHP.

Apart from it's server duties, I want this machine to be a nice workstation - web surfing, word processing, media playing, email, and I would like to tinker with Compiz Fusion (hence the video card)

Hope this helps - my main concern is system performance while running all the server stuff in the background, and a normal to high amount of regular productivity and entertainment apps on top of everything.

---

