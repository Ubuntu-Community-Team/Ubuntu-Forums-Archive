---
title: "HOW: Existing WinXP in UBUNTU 7.10?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by k.bratovanov on 2007-11-15
Hi. I installed Ubuntu 7.10 (I'm brand new) at my PC and I thing, it's great. But sometimes I need some programs from the old WinXP (with WINE is not possible) and i need to reboot a lot of times. I have already the VirtualBOX, but with them I must install the WinXP again (for the image file). Is it possible to run my existing Win through the VirtualBOX (or another program), or to create a VDI image of my existing installation, without to install VMware?

---

### Post by Nano Geek on 2007-11-15
I don't think you can do that, but you could mount your Windows hard-drive in the VM and copy files over. If you're not sure how to do that then I can show you.

---

### Post by k.bratovanov on 2007-11-15
yes, it will be very nice when you give me a little bit suport in that.
:)

Thank you in advance

---

### Post by smacattack on 2007-11-15
I'm not sure If I understand you correctly but would it suit your purposes to use VM converter perhaps? It converts your existing windows partition into a VM image that you can run with VM server etc... The only thing is that it copies the partition so if space is a concern it may not be for you.

This link may help...

[http://www.howtoforge.com/vmware_converter_windows_linux]("http://www.howtoforge.com/vmware_converter_windows_linux")

---

### Post by Nano Geek on 2007-11-15
Here are the instructions from the VirtualBox manual. > Folder Sharing
      Shared Folders allow you to access files of your host system from within the guest system, much
      like ordinary shares on Windows networks would -- except that shared folders do not need a net-
      working setup. Sharing is accomplished using a special service on the host and a file system driver
      for the guest, both of which are provided by VirtualBox.
      In order to use this feature, the VirtualBox Guest Additions have to be installed. Currently, Shared
      Folders are limited to Windows XP, Windows 2000 and Linux 2.4 and 2.6 guests.
      To declare a folder as shared to VirtualBox, you specify a certain path on the host (which will be-
      come the shared folder) and give it a "share name" that only VirtualBox will use. Using this share
      name, which the VirtualBox Shared Folders service will provide to the guest, a drive letter mapping
      can be performed in the guest.
      Shares are created using the VBoxManage command line interface; see Chapter 7, VBoxManage ref-
      erence. The command is as follows:
      VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "C:\test"
      There are two types of shares:
      1.    VM shares which are only available to the VM for which they have been defined;
      2.    transient VM shares, which can be added and removed at runtime and do not persist after a VM
            has stopped; for these, add the -transient option to the above command line.
      Then, you can mount the shared folder from inside a VM the same way as you would mount an or-
      dinary network share:
                                                • In a Windows guest, use the following command:
  net use x: \\vboxsvr\sharename
  Replace "x:" with the drive letter that you want to use for the share, and sharename with the
  share name specified with VBoxManage.
• In a Linux guest, use the following command:
  mount -t vboxsf [-o OPTIONS] sharename mountpoint
  Replace sharename with the share name specified with VBoxManage, and mountpoint with
  the path where you want the share to be mounted (e.g. /mnt/share). The usual mount rules ap-
  ply, that is, create this directory first if it does not exist yet.
  Beyond the standard options supplied by the mount command, the following OPTIONS are avail-
  able:
  iocharset CHARSET
  to set the character set used for I/O operations (utf8 by default) and
  convertcp CHARSET
  to specify the character set used for the shared folder name (utf8 by default).


---

