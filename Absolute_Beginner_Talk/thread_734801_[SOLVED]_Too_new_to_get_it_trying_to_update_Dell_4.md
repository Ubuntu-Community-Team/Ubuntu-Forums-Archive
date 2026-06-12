---
title: "[SOLVED] Too new to get it trying to update Dell 4400 desktop bios on Gutsy."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by valjour on 2008-03-25
Hi-

I got this box about three  months ago reformatted the drive and put on Ubuntu Fiesty without a hitch. Now I've got Gutsy on it and it is not as flexible but I am way pleased to be away from microsludge and learning Ubuntu slowly.
.
 I've read a great deal  and attempted to install all needed "stuff" to update my Dell Dimension 4400 A04 Bios to the latest (A06).  I know on my microsludge Dell 4300  box my last bios update doubled my maximum  memory capacity. I don't know what improvements I may be missing or not.  Machine works fine.  Just want to learn. When I put reading into practice something gets lost.

I don't have floppies but I have cd's.  Is there an easy way to do this thing?  I always want to get the latest updates.  Is it necessary. My machine runs fine.  I am willing to learn.  When I am asked to edit should I use Vi or should I install Emacs?

The first frustration is this...Dell bios page said to type this into terminal... (I assume for repository access via synaptic) Is there a prior step or alteration  that I missed? Same results with sudo...

:~$ wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash
bash: line 226: /etc/apt/sources.list.d/dell-software-temp-bootstrap.list: Permission denied
Downloading GPG key: [http://linux.dell.com/repo/GPG-KEY-libsmbios](http://linux.dell.com/repo/GPG-KEY-libsmbios)
    Importing key.
gpg: no writable keyring found: eof
gpg: error reading `GPG-KEY': general error
gpg: import from `GPG-KEY' failed: general error
GPG-KEY import failed.
   Either there was a problem downloading the key,
   or you do not have sufficient permissions to import the key.
 
I've had trouble importing keys before.  Do I need add something to the third party sources list?.  And isn't the phrasing wrong for Gutsy?  Sometimes I get overwhelmed and don't remember the go arounds that I was learning yesterday much less last month. 

What I have done so far that I can remember (not in any particular order)-

Installed syslinux
installed sysutils
downloaded latest biosdisk from Dell Forum reference to /home and untarred it.
Downloaded A06 Bios to /home
Installed libsmbios1, -lib, -doc, -sxml1
Installed dmidecode
Installed  bootcd, -i386, mkinitramfs
Some gpg installations with no change in the message
Just added debootstrap - same message
There were others that I can not remember.


Seems many ( way more experienced) others  have had problems with upgrading bios. 

I'd be happy just getting downloading keys down and learning how to make myself understood in bash in Gutsy. 

Can someone please help me through the bios upgrade process step by step when I have snares like this.  I often attempt to tackle big jobs because it helps me learn the little details and gain strength.  I am determined. 
.

Thanks,

---

### Post by valjour on 2008-03-25
Trying to troubleshoot I went to Dell repository.
  
 [http://linux.dell.com/repo/software/](http://linux.dell.com/repo/software/)

Notice that Dell repository is a yum repository.  Doesn't that mean RPM? How can I utilize this in deb? Do I need it if I have flash bios and biosdisk on my computer?  Does biosdisk need its own directory?  Trying to work it out while I wait.

Also remembered that I installed tofrodos as well.  I am afraid to utilize most of these tools without guidance.

---

### Post by hyper_ch on 2008-03-25
they do have a debian section, might be that those tools work also under ubuntu.. HOWEVER messing with the bios can render you computer useless. For that I'd rather suggest either getting a debian etch live CD or one of the supported RH/FC live cds and upgrade BIOS from them.

---

### Post by valjour on 2008-03-25
Somehow I stumbled my way to here.  Now I really don't know how to proceed....

pw@pw-desktop:~$ cd biosdisk
bash: cd: biosdisk: No such file or directory
pw@pw-desktop:~$ cd biosdisk-0.75
pw@pw-desktop:~/biosdisk-0.75$ ./ install.sh
bash: ./: is a directory
pw@pw-desktop:~/biosdisk-0.75$ install.sh
bash: install.sh: command not found
pw@pw-desktop:~/biosdisk-0.75$ sh install.sh
cp: cannot create regular file `/boot/memdisk': Permission denied
mkdir: cannot create directory `/var/lib/biosdisk': Permission denied
mkdir: cannot create directory `/usr/share/biosdisk': Permission denied
install: cannot create regular file `/usr/sbin/biosdisk': Permission denied
install: cannot create regular file `/usr/sbin/blconf': Permission denied
install: cannot create regular file `/usr/share/biosdisk': Permission denied
install: cannot create regular file `/etc/biosdisk.conf': Permission denied
install: cannot create regular file `/usr/share/man/man8/biosdisk.8.gz': Permission denied
pw@pw-desktop:~/biosdisk-0.75$ sudo sh install.sh
pw@pw-desktop:~/biosdisk-0.75$ biosdisk mkimage 4400_A06.EXE
Error: You must run /usr/sbin/biosdisk as root
pw@pw-desktop:~/biosdisk-0.75$ sudo biosdisk mkimage 4400_A06.EXE
Error: "4400_A06.EXE" treated as a file, but its not useable/nonexistent
Usage: /usr/sbin/biosdisk [action] [options] /path/fileName[.img|.exe]
  [action]  =  { mkfloppy | mkimage | mkpkg | install | uninstall} 
  [options] =  [-o option ] [-d device] [ -k basimage]
               [-i destination] [--install] [--distro=<distro>]
               [--name=<pkg name>] [--version=<pkg version>]
               [--release=<pkg release>] [--bioslog=<bios changelog>]
               [-h|--help]
pw@pw-desktop:~/biosdisk-0.75$ 



I'll continue on...

---

### Post by hyper_ch on 2008-03-25
```

pw@pw-desktop:~/biosdisk-0.75$ sh install.sh

```

-->

```

pw@pw-desktop:~/biosdisk-0.75$ **sudo** sh install.sh

```

---

### Post by valjour on 2008-03-25
Thanks Hyper Swiss-

My grandfather hailed from the Alps.  I did sudo  that it is just hidden before 

pw@pw-desktop:~/biosdisk-0.75$ sudo sh install.sh
pw@pw-desktop:~/biosdisk-0.75$ biosdisk mkimage 4400_A06.EXE
Error: You must run /usr/sbin/biosdisk as root
pw@pw-desktop:~/biosdisk-0.75$ sudo biosdisk mkimage 4400_A06.EXE
Error: "4400_A06.EXE" treated as a file, but its not useable/nonexistent
Usage: /usr/sbin/biosdisk [action] [options] /path/fileName[.img|.exe]
  [action]  =  { mkfloppy | mkimage | mkpkg | install | uninstall} 
  [options] =  [-o option ] [-d device] [ -k basimage]
               [-i destination] [--install] [--distro=<distro>]
               [--name=<pkg name>] [--version=<pkg version>]
               [--release=<pkg release>] [--bioslog=<bios changelog>]
               [-h|--help]

pw@pw-desktop:~/biosdisk-0.75$ sudo /usr/sbin/biosdisk mkimage /home/pw/4400_A06.exe
[sudo] password for pw:
Error: "/home/pw/4400_A06.exe" treated as a file, but its not useable/nonexistent
Usage: /usr/sbin/biosdisk [action] [options] /path/fileName[.img|.exe]
  [action]  =  { mkfloppy | mkimage | mkpkg | install | uninstall} 
  [options] =  [-o option ] [-d device] [ -k basimage]
               [-i destination] [--install] [--distro=<distro>]
               [--name=<pkg name>] [--version=<pkg version>]
               [--release=<pkg release>] [--bioslog=<bios changelog>]
               [-h|--help]
pw@pw-desktop:~/biosdisk-0.75$ sudo /usr/sbin/biosdisk mkimage -h /home/pw/4400_A06.exe
Error: You do not seem to have specified a BiosExe
Usage: /usr/sbin/biosdisk [action] [options] /path/fileName[.img|.exe]
  [action]  =  { mkfloppy | mkimage | mkpkg | install | uninstall} 
  [options] =  [-o option ] [-d device] [ -k basimage]
               [-i destination] [--install] [--distro=<distro>]
               [--name=<pkg name>] [--version=<pkg version>]
               [--release=<pkg release>] [--bioslog=<bios changelog>]
               [-h|--help]
pw@pw-desktop:~/biosdisk-0.75$ sudo sh install.sh
[sudo] password for pw:


I am having trouble with mkimage command.  I saw the Debian Section in the repository but my browser took a dump early this am- provider is not always up in wee am.

Also read Debian section in biosdisk and it recommended getting kernel-package which I did with all dependencies and recommends. 
Went back to Dell debian repository and downloaded   Packages .gz.gpg and Sources.gz.gpg.  Don't know what to do with them but I have them.  Stopped there with repo dloads.

Should I cd 4400_A06.EXE from my home folder  to put it in at root first or create a root file, say DellBios. for it? Or move it to /tmp?  I think the error message is because bash doesn't like where it lives.



I could just let it sit there for a while.  I don't have to update bios I know but if the circuits fry I have  another box to install and learn linux on anyway. The bios are up to date on that one.)

Thanks Pete

---

### Post by hyper_ch on 2008-03-26
```

Error: You must run /usr/sbin/biosdisk as root

```

---

### Post by valjour on 2008-03-26
Hi hyper-ch,

I am still a little ignorant and new to permissions and the command line.

What I am having trouble doing is figuring out the options I need to utilize with mkimage and where to place the bios because command  said  it cant utilize/read  the DOS file. But I stumbled around and check it out:

pw@pw-desktop:~$ sudo /usr/sbin/biosdisk
[sudo] password for pw:
Usage: /usr/sbin/biosdisk [action] [options] /path/fileName[.img|.exe]
  [action]  =  { mkfloppy | mkimage | mkpkg | install | uninstall} 
  [options] =  [-o option ] [-d device] [ -k basimage]
               [-i destination] [--install] [--distro=<distro>]
               [--name=<pkg name>] [--version=<pkg version>]
               [--release=<pkg release>] [--bioslog=<bios changelog>]
               [-h|--help]
pw@pw-desktop:~$ sudo /usr/sbin/biosdisk mkimage --name=4400_A06.img /home/pw/4400_A06.EXE
+ mkdir -p /tmp/biosdisk
+ cp -f /usr/share/biosdisk/dosdisk.img /tmp/4400_A06.img
+ mount -t vfat /tmp/4400_A06.img /tmp/biosdisk -o loop
+ cp -f /home/pw/4400_A06.EXE /tmp/biosdisk
+ echo '4400_A06.EXE '
+ unix2dos /tmp/biosdisk/autoexec.bat
+ umount /tmp/biosdisk
+ rm -rf /tmp/biosdisk
+ '[' '' == 1 ']'
+ '[' 0 == 1 ']'
+ '[' 0 == 0 ']'
+ echo 'Creating BIOS floppy image at /tmp/4400_A06.img'
Creating BIOS floppy image at /tmp/4400_A06.img
+ '[' 0 == 1 ']'
+ '[' 0 == 1 ']'
+ '[' 0 == 1 ']'
pw@pw-desktop:~$ sudo mv /tmp/4400_A06.img /boot/
[sudo] password for pw:
pw@pw-desktop:~$ sudo cp /usr/lib/syslinux/memdisk /boot/


Now what?  I am blown away that I've figured this much out.

 I've been mixing and matching about five different sources  to figure it out this far.  Don't want to fail now.  I would rather keep this machine running than watch it fry.  Got any suggestions?

My source says that there are only two commands left to boot.  Wish me well.  

A tangential question...My Feisty book tells me to use applications>sys tools>run as another user then utilize the  run box (using xsane as an example).  Did this option leave when i upgraded to Gutsy or is there some option(s)  I have to get to reinstall it?  My apps system tools options consist solely of Apt Key Manager and Gnome PGP both of which I know I installed. Do you have any recommendations for Gutsy  tools...

If you don't hear from me means I failed at my impossible mission;)  Send flowers to the funeral. If all goes well I shall be singing Helvetica uber alles and shooting you a reply.

Anyway you :guitar:    The shadow knows.

Thanks Pete

---

### Post by valjour on 2008-03-27
Hi- 
Now for the tricky part. :confused:

First, an update.   I finally stumbled my way  into root then grub and it was just too difficult for me to figure out how to utilize the kernel and initrd commands. Even as root i could not seem to understand the differences from the bash terminal.  I don't quite get  the command syntax.  Not a good place to hunt and peck around especially in grub.  I'm  military trained and know that one false step there could end my Ubuntu career. 

I'm kinda bummed that I wasn't posting with the bios in place. I need (human) guidance about grub kernel in addition to the help file.  I understand what they want I just don't have the substance to make it happen.  Can't make heads or tails about whether I need the [option] what  [type] and if I need an argument.  All was generic until I started this project. Every article I find in the various communities all have a different approach to updating bios even though they all relate to Dell and use the same tools.

Grub help file  told me that if I use kernel that I will have to reload modules. Does mean I will have to reinstall gutsy from disk?  If so should I backup the whole system to disk?   

Been learning pretty fast but still am not totally self-assured. I realize I am just a baby in the linux realm..

As an after thought do i have to start over as # even though the files are in place?  Is that what you were trying to tell me earlier? I know how to get there now.

Got any pointers to steer me in the right direction? 

Any input you could give would be appreciated when you get the time.

Thanks, Just knowing you're  there, more hyper than me,  has really helped me push myself to expand beyond a totally push button world of make believe microsludge.. 

Now i wait for answers before i get to far ahead of myself.:)

Pete

---

### Post by valjour on 2008-03-28
Hi hyper_ch,

I gave it a day, reviewed what you said and poured over the help and man info.  Then I proceeded.  After I was done and rebooted  my lshw shows this:

 *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 1
          version: A04 (02/12/2002)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification

I went in as root from my Nautilus Terminal.  I utilized the biosdisk install feature.   Does it matter that I wasn't "in the kernel" so to speak?

The version remained the same but the date was not there before.  The exe bios at Dell showed a June 2002 date and a bigger size.  Could it be that  this date was read from  the code or did I fail to update them correctly?  Did I miss something like something that needs editing?  That is a process that I have yet to tackle.  I attempted to run vi once it was a horrible experience. I did not attempt to utilize -bioslog?  

I am sorry when you posted to me days ago in real time my ISP or browser were acting funny.  I could not see your replies and just saw one  that I totally  missed before. 

Thanks for your time and effort in teaching me the ways to bash,

You still rock!

Pete

---

### Post by valjour on 2008-03-29
Redirecting further inquiries to Dell Forum. 

Thanks again Shadow.  My questions are endless but the stupid ones don't get asked at all at this stage in my development.  Thanks for watching me grow. It must bee painful to see my lacks. (The excessive words buy me time to think.)  I'm in that stage where I have to be wild and out of doors.  Just learning what water to drink. Some day I aspire to have a warm wigwam and be a fierce yet helpful warrior too.

---

